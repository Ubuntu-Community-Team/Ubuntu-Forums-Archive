---
title: "No sound in Javva"
date: 2008-06-28
forum: Desktop Environments
---

### Post by PseudoOne on 2008-06-28
Previously I was able to access Java applets across the web *with* sound, but for some reason it has stopped working.  I have installed Java by Sun Microsystems from the Ubuntu repository (including JRE, packages "sun-java6-bin" and "sun-java6-jre").  I have reinstalled the packages, but with no success.  Sometimes the sound will load but the applet will not ("applet bail").  I have **only** used Java on the MMORPG "*RuneScape*".  The graphics usually load, but now the sound doesn't, other times the applet only displays as a grey-coloured box.  (I am using Mozilla Firefox, Java is enabled).

Browser + Version: Mozilla Firefox 3.0
OS: Hardy (Kubuntu) with KDE 3.5.9 (I do have KDE 4, but it has other issues that cause it to be unusable).

I have tried restarting the sound system, but the sound works OK in the desktop environment, but not in any Java applets. (It does work with Adobe Flash).

I have not tested icedtea Java.  

> java -version

*yields:*

> 
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)


I have heard the VM (Virtual Machine) does not work well in Ubuntu, but I have found no official response.  Any workarounds for this?  Note: It had been working *before* I restarted my computer. (After a power failure, but I believe this to be irrelevant).  Graphics and sound had been working before, and occasionally the graphics **do not** load, although the sound had, now, sometimes the graphics do not load, (there's still no sound), or only the graphics load in the applet (Java's problems can be a nuisance).  Would the solution be to use a different compiler/runtime environment/virtual machine? Or is there something else that needs done? Thanks to anyone who can help me, this is rather a depriving situation. :(  (I hope this is not an *exact* duplicate, I could not find any threads that helped, and I hope this is in the correct category).

Thanks :)

EDIT: Sorry about the misspelling in the title :(

---

### Post by Samhain13 on 2008-06-29
Hi.

I play Runescape too, sometimes. I can't offer you a solution to the sound problem. But about the grey box, it seems that selecting "Signed Applet Using SUN Java" has better chances of getting the game to load. However, I'm on Ubuntu and not Kubuntu, using Firefox 3 also. And on my end, "java -version" yeilds:

> java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)

Runescape sounds work fine. But I do experience sound problems when using other Java applets.

---

### Post by PseudoOne on 2008-06-30
I don't see an option for that as right clicking the java applet will give a standard FF right-click menu.

---

### Post by Samhain13 on 2008-06-30
The option is on the webpage. Here's a screenshot...

---

### Post by Vinegarcat on 2008-08-17
Could you post a larger image of that?  I heard the same thing, but I don't see it on the page.

---

### Post by DannyW on 2008-08-17
> **Vinegarcat said:**
> Could you post a larger image of that?  I heard the same thing, but I don't see it on the page.

Select 'Java Options' from the 'Play Now' menu on the menu bar at the top.

---

### Post by xjb2003x on 2008-09-02
I have the same problem whenever I play the game too.  I use Ubuntu and for me, when I have another application loaded that uses sound, java sound will not work.  It will work if I close out the other application and reload.

---

