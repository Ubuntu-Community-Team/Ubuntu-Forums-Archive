---
title: "ssh-keygen problem"
date: 2010-12-18
forum: Desktop Environments
---

### Post by tgernon on 2010-12-18
I aplogize in advance if this turns out to be an embarassing newbie question, but I'm running 10.10 via VirtualBox on my Windows 7 machine and have a problem with ssh-keygen. I'm trying to set up keys to use github, but when I run ssh-ketgen to make rsa keys, it puts them in my local directory, nit .ssh. I had to cretae the .ssh directory, and I did a chmod 700 on it, but it still places them local. Is there some environment initialization I missed? Thanks for the help in advance.

---

### Post by 3Miro on 2010-12-18
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You should create the .ssh with the 700 permissions and then give the .ssh folder to the ssh-keygen (according to the HowTo you will prompted on where you want to put the key).

---

