---
title: "Invert colors w/o compiz?"
date: 2011-11-17
forum: Desktop Environments
---

### Post by timtaves on 2011-11-17
Now that I have 'upgraded' to 11.10 super n no longer inverts screen colors.  I have figured out a way to use the terminal to turn on compiz which then allows me to invert colors but then my system keeps crashing, especially when I have a terminal open.  I think that this is because my method of turning on compiz (compiz --replace) only partly works and leaves some unfinished process running in the background.

Does any one know how to properly turn on compiz in 11.10 or how to invert colors without compiz?  I have already tried fusion and using gnome classic and I have the same problems.

Thanks

---

### Post by svenskmand on 2011-11-22
I am also really missing the invert colors feature. Why did it get removed? Now I cannot browse the web at night due to all the bright colors :(

---

### Post by timtaves on 2011-11-22
Hey there, if you use the command 'compiz --replace' in the terminal it restarts compiz and you can invert the colors again.  The problem is that it really screws up some others things.  The terminal becomes impossible to use for example.

---

### Post by Clancy_s on 2011-11-22
> **svenskmand said:**
> I am also really missing the invert colors feature. Why did it get removed? Now I cannot browse the web at night due to all the bright colors :(

On my system choosing the high contrast theme inverse gives white text on a dark blue background.  I've not yet found a way to customise it (24 hours in to the install) but it should allow nightime browsing.

You could also see if flux works for 11.10 - it changes the colour temperature of your screen depending on your time of day and what you've told it about your lighting.

---

### Post by timtaves on 2011-11-24
Hey guys, check out this link:

[http://brainstorm.ubuntu.com/idea/1095](http://brainstorm.ubuntu.com/idea/1095)

The command:

/usr/bin/xcalib -invert -alter;

works well for me (first install:  sudo apt-get install xcalib).  Does any one know how I can run this command without opening a terminal?  Can I make a key board short cut or an icon or something?

Also, I installed the 'Blank Your Monitor' plugin in firefox.  That works nicely too.

Hope this helps.  Keep posting if there are any more ideas.

---

