---
title: "hostnamectl changes hostname without sudo"
date: 2016-10-26
forum: Desktop Environments
---

### Post by enpheebled-git on 2016-10-26
If I want to change the hostname on one of my Xubuntu 16.04.1 installations I usually edit /etc/hostname and /etc/hosts, which requires doing the usual 'sudo' to access the files in write mode as both have '-rw-r--r-' permissions.

I recently saw reference to the systemd command 'hostnamectl' which changes the environment variable and edits /etc/hostname at the same time, but I have found that it does not require 'sudo'. I can just enter 'hostnamectl set-hostname <whatever>' in a terminal and the string in /etc/hostname has been changed, without ever being asked for a password.

Is hostnamectl supposed to do that? It means anyone can change the hostname without root access. Surely this should require an admin password to do that.

---

### Post by enpheebled-git on 2016-10-26
A more responsive :D discussion on this issue is at [https://www.linuxquestions.org/questions/linux-software-2/systemd-hostnamectl-changes-hostname-without-sudo-4175592291/](https://www.linuxquestions.org/questions/linux-software-2/systemd-hostnamectl-changes-hostname-without-sudo-4175592291/)

---

### Post by Dennis N on 2016-10-27
I checked **hostnamectl set-hostname** in Fedora, and it required admin. password to use this command, so it may be Ubuntu's policy setting.

---

### Post by enpheebled-git on 2016-10-27
> **Dennis N said:**
> I checked **hostnamectl set-hostname** in Fedora, and it required admin. password to use this command, so it may be Ubuntu's policy setting.

Thanks, it seems increasingly certain that this is only an issue in Ubuntu-derived distros. So far it's been tested on Xubuntu 16.04.1, including a fresh unmodified install, and on Linux Mint 18 (a derivative of Ubuntu 16.04) and in each case this problem exists. Everyone with a non-Ubuntu distro has reported that they don't experience this issue.

I have lodged a bug report at [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1637030](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1637030) but it's marked as 'security private' for now, so it isn't generally accessible.

---

