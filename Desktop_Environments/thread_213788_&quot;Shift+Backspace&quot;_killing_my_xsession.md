---
title: "&quot;Shift+Backspace&quot; killing my xsession"
date: 2006-07-11
forum: Desktop Environments
---

### Post by bartmanbsd on 2006-07-11
Hello all,
I am using the latest version of Ubuntu 6.06 and on multiple occasions I have hit “Shift + Backspace” and it kills my X-Sessions resulting in the loss of everything that I have open.  Needless to say it is driving me insane.  I though only “Ctrl+Alt+Backspace” restarted the x-session.  I have poked around /etc/X11/gdm to see if I could find some option about changing but have had no luck.

My question is how do I stop “Shift+Backspace” from restarting my xsession.

---

### Post by mikeytag on 2006-07-11
This really drives a lot of people up the wall. To fix it do the following

sudo gedit ~/.Xmodmap

insert the following into that file:

keycode 22 = BackSpace

Save the file and then reload X. Shift+Backspace will no longer restart your session.

---

