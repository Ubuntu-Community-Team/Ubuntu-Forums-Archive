---
title: "[SOLVED] Evolution Help"
date: 2008-12-28
forum: General Help
---

### Post by Otto-C on 2008-12-28
I setup Evolution  "evolution --version GNOME evolution 2.22.3.1on" my laptop using current instructions. I have Hardy 8.04.1.
When I try to send I get a box Send & Receive showing:

name ...Yahoo.com (Pop)
waiting (then a progress bar)     X Cancel

SMTP: smtp.yahoo.com
Sending message 1 of 1 (then a progress bar)     X Cancel
                                                 X Cancel All

Have no idea what this means or how to correct it. Help!

tia
otto-c

---

### Post by exploder on 2008-12-28
Try changing the incoming server to mail.yahoo.com and see what happens.

---

### Post by Otto-C on 2008-12-28
Incoming was set to mail.yahoo.com. I get the idea of the box now.
However after it finishes.
name ...Yahoo.com (Pop)
waiting (progress bar fills in) X Cancel

this process takes several minutes.Then goes onto the next.

SMTP: smtp.yahoo.com
Sending message 1 of 1 (then a progress bar) X Cancel
                                             X Cancel All

This process never completes.

---

### Post by I wanted to leave on 2008-12-28
> **Otto-C said:**
> Incoming was set to mail.yahoo.com. I get the idea of the box now.
However after it finishes.
name ...Yahoo.com (Pop)
waiting (progress bar fills in) X Cancel

this process takes several minutes.Then goes onto the next.

SMTP: smtp.yahoo.com
Sending message 1 of 1 (then a progress bar) X Cancel
                                             X Cancel All

This process never completes.

These are the settings I use...

pop.y7mail.com Incoming
smtp.y7mail.com Sending

I think these settings are subject to your location and Yahoo

---

### Post by Otto-C on 2008-12-29
I'm on the NE coast of Florida. Florida's First Coast.
While I tried your y7mail from the address bar it went into
my yahoo account. However, when I changed entries in  evolution
it asked for passwords to y7. I used my yahoo passwords to no
avail. Tried several combinations. No joy.
Returned settings to mail.yahoo.com setting. Now in a loop
asking for passwords???

tia
otto-c

---

### Post by I wanted to leave on 2008-12-29
Sorry it didn't work for you. 
Just be sure that you have deleted all settings for pop and smtp servers from evolution, and keep trying. 

Perhaps you could check your Yahoo mailbox for suggested settings :)

---

### Post by Otto-C on 2008-12-31
Thanks to all who responded to this item.

I'm informed the pop accounts are available on
Yahoo's pay accounts.

This item is closed.

Otto-C

---

### Post by dcstar on 2008-12-31
> **Otto-C said:**
> Thanks to all who responded to this item.

I'm informed the pop accounts are available on
Yahoo's pay accounts.

This item is closed.

Otto-C

I have a free Yahoo.com.au mail account with POP (that works fine with Evolution), I just had to set up the POP option on the Yahoo site.

If you want to use the Yahoo SMTP server you need to set the login credentials in that part of the Evolution account setup (it is easier to use your ISP's SMTP server).

---

