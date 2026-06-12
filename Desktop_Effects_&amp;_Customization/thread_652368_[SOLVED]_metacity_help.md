---
title: "[SOLVED] metacity help"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by brett611 on 2007-12-28
I'm embarrassed to ask this but there's no avoiding it!

I did a fresh install of Gutsy, no partitions.  I installed cobiz or whatever the desktop effects thing is.  However, my ATI card didn't like it so I removed it.  Now, I keep getting this issue where the title bar of all windows disappears and I have to enter "metacity --replace"...daily or more frequently.

So I looked for forum help on metacity and it sounds like I should replace it with flubox, to be my desktop 'window manager'.  I thought that's what nautilus was?  Or is Nautilus the equivalent of MSFT Windows Explorer?  And what exactly is a window manager?

Finally, I downloaded flubox but don't know how to "use" it or install it.  ditto for removing metacity.

thanks!

---

### Post by raven77 on 2007-12-28
I was having the same problems as you, and I actually found this solution in another thread here on the forums. I can't find the thread anymore, but if you just want your system to use metacity instead of compiz, here's the permanent way to get it done: 

In terminal, type the command "gconf-editor". This should bring up the "configuration editor". Go to Desktop-Gnome-Applications-Window Manager.

You should see "default" as /usr/bin/compiz. Right-click it, edit key, and change to usr/bin/metacity

Reboot your system, and if you go to system/Administration/System Monitor, and look at processes, you should see metacity running but no compiz.

As for fluxbox, I can't help you there, but my system was much happier when I just changed it to use metacity. I hope it helps you out too.

---

### Post by brett611 on 2007-12-29
Thanks.  I never knew about 'gconf-editor'  that's very helpful.  Unfortunately, Metacity was listed as the current and default.  I'm changing to Flubox and rebooting with my fingers crossed

thx again

---

### Post by brett611 on 2007-12-31
I "solved" the problem - did a full reinstall.  ouch.  but now everything is working fine, even Amarok

---

