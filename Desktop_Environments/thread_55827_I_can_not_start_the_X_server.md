---
title: "I can not start the X server"
date: 2005-08-10
forum: Desktop Environments
---

### Post by Holdem on 2005-08-10
After accepting an update today (think it was xpdf stuff) I rebooted because I wanted to boot-up XP. I left the PC to reboot and came back 30mins later to find the monitor off. Thinking it was on power save I tired to wake it but no joy and the green light was on. Manually rebooted and worked in XP and updated that rebooted back in to XP and then later on rebooted to launch Ubuntu. First off it did a force check claiming HD not umounted properly but could not finish HD check and I maually did that with lots of Y clicking. Rebooted and once it had started Ubuntu it ran through like normal and just as I was expecting the login prompt I got:
 I can not start the X server. It is likely that it is not setup correctly. Would you like to view the X  server output to diagnose the problem. Y or N

X Window System Version 6.8.2
X Protocol Version 11, revsion 0, release 6.8.2
Linux 2.6.10, 686 [ELF]

X10 fatal I/O error 104

The upshot it that I have no GUI which to me renders the whole thing useless. 
Does anyone know how I can fix this? I'm assuming that I can re-install X server with-out touching Ubuntu, if so how?

All comments welcome, thanks in advance.

---

### Post by tonysathre on 2005-08-10
[QUOTE=Holdem]After accepting an update today (think it was xpdf stuff) I rebooted because I wanted to boot-up XP. I left the PC to reboot and came back 30mins later to find the monitor off. Thinking it was on power save I tired to wake it but no joy and the green light was on. Manually rebooted and worked in XP and updated that rebooted back in to XP and then later on rebooted to launch Ubuntu. First off it did a force check claiming HD not umounted properly but could not finish HD check and I maually did that with lots of Y clicking. Rebooted and once it had started Ubuntu it ran through like normal and just as I was expecting the login prompt I got:
 I can not start the X server. It is likely that it is not setup correctly. Would you like to view the X  server output to diagnose the problem. Y or N

X Window System Version 6.8.2
X Protocol Version 11, revsion 0, release 6.8.2
Linux 2.6.10, 686 [ELF]

X10 fatal I/O error 104

The upshot it that I have no GUI which to me renders the whole thing useless. 
Does anyone know how I can fix this? I'm assuming that I can re-install X server with-out touching Ubuntu, if so how?

All comments welcome, thanks in advance.[/QUOTE]
 i would say just reinstall unless u have a lot of things you dont want erased

---

### Post by Holdem on 2005-08-10
[QUOTE=tonysathre]i would say just reinstall unless u have a lot of things you dont want erased[/QUOTE]

My cats got fleas.

Well have it put down and get a new one.

Anyone know how to re-install/repair X server from the command line.

---

### Post by MacAdmin on 2005-08-10
Very simple, I had almost the same problem this morning.
Login to terminal and ran sudo apt-get remove xserver-xorg
it will remove Xserver and ubuntu desktop, but your files would be OK.

Then run sudo apt-get install xserver-xorg.

That is it.

---

### Post by Holdem on 2005-08-11
Thanks for the reply.
I did the xorgconfig but startx would still not work then I reinstalled xserver-xorg and after reinstalling xfonts-base I got the Ubuntu login screen.
Yippie, or so I thought until the desktop came up like this.
[[img]http://xs41.xs.to/pics/05324/Screenshot-2.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs41&d=05324&f=Screenshot-2.png)

So now I'm at a loss as to what needs installing. I had a look at Gnome under Synaptic but it wasn't installed and the description for it was a package of utils including some office stuff, so I guess there is something else that needs installing. 
What next, any ideas?

PS Firefox would not operate just brought up a blank window and I had the standard Gnome desktop but I'd moved the panels around.

---

### Post by MacAdmin on 2005-08-11
Sorry.
here the command sudo aptitude install '~tubuntu-desktop'
That would reinstall your desktop.

---

### Post by Holdem on 2005-08-11
Thanks, I'll give that a try

---

### Post by varunus on 2005-08-11
Also, maybe try reinstalling nautilus and the gnome-session packages.  Also, make sure gnome-settings-daemon (which provides icon themes and GTK themes) is running when you start gnome...if it isn't, something very weird is going on.

The XPDF update didn't do anything to my x server...

---

### Post by Holdem on 2005-08-11
[QUOTE=MacAdmin]Sorry.
here the command sudo aptitude install '~tubuntu-desktop'
That would reinstall your desktop.[/QUOTE]

Although that worked as in it gave no errors it did not resolve my issue. Same desktop as above screen shot.

I'll now try what varunus suggests

---

### Post by Holdem on 2005-08-11
[QUOTE=varunus]Also, maybe try reinstalling nautilus and the gnome-session packages.  Also, make sure gnome-settings-daemon (which provides icon themes and GTK themes) is running when you start gnome...if it isn't, something very weird is going on.

The XPDF update didn't do anything to my x server...[/QUOTE]

Tried the re-installs still no luck. 
Going to back-up data and re-install Ubuntu.

---

### Post by varunus on 2005-08-11
Does running gnome-settings-daemon from applications-run application do anything about the icon and theme?

---

