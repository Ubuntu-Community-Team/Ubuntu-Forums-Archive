---
title: "HOWTO: Minimal Debian Install (w/ Minimal GNOME)"
date: 2007-12-24
forum: Debian
---

### Post by jperez on 2007-12-24
I figured this was the best place to put it since it's a Debian forum.

I am making this tutorial for those that are just starting out with Linux and don't want to have Ubuntu/Kubuntu since it seems a little bloated, just because of the many programs that you may never use, or have Ubuntu/Kubuntu and don't want the bloat.

Take me for instance.  When I first installed Ubuntu on my laptop a few months ago and now have Kubuntu on my PC, it has many other programs that I have no need for!  What did I do?  I discovered Debian Etch 4.0 and it's Net Install CD.  Well, when I installed GNOME and KDE, there was still quite a bit of bloat to it since GNOME and KDE come with their own programs and it can run your space and sometimes your resources down a few notches.  This is especially true of older or low disk space machines.

It took me a while, but with the tidbits of info I found on the internet, I was finally able to achieve my goal.

**What you will need:**
[Debian Etch 4.0r1 (Stable) Net Install CD [ISO]]("http://www.debian.org/CD/netinst/")
An internet connection (broadband recommended)
At least 2GB of space

To start off, make sure to get the ISO that relates to your PC.  Once you've downloaded and burned the ISO, it's time to start!

Put the CD into your CD/DVD-ROM drive and reboot your computer.  When it comes up to the Debian Install startup screen, press enter and the the text installation should start.

Select all options that apply to you and keep an eye out for a dialog box asking about using a network mirror.  When this screen comes up, choose **No**.  Choose to install GRUB and let the install finish.

**If the install stops at a certain point with an error that won't let you proceed, even if it says you can skip it but won't let you, then simply restart your PC and try again.**

Now, here's where the real fun begins.

When the PC restarts and it gets to the UNIX login screen, login as **root** and use the password you provided for the root account during the install.

Once logged in, type:

```
nano /etc/apt/sources.list
```

And put this into the file:

```
deb http://ftp.debian.org/debian etch main contrib non-free
deb-src http://ftp.debian.org/debian etch main contrib non-free
```

Make sure to comment out the CD-ROM repository entry by putting a number sign (#) in front of it, like this:

```
# deb cdrom:...
```

Save it (Ctrl+O) and exit (Ctrl+X) and type in:

```
apt-get update
```

This will update the repositories list.  Once you it's done, we're going to install the base core files needed to run a visual desktop environment, or just the desktop.  As an example, we'll use GNOME, so type in:

```
apt-get install xorg gnome-core gdm
```

This will setup the XOrg server, GNOME core files and the GNOME Display Manager onto your machine.  If you want KDE, type:

```
apt-get install xorg kde-core kdm
```

Now, for the Display Manager (login manager), you can use a very limited, simplistic one.  That that, instead of **gdm/kdm**, use **xdm**.

Now, most people don't want to have to work on the terminal all the time.  For me, I like the full control of the terminal over a GUI like Synaptic, but for the sake of those that are starting out or just plain don't like the CLI (Command-Line Interface), type in:

```
apt-get install synaptic dwww deborphan libgnome2-perl
```

After all that is done, reboot and let it start up.  You're set!  Now you can install a File Manager, Web Browser, Music player, etc of your choice.

Another thing you can do is if you've had a different distribution before and decided to try something new and want to have the same programs, then simply go to the Synaptic Manager and do this:

```
File -> Generate package download script
```

This will generate a shell (terminal) script to download all the packages you've installed on the other distro so they can be downloaded and installed on your new install.

MANY more thanks to **indigo196** for helping me with the shorter version of the minimal install, addition of Synaptic and the suggestion to include the generated script for new systems.

Have fun!

Jesse~

---

### Post by cprofitt on 2007-12-24
I am in the process of making a complete list -- there are some items that you have left off.

I also find it easier to use apt-get install gnome-core than do all the individual things... I will post my steps as I complete them later this week.

---

### Post by jperez on 2007-12-24
Thanks!  If you have a simpler way of doing that, then that's perfect.  Also, what would I be missing?  I followed that and it worked out quite well for me with a minimal install.

Jesse~

---

### Post by cprofitt on 2007-12-24
OK... 

I will edit this post as I run through the build I am doing on my HP Tablet.

The first step was to install from the CD - Netinstall.

reboot.

```

apt-get install gnome-core xorg gdm gnome-volume-manager

```

reboot

the next really big step was to install synaptic

```

apt-get install synaptic deborphan libgnome2-perl

```

I then edit my /etc/apt/sources.list and simply comment out the CD entry

```

# deb cdrom: [Debiant GNU/Linux 4.0 r1 _Etch_ - Official i386

```

If you are using 64bit or another architecture the line will be slightly different.

```

apt-get update
apt-get upgrade

```

reboot

From here you need to add apps and functionality, but you should be set to go as far as the base. I will post some sep. posts for the areas I find necessary for giving me a good 'working' laptop.

---

### Post by cprofitt on 2007-12-24
**Increased Functionality**

```

apt-get install alacarte

```

So you can edit your menus.

```

apt-get install alsa-base asla-utils alsa-tools alsa-oss apmd discover

```

This give your some sound.

More to come, but guests have arrived.

---

### Post by jperez on 2007-12-24
Yeah, that shortens the individual package process and also, you don't really need to have synaptic.  I don't have it because I'm conserving space.  On a 2.2GB hard drive, taking up space is not an option.  Yeah, I install a lot of software from the command line, but that's better for me since I have more control over the files that way.

I did leave out the fact that you need to comment out the CD-ROM though. Thanks for reminding me.

I'll update the thread with your added info.

Jesse~

---

### Post by jperez on 2007-12-25
Updated the HOWTO to include the KDE minimal and Synaptic Script for configuring your new install to have the same packages as your old install.

---

