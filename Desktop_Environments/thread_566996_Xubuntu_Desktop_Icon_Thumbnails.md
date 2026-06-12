---
title: "Xubuntu Desktop Icon Thumbnails"
date: 2007-10-04
forum: Desktop Environments
---

### Post by avantgardaclue on 2007-10-04
Have been a happy ubuntu user now for 2 years. In anticipation of 7.10 i have been trying out ubie variations. First kubuntu, hmmmm, not entirely convinced, think i still prefer gnome. Now i'm trying xubuntu, well am very impressed by the speed esp for my 6 year old box and the fact is that it is not a million miles away from gnome.

Downside is that i currently have gazzilions of applications littering my menus that i'm just never going to use so roll on 7.10 and a fresh install.

Anyhow back to xubuntu... I could be convinced full time if....

1 Desktop icons were thumbnails, esp of images, they show up ok in file manager

2 I could get my fave applications onto the panel (remember i have countless apps in the menus!)

I imagine that these problems are easily addressed... if only i knew how!

Over to you guys please... thanx!

Simon

---

### Post by ugm6hr on 2007-10-05
1. I don't use the Desktop for files, so can't help.

2. This tells you how to add a Mail Panel Launcer: [http://ubuntuforums.org/showpost.php?p=2689344&postcount=8](http://ubuntuforums.org/showpost.php?p=2689344&postcount=8)
At the end, it also explains how to add any program.  You just need to chose the correct "launch" command.  The easiest way to do this is to use the Appfinder Application (in Accessories menu).  Find the program in Appfinder, and then right-click on it and select "More Information" - this will give you a "command" that is generally the same as the application name in lower case.

---

### Post by avantgardaclue on 2007-10-08
Hi ugm6hr, got the launchers working sweet, thanks..... but  disaster!

Xfce crashed, or rather i lost the panel bar at the top of the screen and the task bar at the bottom. Nothing to do with the launchers! I had open a number of applications at the time, certainly not an amount that would cause a problem with either gnome or kde.

There was a screen judder as the open window resized itself to life with out bars at the top and bottom. There has been no way to restore these bars as i am now more convinced that xubuntu is the way to go ahead speed and all that!

Is there a 'display bars' option that may have inadvertently kicked in, if so how do you access it if the panel and menu are no where to be seen? 

In gnome ubuntu i did a reinstall from synaptic (only 1 file apparently) which did nothing, no change.

Any ideas that can rescue this?

thanks... Simon

---

### Post by jim_p on 2007-10-08
I think that the top and bottom bars you refer to are the window manager (like gnome's metacity). In order to revert back to xfce's window magager execute this in a terminal

```
xfwm4 --replace
```

Just in case I am wrong and nothing happens, replace "xfwm4" with "xfwm"

About #2 issue
Go to xfce's control panel and choose Desktop and then on the 2nd tab click the "Edit menu" button and a menu editor will pop up. Remove anything you want from here and tidy your menu



ps I have not worked with xfce in the same level as I have with gnome so please excuse any mistakes

---

