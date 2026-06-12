---
title: "gnome trwon't load"
date: 2009-11-30
forum: Desktop Environments
---

### Post by phredbull on 2009-11-30
Hi, I'm pretty new to Ubuntu, (9.10), but have been slowly learning my way around.

I was making tweaks to my xorg.conf file, (trying to optimize my graphics performance for a game), and rebooted my machine. (Ctrl+Alt+bkspc doesn't seem to do anything.)
I selected Ubuntu from the OS list, (Wubi install), selected the newer kernel, (2.6.31, I think) and see the white pulsing Ubunto logo, then it just goes to login with the  command prompt, no GUI login. I've had similar problems before, and ended up reinstalling. My command line fluency is minimal. (I'm trying to learn, but it's not as intuitive as a GUI.)

Is there a way to either

a) fix Gnome so that it will load properly,
or
b) save all my customizations, installed programs, preferences, etc., and apply them to a new installation?

I am currently running live from a USB stick. I can see my internal HD, but can't see any Linux files on it, only Win files. All my documents are stored on an external HD, so not worried about that, just don't want to have to re-do everything after all the tweaks and customization I've done.

---

### Post by phredbull on 2009-11-30
bump

---

### Post by phredbull on 2009-11-30
Anyone?

---

### Post by phredbull on 2009-11-30
Bumpbump!

---

### Post by phredbull on 2009-12-01
Ima jus' keep on bumpin'!

(Are you guys trying to tell me to reinstall, or just avoiding the thread w/the typo in the title? I fixed the title, it's just that the forum doesn't know it!)

Quintuple posting; talk about bad nettiquette!

---

### Post by Dthdealer on 2009-12-01
When in the **/etc/X11** directory, look for any **xorg.conf.*date*** files.  Move one ontop (overwrite) your current one.

Alternatively enter [B]sudo dpkg-reconfigure -phigh xserver-xorg
[/B] at the command-line.  This is probably the best option.

---

### Post by phredbull on 2009-12-01
Thank you, I've been waiting all day for you! I'll try option#2 now...

BTW, I assume there is no preferences/settings backup in Linux?

---

### Post by phredbull on 2009-12-01
Well, I tried option #2 and nothing happened.

Using my limited command line skills, I managed to see the contents of me /etc/X11 directory, and there was no file xorg.conf.*date*. There was one called xorg.conf~, and I thought "~" might be an abbreviation, so I renamed it xorg.conf~old. Rebooted, but still the same situation. I then booted into recovery mode where I tried the "repair packages" option, then rebooted, but still the same. Any other suggestions?
(I'm now writing from XP, because it takes like 10 minutes to boot from my USB stick. Is this normal?)

---

### Post by andrea000 on 2009-12-01
Well if you can get to the terminal then just reinstall
ubuntu desktop.
> sudo apt-get install ubuntu-desktop

if you can not then press alt and f2 at the same time
then type synaptic and hit enter then just search for
ubuntu desktop and install it.

---

### Post by phredbull on 2009-12-01
Is this the same as doing a fresh install of Ubuntu, or will it just fix the GUI? Will my settings remain intact?

Also, is it likely that my problems are being caused by my tinkering with my xorg.conf file? Originally, I didn't even have one, so I created it in order to squeeze the most performance out of my old ATI GPU.

---

### Post by andrea000 on 2009-12-01
> **phredbull said:**
> Is this the same as doing a fresh install of Ubuntu, or will it just fix the GUI? Will my settings remain intact?

Every thing should be intact it just reinstalling the gui

---

### Post by phredbull on 2009-12-01
Beautiful; hopefully the next time I return to this thread will be to mark it [SOLVED]!

---

### Post by phredbull on 2009-12-01
When attempting "sudo apt-get install ubuntu-desktop", it begins the process, but ends up saying "ubuntu-desktop is already the latest version", and doesn't reinstall.

When trying to launch synaptic, I get, "(synaptic: 1545): Gtk-WARNING**: cannot open display:

Any other suggestions?

---

### Post by phredbull on 2009-12-01
bump

---

### Post by andrea000 on 2009-12-01
ok i don't know what is going on but try starting x
from the terminal

> startx
if it starts go to startup applications under system
preference and make sure all of the gnome options are
checked.

---

### Post by WorLord on 2009-12-01
If you have a file called "xorg.conf" in the /etc/X11 directory, rename it to something else with the following command:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Then try to start the gdm service with the following command:

```
sudo service gdm start
```

If that works, then something in the xorg.conf file is wrong.

Also, logging out restarts the X-server, so when changing/testing xorg.conf files, you only need do that - and not reboot - to test out your new configuration.  

Should your new configuration fail, you can stop the gdm service at the command prompt with the following command:

```
sudo service gdm stop
```

...and then proceed to either move your broken xorg.conf file out of the way, or modify it with nano (or whatever you like) and try to start the service again to see if it worked.

---

### Post by phredbull on 2009-12-01
Woo hoo!:popcorn:
I renamed my xorg.conf file, and now all is good, thanks WorLord! I copied the xorg.conf settings from someone who had the same ATI card as me, but apparently there was a reference to an "undefined input device".

So this is how you learn to become a Linux user, huh? This one issue was a good learning experience, much more informative than simply reinstalling.

Thanks to andrea0000 as well!:KS

Now, back to figuring out how to optimize my GPU...:-k

---

### Post by WorLord on 2009-12-02
> **phredbull said:**
> Now, back to figuring out how to optimize my GPU...:-k

Which GPU?

Also, do this:

CTRL+ALT+F1 will get you to a term.  From there, stop the GDM service like you already know how to do, then do this:

```
sudo Xorg -configure
```

This will create an xorg.conf.new in the /root directory.  It will contain all the data that was auto-detected, including all possible options for your video adapter (commented out in the "Device" section).  From there you can start un-commenting out options and testing your system to see which ones help and which don't.

---

### Post by phredbull on 2009-12-02
ATI Radeon. Kinda old, and apparently, one of the more problematic ones.

Thanks for the additional tips, will surely be helpful!

---

