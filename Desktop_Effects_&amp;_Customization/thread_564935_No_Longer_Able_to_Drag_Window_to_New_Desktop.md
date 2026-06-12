---
title: "No Longer Able to Drag Window to New Desktop"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by Locutus_of_Borg on 2007-10-01
I re-installed kubuntu yesterday along with Compiz Fusion.  I followed the exact same procedure as I had used previously, only now I can no longer drag a window to the edge of my current desktop and pull it over to the next one.  It just stops at the side of the current one.

Any suggestions?

---

### Post by Locutus_of_Borg on 2007-10-01
Fixed: Active Desktop Borders was Disabled.

---

### Post by sawjew on 2007-10-08
How do you enable Active Desktop Borders?  Also do you know how to turn off the desktop rotate with mouse wheel?

---

### Post by Forlong on 2007-10-08
> **sawjew said:**
> Also do you know how to turn off the desktop rotate with mouse wheel?
Do you have ccsm installed?

Then just disable the Viewport Switcher.

---

### Post by sawjew on 2007-10-08
Thanks Forlong, it's easy when you know where to look, but I'm still learning all the options with CCSM.  Do you know how to enable dragging windows to the next desktop?

---

### Post by Forlong on 2007-10-08
> **sawjew said:**
> Do you know how to enable dragging windows to the next desktop?
Depends on how you use your desktops - Cube, Wall or Plane?

---

### Post by sawjew on 2007-10-08
Cube

---

### Post by Forlong on 2007-10-08
Go to Rotate Cube and make sure **Edge Flip Move** is enabled.

---

### Post by sawjew on 2007-10-08
I have already done that, it still doesn't work.

---

### Post by obbe on 2007-10-23
> **sawjew said:**
> I have already done that, it still doesn't work.

same for me, although Edge Flip Move and Edge Flip DnD are both enabled on Compiz Setting Manager, when i move a window to a screen edge nothing happens, rotate cube is obviously enabled, any suggestion?

---

### Post by NawaMan on 2007-10-24
In CCSM, export the configuration and post it here so may be we can take a look.

NawaMan

---

### Post by obbe on 2007-10-24
that's mine

---

### Post by sawjew on 2007-10-24
Here is my configuration.

---

### Post by bluedragon436 on 2007-10-24
I am still learning Linux, and this is one thing I was having an issue with luckly for me I have people to help me here where I am located!!!

---

### Post by NawaMan on 2007-10-24
I think I know the problem. Let try this and see if it works. Goto "Rotate Cube"->"Action". At the very bottom, there are two action "Rotate Flip Left" and "Rotate Flip Right". Set "Screen Edge" of "Rotate Flip Left" to "Left" and set "Screen Edge" of "Rotate Flip Right" to Right". It should work now. :D

Since there are more than one person experience this, may be we should report this as bug.

Hope this helps.

---

### Post by obbe on 2007-10-24
> **NawaMan said:**
> I think I know the problem. Let try this and see if it works. Goto "Rotate Cube"->"Action". At the very bottom, there are two action "Rotate Flip Left" and "Rotate Flip Right". Set "Screen Edge" of "Rotate Flip Left" to "Left" and set "Screen Edge" of "Rotate Flip Right" to Right". It should work now. :D

Since there are more than one person experience this, may be we should report this as bug.

Hope this helps.

i don't have those settings in the "rotate cube" preferences :(

---

### Post by NawaMan on 2007-10-24
Try again with CCSM,I have attached the screenshorts of it in case you can't find.

RotateCube.png (1st picture) is where "Rotate Cube" should be.
Options.png (2nd picture) is where those two options are.

If you still don't see (may try update CCSM first :( ), OR, You can edit it with GConf.
First Run, GConf (in the "System Tools -> Configuration Manager" or run gconf-editor in terminal).
The, navigate to "/apps/compiz/plugins/rotate/allscreens/options/" then set as the screenshort GConf.png (3rd picture).

Hope this help.

---

### Post by bluedragon436 on 2007-10-24
I have followed a few other people on here that have been having this same issue, and after trying a few different things that people have done my cube is rotating, and I can move things from desktop to desktop just fine.  I am not sure why it is that this option randomly quits operating...

---

### Post by sawjew on 2007-10-25
It worked thanks NawaMan :).

---

### Post by obbe on 2007-10-25
I changed the values by gconf editor and it works fine now, thanks NawaMan!! =D>

---

### Post by mpsantiago on 2007-10-26
> **NawaMan said:**
> I think I know the problem. Let try this and see if it works. Goto "Rotate Cube"->"Action". At the very bottom, there are two action "Rotate Flip Left" and "Rotate Flip Right". Set "Screen Edge" of "Rotate Flip Left" to "Left" and set "Screen Edge" of "Rotate Flip Right" to Right". It should work now. :D

Since there are more than one person experience this, may be we should report this as bug.

Hope this helps.

Excellent!

This fixed it for me, thanks :)

---

