---
title: "enabling effects"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by mahela007 on 2008-03-18
i finnaly managed to install ubuntu and installed it while the live cd was in safe mode.
now the installation does not have the nice animated windows.
how do i enable them?

---

### Post by NightwishFan on 2008-03-18
Did you enable the restricted drivers? (Or search for a similar thread?)

After they are enable you can do this:
```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```
Then you can customize effects in the System menu, Advanced Effects or something.

---

### Post by mahela007 on 2008-03-18
how do i enable restricted drivers
?

---

### Post by NightwishFan on 2008-03-18
In Gutsy I think it is called the restricted drivers manager. Somewhere under the System Menu.

---

### Post by mahela007 on 2008-03-18
its not a problem with my hardware
when i installed from the live cd the live cd was in safe mode.
not the version on my harddrive doesnt have the animations
how can i enable them?

---

### Post by Ub1476 on 2008-03-18
Hum, you're saying that you had effects in safe mode, but none after Ubuntu was installed onto your HDD? Post the output of:

```
compiz

lspci | grep VGA
```

Terminal is located in Applications>Accessories>Terminal

---

### Post by NightwishFan on 2008-03-18
You just need to install the restricted drivers. If you already can do effects then just do what I said:
```
sudo apt-get install compizconfig-settings-manager
```
Or try appearance under system set it to extra.

---

### Post by mahela007 on 2008-03-18
nope. didnt work

---

### Post by lavinog on 2008-03-18
Your video card might not be supported...what video card do you have?
if it is ati or nvidia you have to have the restricted driver enabled
you turn the animations on with System > Prefrences > Appearance
then click on the Visual Effects tab and select one.

---

### Post by NightwishFan on 2008-03-18
What did not work??? Lets do a check list.

1) You have modern gpu.
2) You have restricted drivers enabled.
3) You are using Gutsy.(Compiz by default)
4) You have compizconfig-settings-manager installed.

There should be advanced desktop effects under the system menu and you can configure compiz there. Or under appearance in the last tab you can enable "extra". If it does not work you confict with something on the check list possibly.

---

### Post by lavinog on 2008-03-18
if my above post didn't work: open a terminal and type
```
gnome-appearance-properties
```
it should pull up the appearance window again...select a visual effect
if it fails it should give you a message in the terminal why...it would be easier to help you if you post the output here

---

### Post by Ub1476 on 2008-03-18
> **mahela007 said:**
> nope. didnt work

Please post the result of:

```
lspci | grep VGA

compiz
```

---

### Post by jdix123 on 2008-03-18
I'm having a similar issue.  I get this:  

```

jas@QueenMab:/etc/X11$ gnome-appearance-properties

(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/actions of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/apps of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/categories of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/devices of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/emblems of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/emotes of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/mimetypes of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/places of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 72x72/status of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/actions of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/apps of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/categories of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/devices of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/emblems of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/emotes of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/mimetypes of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/places of theme CrashBit has no size field


(gnome-appearance-properties:9971): Gtk-WARNING **: Theme directory 96x96/status of theme CrashBit has no size field

There is no available graphics driver for your system which supports the composite extension.
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: /usr/bin/metacity 
jas@QueenMab:/etc/X11$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
jas@QueenMab:/etc/X11$ 
jas@QueenMab:/etc/X11$ compiz
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: /usr/bin/metacity 

```

I worked pretty extensively to enable effects on my Hardy laptop modifying my xorg.conf file.  A couple of updates ago I started having issues.  Could be this is a Hardy issue, but if anyone has any ideas.

---

### Post by lavinog on 2008-03-18
> **jdix123 said:**
> I'm having a similar issue.  I get this:  

```

...

There is no available graphics driver for your system which supports the composite extension.
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: /usr/bin/metacity 


jas@QueenMab:/etc/X11$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

```


The problem is either your driver is blacklisted or you don't have the restricted driver enabled.
the non-restricted driver doesn't support 3d as far as i know.
what happens if you run glxgears? what framerate do you get...if it is low (under 600 FPS) then the problem is the video driver you are using...

[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")
this link is helpful for setting up the proprietary ATI driver. The restricted driver in synaptic is outdated...this site shows you how to install the current ATI driver.

---

### Post by jdix123 on 2008-03-19
I ran the tutorial you said and now my x server won't start at all.  

I booted with the disc and deleted the current version of my xorg.conf file but for some reason its not creating a new one and I'm getting the same reaction.  

I need to completely reverse this tutorial and I have no idea how to do that when booting from a live cd.  I also can't get a prompt when booting normally, ctrl+alt+F1 does nothing but give me a blinking cursor I can't type with.

Instead of having no desktop effects I now have a laptop shaped paperweight.  Ack!

---

### Post by lavinog on 2008-03-19
can you boot into recovery mode?
or get a command prompt?
if so there should be a backup xorg.conf file.

what method did you use (1 or 2)?
and are you using gutsy or hardy?

---

### Post by lavinog on 2008-03-19
what happens when you try to start x?

---

### Post by jdix123 on 2008-03-19
I'm using Hardy.

I can't get a prompt booting normally.  I see the grub loading screen (which times out at zero seconds) and then the screen goes blank except for a blinking underscore cursor.  If I wait long enough a blue screen appears which looks like an older installation disk dialogue screen but I can't read the text (I'm guessing this is the "Do you want us to try and fix the x server?" dialogue).

I can boot using the live cd but I can't seem to edit anything to make it work properly.

Forgot about recovery mode though.  Der duh derr.  Now I'm back to where I was -- working x server minus effects.

I'm looking on that ati wiki page you linked to (probably should have done this first) and my Mobility Radeon 7500 isn't on the list of supported cards for the fglrx driver.

---

### Post by lavinog on 2008-03-19
ok, I haven't tried it with hardy yet.
for future reference that is something that should be mentioned when you have an issue since hardy isn't officially released yet.

which method from the wiki did you use?

when hardy does officially come out you may want to just go ahead and reinstall it.

---

### Post by jdix123 on 2008-03-20
I mentioned it in my initial post.  As I said, I got the desktop effects working rather well by tweaking with my xorg.conf file, and then the stopped working all of a sudden.  Might be a Hardy issue.

I tried to use the sudo apt-get, or the "ubuntu way."  I then manually changed the driver in my xorg.conf file.  When I rebooted I had the issues.  I used a recovery kernel and reverted to my old xorg.conf file and I'm back where I was -- x server working but no effects.

---

### Post by jon.reeve on 2008-03-25
I'm in the same exact position with my Radeon M6 LY.  I'm assuming this has something to do with the blacklisting of the radeon driver, and the unavailability of the fglrx proprietary driver for these laptop cards (m6 m7 etc). I can't get compiz to work at all now, though it was working fine under gutsy.

---

### Post by jdix123 on 2008-04-06
Bump

---

### Post by jon.reeve on 2008-04-06
II solved this by following the instructions in the sticky about reenabling blacklisted drivers

---

