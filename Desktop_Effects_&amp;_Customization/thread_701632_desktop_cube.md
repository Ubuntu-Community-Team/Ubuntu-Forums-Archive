---
title: "desktop cube"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by jrockpunk1 on 2008-02-19
how do you make there be 4 desktops? ive currently got 2, so when i do ctrl+alt+right it flips to the opposite side (theres 2 deskspaces). to fix this you have to make more little boxes representing deskspaces down the bottom right, right? to do that ive been told to right click one of the squares and click preferences. i did that and it came up with a box that said:
```

workspaces

columns: [4]
rows: [4]

```
no matter what i change those numbers to, it stays as 2 deskspaces. how do i make it more?

---

### Post by SunnyRabbiera on 2008-02-19
well do you have the compiz effects running in the first place?

---

### Post by Het Irv on 2008-02-19
Under General Options in the CompizConfig Settings Manager, goto the Desktop size tab and change your Horizontal Size.

---

### Post by thekylehome@gmail.com on 2008-02-19
Compiz effects must be running, because their getting a flip screen!

---

### Post by SunnyRabbiera on 2008-02-19
yeh but he will need to install that bit as its not installed by default.
lets take him by the steps.

---

### Post by jryprt on 2008-02-19
Try [Forlong's Guide](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)

---

### Post by jrockpunk1 on 2008-02-19
ive got compiz effects working. like the water ripple etc. but when i click on ccsm it says:

```

could not launch menu item:

Failed to execute child process "ccsm" (No such file or directory)

```

---

### Post by Het Irv on 2008-02-19
Try going into Add/Remove and uninstalling and reinstalling ccsm.

---

### Post by mcdan on 2008-02-19
in the terminal type 

$ sudo apt-get install ccsm

---

### Post by steveneddy on 2008-02-19
> **thekylehome@gmail.com said:**
> Compiz effects must be running, because their getting a flip screen!

That isn't your actual e-mail address as your forum name is it?

I think I would change that as soon as possible.

---

### Post by nilarimogard on 2008-02-19
> **jrockpunk1 said:**
> how do you make there be 4 desktops? ive currently got 2, so when i do ctrl+alt+right it flips to the opposite side (theres 2 deskspaces). to fix this you have to make more little boxes representing deskspaces down the bottom right, right? to do that ive been told to right click one of the squares and click preferences. i did that and it came up with a box that said:
```

workspaces

columns: [4]
rows: [4]

```no matter what i change those numbers to, it stays as 2 deskspaces. how do i make it more?

Did you try 4 columns and 1 row?

---

### Post by northern lights on 2008-02-19
You need not change the preferences of those "little boxes", thats the gnome in-built viewport switcher, it's not what's managing your Desktop Effects. Do you have ccsm installed (i.e. is there an "Advanced Desktop Effects" entry in "System > Preferences"? Or can you select "Custom" under "Visual Effects" in "System > Preferences > Appearance"? If not, run ```
sudo apt-get install compizconfig-settings-manager
``` If yes, or after successful installation, open ccsm, select "General Options" and under "Desktop Size" set the "Horizontal Virtual Size" slider to 4.

---

### Post by kool_kat_os on 2008-02-19
> **steveneddy said:**
> That isn't your actual e-mail address as your forum name is it?

I think I would change that as soon as possible.

Users can change their user name?

---

### Post by divindavid on 2008-02-19
you need to turn off desktop effects then click on the bottom right to preferences and do your thing then u can reenable desktop effects

---

### Post by alsamman on 2008-02-19
To add more desktops with the cube thing, go to compiz settings manager, general options, desktop size, and increase the Horizontal size to 4

---

### Post by rainwalker on 2008-02-20
Just to let everyone know, the package is 
```
compizconfig-settings-manager
```
not CCSM

---

### Post by jrockpunk1 on 2008-02-20
ok ive got ccsm working, but i still cant make there be 4 windows. how do i make 4 little boxes that represent workspaces?

---

### Post by divindavid on 2008-02-20
> **jrockpunk1 said:**
> ok ive got ccsm working, but i still cant make there be 4 windows. how do i make 4 little boxes that represent workspaces?

you need to turn off desktop effects then click on the bottom right to preferences and do your thing then u can reenable desktop effects

---

### Post by northern lights on 2008-02-20
Or just change the "Horizontal Virtual Size" - it doen't matter.

Are you reading this thread at all? Several solutions are given above your last post. Good thing ccsm is working - now just follow thru...

---

