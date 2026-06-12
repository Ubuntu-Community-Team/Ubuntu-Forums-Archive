---
title: "Help, Gutsy Freezes"
date: 2008-01-19
forum: Desktop Environments
---

### Post by birddawg on 2008-01-19
Let me say thanks in advance.  
I new to linux, so I having a difficult time trying to troubleshoot my problem.
I dont know if I have one problem or many, but here goes.

For no apparent reason, my desktop will freeze. No harddrive activity, the mouse is froozen, ctrl-alt-backspace does nothing,  My only option left to do is a hard reset.  

This is a new install of Gutsy on a 1.7 Celeron with 512 Mb. 
Everthing seems to work fine just the annoying freeze.  When it's not freezing up, the desktop will suddenly reset to the login screen.

Can someone please point me in the right direction?

Also, Firefox seem to contribute to this problem, especially when I try to access a site like youtube.  But I really cant blame it all on Firefox, because I have Opera and Swiftweasel installed as well and they cause a freeze or reset sometimes as well.

I  had it freeze and reset when a browser was not running.  So if its not running, could it still be a fault?

Thanks once again.

---

### Post by rlwilson2 on 2008-01-19
I have the same problems but no answers yet....

---

### Post by Thund3rstruck on 2008-01-20
> **birddawg said:**
> 
This is a new install of Gutsy on a 1.7 Celeron with 512 Mb. 


Wow, I can't imagine running a modern OS with those specs. Perhaps you should give Xubuntu, ArchLinux, or another lighter distro a go. 

If you're most concerned with troubleshooting, start out analyzing the system logs [/var/log] or System > Administration > System Log

---

### Post by c0met on 2008-01-20
I think that Thunderstruck might be on to something. It might be an idea to choose a lighter version of Ubuntu, say Xubuntu.

---

### Post by rosegarden78 on 2008-01-20
This happens to me when I change things like settings by hand.  Or when I have a lot of web browsers and programs going while clicking the mouse a thousand times per second.  But you may be surprised to learn that thund3rstruck is correct.  I use a system slower than yours without stability problems: Inspiron 1200 1.1 GHz CeleronM 512MB IntelG915graphics.  Here's what I suggest you do:

1) Backup /home
2) Clean install Ubuntu Gutsy or lastest distro
3) Add kdm from package manager
4) Add xfce from Synaptic or aptitude ...

Now you have all three environments and all possible dependencies.

When you login look for a box click it and select XFCE Sesstion.

Try pressing Alt-F2 then type nautilus to access Ubuntu features.  Then click your Launcher and add Xfce Menu.  This is because Nautilus replaces the right click with document creation tools.

I highly suggest you run XFCE (Xubuntu) on login.  Keep GNOME and KDE to satisfy dependencies.  I think you will be pleasantly surprised with the results.

---

