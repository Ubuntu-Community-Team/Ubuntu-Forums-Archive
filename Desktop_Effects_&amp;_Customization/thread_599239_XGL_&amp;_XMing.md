---
title: "XGL &amp; XMing"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by KingWilliam on 2007-11-01
Hi, 

I found this nice program called XMing, it seems to be an Xserver you can run on Windows to login to my ubuntu desktop using XDMCP. Now I would like to use XGL, for the funny effects and stuff. But i am wondering if that is possible using XMing. In my ubuntu-box i have the very old NVidia GeForce 256 and my laptop (wich i use to view my ubuntu system) has a NVidia GeForce Go 7600.

I think i have xserver-xgl installed on ubuntu, but get the error "The Composite extension is not available" when activating visual effects.

I al using gutsy...

Please help me :($$

Greetz...

---

### Post by dadedade on 2007-11-01
I think the processing will be handled by the ubuntu box, not on the PC you run Xming on...
that means that the screen changes caused by XGL would be streamed as well over your network, choking the bandwidth...
In other words, if you want to see the bling of XGL just use your ubuntu box, or switch to linux where you have a better graphics card. 
For VNC, it's better to stick with a normal gnome session.

sorry to tell you that :)

---

### Post by KingWilliam on 2007-11-01
Damn, that is not what i wanted to hear :) I really love the speed of XDMCP but if there is no other solution...

(I know i might sound stupid, thats because im a noob in Ubuntu)

---

### Post by eureko on 2008-03-02
Hi,

I receive the same Xming message, and am using XDMCP very fast, because windows and linux run in the same machine (am running Windows, and Frankesteinizing my box with andLinux).

Is there any way to add graphics acceleration or just GL libraries to Xming?

Thanks

---

### Post by furyy on 2008-03-02
XMing should have OpenGL acceleration. You need to have fast connection though (if you aren't running coLinux :D). Ive played tuxracer with it and had that wobbly effects with XGL before they were in metacity (2-3 years ago :P). Try xming +extension=composite or something like that. There was something about -multiwindow mode whether gl worked or not.

```
 Xming +extension composite 
```

I could only get some GL action if Xming is launch in one window mode. Fullscreen fails with XLib (armagetron) not being able to lock X. Multiwindow should work too.
Also -engine parameter could be of interest.

---

### Post by eureko on 2008-03-02
Hello furyy,

I do have coLinux (Linux andLinux 2.6.12-co-0.7.1 #1 Sat Jul 14 12:13:49 UTC 2007 i686 GNU/Linux) as the kernel. Your answer reminds me that we should start looking for the answer in the product literature (like Xming docs it should come with). Let me read about it before asking --more-- dumb questions, or I'll deserve a RTFM. I'll start looking for the parameters you point me to. Thank you, very much.

Cheers,

eureko

---

