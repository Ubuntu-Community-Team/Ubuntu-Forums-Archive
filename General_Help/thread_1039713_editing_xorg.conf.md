---
title: "editing xorg.conf"
date: 2009-01-14
forum: General Help
---

### Post by roystreet on 2009-01-14
Hello, I'm fairly new at Linux.  I've dabbled in Linux some in the past.  OK, the scenario: I'm trying to edit xorg.conf to enable my mouse buttons.  I'm following a thread found in one of the forums, so don't worry, I'm not just trying it out.  The thread explains that I must edit that file after backing it up. I can edit it just fine & dandy, but I can't save it.  I have kubuntu and I don't have gedit.  So I've used kate to edit it.

Any thoughts?  Remember I'm new :). If there's a better editor for this type of stuff, please let me know.  I'm imagining it's because I'm not editing as root?  

thanks for your help,
~roystreet

---

### Post by MCrittenden on 2009-01-14
You'd be correct. You have to edit as root.

Easiest way is to open up a terminal (Applications -> Accessories -> Terminal), type "sudo kate /etc/X11/xorg.conf" (obviously without the quotation marks), and that will let you edit xorg.conf as root so you can save. Hope that helps.

---

### Post by NT4usB on 2009-01-14
I don't use kate (vi user) but if it's not a graphical editor```
 sudo kate xorg.conf
```

---

### Post by roystreet on 2009-01-14
> **MCrittenden said:**
> You'd be correct. You have to edit as root.

Easiest way is to open up a terminal (Applications -> Accessories -> Terminal), type "sudo kate /etc/X11/xorg.conf" (obviously without the quotation marks), and that will let you edit xorg.conf as root so you can save. Hope that helps.

Now when I was trying to figure this out before I posted this, I thought I had tried that in terminal...But just maybe I typed that incorrectly.  I will try when I get home.


A question for you to add on to this...Should I use kate or should I a different editor?

---

### Post by dcstar on 2009-01-15
> **roystreet said:**
> 
.........
A question for you to add on to this...Should I use kate or should I a different editor?

It doesn't matter.

---

