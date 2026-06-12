---
title: "Foolproof Ubuntu config for non-computer user?"
date: 2009-06-22
forum: General Help
---

### Post by B34N on 2009-06-22
I need to get my father-in-law setup with a new laptop which he will use for nothing more than browsing financial websites and reading e-mail.  I plan on switching him over to Ubuntu running Firefox and Evolution.  The main reasons why I'm switching him from Windows is to speed up boot time and eliminate all of those annoying pop-ups reminding him to upgrade software or renew his contract to Norton.

Is there a way that I can configure Ubuntu to not prompt the user for software updates and instead do the updates automatically or only on demand?  What potential dangers am I facing if I did it this way as opposed to the weekly reminders?

Are there any other admin settings that I should consider?

What remote software should I install so that I can remotely control his laptop from one of my systems?

Thank you!

---

### Post by madverb on 2009-06-22
What's the good of Ubuntu if they don't use a computer?

---

### Post by B34N on 2009-06-22
> **madverb said:**
> What's the good of Ubuntu if they don't use a computer?

Thank you for pointing that out. :o I changed "non-computer" to "non-savy" in the subject line.

---

### Post by ugm6hr on 2009-06-22
There is an option in System -> Admin -> Software Sources (Updates tab) to allow you to automatically install security updates in the background.  No real dangers with this; he just won't know when it is happening.

If you want to maintain remote access to his desktop, why not set him up as a limited user (obviously with access to all disks and devices)?  You could then administer everything using ssh and VNC yourself.  If you are not on the same LAN, you would have to set port-forwarding on his router to allow you access.

If you would prefer to just help out from time to time when he is stuck, consider gitso:
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

### Post by madverb on 2009-06-22
Hehe, let's get serious though. If you need to access his Laptop in a GUI you can use VNC.
System > Preferences > Remote Desktop. Need port 5900 open to his Laptop to do that.
Or you can use SSH which is command line. You might just want to do a quick search on it.
Doing automatic updates shouldn't be a problem. You could look at running it using cron. To make it really easy you can install gnome-schedule and create it that way.

Edit: Figured there would be an easier way to do auto-updates... Now I know too. Cheers, ugm6hr

---

### Post by B34N on 2009-06-22
Thank you for the quick responses.  It was exactly the information that I was looking for regarding the updates.  I'll search for other threads on VNC and remote graphical admin.  I'm not on the same network so I'll have to play around and open some ports.  Most of the time the user will be on their home or office network (which I have control of the routers) but some times they may be on a hotel network or such.

Now I need to find the user a laptop which is the equivalent of a netbook with a 17" screen.  i.e. lightweight, SSD and few features.

---

