---
title: "Xinput and mouse/tablet events"
date: 2009-01-27
forum: General Help
---

### Post by Bubblesix on 2009-01-27
I've been disappointed with the module for my Aiptek Hyperpen 12000U provided with ubuntu: followed the guide at [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) and I had it working on everything but the pressure of the pen.

Googling around I found this guide for some alternative drivers. 
[http://blog.mymediasystem.net/uncategorized/apt-6000u/](http://blog.mymediasystem.net/uncategorized/apt-6000u/)
The guide is not perfect but gets the job done. Now, at the end of it, I could move my pointer around and a quick check with 
```

xinput list
xinput test "Aiptek"

```

Showed me great progress:
```

motion a[0]=571 a[1]=213 a[2]=1020 
motion a[0]=571 a[1]=213 a[2]=956 
motion a[0]=572 a[1]=212 a[2]=866 
motion a[0]=573 a[1]=210 a[2]=744 

```

a[0] is the X axis of the screen
a[1] is the Y axis of the screen
a[2] is the Z axis, the pressure of the pen, 1024 possible values while with the ubuntu provided module a[2] was always -1

At this point my real problem is: if Linux is able to use a[0] and a[1] to move my pointer around on the screen, why is it ignoring the a[2] completely? Is there any way to link it to some mouse event to use it possibly on Gimp?

---

### Post by Bubblesix on 2009-01-27
Found it..
In Gimp you have to Edit -> Preferences.. and then configure that particular input peripheral (aka, the tablet in my case) to be able to listen to "pressure" from the pencil

---

