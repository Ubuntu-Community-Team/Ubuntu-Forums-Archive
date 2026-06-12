---
title: "Eeeeek!  KDE meltdown"
date: 2005-03-25
forum: Desktop Environments
---

### Post by Declan on 2005-03-25
Hi all,

There was me with my hoary gnome based system, and all was well (or almost all).
I think the only kde type thing I had was K3b.  It worked.
Then one day I installed kubuntu-desktop, and I found it to be nice, much nicer than previous kde's.  So I was thinking of keeping it, and maybe alternating gnome-kde as the mood took me.  
And I was beginning to see why Amarok is so well received.

Then the next day (yesterday):
(a)  I did a dist-upgrade
(b) logged into kde and decided to change the colour scheme.

As soon as I went into that the whole system siezed up.  I could see from the led on the computer that something was happening, but I was unable to achieve anything on the desktop, except occasional movements of the cursor.  I couldn't, for example, change virtual desktop.  Nor could I change into a terminal session with CTRL - ALT - F4, as I often do.  

After waiting a respectable length of time, I had to manually power off.  I don't like doing that one bit.

Since then any kde type application I've tried produces this system locking result.  I've tried amarok under gnome and kde a few times, as well as konqueror in both, and ark under gnome.  
On all occasions I've had to manually power off.  

This can't be good.

Any ideas where the problem may be?
Please speak newbie-ese.  Thanks,

[PS: I searched and found that Andre reports a similar problem elsewhere on this forum, but my version may be a bit worse, so maybe it's different].

Declan

---

### Post by Declan on 2005-03-25
A few little questions:

What can happen to the system when one manually powers down.  Obviously filesystems are not unmounted etc.  Is it as bad as I imagine it is?

Is there a safer way to stop the system?  Bear in mind that I can't even get the command line.  Otherwise I would do "shutdown -h now" with sudo.  But I can't do that.

What are the most obvious ways to check where the difficulty lies?  

Thanks,

Declan

---

### Post by Stephen-I-M on 2005-03-25
Unless X is frozen, and it might have been in your case, cntrl-alt-backspace kills the xserver and drops you to the console. Also, cntrl-alt-f2 through f6 will give you consoles, and to get back to the X session type cntrl-alt-f7.

Stephen

---

### Post by ac_dispatcher on 2005-03-25
My Kubuntu Laptop is behind my firewall.  I run sshd on it so in the case of a lockup I can access the box via ssh (or putty in windows).

I usually run "top" in another box to monitor my Laptop. At imes X has froze up and cntrl+alt+back has not worked.  In ssh I was able to stop X or in drastic times reboot the system.


btw the lockups were my fault (trying new stuff) :grin:

---

### Post by Declan on 2005-03-25
Yes, I was trying CTRL - ALT and Backspace, and CTRL - ALT and F4.  But they weren't working.  
Actually, I later discovered that CTRL - ALT and Backspace does indeed work, if I'm willing to wait for about 20 minutes.
I gather from this that the X server is not completely dead.  That and the fact that the cursor can still be moved (occasionally).

The non-KDE stuff seems to be working fine though.  

Then, to add to my troubles, the CD-Rom drive appears to have packed in.  I hope it hasn't, since the thought that in a worst case scenario I can always revert to a Live CD has always been a comfort to me.

Thanks.

Anyone have an idea where the problem might lie?

Declan

---

### Post by Declan on 2005-03-26
Here I am again.  Having a grand chat with myself.

So... supposing that KDE stuff is not going to work for me, would a traditional uninstall - reinstall work?  
What are the key packages that might be involved in messing up my X sessions (if that is what is happening?).  Or is there a way to remove all KDE stuff in one or two fell swoops?

Thanks!

Declan

---

### Post by arctic on 2005-03-26
try to remove all your hidden kde related folders &#8594; /.kde /.qt etc. then try to restart your session. does it crash again? if yes, there must be a serious memory leak somewhere and you should report the bug to the developers.

---

### Post by Declan on 2005-03-28
Arctic, thanks.  Deleting those files did the trick, and all is back to normal.  
I was reluctant in the past to touch the .* files, but I gather now that whatever programme uses them simply regenerates them if they're missing.  Which is good to know.  Thanks again,

Declan

---

