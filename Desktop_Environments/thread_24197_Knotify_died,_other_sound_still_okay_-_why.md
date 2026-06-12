---
title: "Knotify died, other sound still okay - why?"
date: 2005-04-05
forum: Desktop Environments
---

### Post by df-sean on 2005-04-05
Using Kubuntu Hoary, which is freaking AWWWW-some!!!  But one little problem: I got lusty and tried installing/enabling the composite manager for Xorg -- which just doesn't work at all for me -- so I gave up.  But ever since then, no notifications.

I can play Amarok just fine (uses Artsd)
I can even play the test sound in control center
I just can't hear any notifications

What logs can I check -- how can I fix this?

---

### Post by cwaldbieser on 2005-04-05
I get this behavior sometimes if I play around with the sound server too much.  If I log out of Kubuntu and back in, that usually fixes things.

Also, if you have Kubuntu set to use Esound as your sound system, make sure that is still running (ps -al | grep esd).

---

### Post by df-sean on 2005-04-06
Thanks for the tip!  But unfortunately, I'm not using ESD and I've rebooted several times -- still no notifications, but Amarok plays fine.   :|

---

### Post by cwaldbieser on 2005-04-06
If you go into System Notifications, can you play the sounds directly from there?  A couple times when getting the bleeding-edge Hoary updates I managed to turn off the sounds for the notifications in there...

---

### Post by df-sean on 2005-04-08
I can play the "test" sound, but the little play button to preview my notification sounds doesn't play.  Any ideas?

---

### Post by Hinko on 2005-04-08
[QUOTE=df-sean]I can play the "test" sound, but the little play button to preview my notification sounds doesn't play.  Any ideas?[/QUOTE]
 Arts can use multiple soundcards, while other programs usually use audio 0 . 
Do you have an onboard audio you don't use?

---

### Post by df-sean on 2005-04-08
I had an idea.  I decided to try renaming these two files:

~/.kde/share/config/knotify.eventsrc 
~/.kde/share/config/knotifyrc

Then I rebooted and now my notifications all work great.  Thanks for your help anyway guys!

---

