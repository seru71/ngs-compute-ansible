Intro
--
The code was forked from https://github.com/MonashBioinformaticsPlatform/bio-ansible and adopted to specific needs of 
creating a generic bioinformatics compute environment for ZAO@PIWet


Requirements
--

VM or container with Ubuntu 16.04 and some GBs of root disc space.
A large disc dedicated to NGS data and results is recommended and expected to be mounted in /ngs.
And of course sufficient number of cores and amount of RAM for your analyses.


Setup
--

After creating the target VM/container, SSH to the VM and add your public key to /root/.authorized_keys
Alternatively install (on your machine) sshpass for pass-based SSH:

`apt install -y git sshpass`

Make sure that Python is installed on the VM, and note its IP address (IP_VM). 

Install ansible (on your machine).

`apt install -y git ansible`

Clone this repo and play the book
`git clone git@github.com:seru71/ngs-compute-ansible.git`
`cd ngs-compute-ansible`
`ansible-playbook -u root --private-key=~/.ssh/id_rsa -i [IP_VM], bia-pipeline-env.yml`


Credits
--

99% of the tasks in the playbook come from https://github.com/MonashBioinformaticsPlatform/bio-ansible

Below is an extract of README from that project:
   
 1. You need to manually download some packages that require license agreements.  See `tarballs/README`

 2. There are scripts to download various databases in `scripts/`. These have deliberately not been added to ansible.

 3. Download blast databases

    cd /references/blast
    sudo -u sw-installer $(which update_blastdb.pl) --passive --verbose '.*'


