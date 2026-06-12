---
title: "[Ubuntu 18.04] How to put bare sound applet in Metacity panel?"
date: 2020-06-15
forum: Desktop Environments
---

### Post by cross05 on 2020-06-15
I detest the Gnome 3 UI.  So, I'm running Metacity.

The gargantuan kitchen-sink indicator applet is total rubbish, I don't want all of it.  I'm not alone in this thinking since there are individual applets available for most of what it provides.
One applet I cannot find an individual version of is the sound-indicator applet.  Is there any way to get a sound control in the panel without loading that overbloated kitchen-sink catch-all?

As an alternative, is there a way to edit what gets put into the kitchen-sink applet so I can remove the bloat?

Thanks.



(I did attempt to search the forums.  These forums and the advanced search in particular are not intuitive, so I didn't get very far in my search.)

---

### Post by #&amp;thj^% on 2020-06-18
You can just use Pulseaudio to control all your sounds.
Make sure the important piece is installed with:
```
sudo apt install pavucontrol
```
to use it run:
```
pavucontrol
```
Also there should still be this: 
Run:
```
gnome-volume-control-applet
```

---

