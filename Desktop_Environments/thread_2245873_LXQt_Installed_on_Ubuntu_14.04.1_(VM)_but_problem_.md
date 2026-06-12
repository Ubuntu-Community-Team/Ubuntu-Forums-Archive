---
title: "LXQt Installed on Ubuntu 14.04.1 (VM) but problem with unmet dependencies"
date: 2014-09-26
forum: Desktop Environments
---

### Post by parker-hugh on 2014-09-26
Installed LXQt on Ubuntu 14.04.1 but problem with unmet dependencies

I have created a clean install of Ubuntu 14.04.1 in a VirtualBox on Windows 7 laptop (Dell Vostro 1520) using "Ubuntu-14.04.1-desktop-amd64.iso"

NO "non-free" or "third-party" software selected then update through software updater and reboot

I installed LXQt as instructed on several forums posts....

sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily
sudo add-apt-repository ppa:gilir/q-project
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install lxqt-metapackage    # error encountered after running this code
sudo apt-get install lxqt-panel
sudo apt-get install openbox    

... and error was encountered at the end of the processing of the sudo command indicated above

last few lines of terminal window showed following message….

```
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/sddm_0.0.1~bzr535+201409221547~ubuntu14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
hugh@DELL-VM-3-UBUNTU:~$
```

So I did a reboot and was prompted with message “System program problem detected”  with following message...
 "Sorry, a problem occurred while installing software, Package: sddm 0.0.1-bzr535.... "

When I ran the last sudo command, there is also a problem, here is the output from the terminal window...

```
hugh@DELL-VM-3-UBUNTU:~$ sudo apt-get install lxqt-metapackage
[sudo] password for hugh:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
lxqt-metapackage is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 sddm-theme-maldives : Depends: sddm but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

hugh@DELL-VM-3-UBUNTU:~$ sudo -i
root@DELL-VM-3-UBUNTU:~# apt-get -f install
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sddm
The following NEW packages will be installed
  sddm
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
118 not fully installed or removed.
Need to get 0 B/249 kB of archives.
After this operation, 1,080 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 221765 files and directories currently installed.)
Preparing to unpack .../sddm_0.0.1~bzr535+201409221547~ubuntu14.04.1_amd64.deb ...
Unpacking sddm (0.0.1~bzr535+201409221547~ubuntu14.04.1) ...
dpkg: error processing archive 
/var/cache/apt/archives/sddm_0.0.1~bzr535+201409221547~ubuntu14.04.1_amd64.deb (--unpack):
 trying to overwrite '/etc/dbus-1/system.d/org.freedesktop.DisplayManager.conf', which is 
also in package lightdm 1.10.1-0ubuntu1
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/sddm_0.0.1~bzr535+201409221547~ubuntu14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@DELL-VM-3-UBUNTU:~# 

```

When the login screen appeared, I clicked on the small Ubuntu logo opposite username, then 

I selected the desktop environment from the list “LXQt Desktop.”

I was then prompted with the following message
Welcome to LXQt
Please select your default Window Manager.
Other.  Chose your favourite one.

You will be able to change this any time through
Preferences > Session Settings > Basic Settings

Any idea what might be the problem? I am fairly new to Linux and only know a limited amount of knowledge, but I can usually get by with the help of google.

I was able to shut down the VM and restart and select Ubuntu desktop from the list and was able to use Ubuntu desktop as before except keep getting error message as before so click ok to remove message.

when i logged back into Ubuntu, I ran sudo apt-get update and then upgrade, got following resopnse….

```
hugh@DELL-VM-3-UBUNTU:~$ sudo apt-get upgrade
Reading package lists… Done
Building dependency tree
Reading state information… Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
sddm-theme-maldives : Depends: sddm but it is not installed
E: Unmet dependencies. Try using -f.
hugh@DELL-VM-3-UBUNTU:~$
```

Any idea how to resolve these dependencies?
I chose not to install ANY "non-free" or "third-party" software so not sure what the problem is.

---

### Post by vasa1 on 2014-09-26
So did you then run **sudo apt-get -f install**? And where did you get **sddm-theme-maldives** from?

---

### Post by parker-hugh on 2014-09-27
Thanksk vasa1 for your response. This was a fresh install using "Ubuntu-14.04.1-desktop-amd64.iso" and NO "non-free" or "third-party" software selected during install.

then after reboot all I did was ....

sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily
sudo add-apt-repository ppa:gilir/q-project
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install lxqt-metapackage    # error encountered after running this code
sudo apt-get install lxqt-panel

So I don't know where sddm-theme-maldives came from unless from one of the steps above. Not sure how to resolve this as I'm fairly new to Linux. If anyone can help I would be grateful.

---

### Post by parker-hugh on 2014-09-27
someone else suggested I run following to help resolve this issue...

sudo apt-get -o Dpkg::Options::="--force-overwrite" install sddm

I did this today and after reboot I was able to select LXQt desktop and  managed to get it working. I don't know the details of why it worked as I  am pretty new to linux, but I'm happy with the result.

Many thanks for your help on this.

---

### Post by Mike_Walsh on 2014-09-30
Incidentally, re: your getting the 'error' message coming up again and again...

I've found, myself, that the only way to stop this from happening is to allow the system to go ahead & send the error report; otherwise, it just keeps coming up again, and again, and.....

Regards,

Mike.

---

