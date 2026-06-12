---
title: "Can't get AWN to start"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by rsteckly7 on 2007-12-22
Hi,

I know there are some posts out there on this, but I'm really lost.  I am running Xubuntu with compiz-beryl.  I installed Awn Manager by using the work around for Gutsy Gibbon, namely adding the repositories, updating the package list, and then downloading the package.

I also added awn to my auto starting applications.

When i start, I see a small box pop up in the upper left corner.  there is a small flicker on the bottom of the screen, but nothing happens.  I unchecked hide when not in use, but I can't think of anything else to do.

Also, do any of you know what it means when you uncheck have XFCE manage my desktop?  Its really strange because I then can't see my files.  What is that feature for?

---

### Post by Nano Geek on 2007-12-23
Run this in the terminal and tell me what it says/does. ```
 avant-window-navigator
```

---

### Post by rsteckly7 on 2007-12-23
Okay.

I ran it in Terminal and it says Screen isn't composited.  Please run compiz or another compositing manager.  I thought I was running compiz, though...

---

### Post by Nano Geek on 2007-12-23
Try running this now. ```
compiz --replace && avant-window-navigator
```

---

### Post by rsteckly7 on 2007-12-23
It says no whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by fwaokda on 2007-12-23
you need to make sure that in visual effects, under appearances, that it is set to something other than "none". Hope that was an easy overlooked problem that'll get you up and running. ;)

---

### Post by rsteckly7 on 2007-12-23
Solved....sort of.  You were quite right about the visual effects.  The problem was when I went in to check visual effects, I received an error message that they could not be enabled.  So, I went in and installed xgl, restarted, enabled visual effects and lo and behold the awn dock is there.

The only problem I'm having is that the computer is not very responsive now.  It is quite slow--I have an Everex Stepnote 1501 with a VIA Chrome 9 chip.  Its not the greatest chip in the world, although I'm surprised at how unresponsive it is.  Any thoughts?  Should I uninstall xgl?  (how would I do that btw?)  If there is no work around to make things more responsive, I'm going to have to do something...

---

### Post by Nano Geek on 2007-12-23
No, I'm afraid XGL is your only option with Compiz.

However, you could try XFCE's built-in compositing manager. 
It's not as fancy as Compiz but it will let you use AWN.

---

