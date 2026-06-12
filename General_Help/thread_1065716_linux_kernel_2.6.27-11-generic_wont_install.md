---
title: "linux kernel 2.6.27-11-generic wont install"
date: 2009-02-10
forum: General Help
---

### Post by bryncoles on 2009-02-10
ok, its been a few days now and no update has fixed the issue. but whenever i install anything, i geta  reboot notification, and an error message, thus:

> E: linux-image-2.6.27-11-generic: subprocess post-installation script returned error exit status 2
E: linux-restricted-modules-2.6.27-11-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

anyone know what my problem is?

im running ibex on a dell inspiron 1525n, preinstalled ubuntu, and yes, ive posted on launchpad about this but no movement there either.

---

### Post by gettinoriginal on 2009-02-10
I am only a user, so don't understand the kernel problems, but have you checked your Software Sources, Updates, to make sure that it says Normal Releases at the bottom ??

---

### Post by bryncoles on 2009-02-10
hiya! yep, im updating for normal releases only... stumped about this but its starting to grate against me... :(

---

### Post by gettinoriginal on 2009-02-10
I am sending a screenshot of my Syanptic, check yours to make sure that linux-restricted-modules are installted properly, and if they are, I would check them for reinstall anyway.
[ATTACH]102875[/ATTACH]

---

### Post by bryncoles on 2009-02-10
clicked for reinstall (good idea... i didnt think of that), but alas, it didnt help! :( bum!

---

### Post by Yellow Pasque on 2009-02-10
> E: linux-image-2.6.27-11-generic: subprocess post-installation script returned error exit status 2
Is there any output before this?
I've seen a lot of people have problems installing kernels because of the nvidia-common script that's installed automatically (even if your system doesn't have nvidia graphics).

---

### Post by bryncoles on 2009-02-10
yeah, i get an error status 2! whats the work-around for it, do you know?

---

### Post by Yellow Pasque on 2009-02-10
> **bryncoles said:**
> yeah, i get an error status 2! whats the work-around for it, do you know?
It depends on what caused the post-install script to fail.
...
> Is there any output before this?

---

### Post by bryncoles on 2009-02-11
sorry for the late reply...

the full error message (after running sudo apt-get install -f) is:

> After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27-11-generic (2.6.27-11.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-11-generic:
 linux-restricted-modules-2.6.27-11-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-11-generic; however:
  Package linux-restricted-modules-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configNo apport report written because the error message indicates its a followup error from a previous failure.
           No apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.11.14); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-11-generic
 linux-restricted-modules-2.6.27-11-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules
E: Sub-process /usr/bin/dpkg returned an error code (1)

does that help any?

---

### Post by Yellow Pasque on 2009-02-11
It looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193439](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193439)

---

### Post by bryncoles on 2009-02-11
ah, thats useful to know. provides a lead at least! but... what to do about it? im not quite sure i follow the thread of what they're talking about in that bug...

---

### Post by bryncoles on 2009-02-13
bump? im still unable to install the new kernel, and if i run any updates / install any software i have to restart my computer, as it tries (and fails) to install the 2.6.27-11 kernel...

---

### Post by bryncoles on 2009-02-14
bump... still got an issue here...

---

### Post by gettinoriginal on 2009-02-14
Found this on another thread, they said it solved it for them:
sudo dpkg --configure --pending
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean

sudo apt-get update
sudo apt-get --reinstall install linux-image-2.6.27-11-generic

---

### Post by bryncoles on 2009-02-14
hiya! thanks for joining me ;)

interesting... this causes me to fall at the first hurdle!

> sudo dpkg --configure --pending

Setting up linux-image-2.6.27-11-generic (2.6.27-11.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-11-generic:
 linux-restricted-modules-2.6.27-11-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-11-generic; however:
  Package linux-restricted-modules-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.11.14); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-11-generic
 linux-restricted-modules-2.6.27-11-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules

and 

> sudo dpkg --configure -a

Setting up linux-image-2.6.27-11-generic (2.6.27-11.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-11-generic:
 linux-restricted-modules-2.6.27-11-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-11-generic; however:
  Package linux-restricted-modules-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.11.14); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-11-generic
 linux-restricted-modules-2.6.27-11-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules

and 

> sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27-11-generic (2.6.27-11.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-11-generic:
 linux-restricted-modules-2.6.27-11-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-11-generic; however:
  Package linux-image-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-11-generic; however:
  PackNo apport report written because the error message indicates its a followup error from a previous failure.
                                No apport report written because the error message indicates its a followup error from a previous failure.
                                                          No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                      No apport report written because MaxReports is reached already
    age linux-restricted-modules-2.6.27-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.11.14); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.27.11.14); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-11-generic
 linux-restricted-modules-2.6.27-11-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules
E: Sub-process /usr/bin/dpkg returned an error code (1)

and... well, im sure you get the idea! im getting the same error messages for each command. not sure what to make of this.... its certainly the most persistent issue ive come across on the 'buntu....

any other ideas? does this error message help illuminate the issue any?

---

### Post by gettinoriginal on 2009-02-14
At your grub splash, do you have an older kernel you can boot from ??

---

### Post by bryncoles on 2009-02-15
yeah, i tread some good advice a while ago about keeping at least 1, maybe 2 old kernels around to boot from, in case issues arise with the new one, so currently im logged in under 2.6.27-9. so, luckily i can still use my machine. 

however, everytime i run an update or try and install something, my computer tries to configure the 2.6.27-11 kernel, fails and requests a restart. thats less than ideal (but at least usable)!

---

### Post by bryncoles on 2009-02-15
... or if no-one can help me get this kernel installed, can we find a way to stop my computer trying to install it every time i run an update / install a new software? and then ill just wait for the next version of the kernel and hope that works... 

its just getting really annoying having to resart my computer everytime i dont actually update it!

---

### Post by kevdog on 2009-02-15
Try this (I've done this for other packages)

sudo aptitude hold 2.6.27-9-generic

I think this will at least prevent synaptic from trying to upgrade the packages.  I think you can do this with syaptic also, but I don't know how.

---

### Post by bryncoles on 2009-02-16
cool, thanks kevdog. if that works it'll tide me over till the next kernel release! before i input that command though, can i just check, how do i undo that command, for when the next kernel is put out and i actually do want to update....?

---

### Post by bryncoles on 2009-02-18
*blush* figured out the answer to my above question by typing ```
man aptitude
``` in the terminal. the answer is 'Yes', the same command but with 'unhold' instead of 'hold' will do it. 

alas, it didnt solve my problem. 

but i scratted around more on the internet, using > 2.6.27-11 generic User postinst hook script [/sbin/update-grub] exited with value 2 ubuntu as my search query, and found this:

[https://lists.ubuntu.com/archives/kernel-bugs/2009-February/047330.html](https://lists.ubuntu.com/archives/kernel-bugs/2009-February/047330.html)

whihc suggested startup manager would be the issue. so i changed the option in startup manager to automatically update boot options, ran sudo apt-get autoremove and it configured fine! 

problem is now solved, and my thanks to evereyone who tried to help me with this! every post you make, whether it solves my problem or not, teaches me something new! ;)

---

