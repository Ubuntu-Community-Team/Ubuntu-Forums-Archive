---
title: "Gnome 3 in Lucid?"
date: 2011-09-21
forum: Desktop Environments
---

### Post by pepsifx357 on 2011-09-21
I was searching through google for a tutorial for installing gnome 3 in lucid 32bit.

I found a few and went through them.  I basically destroyed my desktop and never got gnome 3 to install.  The first tutorial installed kernel 3.0.0.10 and 3.0.0.11 on my machine, with nothing else.  I didn't understand that at all! The second tutorial got dependency errors, failed to fetch this and that errors and it removed my current gnome install for a broken one that left me with X and a terminal window.  I've got it almost back to normal now using "ppa-purge."

It seems that the PPAs that they mention don't have a lucid folder nor do any of the other PPAs mentioned, so I had to add them to the sources.list and substitute "lucid" for "natty."  

Just for reference the PPA that I used was:

ppa:gnome3-team/gnome3

I can't seem to find the other one that nearly made me have to reinstall ubuntu.


So how do I get gnome 3 on my 10.04?


thanks

---

### Post by mikewhatever on 2011-09-21
You don't. The earliest Ubuntu release that's supposed to work well with Gnome3 is 11.10. Lucid has Gnome2, and if you try installing Gnome3 packages, things will break.

---

### Post by kurt18947 on 2011-09-21
> **mikewhatever said:**
> You don't. The earliest Ubuntu release that's supposed to work well with Gnome3 is 11.10. Lucid has Gnome2, and if you try installing Gnome3 packages, things will break.

Mike has it right.  People here had Gnome 3/Gnome Shell working on 11.04 but nothing earlier that I'm aware of.

---

### Post by Frogs Hair on 2011-09-21
If the PPA at the link is the one you tried  it is for 11.04 . Beware there are some outdated  PPA'S still displayed  on web pages .  
There was a Gnome Shell package in the repository , but that ran on Gnome 2.32 

[https://launchpad.net/~gnome3-team/+archive/gnome3]("https://launchpad.net/%7Egnome3-team/+archive/gnome3")

---

### Post by pepsifx357 on 2011-09-22
thanks for the info guys.

---

