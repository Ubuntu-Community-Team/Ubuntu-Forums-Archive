---
title: "Totem won't access the DVD menu"
date: 2005-07-13
forum: Desktop Environments
---

### Post by filemanager on 2005-07-13
For some reason when I put a DVD in, Totem plays it from beginning to end, I can pause and "step forward" and backward or whatever, but I can't get to the menu!! Does anyone know how to fix this?

I'm running amd64 if that makes a difference.

---

### Post by filemanager on 2005-07-14
Anyone?

---

### Post by doclivingston on 2005-07-14
The version of Totem in Hoary doesn't support DVD menus. The bleeding-edge cvs version does, so Breezy should have DVD menu support.

---

### Post by ahyden on 2005-07-15
Have you tried Go -> DVD Menu in the main menu? (or just press the 'm' key)

---

### Post by filemanager on 2005-07-16
Yes 'm' doesn't work, and neither does the choice from the menu.

That would explain it though.

Does anyone know if xine supports DVD menus?

---

### Post by Morimando on 2005-07-16
Xine should support it. It pretty much supports everything, though ^^
If you experience problems, look at the libdvdcss and other libdvd stuff ^^

---

### Post by manicka on 2005-07-16
Have you tried totem-xine?

---

### Post by RastaMahata on 2005-07-17
try totem-xine, and if that doesnt work, try vlc

---

### Post by Tuomas on 2008-06-25
Three years have passed, and totem can still not access dvd-menu or play subtitles. What's going on?

---

### Post by jualin on 2008-07-02
> **Tuomas said:**
> Three years have passed, and totem can still not access dvd-menu or play subtitles. What's going on?

Actually installing the package totem-xine solves the problem. The problem is not with Totem is with gstreamer which has no access to DVD Menus. The Xine Frontend has access to the menus. I don't know why Ubuntu chooses to work with gstreamer as the default frontend instead of using xine.

---

### Post by Einstein_101 on 2008-07-02
> jualin  	
[QUOTE]
Originally Posted by Tuomas View Post
Three years have passed, and totem can still not access dvd-menu or play subtitles. What's going on?
Actually installing the package totem-xine solves the problem. The problem is not with Totem is with gstreamer which has no access to DVD Menus. The Xine Frontend has access to the menus. I don't know why Ubuntu chooses to work with gstreamer as the default frontend instead of using xine. [/QUOTE]

If I recall correctly, Ubuntu 6.06 had xine as their default, but there were complaints on the mailing lists (or forums, I don't remember) about the devs picking xine over gstreamer. The reasoning behind the push for gstreamer wasn't because xine sucked, but because xine wasnt a part of gnome, and gstreamer was.

The funny part is the version of gstreamer at the time of the discussion was actually the first version to function properly. All previous versions were slow, had numerous memory leaks, and suffered from random crashes - which is the exact reason why the Ubuntu team went with xine in the first place.

Well 2 years have passed, and gstreamer still hasn't caught up to xine. Personally, I think this is a perfect example of knowing when to just trust the developers and let them do their thing.

---

### Post by aptperson on 2008-07-03
I have the same problem. So I followed your advice and installed totem-xine and I still cannot access the DVD menu? Do I need to remove gstreamer?
The most annoying thing is I have just upgraded to Hardy from Gusty where I had fixed this problem, but I cannot remember how.

---

### Post by Einstein_101 on 2008-07-03
> **aptperson said:**
> I have the same problem. So I followed your advice and installed totem-xine and I still cannot access the DVD menu? Do I need to remove gstreamer?
The most annoying thing is I have just upgraded to Hardy from Gusty where I had fixed this problem, but I cannot remember how.

You betcha! You don't have to remove the entire gstreamer framework, only the totem-gstreamer package.

Don't feel bad - every now and then I'll either switch back and forth between Ubuntu and Slackware, or I'll take a brief vacation into Windows XP Pro. I always remember the major processes, but it bugs the crap out of me when I forget the little things.

---

### Post by aptperson on 2008-07-03
I thought so. Thanks totem works fine now.

---

### Post by jualin on 2008-07-04
Sorry, I just got read the thread. Yes you had to remove totem-gstreamer. Glad Einstein helped you though! :lol:

---

