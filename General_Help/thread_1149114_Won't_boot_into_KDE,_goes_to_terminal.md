---
title: "Won't boot into KDE, goes to terminal"
date: 2009-05-04
forum: General Help
---

### Post by Sadistic Tribble on 2009-05-04
OK. I have an [_[COLOR="Blue"]MS-1634[/COLOR]_]("http://us.msi.com/NB/product_spec.asp?model=MS-1634") with a Turion 64 X2, 2GB RAM and a 80GB HDD. I just installed Kubuntu 9.04 on the entire system (for those who saw my post earlier today about partitions, I decided to forgo the Windoze install entirely). 

So I got Kubuntu installed, and everything seemed to be working. I installed the ATI Proprietary driver for the Radeon, installed adept (which somehow was not in my original install... just did an apt-get) and downloaded a bunch of packages, mostly games and programming tools.

Now, the system will not boot into KDE. It displays the loading screen, but goes into tty and says something about "softreset failed", "Loading, please wait...", "19+0 records in", "19+0 records out", and some kinit lines (these are
"kinit: name_to_dev_t(/dev/disk/by-uuid/<a bunch of hex numbers>) = dev(8,5)", 
"kinit: trying to resume from /dev/disk/by-uuid/<the same numbers>", and 
"kinit: No resume image, doing normal boot..."). 

It then goes into the terminal, displaying "Ubuntu 9.04 Pascal tty1" (pascal is the computer name), and asking me to login. The terminal seems to be fully functional, it's just not getting into KDE.

I think it was the ATI driver that did it, though, so how do I fix this/ get a different driver?

---

### Post by paradigm2 on 2009-05-04
I'm not very familiar with the newer KDE, but what happens if you go to the terminal it dumps you in and do

```

startx

```

?

---

### Post by Sadistic Tribble on 2009-05-04
Ah- forgot to mention that.

```
Xsession: unable to start X session --- no "/home/sadistictribble/.xsession" 
file, no "/home/sadistictribble/.Xsession" file, no session managers, no window 
managers, and no terminal emulators found; aborting.
```

(line shortened into three lines for clarity)

[EDIT]: After I click "okay", I see (in the terminal again) a bunch of lines reading:
"(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:#:#) found", and differing only in the last numbers, except th very last line, in which the second 0 is a 1.

also, this line
"swlDalGetDisplayIndex:ERROR: The number of Active Displays is 0"
is displayed twice.

---

### Post by paradigm2 on 2009-05-04
> **Sadistic Tribble said:**
> Ah- forgot to mention that.

```
Xsession: unable to start X session --- no "/home/sadistictribble/.xsession" 
file, no "/home/sadistictribble/.Xsession" file, no session managers, no window 
managers, and no terminal emulators found; aborting.
```

(line shortened into three lines for clarity)

[EDIT]: After I click "okay", I see (in the terminal again) a bunch of lines reading:
"(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:#:#) found", and differing only in the last numbers, except th very last line, in which the second 0 is a 1.

also, this line
"swlDalGetDisplayIndex:ERROR: The number of Active Displays is 0"
is displayed twice.

Cute name btw. :)

