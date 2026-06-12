---
title: "compiz not working!"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by lik on 2007-11-13
How can I get back the original ubuntu window manager? after I installed compiz the title bar of every windows was gone... no minimize, move etc. no multiple desktops. can't run compiz config or anything. and when i click  the show desktop icon (botom left), it says my current window manager doesn't support it. 

thanks in advance!

---

### Post by nero_86 on 2007-11-13
In terminal you can stop your compiz and start metacity (if you are using gnome)

```
metacity --replace &
```

What tipe of graphic card are you using? nvidia or ati?
Your problem can be in the setting of the xorg.conf file.

---

### Post by lik on 2007-11-13
I'm using a nvidia 7600.

I changed to metacity but can't turn on the visual effects, when I do so it turns to the same problem. 
can you explain me what to do with the config file? I'm completely new to linux. 
Thanks a lot!

---

### Post by Forlong on 2007-11-13
Try this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restart X and run desktop effects again.

---

### Post by lik on 2007-11-13
it worked!! thanks!!

now i can enter the compiz config and things are working!

could you tell me how to use the entire cube? not just the buttons in bottom right of desktop. and the fire animations for minimize-maximize.

sorry for all questions but i'm really new to this. (second day user lol) 
thank you a lot for your help,

---

### Post by Forlong on 2007-11-13
> **lik said:**
> could you tell me how to use the entire cube?
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under "Getting the cube".
> **lik said:**
> and the fire animations for minimize-maximize.
See in that same guide under "Reasonable window effects" and instead of "Magic Lamp" choose **Burn** (I'd recommend using it for the Close Animation, though)

---

### Post by lik on 2007-11-13
thank you so much..... i'm loving the ubuntu experience because of all the support this forum and guys like you give newbs like me! 
best regards!

---

