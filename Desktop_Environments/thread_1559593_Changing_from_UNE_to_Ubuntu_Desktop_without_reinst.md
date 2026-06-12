---
title: "Changing from UNE to Ubuntu Desktop without reinstalling?"
date: 2010-08-23
forum: Desktop Environments
---

### Post by crjackson on 2010-08-23
I got a Gateway Netbook for the wife.  Installed UNE 10.04.  Wife hates the interface and wants it to look like her full sized laptop.

I went into synaptic and installed ubuntu-desktop.  I can't figure out how to get the ubuntu-desktop interface to load and the ubiquity interface to go away.

How can I do this without having to reinstall everything?

TIA

---

### Post by KdotJ on 2010-08-23
Hey, you'll be happy to know the answer is simple (and didn't even require installing ubuntu-desktop metapackage).

When the netbook boots up, and gets to the GDM login screen, click on the username but don't log in just yet... at the bottom of the screen, see the little menu labelled "Sessions", simply select "GNOME" from this menu. Then continue to log in... should do the trick

---

### Post by crjackson on 2010-08-24
> **KdotJ said:**
> Hey, you'll be happy to know the answer is simple (and didn't even require installing ubuntu-desktop metapackage).

When the netbook boots up, and gets to the GDM login screen, click on the username but don't log in just yet... at the bottom of the screen, see the little menu labelled "Sessions", simply select "GNOME" from this menu. Then continue to log in... should do the trick

You know I looked for a sessions icon but couldn't find it.  I guess I needed to click on the login name for it to appear.  Is there a way to make that the DEFAULT so it won't have to be selected each time?

When I installed the ubuntu-desktop package, I noticed it removed an alsa package.  Do u suppose I screwed something up?  I don't remember what alsa package it was.

I wonder if I should remove the ubuntu-desktop package then?

---

### Post by KdotJ on 2010-08-24
> **crjackson said:**
> You know I looked for a sessions icon but couldn't find it.  I guess I needed to click on the login name for it to appear.

This is true, you need to select the username first before Sessions appears

> **crjackson said:**
> Is there a way to make that the DEFAULT so it won't have to be selected each time?

I'm pretty sure that the one you select will be remembered for future logins

> **crjackson said:**
> 
When I installed the ubuntu-desktop package, I noticed it removed an alsa package.  Do u suppose I screwed something up?  I don't remember what alsa package it was.

I wonder if I should remove the ubuntu-desktop package then?

I shouldn't think anything was messed up by this, though you may have "Ubuntu Desktop" as an option on the Sessions menu, but this is the same as GNOME really. As for the package it removed, it might of been the netbook-remix metapackage? Does everything work ok still?

---

### Post by crjackson on 2010-08-24
You are correct.  The session remained as the last selected.

Everything seems to work as expected and the wife seems pretty happy with it.  The only issue I have is that when she needs to print a PDF document from acroread, the bottom part of the printing dialogue is cut off and there is no way to see/click the ok or cancel buttons.

If you have any thoughts on that, I'd love to hear them...

---

