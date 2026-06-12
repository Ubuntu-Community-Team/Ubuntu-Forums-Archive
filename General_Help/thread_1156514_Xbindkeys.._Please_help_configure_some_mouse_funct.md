---
title: "Xbindkeys.. Please help configure some mouse functions.."
date: 2009-05-11
forum: General Help
---

### Post by killabee44 on 2009-05-11
Hi all,

I am trying to set my mouse's scroll wheel to do a:

control+t when right tilting

and:

control+w when left tilting

I ran XEV and it said that right tilt is button 7 and left tilt is button 6 on my logitech mx1100 mouse.

My xbindkeysrc file looks like this:

```
"/usr/bin/xvkbd -xsendevent -text "\[ctrl]\[t]""
m:0x10 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[ctrl]\[w]""
m:0x10 + b:6
```

I am sure xbindkeys is running since I can see it from the htop process viewer.

What am I doing wrong? With the config above nothing happens. I am using Jaunty. Thanks.

---

### Post by killabee44 on 2009-05-12
I figured it out...



```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[F4]""
m:0x10 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[n]""
m:0x10 + b:6

```

Now I can tilt right and close a tab or window in firefox. Tilting left opens a new window.:)

---

