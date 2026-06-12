---
title: "No Border"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by sdil on 2007-10-24
I am Ubuntu 7.10 Gutsy Gibbon user .... I just now install Advanced Desktop Effect manually ( because my repo having problem ). I using 3D Cube, Expo, Widget and more comfortably without any problem. But, my windows have no windows border.

Any ideas to solve it ?

---

### Post by Gwijde on 2007-10-24
I had this problem too,  but in 7.04, a reinstall shud do it really

using synaptic shud be best.
it worked for me, hope i cud help

---

### Post by leona on 2007-10-28
resintall what?

---

### Post by Forlong on 2007-10-28
Try this in a terminal:```

sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
(you have to restart X to make it work)

---

### Post by leona on 2007-10-28
solved after reading this post.
> **JBAlaska said:**
> Try removing ccsm in synaptic and restarting x, then you should see "Advanced Desktop Effect Settings".

**When you start "Advanced Desktop Effect Settings" , go to the "windows decorations" plugin and type emerald in the command box (needs to have emerald installed) "sudo apt-get emerald"**

edit to add, sorry no this didn't solve my problem, it just turned the effects off which gave me my borders back, drat, looks like I can only have one or the other, border or effects.

---

### Post by leona on 2007-10-30
> **F1r3 said:**
> I have an nvidia graphics card as well and had a lot of the same problems posted in this thread. 
No borders and my terminal windows came up white.
I looked around for a while and found this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restarted X and everything worked for me.

This however, did fix my problem :)

---

