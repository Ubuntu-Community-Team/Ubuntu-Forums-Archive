---
title: "Twinview and tooltips"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by dysphasi on 2008-01-09
Ok, got a bit of an annoying problem here using the gnome panel and twinview with an nvidia card.

Basically I want my panel to be on the one screen, I'm using a tv so don't want it stretched onto that, the tv is just so I can watch vids/use myth.

 I can't find out how to fix the panel to stick only to the one screen anywhere (except using xinerama, which I trying to not use atm).

So...in gconf-editor I've made sure all my applets aren't positioned relative to the right of the screen.

HOWEVER, the tooltips for the applets on the right side still stretch over onto the tv screen, this makes them unreadable.

So basically how can I keep all tooltips to the one screen, my monitor, and not have them stretch onto the tv?

Thanks in advance!

---

### Post by codesplice on 2008-01-09
I used the nvidia-settings utility to set up two monitors as separate x-sessions.  This way, I can use an external CRT for playing media, and use my notebook's LCD for general computing.  

run nvidia-settings, click on the "X Server Display Configuration" tab, select the monitor you want to configure, and click "Configure..."  Select "Separate X Screen", Save the changes, and reboot.

---

### Post by dysphasi on 2008-01-09
ta, actually ended up doing that, looks good. Only problem is my settings aren't saving for nvidia-settings. Any ideas?

My post for that is here:
[http://ubuntuforums.org/showthread.php?t=662679](http://ubuntuforums.org/showthread.php?t=662679)

---

### Post by codesplice on 2008-01-09
Try running it as sudo?

It'll need those permissions if you want it to save the settings to your xorg.conf.

---

### Post by dysphasi on 2008-01-09
I did, soz, should have been a bit clearer. I can save/merge the xorg.conf ok, that's fine.

My trouble is that any changes I make to tv settings, ie. overscan and flicker reduction aren't saved.

And yes, I am making the changes as sudo, and running nvidia-settings -l at startup, but no joy, the tv settings keep returning to default.

---

### Post by codesplice on 2008-01-09
Posted in the other thread.  lemme know if that helps in or if I need to keep hunting :)

---

