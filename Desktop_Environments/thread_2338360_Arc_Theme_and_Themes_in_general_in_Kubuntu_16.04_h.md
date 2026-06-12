---
title: "Arc Theme and Themes in general in Kubuntu 16.04 have the colour palette all wrong"
date: 2016-09-27
forum: Desktop Environments
---

### Post by vdashv on 2016-09-27
Hello

Greetings! 

I'm new to ubuntu with almost limited experience in linux.

I recently upgraded to kubuntu and its amazing. Except for a few things.

I'm a huge fan of the dark themes, so you can guess how elated I was on finding an inbuilt dark theme in Kubuntu.

So I put that on and wham! The dolphin file browser has a black background (like its supposed to) but the icons are all wrongly coloured because of which they almost seem invisible! A sight for gore eyes!

I looked online for a solution and it seems the color settings, subheading "View" needed to be changed. I tried many combinations and was able to fix the background thing on dolphin at least.

I tried the bright theme too, its all fine and dandy too, until you go and select a folder in dolphin and then hover over it aaaaaand its gone! poof! dissaperado!

I chalked up the above problems on the themes themselves and went on with life. I explored the wonders of the KDE desktop environment and man is it fine. damn.

Anyways, I went off my knockers when I came across the Arc theme. Well hello there. 

I went over the github page and followed the instructions. Installed it and looks amazing, at least the part that does work though!

So as it happens to be this [https://raw.githubusercontent.com/varlesh/Arc-Dark-KDE/master/preview.png](https://raw.githubusercontent.com/varlesh/Arc-Dark-KDE/master/preview.png) is what the Arc theme is supposed to look like for people and maybe even does for many. 

This
[https://i.imgur.com/ac2mg9P.png](https://i.imgur.com/ac2mg9P.png)
 is sadly what happens for me.

FML.

:mad: :( ](*,)

---

### Post by vasa1 on 2016-09-27
> **vdashv said:**
> ... [This]("https://i.imgur.com/ac2mg9P.png") is sadly what happens for me.
...
Please note the following from the [Forum's posting guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"):> If you include screenshots, use the forum attachment system rather than an offsite host such as imgur.

---

### Post by vdashv on 2016-09-27
Done

---

### Post by Frogs Hair on 2016-09-28
Make sure gtk2-engines-murrine are installed. I've not used arc themes on KDE only Gnome.

---

### Post by vdashv on 2016-10-01
> **Frogs Hair said:**
> Make sure gtk2-engines-murrine are installed. I've not used arc themes on KDE only Gnome.


on doing

```
sudo apt-get install gtk2-engines-murrine

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk2-engines-murrine is already the newest version (0.98.2-0ubuntu2.2).
gtk2-engines-murrine set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

```

---

### Post by vdashv on 2016-10-29
Bump

---

### Post by Frogs Hair on 2016-10-30
I see special instructions for Kubuntu 16.04 in the readme file included with the theme  , did you use those instructions ?

---

