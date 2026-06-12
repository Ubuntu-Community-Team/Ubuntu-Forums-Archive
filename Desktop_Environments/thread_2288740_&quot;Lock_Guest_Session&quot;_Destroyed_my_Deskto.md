---
title: "&quot;Lock Guest Session&quot; Destroyed my Desktops"
date: 2015-07-29
forum: Desktop Environments
---

### Post by ScottCh on 2015-07-29
Hi All,

I have a recent install of Ubuntu 14.04 on my laptop.  I got up from my desk recently and intended to lock my desktop session.  As occasionally happens the mouse moved a little when I made the menu selection, and I accidentally clicked the "Lock Guest Session" menu entry instead of locking my own desktop session.

When I returned, I went to unlock my laptop and I found that the desktop now showed a guest session.  An informational popup on the display told me that I was using a guest session and would have limited access.  I used the settings menu to change back to my own user's session, and this started a weird sequence of events.  First the screen blanked completely.  A few seconds later, the GDM display appeared and prompted me for the password on my account.  After I entered my password, the display blanked again, this time for several seconds.  Then GDM returned, and prompted me to log in yet again.  I re-entered my login information, and the screen blanked for a few more seconds.  Then it showed the Ubuntu splash screen, and gave me a new desktop session. 

So the applications and desktops from my previous user session had all been killed.  This seems like a rather drastic result for having clicked something as innocuous as "Lock Guest Session".  What does that even mean, if no guest session exists?  It seems odd to me that this option is even available.  How can one lock a guest session when there is no guest session on the system?  This menu selection is always present in the settings menu on my system.

My intention was not to voice a whiny complaint here...  Well, not if something constructive can come out of it.  Does this menu selection have a purpose?  Is this how it's intended to work?  If not, is there a straightforward way to remedy what happened on my system?

Thanks,

Scott C.
Cary, NC USA

---

### Post by CantankRus on 2015-07-29
In 14.04 unity I see  "lock/switch account" which is the same as bringing up the screen locker with ctrl+alt+L or Super+L.
From the same menu I can also switch between the guest account and my account with both desktops remaining as I left them.
Same behaviour as you see, except I only need to log in once to get back into my account and the desktop is as I left it.

Don't know the cause of your issue but I have no problems here.
Possibly your compiz settings, if you have altered them.
Try creating a new account and see how switching between the new and guest account behaves.

---

### Post by ScottCh on 2015-07-30
Well this is odd.  My menu selections are different (image attached).  Seems like a clue.

I have changed some Unity settings to reduce the amount of memory utilization due to there being only 2 GB of RAM in this computer.  I don't think that reducing the number of virtual desktops would have caused this.  

Since these appear to be nonstandard menu selections, I'll do some searching to see what could have caused them to change.

Thanks,

Scott C.

---

