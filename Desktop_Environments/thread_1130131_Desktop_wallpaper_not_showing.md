---
title: "Desktop wallpaper not showing"
date: 2009-04-19
forum: Desktop Environments
---

### Post by sjprice on 2009-04-19
`So, on 8.10 running Gnome, the wallpaper does not appear. I have Drapes and I can change the wallpaper, but it is not on the screen. Right click and Change wallpaper, I can see Drapes changing it, but not displaying it. Ran Drapes from the command line, no errors.

Wallpaper does show up briefly when logging in, but once the Panel and iscons show up, no wallpaper.

Steps I have taken:

Completely removed Drapes and reinstalled.

Moved up the the Nvidia 180 driver (was on 177)

Reinstalled Compiz

Generated a new xorg through Nvidia settings.

Verified in gconf-editor apps/Nautilus/preferences that show wallpaper is ticked.

I am really stumped...any help?

---

### Post by sjprice on 2009-04-19
Bump, and I should also add that I had set up VNC over an SSH tunnel around the same time. I know that the option is there to remove the wallpaper when it is connected, but that is unchecked.

Is it possible that VNC is looking at a local port, like it is always connected?

Just stabbing in the dark...

---

### Post by sjprice on 2009-04-20
Bump for the Monday crowd. Still trying different things, still no success.

---

### Post by sjprice on 2009-04-20
Created a new user and logged into that user and wallpaper showed up. So it has to be a config somewhere.

Is there a Gnome config or Nautilus config that I am missing? In the grand scale of things, this is not a big deal, but I have to do something instead of play WoW. :)

---

### Post by sjprice on 2009-04-20
So, I found this bug ([https://bugs.launchpad.net/ubuntu/+source/vino/+bug/289034](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/289034)) which is basically that after disconnecting from VNC that the wallpaper is gone forever. And I connect via VNC constantly, and the current version installed 2.24 is affected. 

There is also a patch, but 2 things:

1) I disabled vino from starting and I still did not have wallpaper. Do you think this means that is not the source? I.E. if I apply the patch, it wont help

2) How do I apply the patch? I have not done make makefile in forever. Could someone give me the basic steps?

---

### Post by ionoff on 2009-04-21
Hit Alt-F2 and enter gconf-editor. Once it opens, navigate to desktop > gnome > background and make sure 'draw_background' is enabled.


Source:
[http://ubuntuforums.org/showpost.php?p=6695158&postcount=2](http://ubuntuforums.org/showpost.php?p=6695158&postcount=2)

---

### Post by sjprice on 2009-04-21
Dang, I knew it had to be a simple solution.

Thanks!

---

### Post by duuster on 2009-05-27
That worked for me ! ! !
Thank you...thank you. :D

---

