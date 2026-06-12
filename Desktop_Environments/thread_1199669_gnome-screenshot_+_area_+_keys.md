---
title: "gnome-screenshot + area + keys"
date: 2009-06-29
forum: Desktop Environments
---

### Post by martin_legion on 2009-06-29
Hello.
Is there a way to take a screenshot of a selected area without having to open gnome-screenshot.
There are 2 key combinations available, one to capture the whole desktop and the other to capture the focused window, but I can't figure out how to capture the selected area by using the keys.
Thanks!

---

### Post by delectate on 2009-06-29
a ha,I use compiz fusion 's plug-in

Now ,when I press Super + button1,I can select any area where I want

try ccsm

---

### Post by VCoolio on 2009-06-29
You can make a key binding for the command "gnome-screenshot -a". It will turn your mouse cursur into a crosshair so you can grab an area and then save it.

---

### Post by martin_legion on 2009-06-29
> **VCoolio said:**
> You can make a key binding for the command "gnome-screenshot -a". It will turn your mouse cursur into a crosshair so you can grab an area and then save it.

That's EXACTLY what I was looking for. I've read the man for gnome-screenshot but didn't see the -a flag... 
Anyway.. I love this forum.

thanks a lot!

---

### Post by Tom Feiner on 2009-06-30
I've ran into this issue myself a few days ago, and luckily, I ran gnome-screenshot --help and saw the -a (--area) option which is exactly what you need.

I also noticed that the man page is out of date, and opened a bug in ubuntu to fix it , so that other people won't miss this option:
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/393401](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/393401)

In addition to running gnome-screenshot -a manually to capture an area of the screen, you can also map it as a custom keyboard shortcut, so it'll be easily available. I mapped CTRL+PrintScreen to gnome-screenshot -a.

This really is a great feature, it would be nice to have a some sort of keyboard shortcut mapped to this function by default. 

Tom

---

### Post by KWLLC on 2010-01-04
> **Tom Feiner said:**
> I've ran into this issue myself a few days ago, and luckily, I ran gnome-screenshot --help and saw the -a (--area) option which is exactly what you need.

I also noticed that the man page is out of date, and opened a bug in ubuntu to fix it , so that other people won't miss this option:
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/393401](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/393401)

In addition to running gnome-screenshot -a manually to capture an area of the screen, you can also map it as a custom keyboard shortcut, so it'll be easily available. I mapped CTRL+PrintScreen to gnome-screenshot -a.

This really is a great feature, it would be nice to have a some sort of keyboard shortcut mapped to this function by default. 

Tom
Two comments.... 
1) the info page is much better for gleaning information on this.
2) another hole either in the program or in all of the documentation is how to name the .png something more useful like date & time.

---

### Post by treerink on 2010-09-20
Thanks! To get this working with a shortcut (without the terminal) I had to add the -i:

Ubuntu 10.10:

System -> Preferences -> Keybord Shortcuts -> Add ->  
 name: grab area                                                                    (for example)
 command: gnome-screenshot -i -a 
 Click -> Shortcut: New Shortcut : Ctrl+Alt+4                               (for example, like Apple+4 on the Mac)

You have to add the -i (interactive) otherwise the -a is ignored!

Ubuntu 11.10:

Go to System Settings
click Keybord
click Shortcuts
click Custom Shortcuts
click +
fill in Name:     grab area                   (for example)
fill in Command:  gnome-screenshot -i -a
click Apply
click with the right mouse at:  New Shortcut  (at the right)
and press Ctrl+4                              (for example, like Apple+4 on the Mac)
now it works, you can just close the window

---

### Post by KWLLC on 2010-09-21
> **treerink said:**
> Thanks! To get this working with a shortcut (without the terminal) I had to add the -i:

System -> Preferences -> Keybord Shortcuts -> Add ->  
 name: grab area                                                                    (for example)
 command: gnome-screenshot -i -a 
 Click -> Shortcut: New Shortcut : Ctrl+4                               (for example, like Apple+4 on the Mac)

You have to add the -i (interactive) otherwise the -a is ignored!
AAH. Works like I want. Thanks to all!

---

### Post by hipodilski on 2012-03-14
If you want to be able to make quick screenshots (not invoking gnome-screenshot -a -i), you better assign keys to use imagemagick's import use cmd:


**import -frame screenshot.png**


best
hip0
[http://www.pc-freak.net/](http://www.pc-freak.net/)

---

### Post by kingocounty on 2012-05-21
> **treerink said:**
> Thanks! To get this working with a shortcut (without the terminal) I had to add the -i:

Ubuntu 10.10:

System -> Preferences -> Keybord Shortcuts -> Add ->  
 name: grab area                                                                    (for example)
 command: gnome-screenshot -i -a 
 Click -> Shortcut: New Shortcut : Ctrl+Alt+4                               (for example, like Apple+4 on the Mac)

You have to add the -i (interactive) otherwise the -a is ignored!

Ubuntu 11.10:

Go to System Settings
click Keybord
click Shortcuts
click Custom Shortcuts
click +
fill in Name:     grab area                   (for example)
fill in Command:  gnome-screenshot -i -a
click Apply
click with the right mouse at:  New Shortcut  (at the right)
and press Ctrl+4                              (for example, like Apple+4 on the Mac)
now it works, you can just close the window

I know this is an old thread but I wanted to say that this works in 12.04 and also, thank you!

---

### Post by oldos2er on 2012-05-21
Old thread closed.

---

