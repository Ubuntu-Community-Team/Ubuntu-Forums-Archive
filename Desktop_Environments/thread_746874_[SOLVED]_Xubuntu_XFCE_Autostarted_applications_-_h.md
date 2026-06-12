---
title: "[SOLVED] Xubuntu XFCE Autostarted applications - how to EDIT"
date: 2008-04-06
forum: Desktop Environments
---

### Post by Spunner on 2008-04-06
I have googled my fingers off - cannot find this one: ](*,)

I have somehow managed to get "Volume Manager" in my autostarted applications on my main machine.  I would love to be able to enable it on my other ones...

How do I EDIT the entry to find out which command is given, which volume manager it is. (I have thunar-volman installed on both machines, and I have commented out those lines around line 40 to do the magic to get USB working, but still don't know how to get my USB devices to be automatically recognised on my other machines...

Applications --> Settings -- > Autostarted Applications, I can ADD or REMOVE, but not VIEW or EDIT...

Any gurus out there?  (I'm going into my 2nd month with linux - it's been a steep learning curve, but very rewarding)

---

### Post by mdramige on 2008-04-06
/home/user/.config/autostart contains the launchers that I've added myself in the Autostarted apps GUI. I'm still looking for the others.

---

### Post by Spunner on 2008-04-06
Yep, found that one - but not the rest...  thanks for the post... anyone else??  :)

---

### Post by Spunner on 2008-04-09
HELP??

Is this the right place to post this one?

---

### Post by sardion on 2008-04-13
So I don't have xubuntu anymore, but I remember this problem.

If you do the following in terminal

locate autostart

you will probably find them.

It's something like /etc/xdg/autostart

There's definitely an xdg in there, so als try

locate xdg


Hope that helps (and yes it is the reight place to ask)

---

### Post by Spunner on 2008-04-13
Thank you, thank you, thank you!!  You get 3 gold stars.

One for answering my question (although there really should be an edit function - should I do a bug report?)

Two for introducing me to locate.  As I said, I am new to linux.

whereis is only so helpful, so I have resorted to using:

```

cd /
sudo find | grep autostart
```

where a simple locate autostart is much faster!

PS: Yes, they are in /etc/xdg/autostart/ - all in .desktop files.

---

