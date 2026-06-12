---
title: "Desktop Icons Have Disappeared"
date: 2009-09-24
forum: Desktop Environments
---

### Post by EmyrB on 2009-09-24
Hi All,

Just a quick one, I changed my monitor last night to a wide screen 19". I changed the resolution to the correct one, but the Icons I had on my desktop have disappeared. If I try and create new ones, they too don't appear. I seem to remember that I have a corrupt file somewhere in my home directory, but for the life of me I can't remember. Any ideas?

Cheers

EmyrB

---

### Post by sedawk on 2009-09-24
You can try to create a new user and login to the
desktop of that new and fresh user.
Check if you have the same problem with the new user.

---

### Post by EmyrB on 2009-09-25
Hmmm, why didn't I think of that :) I shall give that a try.

Cheers

EmyrB

---

### Post by EmyrB on 2009-09-28
OK, sorry about the delay, only now I have had time to create a new user. The new user profile shows icons on the desktop, so I guess my old user is corrupt or just a config file for Gnome.

I don't want to create a new user profile and tweak it again, so if anybody can tell me what file(s) I need to recreate, I would be very grateful :D

Cheers

EmyrB

---

### Post by H4F on 2009-09-28
Same problem I have. All icons of desktop have disappeared . Some time I rebooted they work . some time they don't. don't even know what to start from

---

### Post by Simian Man on 2009-09-28
Sounds like a problem with nautilus - the file browser that also controls the desktop.  You can try moving or deleting ~/.nautilus and logging back in.

---

### Post by blur xc on 2009-09-28
Desktop icons are so Win 98...

j/k

BM

---

### Post by EmyrB on 2009-09-29
Hey Simian Man, that was it, I renamed /~nautilus to nautilus.old and logged out and back in again and all my desktop came back.

Edit: How do I mark posts as solved?

Cheers

EmyrB

---

### Post by EmyrB on 2009-09-30
Unfortunately, I spoke too soon. Tonight, I logged into my profile and no icons on the desktop :(

The metafiles folder inside the new /~nautilus folder only has two files, whereas the original created when I setup the PC has 61 files.

Can I copy them over to the new folder?

Cheers

EmyrB

---

### Post by OrbitEleven on 2009-11-04
I'm having the same issue. Logging out and back in helps, but it doesn't stick

---

### Post by thockin on 2010-01-20
This happens to me about once a week.  It's pretty darn annoying.

---

### Post by etfloyd on 2010-01-26
Same symptom happens to me every couple of days. Icons will just disappear. Typically, an hour or so later, gdm will simply stop responding to mouse clicks and keyboard.  Mouse still moves, just can't do anything.  The only way back is to restart gdm (ctrl-alt-bksp) - everything comes back to normal for a while, but the restart crashes all in-flight desktop apps, of course. Most annoying! (FWIW, I'm running Karmic 64-bit with the latest updates.  I've been trying updated kernels [most recently 2.6.33-020633rc5-generic] to see if that would help, but it happened again a few minutes ago, so no joy. I can't find any symptoms in the logs - it just stops working, silently.)

---

