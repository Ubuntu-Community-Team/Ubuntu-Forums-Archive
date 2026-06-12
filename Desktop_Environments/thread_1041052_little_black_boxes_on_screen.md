---
title: "little black boxes on screen"
date: 2009-01-16
forum: Desktop Environments
---

### Post by tropdoug on 2009-01-16
Hi guys

I have recently put 8.10 onto my laptop, I installed Kubuntu first of all, but could not sort out the network manager which just refused to connect. So I switched over to Gnome and removed all the KDE related apps and desktop. When I rebooted into gdm I find that where I should see information boxes, like the update manager's message, I see just a black rectangle. This is annoying and also occurs whenever I hover the mouse over a menu item, or option in a setup window etc.

Can anyone suggest what is not working, and how to get it working. Unfortunately I can't seem to catch one using screen print, because they disappear as soon as the focus is removed. 

Douglas

---

### Post by FIONEX on 2009-01-16
haha that's one hell of a bug.  Just to be clear, I think you're confusing GDM which is the Gnome Display Manager (which actually just performs login and session option selection) with the gnome desktop.  They're two separate things.  Anyways, are you trying to say that the "Notification Area" in the gnome panel showing black boxes?  If so, then you've run into some weird bug that I've never seen before.  I really recommend you just reinstall an authentic gnome-ubuntu from scratch as opposed to switching a kubuntu to gubuntu.  I know it's a stupid suggestion, but I can't figure out why that would happen.

The reason I say this because sometimes, when bugs like this happen, you'll waste more time trying to figure out why and there might not be a fix anyways.  So a fresh gubuntu (regular ubuntu) install would be easier...

---

### Post by tropdoug on 2009-01-17
Thanks for the clarity, I did not realise that GDM just handled the login etc, so that's another bit of learning to file away. I came to a similar thought myself after a while, so did a clean reinstall plus reformatted the root partition. & installed Ubuntu 8.10. Unfortunately whatever is causing this, must be in a config file on my /home partition because it's still occuring. Now I am thinking well which hidden file would it be in, or what bit of config script?

Any ideas?

---

### Post by tropdoug on 2009-01-19
Bump

---

### Post by tropdoug on 2009-01-22
Bumpity bump bump bump

---

### Post by anonymousnobody on 2009-02-12
Haha! I have the exact same problem. Whenever I mouseover anything, it becomes a black box. I just installed Ubuntu 8.04 and the mouseover was working fine earlier in the day. Then I fidgeted with the various appearance, compiz, and emerald settings. I think the boxes are a result of either compiz or emerald.

In emerald, I switched from vrunner to truglass. Could that be it? Or maybe one of the compiz settings? I just didn't notice the effect right away.

---

### Post by sharon.gmc on 2009-02-12
It only happens whenever you put the mouse over a menu?  What can be happening?

---

### Post by anonymousnobody on 2009-02-13
> **sharon.gmc said:**
> It only happens whenever you put the mouse over a menu?  What can be happening?

No. Black boxes replace the mouseover text.

---

### Post by anonymousnobody on 2009-02-15
> **tropdoug said:**
> Hi guys

I have recently put 8.10 onto my laptop, I installed Kubuntu first of all, but could not sort out the network manager which just refused to connect. So I switched over to Gnome and removed all the KDE related apps and desktop. When I rebooted into gdm I find that where I should see information boxes, like the update manager's message, I see just a black rectangle. This is annoying and also occurs whenever I hover the mouse over a menu item, or option in a setup window etc.

Can anyone suggest what is not working, and how to get it working. Unfortunately I can't seem to catch one using screen print, because they disappear as soon as the focus is removed. 

Douglas

I think I figured out the problem. In System > Preferences > Appearance, pick the Theme tab and pick a the theme you are currently using. Then click customize. Go to the colors tab. Either change the Tooltips color background or reset to defaults. Hope this help.

---

### Post by tropdoug on 2009-02-17
The system >appearance thing is the correct way to fix your problem. I was able to get screen shots finally of what was occuring, and because I couldn't get an answer of this thread I started a new one, and got the answer almost straight away. I apologise for not posting the fix here.

---

### Post by -VladV- on 2011-06-30
Just a note to whoever stumbles upon this thread later.

I had a similar issue after upgrading to Natty; it may or may not be the same problem as OP had.

In my case it turned out to be caused by a bug in metacity.
See  [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/758609](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/758609)  and [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/776784](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/776784).

The solution (as suggested by Felix in [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/758609/comments/10](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/758609/comments/10)) is:
- uncheck /apps/metacity/general/capture_before_unmap in gconf-editor,
- logout and login again.

---

