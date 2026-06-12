---
title: "MATLAB installer script not working"
date: 2010-10-11
forum: Education &amp; Science
---

### Post by SCUEY on 2010-10-11
Hi, I'm trying to install MATLAB on Ubuntu 10.10 and am having trouble getting the installer script to run.  I am using these links as a reference (after trying the MATLAB manual):

[https://help.ubuntu.com/community/MATLAB]("https://help.ubuntu.com/community/MATLAB")
[http://linux.dsplabs.com.au/forums/ubuntu-linux-help/matlab-on-ubuntu-t8.html]("http://linux.dsplabs.com.au/forums/ubuntu-linux-help/matlab-on-ubuntu-t8.html")

I have an ISO, installation key, and license.dat.txt file from my university.  I *have* placed the licence.dat.txt file in my installation directory as the second link suggests.

The result is that I run the install script and it does nothing.  I cannot even run ./install -h to see the help, so something is wrong.

Here are the exact steps I'm taking:

sudo mkdir /mnt/MATHWORKS_R2010A
sudo mkdir /opt/matlab
sudo mount /<path to my ISO> /mnt/MATHWORKS_R2010A -o loop
cd /opt/matlab
sudo sh /mnt/MATHWORKS_R2010A/install



I've also tried changing the permissions of the /mnt/MATHWORKS_R2010A folder to the most favorable possible.  No luck.

Any ideas?  Thanks.

---

