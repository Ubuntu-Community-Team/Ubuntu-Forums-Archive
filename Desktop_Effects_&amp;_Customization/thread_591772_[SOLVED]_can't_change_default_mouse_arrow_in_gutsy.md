---
title: "[SOLVED] can't change default mouse arrow in gutsy"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by strungoutfan78 on 2007-10-25
i've gone through the proper steps to install the new cursor themes but to no avail.  every theme i install works in every manner it should except for the most important one.... THE DEFAULT ARROW POINTER.

now here's the catch.  if my poiner is over the desktop, it is  the default DMZ icon.  if i move it over, say, a firefox window (or in my case flock), it draws the pointer from the newly installed theme.

WHY?!?:confused:

i'm quite positive i could remedy this with a little cuttin, pasting  and renaming of files in the /usr/share/icons folder, but i'm not really sure what program i need in order to view and edit the icons.  i've tried inkscape and gimp and neither recognize the format.

thanks for any tips.:)

---

### Post by strungoutfan78 on 2007-10-25
well here's a hint....  it has something to do with compiz-fusion.

if i change window managers from compiz to metacity, voila, mouse pointer works fantastic.  reload compiz.... :( no good.

at least that get me pointed in the right direction to go sniiffing around

---

### Post by strungoutfan78 on 2007-11-08
that's funny.  it's been a while since i posted this i know, but for some reason the problem seems to have fixed itself.  i guess i had become so used to it i didnt even notice.  maybe it had something to do with the "HWcursor" = off option i added to xorg.conf.  (although i thought that was strictly an nvidia option and i have an intel 915 chipset)  who knows. :guitar:

---

### Post by techstop on 2007-11-08
If anyone else needs to know how to set custom cursor themes, then here is the answer. You need to open ccsm, go to General Options, and then type in the name of the cursor theme in the "Cursor theme" text box. (obviously you need to install the cursor theme)

---

### Post by lian1238 on 2007-11-09
Same/similar problem here. I typed the name in ccsm, and it works better now. But the resize and move cursors are still not the same as the theme. Rolling over an edge shows the default theme. On resizing, I get the redglass theme.

---

### Post by FuturePilot on 2007-11-09
> **lian1238 said:**
> Same/similar problem here. I typed the name in ccsm, and it works better now. But the resize and move cursors are still not the same as the theme. Rolling over an edge shows the default theme. On resizing, I get the redglass theme.

I've seen that happen before when switching cursor themes. Logging out and logging back in usually takes care of it.
Cursor themes can also be changed with System>Preferences>Appearance. Click Customize and go to the Pointers tab

---

### Post by lian1238 on 2007-11-09
> **FuturePilot said:**
> I've seen that happen before when switching cursor themes. Logging out and logging back in usually takes care of it.

I had done that and had come back to say it was fixed, but you beat me to it.:D

---

### Post by playme123 on 2007-11-09
> **FuturePilot said:**
> I've seen that happen before when switching cursor themes. Logging out and logging back in usually takes care of it.
Cursor themes can also be changed with System>Preferences>Appearance. Click Customize and go to the Pointers tab

thanks for that I wondered how you did it:)

---

### Post by strungoutfan78 on 2007-11-14
Holy cow, that did it.  Now I see why.  I didn't even realize that you could specify the cursor theme in ccsm.  Thanks a million!:guitar:

---

