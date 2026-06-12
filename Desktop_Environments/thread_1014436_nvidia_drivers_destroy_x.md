---
title: "nvidia drivers destroy x"
date: 2008-12-17
forum: Desktop Environments
---

### Post by epotn on 2008-12-17
im trying to install the glx 177 nvidia drivers and i install and activate them but when i restart X, X stops working and im left with the terminal, i was trying to read how to install the drivers and get them to work but nothing seems to really be helping
thanks

---

### Post by p388l3s on 2008-12-17
what errors do you see when you type:

```
startx
```

alternatively if you type ```
dmesg
``` you may also see errors relating to x and why it's not starting, your going to have to troubleshoot the problem a step at a time, first step find out what errors x is throwing out then you can start to understand the problem.

Also see this thread for more help:

[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)

Hope this helps

---

### Post by epotn on 2008-12-17
yea i read that link my problem doesn't seem to be on there it seems that people are having trouble activating they're drivers mine activates but X gets messed up, when i 'startx' it spits out

(EE) Failed to load module "glx" (module does not exist, 0)
Primary Device is not PCI
(EE) No device drivers detected

Fatal server error: no screens found giving up
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): server error

it seems that its not detecting the driver i have installed a couple different ways from the repository, directly downloading the .deb's from nvidia site, so idk i guess im SOL, but how do i revert to the default X replace orginal xorg conf and delete nvidia drivers?

---

### Post by p388l3s on 2008-12-18
The cannot find glx *shouldn't* stop x from starting but the tell-tale is the no screens found, it's probably the wording in the xorg.conf file, next step in troubleshooting this is to post a copy of you xorg.conf here for us to look at.

You can find that in /etc/X11/xorg.conf

if you can post a copy of that it may be a trivial fix to get you back up and running.

---

### Post by dagoth_pie on 2008-12-18
just a suggestion, the graphics card model or at least series would help here, if its too old then it won't run with newer drivers, if its too new, you'll need to manually download and install them, if possible avoid this though, otherwise the ubuntu updates to the kernel will stuff it up unless you wipe the drivers, then install again after the update, try stick to the ubuntu drivers

---

### Post by epotn on 2008-12-18
the xorg.conf is the exact same default one that is created when you first install ubuntu, idk if its different for everyone (im guessing it *is*) but my graphics cards are 2 8800 gtx sli'd, idk i think this is maybe just a weird 8.10 thing cuz i used the nvidia drivers for 8.04 which i think im going to revert to

---

### Post by dagoth_pie on 2008-12-18
well your using the right drivers, although just to point this out, the drivers are all the same, no matter what version of ubuntu you are using, since they are released by nvidia as "binary blobs", the only difference from version to version of ubuntu is the scripts to automatically compile them, so to the best of my knowledge, this is more likely to be a problem in ubuntu that should be fixed so not to many more people run into it...

so one question, are you using envyng, or the built in restricted drivers manager?

---

### Post by epotn on 2008-12-20
the built in restricted by i also tried apt-get then nvidia-xconfig, or w/e but yea the built in restricted driver manager is giving me alot of problems, cuz i had 8.04 and used it for nvidia drivers and it worked but when i upgraded it doesn't

---

### Post by dagoth_pie on 2008-12-20
```
sudo apt-get install envyng-core
sudo envy -t
```
thatll run the envyng program in text mode, as far as i know theres no gtk frontend for it, but its still reasonably simple... if you select 177 i should do fine, ive had to use this for installing the drivers on friends pcs, the graphics driver installer is why i still use 810

---

### Post by Kirky_D on 2008-12-20
The way i've always done it is by downloading the .run file from nvidia's site I usually get the largest one, not sure what the differences are though (this is a handy link by the way: [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606) ) 
Then press Ctrl-Alt-F1 and login with your username and password. Next do 'sudo killall gdm' (if your using kubuntu its kdm and for xfce i think it's xdm, not sure on that one though) 
After that i navigate to where i saved the driver file and run 'sudo sh nvidia-driver-name.run' I then say yes to everything it asks (this includes a new xorg.conf) then when that's done simply type 'sudo gdm' and i'm good to go.

EDIT: it will probably ask you to compile a new kernel module, and for that you need build-essential to be installed: 'sudo aptitude install build-essential'

---

### Post by dagoth_pie on 2008-12-21
> **Kirky_D said:**
> The way i've always done it is by downloading the .run file from nvidia's site I usually get the largest one, not sure what the differences are though

Because of the way Ubuntus updates work its best to avoid doing this, if you use the .run file from the Nvidia site, you'll have to unistall the driver before installing a kernel update, then install it again after, since the kernel updates are simple, in with all the other updates, you'll probably end up forgeting it and clicking "install all updates" then you'll have serious problems, if you've got a geforce 5, 6, 7 or 8 series, its just extra effort, for your particular card, the 177 driver is the one thatll get given if you search on the nvidia site, I'd reccomend the envyng program, at least try it first then use the Nvidia binaries as a last resort

---

