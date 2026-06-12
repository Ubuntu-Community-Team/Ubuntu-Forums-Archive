---
title: "Screen Resolution can't be changed in Gusty!?!"
date: 2007-11-06
forum: Desktop Environments
---

### Post by mattmagician on 2007-11-06
So i just updated to Gusty, and now i've got a problem....my screen resolution changed. it used to be about 1400x?
and have no free space. but now its 800x600 and has space on the side, everythings way over sized, and in the Screen Resolution chooser, only 800x600 and 640x480
...halp?

---

### Post by taurus on 2007-11-06
What graphic card do you have?  Have you tried to modify to include the resolution that you want to use?

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by RTrev on 2007-11-06
> **mattmagician said:**
> So i just updated to Gusty, and now i've got a problem....my screen resolution changed. it used to be about 1400x?
and have no free space. but now its 800x600 and has space on the side, everythings way over sized, and in the Screen Resolution chooser, only 800x600 and 640x480
...halp?

Try this:

```
sudo dpkg-reconfigure xserver-xorg
```

It should give you the option to pick the correct resolution.

---

### Post by jimjan on 2007-11-07
on this issue we have two suggestions above

sudo dpkg-reconfigure xserver-xorg
gksudo gedit /etc/X11/xorg.conf

will one work or both work in live cd mode?
i can not get cd to boot so can this be done in boot command

thanks

---

### Post by taurus on 2007-11-07
> **jimjan said:**
> on this issue we have two suggestions above

sudo dpkg-reconfigure xserver-xorg
gksudo gedit /etc/X11/xorg.conf

will one work or both work in live cd mode?
i can not get cd to boot so can this be done in boot command

thanks

Boot int recovery mode from GRUB menu and reconfigure your X with

```
dpkg-reconfigure xserver-xorg
```
Then, reboot your machine with

```
shutdown -r now
```
And if you need to edit /etc/X11/xorg.conf, then run

```
nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.

---

### Post by jimjan on 2007-11-08
> **taurus said:**
> Boot int recovery mode from GRUB menu and reconfigure your X with

```
dpkg-reconfigure xserver-xorg
```
Then, reboot your machine with

```
shutdown -r now
```
And if you need to edit /etc/X11/xorg.conf, then run

```
nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.

thanks for reply
one clarification

it seems these steps are for install status of distro
is there a way to handle this monitor problem in  ''**live cd**'' mode

as background, usual boot method fails with live cd
using xubuntu gusty cd, mdsum checked
if i go into safe graphics mode it tells me i must do manual configure
i have tried to configure monitor but not successful so far

have dell monitor model e773c
intel card 82865g 
[by the way, does this sound right for a video card? if not, how do i tell what type of card i have--where do i look through winxp or with live cd]

steps to take? xubuntu gusty not work with my video card or monitor?
thanks

---

### Post by taurus on 2007-11-08
> **jimjan said:**
> thanks for reply
one clarification

it seems these steps are for install status of distro
is there a way to handle this monitor problem in  ''**live cd**'' mode

as background, usual boot method fails with live cd
using xubuntu gusty cd, mdsum checked
if i go into safe graphics mode it tells me i must do manual configure
i have tried to configure monitor but not successful so far

have dell monitor model e773c
intel card 82865g 
[by the way, does this sound right for a video card? if not, how do i tell what type of card i have--where do i look through winxp or with live cd]

steps to take? xubuntu gusty not work with my video card or monitor?
thanks

If the LiveCD doesn't work with your machine, you can always try the alternate CD since it's a text based mode installer.  If you want to be sure which onboard graphic card do you have, just run

```
lspci
```
but yes, that looks like one of the Intel onboard graphic card controllers that comes with Dell.

---

### Post by shawnc_nmb on 2007-11-08
I just upgraded from Feisty to Gutsy myself and half the** Intel 945 Chipset Onboard** Graphics Card,  Anyway  in my old Feisty setup I had to use 915resolution  to set my resolution to my native 1440x900 mode.  When i upgraded to gutsy, they are using a newer version of X so the **XORG.CONF** file was different, and it had better drivers for the intel chipset.  I suggest Backing up your current **xorg.conf** file, and reconfiguring your xorg and I'll explain how I personally did it

In Terminal Window type the following...

[PHP]
sudo su
cp /etc/X11/xorg.conf /etc/X11/xorg.backup_conf

sudo dpkg-reconfigure xserver-xorg
[/PHP]


I wrote a [blog post]("http://www.shawnc.org/2007/10/30/ubuntu-gutsy-and-the-intel-video-chipset/") about it a few weeks ago, you can review it here as the whole blog is about my personal experiences

---

### Post by jimjan on 2007-11-08
> **taurus said:**
> yes, that looks like one of the Intel onboard graphic card controllers that comes with Dell.

thanks for reply and suggestion

---

### Post by bharadwaj on 2007-11-10
try enabling restricted drivers or try to install 915 resolution on my desktop evev i had the problem like you later it was fixed by 915 resolution in repos

---

### Post by OldManRiver on 2007-12-12
All,

When I run the suggested command:```
dpkg-reconfigure xserver-xorg
```My machine will not show Gnome/Xwin at all.

Always have to go cmd line and restore to older xorg.conf and reboot.  That always forces me into 800x600.

I even added the modeline in my xorg.conf and still can not get out of the low res mode.

OMR

---

### Post by RTrev on 2007-12-12
> **OldManRiver said:**
> All,

When I run the suggested command:```
dpkg-reconfigure xserver-xorg
```My machine will not show Gnome/Xwin at all.

Always have to go cmd line and restore to older xorg.conf and reboot.  That always forces me into 800x600.

I even added the modeline in my xorg.conf and still can not get out of the low res mode.

OMR

Do you see the many screens of questions it asks, or does the command simply not work for you?

---

### Post by OldManRiver on 2007-12-12
> **RTrev said:**
> Do you see the many screens of questions it asks, or does the command simply not work for you?

RTrev,

Command works and build the xorg.conf file, but on reboot the only thing I get is command line, as the config it builds is totally wrong.  So then, as I explained, I have to go revert to the old version of xorg.conf and reboot to get Gnome/XWin up again.

I've been working with NeddySeagoon on irc.freenode.net #gentoo and he is the best help I can find, but he is not alway available.  If you go to my post at:
> [http://ubuntuforums.org/showthread.php?t=637969](http://ubuntuforums.org/showthread.php?t=637969)
see problem #2

you can see where I'm at with the debugging and all.  It also contains the link to the modeline gen script Neddy hooked me up with.  He and I worked this problem, before on my Gentoo box and it was so bad I opened a bug report to X11/Xorg.  Will find that and post shortly.  Problem seems to be isolated to my Monitor which is AMW MR19C-AB.  The sync on this monitor seems to be where the problem is, but not totally sure.


OMR

---

