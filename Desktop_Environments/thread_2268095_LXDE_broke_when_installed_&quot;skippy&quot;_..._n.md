---
title: "LXDE broke when installed &quot;skippy&quot; ... no borders, titlebars and toolbars"
date: 2015-03-06
forum: Desktop Environments
---

### Post by mind_exploit on 2015-03-06
Hey, guys :)

I have Chromebook and run Ubuntu with LXDE, using Crouton. All was fine until yesterday I installed "skippy" (formelly "skippy-xd"). This is a task switcher for minimalist desktops, that is simialr to "Present Windows" in KDE4 or pressing "Win" in Gnome3 - user see previews of all opened windows.
[https://code.google.com/p/skippy-xd/](https://code.google.com/p/skippy-xd/)

After the installation - it didn't want to run, cause it threw an error: "[COLOR=#000000]Error of failed request:  BadAccess (attempt to access private resource denied)". Searched for it, and found out that the current window manager doesn't allow skippy to access something. But it got too late, so - I left it for today.
And this morning, when I ran LXDE - I found out that I have no cursor and all windows have not borders, titlebars and toolbars.

I removed skippy, restarted LXDE - and no change :( ... 

How can I fix it? ... 

PS1: I can re-install it, but I want to try to fix it first :) ...

PS2: At work I tried "skippy" with OpenBox, and it worked fine :) ... so what could have caused the problem with "BadAccess" ? ... [/COLOR]

---

### Post by mind_exploit on 2015-03-06
I managed to fix it :) ... 


After some research - I found out that somewhere in the config files should be specified which window manager LXDE should use. And found out that in desktop.conf:


[Session]
window_manager=openbox-lxde


Then, after a while - I ran "sudo apt-get install openbox" - then it had to install some additional stuff, and when I restarted - it was all OK :) ... 


.........


Hope this helps someone else.

---

