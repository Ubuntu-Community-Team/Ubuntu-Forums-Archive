---
title: "Kubuntu Desktop (kubuntu-artwork-usplash)"
date: 2007-03-03
forum: Desktop Environments
---

### Post by nixfreak on 2007-03-03
I tried installing kubuntu desktop on my server which has ubuntu server installed with VHCS

it got terminated coz i had new mails in mail folder, so i chacked them and tried to restart the installation, but i got this error now

I get this when i try to use sudo aptitude upgrade :

```
The following packages have been kept back:
  linux-image-server
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up kubuntu-artwork-usplash (6.06-22) ...
Cannot find /lib/modules/2.6.15-23-server
dpkg: error processing kubuntu-artwork-usplash (--configure):
 subprocess post-installation script returned error exit status 1
Setting up usplash (0.2-4) ...
Cannot find /lib/modules/2.6.15-23-server
dpkg: error processing usplash (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on kubuntu-artwork-usplash; however:
  Package kubuntu-artwork-usplash is not configured yet.
 kubuntu-desktop depends on usplash; however:
  Package usplash is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kubuntu-artwork-usplash
 usplash
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up kubuntu-artwork-usplash (6.06-22) ...
Cannot find /lib/modules/2.6.15-23-server
dpkg: error processing kubuntu-artwork-usplash (--configure):
 subprocess post-installation script returned error exit status 1
Setting up usplash (0.2-4) ...
Cannot find /lib/modules/2.6.15-23-server
dpkg: error processing usplash (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on kubuntu-artwork-usplash; however:
  Package kubuntu-artwork-usplash is not configured yet.
 kubuntu-desktop depends on usplash; however:
  Package usplash is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kubuntu-artwork-usplash
 usplash
 kubuntu-desktop
```

i think i found the solution but it was ine french, so i used google translator to translate it but i dont really get it coz its not in perfect english and im really new at linux, only the 2nd day using linux :(

This is what it said on the site:

```
Errors were met during the execution:
kubuntu-artwork-usplash


In fact there is a double problem:
the first known as:
                        Cannot find /lib/modules/2.6.15-23-server 

the second known as:
                        Errors were met during the execution:
                        kubuntu-artwork-usplash

And of course the first causes the second.

The solution:
                       A priori there is a problem in the /boot/ repertory on the bonds symbolic systems which do not point
                       not on the good version system.  It is necessary to check before doing anything if not it is
                       a réinstall system) .OLALALALLALLALALALALA….
                       To check the version system: uname - R
                       To go to see in the /boot/ repertory, there must be the files: vmlinuz-xxxx, System.map-xxxxxx,
                       config-xxxx, initrd.img-xxxxx with the extension of the version system (raised by the order
                       uname). And with all the blows, the files vmlinuz System.map ..... do not point on the goods
                       files. If such is the case, it is necessary to one by one remove (not rm - RF of dead) the files
                       bonds then to recreate them towards the good system files (NO REBOOT BETWEEN TWO rm and
                       ln)
                       In fact in your /boot/ repertory, the redirections (ln - S) are not done on the good files:
                             ln - S vmlinuz-2.6.15-23-386 vmlinuz
                             ln - S System.map-2.6.15-23-386 System.map
                             ln - S config-2.6.15-23-386 config
                             ln - S initrd.img-2.6.15-23-386 initrd.img


Result after correction:                                   
sudo dpkg --configure - has
Password:
Parameter setting of kubuntu-artwork-usplash (6.06-21)…

Parameter setting of kubuntu-desktop (0.85)…
```


So please tell me how to fix it.

Thanx in advance

Freak

---

### Post by disturbedite on 2007-03-03
well, simply put, it looks as if usplash couldn't find your kernel.  i know you're new to linux, but if you could compile usplash yourself, you could probably pass something like EXPORT=kernel /path/to/kernel.

it looks as if you have to create a symbolic link to your kernel since usplash couldn't find it.  to do that you need to do this command from command line:

ln - S vmlinuz-2.6.15-23-386 vmlinuz
ln - S System.map-2.6.15-23-386 System.map
ln - S config-2.6.15-23-386 config
 ln - S initrd.img-2.6.15-23-386 initrd.img

---

### Post by nixfreak on 2007-03-03
10x alot for the reply

so what should i do use these commands? or compile usplash? (will i have to DL the Usplash source and then compile or is it in Ubuntu repositories?)

---

### Post by disturbedite on 2007-03-03
no, don't worry about compiling, i was referring to that as if you were more experienced.  this can be solved by doing the commands i mentioned.  i've never had any problems with usplash so i'm completely sure where you would have to create the links (via the commands i listed).  you'll have to wait for someone else to comment about that, or figure it out yourself.  sorry...

---

### Post by nixfreak on 2007-03-04
> **disturbedite said:**
> no, don't worry about compiling, i was referring to that as if you were more experienced.  this can be solved by doing the commands i mentioned.  i've never had any problems with usplash so i'm completely sure where you would have to create the links (via the commands i listed).  you'll have to wait for someone else to comment about that, or figure it out yourself.  sorry...


nuthing works :(....i even tried uninstalling it, but still a similar error related to kubuntu-artwork-usplash.....

plz help i dont wanna do another reinstall, im actually runnin 3-4 sites there, so dont wanna reinstall coz then sites go down for a while.

10x

Freak

---

