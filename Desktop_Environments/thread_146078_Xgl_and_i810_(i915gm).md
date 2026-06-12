---
title: "Xgl and i810 (i915gm)"
date: 2006-03-17
forum: Desktop Environments
---

### Post by aperry on 2006-03-17
Yes, this is yet another message about Xgl...

However, I'm not writing this to ask for help, but to help people who might have the same problem I did.
So to make it short: do everything listed in the XglHowto ( [http://wiki.ubuntu.com/XglHowto](http://wiki.ubuntu.com/XglHowto) ), make sure your driver is "i810" in your xorg.conf file, and that should be it.
However, if when you launch gnome-window-decorator after launching "compiz --replace ..." including the decoration plugin, it means you've got the same problem I did. In this case, open your gconf-editor, go to the "apps/compiz/general/allscreens/active_plugin" key, and add every module that you add in your command line (decoration before wobbly, this is important).
Then, launch compiz again with "compiz --replace gconf", and then gnome-window-decorator (with the final "&" if you wish).
It should now work...

Two things however: I first tried running Xgl from the LiveCD, and quite astonishingly, it was smoother. I didn't need to add the plugins to gconf, either. I'll report those as bugs after Dapper is released, since there's quite a rush among developpers until then...

-- 
Alain Perry

---

### Post by aperry on 2006-03-22
Ok, so feeling that I hadn't really tried enough, I got back on the subject today, after an update of the i810 xorg driver in the Dapper packages.
For those interested (there doesn't seem to be a lot, but I thought I'd write it here anyway), it actually works quite well, with very small anoyances that are planned to be corrected in the near future. I just had tried several method before understanding the gconf problem, and some of these "methods" left some files installed on my system. After reviewing all I could (thanks to apt-file and locate), I got rid of them and could finally enjoy Xgl working well enough.

---

### Post by nalmeth on 2006-03-22
Cool.. Seeing as its working for some people, maybe it will work for me (915G not 915gm). The liveCD did NOT work, even though it picked the i810 driver. I don't think I'm willing to upgrade my PC to dapper yet for something I'm not sure will work. Maybe on another partition. my dapper laptop probably won't run XGL, so I will just have to wait I suppose.

BTW shouldn't this go in the Dapper forum? You aren't trying to tease the breezy users are you?

---

