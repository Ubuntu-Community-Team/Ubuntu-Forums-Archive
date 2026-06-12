---
title: "Screen Sver problem"
date: 2008-05-26
forum: Desktop Environments
---

### Post by duncanyoyo1 on 2008-05-26
Hello, I recently installed the extra screen savers from
```
xscreensaver-data-extra
```
and
```
xscreensaver-gl-extra
```

Now when I go to change my screensaver, I get a system lock up. The mouse still moves, but there is no response to keyboard shortcuts like Ctrl+Alt+Backspace

So I am asking
1. Why is this happening
and 
2.How can I get it to stop

My System specs are

AMD Ahtlon 6000+ @3.22GHz
nVidia GeForce 8500GT
3GB DDR2 RAM
500 GB SATA Hitachi hard drive
Running Ubuntu 8.04
also I have Compiz-Fusion and AWN

I believe this to be an OpenGL error, but I could very well be wrong.

---

### Post by drewcoon on 2008-05-26
Do you have Compiz going? I have this exact same issue (it's affected by Compiz for me).

I fixed my similar problem by getting xscreensaver off synaptic, and substituting gnome-screensaver with it.

try,

```
sudo apt-get install xscreensaver
```

then add a startup script in System > Preferences > Sessions,

```
xscreensaver -no-splash
```

The only drawback is that the lock screen button stops working, since it uses gnome-screensaver somehow. Worth a shot though I think... Worked for me :)

Also I have crappy onboard ATI graphics, which makes me think you are right about it being an OpenGL error, because it's obviously not a graphics hardware issue.

---

### Post by duncanyoyo1 on 2008-05-26
Meh, I never use the lock screen thing, and thanks.

It seems to be ONE specifis screen saver thats causing me problems though.

IMSmap is whats messing my system up. 

But that xscreensaver program lets me disable it so it's all good. =D

---

