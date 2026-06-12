---
title: "Computer freezes after monitor turns off"
date: 2012-01-26
forum: Desktop Environments
---

### Post by /dev/random/username on 2012-01-26
So here is my problem...

I used to use Unity as my main DE (Ubuntu 11.10 64bit) obviously.. however its too much hassle for me to use it, so I installed KDE (installed kubuntu-desktop package from Software Center)

Everything is running great until my monitor turns off after 10 minutes of inactivity and pc freezes immediately.. no keyboard/mouse funny thing is music keeps playing in the background.

So far my workaround is to disable "Screen Energy Saving" from Settings > Power Management. I did not have this issue with Unity

System Specs:
AMD Phenom X3 720BE (stock overclock)
4GB DDR3 1333
HD5870
OCZ Vertex2 120GB (Full Disk Encryption)

---

### Post by inobe on 2012-01-26
it may be a conflict between desktops, if you like kubuntu, a full install takes minutes minus backup time.

[http://www.kubuntu.org/](http://www.kubuntu.org/)

there are some nice things about this derivative, the desktop version can be upgraded to the latest and greatest stable release using a ppa, in which of course is 4.8.0, it's came a long way from your current version, however it continues upgrading...


[http://www.kubuntu.org/news/kde-sc-4.8.0](http://www.kubuntu.org/news/kde-sc-4.8.0)

if you need any further advice or have questions, i will be checking back for replies.

---

### Post by /dev/random/username on 2012-01-27
Look like I'll be installing fresh Kubuntu, my concern is the dejapup backup since it backups my home directory and there are Unity files and configurations.. would that conflict with Kubuntu?

---

### Post by inobe on 2012-01-27
just pack up your docs, music, pics etc... and leave:P

---

### Post by gdea73 on 2012-03-09
I have this exact same problem, I can't seem to find any other instances of it.

Running 10.10, the exception is, I never changed desktop environments. Still running Gnome 2. This has only been happening recently though I don't know what caused it as the computer has to be left for a while for it to be fixed. I didn't change anything major nor have I seen any other problems.

---

### Post by Zorael on 2012-03-10
If you have the terminal knowhow, you could try changing to a textual tty terminal when your monitor is turned off like that. Hit **Ctrl+Alt+F1**, and if that doesn't work, **Alt+SysRq+R** first and then retry **Ctrl+Alt+F1**. You should end up with a login prompt. If it works, that may be indicative of a GPU hang or simply X freaking out somehow. Log in.

The log file at **/var/log/Xorg.0.log** may say something of interest. If you don't want to read them in the tty, just copy them to your home directory with '**cp /var/log/Xorg.0.* ~/**'. Likewise, save the output of **dmesg** for later reading by entering something like '**dmesg > ~/dmesg.log**'.

To restart your graphical environment from the textual terminal;
```
$ sudo stop kdm **&&** sleep 10 **&&** sudo start kdm

*#alternatively if using the gdm login manager*
$ sudo stop gdm **&&** sleep 10 **&&** sudo start gdm

*#alternatively if running the lightdm login manager*
$ sudo stop lightdm **&&** sleep 10 **&&** sudo start lightdm
```
It should take 10+ seconds. Note the **double** ampersands (**&&**)! Entering single ones here are bad and will make your system drunk.

(I'd recommend against using **sudo restart** here as it - to my experience - seems to leave some desktop processes like kded4 still running?)

---

### Post by gdea73 on 2012-03-10
thanks for the reply, I'll be sure to try switching to tty1 next time it appears to hang.

my only concern is it seemed to be a complete hang last time I noticed; I couldn't get out of it unless I hard-reset it. No keyboard combinations I tried seemed to do anything, though I haven't tried Ctrl + Alt + F1 yet.

---

### Post by gdea73 on 2012-03-11
Okay, this becomes further confusing. I tried Ctrl + Alt + F1 last time, but the computer was totally frozen. It didn't accept any keyboard input, even REISUB.

So I turned off auto-monitor-off, and left it a couple of hours, and it was still displaying the screen saver fine when I got back home.

I tried the command "xset dpms force off" to turn off the monitor manually, and this did NOT cause it to hang.

Does the power management utility use a different command to turn off the monitor? I'm puzzled now...

---

### Post by enapupe on 2012-08-29
> **gdea73 said:**
> Okay, this becomes further confusing. I tried Ctrl + Alt + F1 last time, but the computer was totally frozen. It didn't accept any keyboard input, even REISUB.

So I turned off auto-monitor-off, and left it a couple of hours, and it was still displaying the screen saver fine when I got back home.

I tried the command "xset dpms force off" to turn off the monitor manually, and this did NOT cause it to hang.

Does the power management utility use a different command to turn off the monitor? I'm puzzled now...

I'm having the same issue, but I'm not a KDE user. I run Ubuntu 12.04 3.0.0-17-generic.

No CTRL ALT F[number] or REISUB works. Tryed to plug/unplug usb devices (mouse/kb).


I run xset dpms force off through my joystick and my computer recovers fine after it.

The curious is that not too long a monitor power off, it recovers fine, only many hours reproduce this issue.

---

