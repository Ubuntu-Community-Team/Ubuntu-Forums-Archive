---
title: "Desktop effects could not be enabled"
date: 2009-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jmegie on 2009-11-09
I just installed 9.10 on my Dell Latitude E5500. It has an Intel Mobile 4 integrated graphics controller.

Everything video related is flawless until I dock at the office with two 17" wide screen monitors. Once docked, I'm able to get dual screens appropriately and even get proper resolutions with no headache. But the visual effects are set to none. If I try to enable Normal, Extra, or Custom (which is what I typically use) it attempts to enable it and then says "Desktop effects could not be enabled."

The effects work perfectly on the laptop when it is un-docked. I've looked around and found various people with the same issues, but no solutions posted.

Any help is appreciated. Xorg.0.log file doesn't show any errors.

---

### Post by NotWindowsXPagain50 on 2009-11-09
The card is not able to have 2 monitors at a time

The known solution: Upgrade your graphic card!


:D[Post By NotWindowsXPagain50]("http://ubuntuforums.org/member.php?u=951051")

---

### Post by jmegie on 2009-11-09
The card does in fact support dual monitors - both of my displays work. That doesn't really make any sense, since it worked in 9.04.

Also, this is a laptop, so I can't upgrade the graphics card.

---

### Post by teward on 2009-11-09
Okay, first, it might be because its an Intel card.  I have a Dell Latitiude E6500, without a docking station though, and I have it working with multiple monitors (the one with the laptop, and an external one).  I have an nVidia card, though.  Perhaps it's the Intel integrated graphics card... I know that Intel graphics cards are not the best in the world.

However, I can use desktop effects (except when programming in Java; the program I use doesn't like the effects from compiz and whatnot) on **both** monitors.  As for why it doesn't work, perhaps it has something to do with 9.10, and not the computer itself.  What specifically the problem is, I don't know (I use 9.04, and I don't have the problems that 9.10 has).

**EDIT:

Is it possible that the problem stems back to the docking station itself?  Perhaps the docking station uses different graphics connectivity, and thus different graphics drivers, and those different drivers are not compatible with desktop effects.

END EDIT**

---

### Post by jmegie on 2009-11-09
Yeah, I'm thinking it's a 9.10 problem since it was working in 9.04. Unfortunately the E5500 model is only available with an Intel card (boo), so I was stuck since that's the only model our company orders.

---

### Post by NotWindowsXPagain50 on 2009-11-09
Maybe a problem with driver?:D

---

### Post by buggybugg on 2009-11-09
The same here. HP - Laptop on a dockingstation, I assume it has something to do with the version of compiz in karmic.

What I did to test was run the command compiz --replace

```
bbg@HP-Laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2304x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 
```as you can see, compiz doesn't like my screen resolution (2304 because first display width 1024 and second 1280) I think thats the problem but don't know how to fix it. Maybe a bug??

---

### Post by teward on 2009-11-09
I think it's a problem with the use of a docking station and 9.10.  So many people believe 9.10 was released really really early, before it was ready.  Kinda like Windows Vista was.

**EDIT: For HP computers, go post in general support.  This forum here (at least this subforum) is for Dell support. **

---

### Post by nihonbun on 2009-11-09
I use a dell 1545 as well, and I can't get desktop effects to work in 9.10 even with just the laptop.

---

### Post by jmegie on 2009-11-10
I think you're correct with it having something to do with the docking station. I messed around all day yesterday and was not able to get it to work the way I wanted it to.

I took my laptop home last night and used it (off dock) and had all my enhancements.

Now here's the kicker - I got to work this morning, docked it, and wouldn't you know it, my enhancements are all fully functional on both monitors.

I have made no changes what-so-ever. All I did last night is surf the web and do a little homework.

I'm baffled as to how it just started working on the dock.

---

