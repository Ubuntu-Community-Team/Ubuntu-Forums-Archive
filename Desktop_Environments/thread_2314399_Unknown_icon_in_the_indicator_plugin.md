---
title: "Unknown icon in the indicator plugin"
date: 2016-02-20
forum: Desktop Environments
---

### Post by darren33 on 2016-02-20
I can't figure out what the question mark icon is in the indicator plugin (second from the left):

[ATTACH=CONFIG]267405[/ATTACH]
(Click to enlarge)

If I click on it, it highlights but doesn't appear to do anything.  Hovering doesn't give any pop-ups.  If I change icon sets, depending on the set, it can appear as a box with a red circle-and-slash.  I tried going into settings and clicking "Clear known indicators", but it comes back when I restart the desktop.

Any ideas how to figure out what it is and how to get rid of it?

Thanks.

---

### Post by egeezer on 2016-02-21
If it shows a red circle and slash, it means it does nothing.  Right-click it and choose "Remove" and it will be gone.

---

### Post by darren33 on 2016-02-21
Thanks for the reply.

I can't figure out any way to remove individual icons from the indicator plugin.  If I right-click and select "Remove", it removes the entire plug-in.  If I restore the plug-in and restart the desktop, the question mark icon returns.

It doesn't seem to be doing any harm.  It's just annoying because I wish I could figure out what it is.  Do I have a program quietly crashing in the background?  I have no idea.  dmesg output doesn't show anything out of order.

---

### Post by egeezer on 2016-02-21
I think if at least one icon set shows that plugin as a blank (red circle/slash), it either isn't in use, or if installed, isn't functioning.  I have seen the same thing on one occasion, and simply removed the icon and whatever went with it.  That was a while ago, and I have yet to notice anything wrong.  But remember, YMMV.

Edited to add: what does Settings > Panel > Items say about the entry in that position?

---

### Post by darren33 on 2016-02-21
It's inside the Indicator Plugin.  It's not its own item.  I just don't know how to figure out what it's for.

---

### Post by egeezer on 2016-02-22
If you're patient, you could look through                       

   /usr/share/xfce4/panel/plugins 

and eliminate the ones you know about so you could identify the odd one that contains your mystery icon.

---

### Post by yoshii on 2016-02-23
Check your session startup preferences in the application autostart section.  You might find out what's going on there and you can disable it there.

---

### Post by darren33 on 2016-02-23
> **yoshi2 said:**
> Check your session startup preferences in the application autostart section.  You might find out what's going on there and you can disable it there.
Thanks for that.  Turns out there's something wrong with my Dropbox app. :???:

One problem solved.  Now on to the next problem!

Thanks again!

---

