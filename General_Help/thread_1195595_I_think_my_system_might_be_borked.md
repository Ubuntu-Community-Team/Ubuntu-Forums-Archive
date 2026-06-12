---
title: "I think my system might be borked"
date: 2009-06-24
forum: General Help
---

### Post by mechanicalturk on 2009-06-24
I borked something bad.

When I try to use the mouse left clicking doesn't seem to work consistently.  Wherever I move the mouse the tool tip shows up displaying:

```

I'm having some serious boot issues so I'm trying to reinstall grub
through the Ubuntu LiveCD.  I'm a little confused over something.  sudo
fdisk -l yeilds the following sda1 - * (boot) - NTFS (Vista) sda2 - 
Extended sda5 - Linux Swap sda6 - Linux Root sda7 - Linux Home

```

WTF?

And when I try to use the update manager, I get this...

[[IMG]http://img193.imageshack.us/img193/5227/screenshotfag.th.png[/IMG]](http://img193.imageshack.us/i/screenshotfag.png/)

Also imageshack hates me (look at the URL)

FML


Edit:  It appears that the above tooltip was from the post below mine in the forum.  So now I think my system is just borked rather than compromised.  Old tooltips follow me around and I can't left click much.  I'm still confused.  Keyboard works great though.

This is a sudden problem.

---

### Post by mechanicalturk on 2009-06-24
More information:

It seems to be confined to window manager related clicks/movements and seems to be a focus problem.  Usually if I right click on a spot just before I left click on the same spot it works.

Additionally, if I load up say OpenArena, left click works (makes me shoot) there every single time.

I have tried switching between compiz and metacity, and both appear borked in the same way.

Let me know what other diagnostic information it would be useful to provide.

---

### Post by jimv on 2009-06-24
This sounds silly, but have you tried rebooting?

---

### Post by mechanicalturk on 2009-06-24
No, not silly at all.  I restarted X first with ctrl+alt+bcksp, that didn't fix it.  Soft reboot with ctrl+alt+del didn't fix it.  Hard reboot with turn off and leave for a bunch of time didn't fix it.

Replacing the batteries in the mouse didn't fix it.  As far as I can tell, there aren't any extra processes running when I check using ps -A, and xwininfo -root -tree doesn't seem to show anything strange either.  

The strange thing is, even at the greeter window for login, trying to click on options doesn't work, and the on-mouse-over highlight doesn't occur for a while.

Seriously flux0red as I don't remember making any config changes recently.  The last thing I did was install and run pokerstove through wine, and that doesn't seem like the sort of activity that would result in this strange problem.

I'm going to try plugging in a different mouse.

---

### Post by mechanicalturk on 2009-06-24
Strange again.  A wired mouse seems to work with no problems, but I plugged the wireless one (with fully charged rechargables) into the upstairs computer running Windows, and it works fine.  

Actually, there was this one time where Gnome was constantly reporting that the battery in the mouse was low - even with brand spanking new batteries.  It might be related.

Anyway, I'll just switch the mice.

---

### Post by jimv on 2009-06-24
Could be the mouse...my bluetooth mouse was always freaking out in Ubuntu even though it was fine in Windows.  I ended up getting a corded mouse anyway, as I hate dealing with batteries.

---

