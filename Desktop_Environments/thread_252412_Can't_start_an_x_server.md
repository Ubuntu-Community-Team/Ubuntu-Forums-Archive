---
title: "Can't start an x server"
date: 2006-09-06
forum: Desktop Environments
---

### Post by RuarriS on 2006-09-06
I tried to install the official Nvidia drivers using this Envy script found [here]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html"). 

But during installation it erased all my other nvidia-glx drivers, but could not complete the installation of the new ones because it said another x server was running, and to close that one. Well i didn't know how to do that, so i just rebooted and the same thing happens, even when I use the official installer from nvidia.com

Anyone know how I can install some drivers so i can get back to a graphical interface?

---

### Post by Anduu on 2006-09-07
Boot into recovery mode from grub and run the script from there.

---

### Post by RuarriS on 2006-09-07
alright that got me a litttle farther, but now it says that it can't find the kernel source files which i think i installed the right ones. It says something about setting the path with the command --kernel-sources-path but I don't know what to do witht that. Any suggestions

---

### Post by Anduu on 2006-09-07
I am not sure where to go from here as I don't have an NVidia card...all i can suggest is make double/triple sure you have the right kernel modules and maybe fire an email or pm to Aalberto...he is quite a helpful guy around these parts ;)

---

### Post by hraposo on 2006-09-07
Try this:
> sudo apt-get remove nvidia-glx linux-restricted-modules-$(uname -r)
sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx


---

### Post by hraposo on 2006-09-07
Try this:
> sudo apt-get remove nvidia-glx linux-restricted-modules-$(uname -r)
sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx


---

### Post by RuarriS on 2006-09-07
I tried both the commands you suggested:
sudo apt-get remove nvidia-glx linux-restricted-modules-`unname -r`
sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx

but it says:

Package linux-restricted-modules-2.6.15-26-k7 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source

I'm using an athlon x2 4200 processor with the 2.6.15-26-k7 kernel, so should I just try to use another kernel, and if so how do i do that. Thanks

---

### Post by whizbaby on 2006-09-07
Try **sudo apt-get update** first, then again the commands *hraposo* suggests.

---

### Post by RuarriS on 2006-09-07
Tried that and same results =/

---

### Post by whizbaby on 2006-09-07
I did:
#####@######:~$ **apt-cache showpkg linux-restricted-modules-2.6.15-26-k7**
Package: linux-restricted-modules-2.6.15-26-k7
Versions:
2.6.15.11-3(/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)

Reverse Depends:
  linux-restricted-modules-k7,linux-restricted-modules-2.6.15-26-k7
[b]Dependencies:
2.6.15.11-3 - linux-image-2.6.15-26-k7 (0 (null)) linux-restricted-modules-common (2 2.6.15) module-init-tools (0 (null)) nvidia-kernel-common (0 (null)) nvidia-glx (16 (null)) nvidia-glx-legacy (0 (null)) avm-fritz-firmware-2.6.15-26 (0 (null))[/b]
Provides:
2.6.15.11-3 - nvidia-kernel-1.0.7174 nvidia-kernel-1.0.8762
Reverse Provides:

What if you try to install the packages listed under 'Dependencies'?

---

### Post by whizbaby on 2006-09-07
I did:
#####@######:~$ **apt-cache showpkg linux-restricted-modules-2.6.15-26-k7**
Package: linux-restricted-modules-2.6.15-26-k7
Versions:
2.6.15.11-3(/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)

Reverse Depends:
  linux-restricted-modules-k7,linux-restricted-modules-2.6.15-26-k7
[b]Dependencies:
2.6.15.11-3 - linux-image-2.6.15-26-k7 (0 (null)) linux-restricted-modules-common (2 2.6.15) module-init-tools (0 (null)) nvidia-kernel-common (0 (null)) nvidia-glx (16 (null)) nvidia-glx-legacy (0 (null)) avm-fritz-firmware-2.6.15-26 (0 (null))[/b]
Provides:
2.6.15.11-3 - nvidia-kernel-1.0.7174 nvidia-kernel-1.0.8762
Reverse Provides:

What if you try to install the packages listed under 'Dependencies'?
(I suppose you (or synaptic) didn't comment out *universe* and *multiverse* in the /etc/apt-sources.list)

---

### Post by RuarriS on 2006-09-07
I tried commenting out the universe and multiverse lines in /etc/apt/sources.list, and installing those packages, but when i got to 

apt-get install avm-fritz-firmware-2.6.15-26 

it gave me the same error about being obsoleted or missing.

Edit: i should point out my graphics card is a 6800GS so i didn't attempt the legacy one

---

### Post by whizbaby on 2006-09-07
> **RuarriS said:**
> I tried commenting out the universe and multiverse 
Sorry, you misunderstood me, I didn't want you to comment these out (I wanted to know if you removed the '#' in front of the lines in sources.list). But if the rest didn't spit any errors going on should be okay (don't understand that avm- fritz dependancy anyway). I suppose you tried again to install the restricted-modules after that?

---

### Post by RuarriS on 2006-09-07
No, before when I tried the lines weren't commented out (I added the #'s in, after misreading your post), it still didnt work. I tried again to install the restricted modules, and it either says they are the most up to date.

---

### Post by RuarriS on 2006-09-07
whizbaby, could you post your sources.list, or atleast which repository you found that in? cuz when i run:

apt-cache showpkg linux-restricted-modules-2.6.15-26-k7

it returns:

Reverse Depends:
Dependencies:
Provides:
Reverse Provides:

---

### Post by whizbaby on 2006-09-07
This is my sources.list (removed comments and cd because you've got the same in your's)

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper multiverse main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper multiverse main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

I think you are missing some multiverse stuff (that's where I found it). (besides, you could type each repository in your browser, look in pool and download manually, that's sometimes usefull)
And yes, I'm half a Bratwurst.

---

