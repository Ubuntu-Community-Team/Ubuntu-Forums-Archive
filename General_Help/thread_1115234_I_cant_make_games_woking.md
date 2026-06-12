---
title: "I cant make games woking"
date: 2009-04-03
forum: General Help
---

### Post by ariedry on 2009-04-03
everytime im runing a game thats happen ... even games for linux like Nexuiz ..


[IMG]http://i301.photobucket.com/albums/nn61/ariedry/screenshot2.png[/IMG]

---

### Post by ibuclaw on 2009-04-03
That looks distinctively like your graphics driver is failing to render anything 3D.

What card do you have? And what driver are you using for that card?

Can you post the following:
```
glxinfo > ~/Desktop/glxinfo.txt
```
The information inside glxinfo.txt

```
glxgears
```
Leave it running for a minute or two. Tell us if you can see the three gears rotating, and post the output FPS from that command.

Regards
Iain

---

