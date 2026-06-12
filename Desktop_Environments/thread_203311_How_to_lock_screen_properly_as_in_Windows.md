---
title: "How to lock screen properly as in Windows?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by H.E. Pennypacker on 2006-06-25
This is one of the most aching problems I've had with Ubuntu: not being able to lock the screen as I'd like it to.  Ideally, I should be able to lock the screen, close the laptop lid, open the laptop lid after returning, and type in a password to unlock the screen.  This is how it works in Windows.

With Ubuntu, I lock the screen, and all is well as long as I don't close the laptop lid.  Suppose I close it, and walk away.  If I do that, and return at a later time, the screen (the monitor) is entirely turned off, but the computer is still on.  I think it went into sleep (suspend) mode or something.  It's certainly not hibernation because the system is still on.

All I want Ubuntu to do is ask me for a password when I open the laptop lid.  For it to do that, of course, the monitor should come back on when I open the lid.  One reason I close the lid is because I am trying to make sure monitor's backlight does not decrease its lifetime (the longer it stays on, the sooner it will die).  So, turn off the monitor when I close the lid, but turn back on when I open it.

I'd like all this to happen without any keyboard work.  Just turn off and on as a I close and open the lid, respectively. 

How do I do this? ](*,)

Ubuntu 6.06
Dell Inspiron 2200
Intel i915 video card chipset.

---

### Post by porchcth on 2006-06-25
On my Samsung notebook, it works as you describe it (and as I'm used to it from Windows).
Maybe you have to set the correct action when closing the lid.
Go to System->Preferences->Power Management
and in the Running on AC / Running on Battery pages
set the option 'When laptop lid is closed'
to 'Suspend'.

Regards,

porch.

---

### Post by H.E. Pennypacker on 2006-06-25
But I don't want it to suspend.  That is the very problem I am dealing with.  You know, it doesn't really matter if it suspends or not, as long as it immediately comes back up as soon as I open the lid.  I am not concerned with system resources, just the backlight (because I don't want to buy another laptop as I did last time).  That's why I always turn off the monitor when not using it.

---

### Post by porchcth on 2006-06-25
If I use the Suspend (not hibernate) option, it takes about 10 seconds until the screen comes up again after I open the lid.
Is that not immediate enough for your purposes?

---

### Post by H.E. Pennypacker on 2006-06-25
[QUOTE=porchcth]If I use the Suspend (not hibernate) option, it takes about 10 seconds until the screen comes up again after I open the lid.
Is that not immediate enough for your purposes?[/QUOTE]

No, its not that.  The problem is that the monitor never turned back on after opening the lid.  I can't find an explanation for it, but the problem has now been solved.  I went to Power Management, and changed "When Laptop lid is closed" to "Suspend."  That has solved my problem.  

Now, I can lock the screen, close the lid, and when I open the lid, the lock screen comes back up after having turned off the monitor.  Best of both worlds.

Thanks a lot!

---

