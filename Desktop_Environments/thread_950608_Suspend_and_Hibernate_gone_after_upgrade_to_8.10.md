---
title: "Suspend and Hibernate gone after upgrade to 8.10"
date: 2008-10-17
forum: Desktop Environments
---

### Post by jdfoote on 2008-10-17
Ever since I upgraded my 8.04 install to Intrepid Ibex, the suspend and hibernate options have disappeared.

Any ideas about why, or how to get them back?

---

### Post by smylie on 2008-10-18
Yup - disappeared on my laptop too. Guess that's why it's a beta =)

I'll log a bug report for it, but in the interim, you can suspend by using the command pm-suspend from a terminal.

(And probably by pushing your computers suspend button if it has one)

---

### Post by brianfreytag on 2008-10-18
Go to System -> Shutdown

You'll find those options right there.  They aren't there when you click your name at the top right.

Enjoy.

---

### Post by XMAG on 2008-11-10
System > Shutdown does not show the suspend option, the 3 options it shows are Shutdown Restart and Hibernate.

[http://www.dedoimedo.com/images/computers/ubuntu-8.10-shutdown-2.jpg](http://www.dedoimedo.com/images/computers/ubuntu-8.10-shutdown-2.jpg)

The dropdown menu from User Switch shows these 3 and Logout, but not Suspend

Where did it go?????????????????????????

---

### Post by smylie on 2008-11-10
I believe ubuntu removes the suspend option if it doesn't think it will work on your laptop.

I'm not sure how to get it back, (other than maybe rebooting to see if it was a temporary glitch), but you can at least test if it's working by calling it manually from a terminal/console:

$ sudo pm-suspend

Cheers
Dave Smylie

---

### Post by XMAG on 2008-11-10
I'm on a Desktop here, but maybe that's it, because the command does nothing to my computer

---

### Post by smylie on 2008-11-10
Whoops. Desktop/laptop  .. .  should be able to suspend both provided they're not ancient...

Cheers
Dave Smylie

---

### Post by XMAG on 2008-11-10
My motherboard is ASUS P4XP-X and the CPU a Pentium 4 1.8Ghz

---

### Post by smylie on 2008-11-10
did you try pm-suspend from a console?

---

### Post by XMAG on 2008-11-10
yes, from a root shell and with sudo, neither worked

---

### Post by smylie on 2008-11-10
didn't work as in, no command found?  or didn't work as it ran, tried to suspend, but failed?

If it's the latter, I suspect you've found the reason that suspend isn't present on the list...

---

### Post by XMAG on 2008-11-10
no, it simply does nothing, no command not found message and nothing happens, i just get a new shell prompt

---

### Post by smylie on 2008-11-10
Sounds like it's the latter (suspend failing).

Not promising - but you could take a look at  /var/log/pm-suspend.log and you might get some clue as to what's going on.

Cheers
Dave Smylie

---

