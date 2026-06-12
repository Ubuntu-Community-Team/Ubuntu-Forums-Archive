---
title: "2 Unity questions"
date: 2012-04-29
forum: Desktop Environments
---

### Post by Ghost_Mazal on 2012-04-29
Lo all ,

I am gonna give unity another try. Didn't like it back when it released , but decided to give it another chance. 2 Questions:

1. By default you invoke the dash with the "super" key (windows key) yes ? But I use my super key for my compose key. Can I configure unity to use another key to invoke the dash as now it doesn't work.

2. Where is the side bar settings ? (size of icons etc.) I can't find it anywhere.

Thank you

---

### Post by JRV on 2012-04-29
Number two

Install compizconfig-settings-manager with the command:
```
sudo apt-get install compizconfig-settings-manager
```
Run the program with the command:
```
ccsm
```

Select the Ubuntu Unity Plugin.
Icon size is under Expermintal.

Notice the warning message whenb ccsm starts.
Lots of people have messed things up using ccsm, however the Ubuntu Unity Plugin seems to be safe.

Sorry I can't help with number one.

---

### Post by grahammechanical on 2012-04-29
Question 2: Go to System Settings>Appearance

Question 1: Go to CCSM (CompizConfig Settings Manger) and the Ubuntu Unity Plugin = Key to show the launcher.

Regards.

---

### Post by Ghost_Mazal on 2012-04-29
> **JRV said:**
> 

Notice the warning message whenb ccsm starts.
Lots of people have messed things up using ccsm, however the Ubuntu Unity Plugin seems to be safe.

Sorry I can't help with number one.

Hmm , so it would be best rather to leave everything as is ?

> **grahammechanical said:**
> Question 2: Go to System Settings>Appearance

Question 1: Go to CCSM (CompizConfig Settings Manger) and the Ubuntu Unity Plugin = Key to show the launcher.

Regards.

Thanx

---

### Post by Perfect Storm on 2012-04-29
You could try MyUnity to configure Unity. It's in Software Center.

---

### Post by grahammechanical on 2012-04-29
> Hmm , so it would be best rather to leave everything as is ?

The warning is there because starting with 11.04 certain of the Compiz effects broke the Unity user interface. And too many people were trying out these effects without knowing what they were doing.

I use CCSM to get the wobbly windows effect. No problems. I use CCSM to make the top panel transparent and likewise the launcher. No problems.

I am not that adventurous to try out anything else. Mainly because I do not understand what is supposed to happen when I select some of these effects.

If you try out one of these effects and you loose the desktop, then log out and log back in as Ubuntu 2D and then change back the changes. Compiz does not work in the Ubuntu 2D session. It is best to try out the effects one at a time.

At lot of work has been done on Compiz during the development of 12.04. I personally, think it was a mistake to make CCSM available when Unity was brought in. Each of the Compiz effects should have been tested and brought in after proving to be compatible. But CCSM is not developed by Ubuntu. And Unity was rushed in, as far as I can tell.

Regards

P.S. This link might help you a little bit.

[http://ubuntuforums.org/showthread.php?t=1892851]("http://ubuntuforums.org/showthread.php?t=1892851")

You would be testing to find out if this advice works in 12.04. :)

---

### Post by Ghost_Mazal on 2012-04-29
That MyUnity works quite nice thank you.

I had a look at ccsm , but decided not to mess with anything , not until I know what I'm doing :P

---

