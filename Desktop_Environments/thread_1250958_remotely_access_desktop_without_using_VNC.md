---
title: "remotely access desktop without using VNC"
date: 2009-08-27
forum: Desktop Environments
---

### Post by thgis on 2009-08-27
Hey.
I just started using ubuntu. I'm used to windows and have used remote desktop available in windows XP pro a lot. I want to do the same with my ubuntu linux workstation. I have tried using VNC (vino and vinagre) but are not very satisfied with the result. Specially I find it annoying that I can't change the resolution as I can on windows remote desktop. Further it seems a lot slower although it is on 100 mbit.

Is there another way to remotely connect and use programs on my remote ubuntu desktop?

Regards,
Thomas

---

### Post by i.r.id10t on 2009-08-27
If you have a local x server (cygwin-x on windows, just plain 'ol X on a *nix box) then you can export your display over a ssh tunnel.

---

### Post by bterminalx on 2009-08-28
If you're looking at school, and they use windows, then the Remote Desktop Connection should be avaliable.

You can run a RDP server on ubuntu.

```
sudo apt-get install xrdp
```

If they don't have that option avaliable, you can always get the really really really portable lite version of UltraVNC (I personally recommend)

---

### Post by Rajwinder on 2009-08-28
You can also use terminal server client under applications then internet and then select it.

---

### Post by tlyczko on 2009-11-04
is the TS client available in Xubuntu or is it a different install??

---

