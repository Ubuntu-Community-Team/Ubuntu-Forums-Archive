---
title: "very slow shutdown process in 8.04 hardy"
date: 2008-04-24
forum: Desktop Environments
---

### Post by dage on 2008-04-24
Hello,
I've just installed Hardy this afternoon (24/04/2008). Everything work fine except usb mount (I won't mention it here) and shutdown process. 

It takes 30s to shutdown GDM and 5 more second to shutdown the whole pc.
My don't use splash screen during boot up and my vga mode in grub is 794

Can someone help me to fixe it ?
Best regard.

---

### Post by dage on 2008-04-24
I think I've just repair the prob: I reinstall the binary driver downloaded at nvidia.com of my graphic card.
So right now I've the binary driver install and Restricted Hardware Driver installed (nvidia-glx-new). Does it cause any conplict to my system ?

---

### Post by adohall on 2008-04-24
I have the same problem. I installed the nVidia driver through Synaptic (or the package manager) and now shut down is very slow. How do I get hold of this binary driver you mentioned. Do you have a URL? I'd be very grateful for your help. Thanks.

---

### Post by dage on 2008-04-25
you can go here to download the driver: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Before installing, I think it's better to uninstall (disable) the restricted drivers installed automatically by "Hardware drivers" of Ubuntu.

To installed the new driver, u'll have to boot at rescue mode.
Read more instruction at the driver download page.

Have fun.

---

### Post by Blaxter on 2008-04-28
I'm in the same situation. When i click on System/quit it takes around 60s to show up the options with restart/shutdown/hibernate and so on. 

I don't know what should i try for getting some debug/log information :-/. In old version (<8.04) this action it takes around 5s (which it's many time, but it's reasonable enough), now it's totally unsuable (i use to ctrl+alt+backspace and then click on shutdown or whatever) :(

---

### Post by adohall on 2008-04-28
You may find, as I did, that after a day or so, shut down speeds up to Gutsy Gibbon levels and the terminal-style log messages disappear. Why? I don't know. Silent update? System smart enough to ignore repeated device failures on shutdown (dbus etc)? Actually, I turned off bluetooth and print services on startup. Maybe that was significant.

---

### Post by Blaxter on 2008-04-30
i've solved, it's a problem with gnome-power-manager, just go to System > session and active power manager. This's a [bug reported on 7.10]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078")

---

### Post by gdjsky01 on 2008-04-30
I upgraded from GG to HH and have had two problems:

One is the usual* "It will take days of fiddleing to get my ATI graphics chip using dual monitors to work.*" :( The desktop bars on top and bottom both get corrupted with random noise. But I'll defer that to the video forum...

While not *'shutdown per se'* when I go to logout or lock the screen the desktop hangs for at least 60 seconds before the choice panel shows (sometimes the panel does not show and everything acts like I had never clicked the Logout/Switch User button on the menu bar. When I launch other apps from the menu bar this does not happen.

---

### Post by sladen on 2008-05-10
I upgraded from 7.10 to 8.04 and see lots of text on the screen and slow shutdown when I booted up using kernel 2.6.24-16-generic. When I start with kernel 2.6.22-14-generic the problem seems to go away.

---

### Post by sladen on 2008-05-10
> **sladen said:**
> I upgraded from 7.10 to 8.04 and see lots of text on the screen and slow shutdown when I booted up using kernel 2.6.24-16-generic. When I start with kernel 2.6.22-14-generic the problem seems to go away.

Oops. 2.6.22-14-generic does the same but Firefox seems to be much slower.

---

### Post by Electric Bill on 2008-08-11
> **Blaxter said:**
> i've solved, it's a problem with gnome-power-manager, just go to System > session and active power manager. This's a [bug reported on 7.10]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078")
I was playing around in System>Preferences>Sessions and disabled Power Manager since mine is a desktop system.
Big mistake.
Thanks Blaxter.
AOK now.

Bill

---

