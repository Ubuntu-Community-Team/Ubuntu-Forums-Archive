---
title: "Ubuntu 14.04: Custom Unity Session with Top Panel but without Launcher?"
date: 2014-10-29
forum: Desktop Environments
---

### Post by myacct on 2014-10-29
Hello,

I'm interested in creating a custom xsession with Unity's Top Panel but without the Unity Side Launcher and Search.  I'd trying to create a session combining of the Unity Top Panel with Cairo-dock and the ElementaryOS SlingShot launcher. 

I've been following the instructions [here]("http://ubuntulandforever.blogspot.com/2012/06/how-to-disable-unity-launcher-and-use.html") without success.  I'm using an up-to-date version of Ubuntu 14.04 and have installed all of the transitional unity-2d packages

Thanks in advance for any insights

---

### Post by Frogs Hair on 2014-10-29
The linked article is from 2012 and likely for 12.04. !4.04 uses a different version on unity and is based on Gnome 3.10 rather than 3.4. The unity 2d session was removed in 12.10

---

### Post by myacct on 2014-10-29
Yea, I notice that.  However, I was hopeful that there might be a way to make the unity-2d packages in the 14.04 repository do the trick.  Either way, it stands to reason that there should be a method to create a custom session with the top panel by itself, I hope.

---

### Post by Frogs Hair on 2014-10-29
If you want a traditional style session which you can install a dock in, the gnome-session-flashback should do the trick. Making Unity 2d work in 14.04 could be possible, but you would have to build and test the packages yourself if no one else has. Unity 2d belongs to different version of Unity and different versions of Gnome use different libraries.

---

