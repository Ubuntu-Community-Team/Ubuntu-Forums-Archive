---
title: "Ubuntu 12.10- No Unity GUI"
date: 2012-10-21
forum: Desktop Environments
---

### Post by JerBear64 on 2012-10-21
I recently upgraded from 12.04 to 12.10. After logging on, I found that all of my items from 12.04 were still there, but the Launcher and the top bar were gone. Application top bars were also missing. After doing a fresh install, I still have these problems. I'm convinced that it's a problem with my graphics card. :mad:

Computer specs:
Dell Dimension 3000
Intel Pentinum 4 Processor
Radeon 9200 PRO (According to the Windows ATI Catalyst Control Center, I have two of these)

Partitions:
Ubuntu 12.10 (Fresh Install )
Memtest86+
Windows XP Professional (just in case WINE won't load an app)

---

### Post by puntigamer on 2012-10-22
It's maybe because the system tries to install new AMD/ATI drivers, which no longer support your card (I'm not sure if your VGA is supported or not). I had the same problem! Give this PPA a try! ;) [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
This will downgrade X and patch the legacy ATI driver to go with 3.5 Linux :)

I hope that this will solve your problem!

---

### Post by JerBear64 on 2012-10-22
My 12.10 disk finished reburning literally as I typed this post. Once I install it, I will try what you suggested.

---

### Post by JerBear64 on 2012-10-22
Unfortunately, that did not work. After installing, GRUB won't load Ubuntu, and I had to start Ubuntu via Recovery Mode. Unity still is not showing up.
My card is VGA compatible, if that has anything to do with it.

---

### Post by Cenko on 2012-10-23
Can it be that one needs to install the linux-source before the drivers, so that the new drivers kernel module are built?

```
sudo apt-get install linux-source
```

I installed fglrx-legacy after linux-source and got my top bar and launcher. But it is horribly slow, and almost unusable.

---

### Post by JerBear64 on 2012-10-23
Which graphics card do you use? If it's almost unusable on one of the HD ones, then I'm pretty much screwed with my computer.

---

### Post by Cenko on 2012-10-23
> **JerBear64 said:**
> Which graphics card do you use? If it's almost unusable on one of the HD ones, then I'm pretty much screwed with my computer.

I have radeon HD 3100. Any idea for any fix?

---

### Post by IWantFroyo on 2012-10-23
Try running:
```
sudo apt-get install unity
```
To see what will happen.

For now, it might be easier for you to use some other DE, such as Gnome-shell.
```
sudo apt-get install gnome-shell
```

Good luck!

---

### Post by stinkfoot on 2012-10-23
> **IWantFroyo said:**
> Try running:
```
sudo apt-get install unity
```
To see what will happen.

For now, it might be easier for you to use some other DE, such as Gnome-shell.
```
sudo apt-get install gnome-shell
```

Good luck!

Have the same problem no unity sidebar and no topbar
tryed sudo apt-get install unity. 

got the following

unity is already the newest version
you might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
libsane:i386 :Depends: libtiff5:i386 (>4.0.0-1~) but is not going to be installed
libtiff4: Depends: libjbig0:i386 but is not going to be installed
E:Unmet dependencies. Try 'apt-get -f install' with no packages ( or specify a solution).

---

### Post by JerBear64 on 2012-10-23
Update Manager told me there are updates. Turns out it was a whole Compiz update. I installed them and restarted the computer. No difference. In Recovery Mode, however, Unity shows up, although it is slow and almost unusable, like mentioned earlier.
I've installed GNOME via apt-get install gnome-panel. How would I add later versions of GNOME other than GNOME Classic?
Also, I'm glad that people are taking the initiative to try to get Unity working. :D

---

### Post by aloced on 2012-10-24
I have the same issue with ubuntu 12.10.  I can not get the top or side bars.

I have no physical monitor since I'm using a VPS and I'm running tightVNC on windows 7 (32 bit version). I use fireSSH to get a shell.

On tightVNC I do a backgroud but no sidebar/launcher or topbar.

I can right click the mouse and get the popup to change the desktop background (which i can change) - hence, I can also get the "all settings" in that popup.  

I can also press f3 and get the nautilus file viewer.

I'm hoping their is a solution or maybe i should just blow everything away and use 12.04...I'm thinking about it.

---

### Post by JmCourir on 2012-10-26
Hi! 
Same issue here when I put my monitors in multiple display. :( 

Hope someone will find out what to do ... 
JmCourir

---

### Post by aloced on 2012-10-28
I'm using a VNC with a VPS.

And I finally got the classic gnome desktop to work by placing

gnome-session --session=gnome-classic &  

in the ~/.vnc/xstartup file.  

BUT I THINK the overall issue for everyone - YOU ARE NOT LOGGED in.  (i.e. It will not show the top and side bar/launcher).

I think this because when I log out of classic gnome it exhibits the original problem (no bars or launcher). 

I'm sure someone knows how to get the login screen to popup so you can login.  I'm not sure how.

---

### Post by sturdy on 2012-11-03
Had this problem for several days after upgrade from 12.04 to 12.10. I have an ATI HD3850 vid card and puntigamer had the answer

[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

...worked for me but I'm getting rather tired of these constant fglrx issues with every upgrade. Now to remember until the next upgrade :(

---

### Post by drazen167 on 2013-01-04
I had this same problem with my laptop(vostro 3550 and ATI/AMD graphics card).
You have to reset the graphics settings to view the upper bar and dash.
type this in terminal : "sudo software-properties-gtk"
Go to "Additional Driver tab" and
then choose the first option (X.org X Server).
Then Reboot.
I hope this solves the problem.

---

### Post by MathieuDude on 2013-03-29
I understand but how can i get to cmd/console, I just got ubuntu on my older computer to test it out and to run a server on but i encountered this problem. BTW im using the windows installer and not a disk. I'm trying the 12.04 LTS but if you could get back to me soon that would be amazing.

Thanks,

MathieuDude

*EDIT*

Could you pm me the anwser??

---

