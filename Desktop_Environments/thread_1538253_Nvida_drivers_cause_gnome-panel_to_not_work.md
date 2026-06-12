---
title: "Nvida drivers cause gnome-panel to not work"
date: 2010-07-24
forum: Desktop Environments
---

### Post by flood222 on 2010-07-24
I need some help here. I have Ubuntu 10.04 installed. Everything works fine until I enable the Nvidia drivers. When I enable the drivers and reboot the top and bottom panel stop displaying. If I issue command 'pkill gnome-panel' it all comes up and works correctly. 
 
lspci output shows: 
VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a2)
 
I am at a loss here as I am somewhat new to Ubuntu. Does anyone have ideas on where to start looking for the problem? 
 
I've thought about setting up a startup script to run 'pkill gnome-panel' after I login, but that doesn't really fix the core of the problem.

---

### Post by flood222 on 2010-07-25
Anyone have any pointers on what log files to start looking at?

---

### Post by jerrykenny on 2010-07-25
I wonder if theres some specific setting in your bash profile . . . try creating a new user, then login as the new user.

If its a bash config issue the new users screen will be fine, whilst yours will be still borked.

---

### Post by flood222 on 2010-07-25
Thanks for the suggestion but that didn't work. 

Same result with new user.  Can log in ok, but the top and bottom panel don't load.  Desktop icons don't either.  

`pkill gnome-panel` brings back the top and bottom panels and desktop icons. 

WTF..lol.  So frustrating.  I can unload the Nvidia drivers and it works except the video card performance sucks.

---

### Post by flood222 on 2010-07-25
Another piece to the puzzle.  

When I initially enable the Nvidia driver and reboot everything works fine (at the default resolution 300x300 or something).  Then I set the resolution higher and save the xorg.cfg file.  Upon reboot is when the panels stop working.

---

### Post by randywilharm on 2010-07-25
Be certain you have JOCKEY installed in Lucid, but I think it comes that way by default...

I have funny little issues with Gnome too, similar to yours but it doesn't mess up too much


And I thank you for this:

pkill gnome-panel


It works fine...

---

### Post by flood222 on 2010-07-26
Well I ended up just adding a script to System/Preferences/Start up Applications

```
sleep 15
pkill gnome-panel
pkill nautilus
```

Works just fine.  I know it doesn't fix the underlaying cause of the issue, but it works just the same.

---

### Post by Ub28 on 2010-07-27
NVIDIA drivers are buggy and nobody except NVIDIA can fix them.  I've reported problems about NVIDIA drivers on here, but nobody seems interested in helping.

---

