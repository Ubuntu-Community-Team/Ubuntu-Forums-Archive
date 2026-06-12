---
title: "Synaptic broken after attempted OpenOffice 3.1 install"
date: 2009-05-08
forum: General Help
---

### Post by FrogPrince on 2009-05-08
Hi,

I'd already written this, but for some reason it didn't get posted. Never mind, I'll try again...
First of all, I'd like to say that I'm loving this Ubuntu Jaunty. I was a happy Archlinux user and I'd heard all sorts of wonderful reviews of Jaunty so I thought I'd give it a try. The last time I used Ubuntu was Dapper Drake - what progress Ubuntu has made since then! This release is sooo fast and user friendly it's unbelievable! I'd love to shake Shuttlworth and his developers by the hand for this!
Anyway, to my problem. I tried yesterday to install OpenOffice 3.1 but the installation process got stuck and ever since I haven't been able to use Synaptic. Now, before anyone tells me that Ubuntu isn't rolling release and that I should wait for the next Ubuntu, I just want to say that I know that I'm not using Arch anymore and that Ubuntu only provide security updates. The trouble is for me that I have files that won't open with OpenOffice 3.0 due to a bug and I really wanted to install 3.1 for that reason. 
So, I installled by adding the following repositories:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```

Then, after I updated apt my problems started. So, I took out those two repositories and did the following:

```
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```

At first, this seems to work. But whenever I try to use Synaptic it still wants to update Openoffice and hangs. Does anyone know if there's a way to clear this problem without having to reinstall Ubuntu.

Thanks for any help!

---

### Post by salvachn on 2009-05-14
Try:
> sudo apt-get install -f
It may help.

---

### Post by kpkeerthi on 2009-05-14
> **FrogPrince said:**
> 
 But whenever I try to use Synaptic it still wants to update Openoffice and hangs.
I was able to upgrade to Ooo3.1 successfully. I had to do a dist-upgrade instead of upgrade (refer to man page if you want to know the difference)
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