Well it looks like maybe your x configuration might have gotten all messed up. :(

Check /etc/X11 and see what you have in there.  Specifically:

/etc/X11/xorg.conf
/etc/X11/Xsession.options
/etc/X11/xinit/xinitrc

for a start.  You may want to consider first using the bakup files if present (after saving the current ones in a separate name).  It looks like something got messed up when these programs were installed.....

---

### Post by Sadistic Tribble on 2009-05-04
/etc/X11/xorg.conf
/etc/X11/Xsession.options
/etc/X11/xinit/xinitrc

all exist. Should I post the contents?

I just installed 9.04 today. I'm beginning to think that reinstalling would be easier than trying to fix this...

---

### Post by paradigm2 on 2009-05-04
Here this mighty be easier and more helpful:

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

### Post by paradigm2 on 2009-05-04
> **Sadistic Tribble said:**
> /etc/X11/xorg.conf
/etc/X11/Xsession.options
/etc/X11/xinit/xinitrc

all exist. Should I post the contents?

I just installed 9.04 today. I'm beginning to think that reinstalling would be easier than trying to fix this...

Its up to you on that.  If you don't have a lot on the drive... but it might just be some little simple error.

I'd probably look at the other link I gave.

If nothing else try:

```

sudo dpkg-reconfigure xserver-xorg

```

and give it a shot.

---

### Post by Sadistic Tribble on 2009-05-04
It complains about the keyboard, has me enter a bunch of settings, then dumps me back to the terminal with the message: "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20090504234311".

I don't think I've edited xorg.conf. I've opened it with nano, but haven't saved (or even made) any changes. I did make the backup as suggested in that post.

---

### Post by paradigm2 on 2009-05-04
> **Sadistic Tribble said:**
> It complains about the keyboard, has me enter a bunch of settings, then dumps me back to the terminal with the message: "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20090504234311".

I don't think I've edited xorg.conf. I've opened it with nano, but haven't saved (or even made) any changes. I did make the backup as suggested in that post.

That message indicates that it reconfigured your files and saved a backup copy to the given filename (so that you may get it back, if needed).  Reboot now and see if it worked or is at least getting further.

```

sudo shutdown -r now

```

---

### Post by Sadistic Tribble on 2009-05-04
Nope, no change. Gets to the loading screen, progress bar seems to get to the end, then it's back to the command line.

---

### Post by paradigm2 on 2009-05-04
> **Sadistic Tribble said:**
> Nope, no change. Gets to the loading screen, progress bar seems to get to the end, then it's back to the command line.

Doing these two in order still gets the same?

```

sudo /etc/init.d/kdm start

```

```

startx

```

---

### Post by paydaydaddy on 2009-05-05
Give this a try. It will reset the system to use the default graphics driver.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then run ```
startx
```. Post back with results.

---

### Post by Sadistic Tribble on 2009-05-05
When I try "sudo /etc/init.d/kdm start", it displays 
"stat /usr/bin/kdm: No such file or directory (No such file or directory)
Already running."

When I set it to use the default graphics driver then used startx, it displayed a horribly distorted kubuntu logo across the top of the screen (which is somewhat similar to what it did when I was logging in through KDE). No luck on reboot, though; it does the same thing it's been doing.

[EDIT]- Something interesting, could point to a hardware problem- I was going to uninstall Kubuntu last night so I tried running DBAN to clean up the system. DBAN wouldn't even start, giving me the notorious "finished with non-fatal errors" message.

---

### Post by ooolongT on 2009-05-14
I would like to bump this thread, I am having an identical problem and, although its a new install, I endeavored to get mutt running yesterday (no mean feat) and therefore I would hate to have to reinstall Kubuntu.  

I am at the same place, I have tried everything that was suggested in the thread thus far with the exception of the link that was given to reconfigure xorg.conf.  That was a little over my head and was dated 2005 so when I opened the file nothing looked as described in that post, I think it is all done automatically now.  

Are there any logs or anything else I can post to help resolve this?

---

### Post by winter123 on 2009-05-31
> **paradigm2 said:**
> Cute name btw. :)

Well it looks like maybe your x configuration might have gotten all messed up. :(

Check /etc/X11 and see what you have in there.  Specifically:

/etc/X11/xorg.conf
/etc/X11/Xsession.options
/etc/X11/xinit/xinitrc

for a start.  You may want to consider first using the bakup files if present (after saving the current ones in a separate name).  It looks like something got messed up when these programs were installed.....



BUMP!!! Same issue, however the /X11 folder does not exist. I have ATI as well and kubuntu 9.04.

(This happened right after i uninstalled whatever Power Management software was installed with it because it was "not the default one" in system settings. Doubt it's related but thought i'd throw it here. )

Kubuntu has been working fine for weeks so i don't know what happened if it's not that. Any ideas??

---

### Post by Liametc on 2009-08-09
bump that

am getting the same problems for no reason

i can get into kubuntu through recovery mode on my 2.6.28-11-generic kernel but not the latest one up which i think is 2.6.28.14 

could a kernel update be the problem?

---

### Post by Liametc on 2009-08-09
ok it seems that ive solved it for me

i set up my wacom tablet which involved me having to change the xorg.conf file

i unplugged the wacom tablet before logging in to allow me to charge up my phone

it wasnt until i re-plugged in my wacom tablet and rebooted that it started working properly

i think that if the xserver doesnt see all the things it has listed it doesnt want to play ball

a really annoying problem, with a simple solution. :lolflag: hope this helps somebody

---

