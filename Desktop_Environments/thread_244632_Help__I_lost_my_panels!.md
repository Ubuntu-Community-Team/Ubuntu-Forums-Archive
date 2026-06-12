---
title: "Help?  I lost my panels!"
date: 2006-08-26
forum: Desktop Environments
---

### Post by zami on 2006-08-26
Ack!

I lost my panels!

I tried to install XPenguins ( [http://xpenguins.seul.org/](http://xpenguins.seul.org/) ) 
and my entire desktop locked up when I tried to actually add one to the panel.  I suspect it's supposed to actually go on the desktop, but that did absolutely nothing, so I tossed one into the panel... KABOOM.

The only thing I could get a response from was hitting my computers power button, wich brings up the shut-down/log-out screen for me.  But I coudln't even select to shut-down or log-out, so I hit the hard reset switch on the back of the machine.

I logged in just fine and my keyboard is working, and I can start my browser just because a shortcut is on my desktop.

But my panels are still shot.  The workspace selector is a white blur, the menu bar is still there but unresponsive.

Alt+F2 does nothing (supposed to bring up the terminal isn't it?)

I read elshwere that right-clicking on the desktop would bring up a Launch Terminal button... nope, nothing like that in my right-click menu.

Any suggestions?

(My mother-in-law is here and was delighted by the googly eyes on my toolbar, thought I'd add something else froofy... why... whyyyy would I think such a thing!?)

-zami

---

### Post by ahaslam on 2006-08-26
What DE are you using? If you're using Xfce I can help.

BTW, ctrl + alt + F1-6 should bring up a terminal

Tony ;)

---

### Post by zami on 2006-08-26
Thanks!  Having that terminal (so strange to see it full screen like that!) is a huge help... I've found a few other "lost panel" type posts and if I can try some terminal commands I might be able to get ... somewhere....

And I'm using the Gnome desktop.  Guess that's a rather important bit for me to have left out.  :)

-zami

---

### Post by ahaslam on 2006-08-26
Try **gnome-panel**

Tony

---

### Post by shamrock_uk on 2006-08-26
Alt+F2 brings up a 'run' dialogue. Alt+F1 brings up your menus.

Try Ctrl+Alt+Backspace to quit X. Try Alt+SysReq+R before that if it doesn't work the first time. 

I would try selecting 'failsafe gnome' next time you're back at the logon screen and see if that'll get you to a functioning desktop.

---

### Post by zami on 2006-08-26
Thank you both so much!

Once I got to a terminal, I followed the "reset yer panels" instructions from another post

gconftool-2 --recursive-unset /apps/panel

worked like a charm!  Yes my panels need to be re-tweaked, but... THEY WORK!

Shwew!

Just for the info, Shamrock, what is Alt+SysReq+R ?

Again, thank you folks for the quick rescue.  I needed it!

-zami

---

### Post by ahaslam on 2006-08-26
No worries mate, glad to help.

Tony ;)

---

### Post by ahaslam on 2006-08-26
> **zami said:**
> what is Alt+SysReq+R ?
For me that just takes a screenshot, replacing 'alt' with 'ctrl' refreshes.

Tony.

---

### Post by welshbyte on 2007-01-30
[https://bugs.launchpad.net/ubuntu/+source/xpenguins-applet/+bug/37669](https://bugs.launchpad.net/ubuntu/+source/xpenguins-applet/+bug/37669)

If someone from this thread could confirm that bug it might help the process. Cheers.

---

