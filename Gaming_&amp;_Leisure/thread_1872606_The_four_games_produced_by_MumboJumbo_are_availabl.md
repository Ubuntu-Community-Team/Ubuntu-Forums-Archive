---
title: "The four games produced by MumboJumbo are available in Ubuntu Software Center"
date: 2011-10-31
forum: Gaming &amp; Leisure
---

### Post by CityAceE on 2011-10-31
I proud to report that first four games for Ubuntu produced by MumboJumbo have became available in Ubuntu Software Center today. There are 7 Wonders: Magical Mystery Tour, Chainz Galaxy, Midnight Mysteries: Devil on the Mississippi and Unlikely Suspects.

They are available just for Ubuntu 10.10 and Ubuntu 11.04. Versions for Ubuntu 11.10 will be available during a few days.

[[IMG]http://i28.fastpic.ru/thumb/2011/1031/5f/ec46c9995fa33b80a4f0d4513bd9ba5f.jpeg[/IMG]](http://fastpic.ru/view/28/2011/1031/ec46c9995fa33b80a4f0d4513bd9ba5f.png.html)

---

### Post by sffvba[e0rt on 2011-10-31
*Thread moved to **Gaming and Leisure**.*


404

---

### Post by Hylas de Niall on 2011-10-31
Great stuff! I need more games :)
Especially the hidden object variety! Many thanks
:)

---

### Post by thatguruguy on 2011-11-02
Is this any closer to happening on 11.10?

---

### Post by stee1rat on 2011-11-03
Ye, it would be great to see this game in 11.10. Is there any news about it?

---

### Post by ubuntukid on 2011-11-04
Patiently sitting here at my 11.10 computer waiting to play Chainz Galaxy :popcorn:

---

### Post by stee1rat on 2011-11-10
Looks like "few days" already passed.. and still nothing. Why is it a problem to put this game on 11.10 software center?

---

### Post by CityAceE on 2011-11-10
Today's answer for Canonical:

> It is in the Software Center for Ubuntu 11.04. They were not tested for
11.10 because of the delay in getting them published. We are testing
them now and plan on making them available for 11.10 shortly.

---

### Post by thatguruguy on 2011-11-22
For anyone waiting for the rollout of these games in the USC on 11.10, they are available now.

---

### Post by CityAceE on 2011-11-22
The games are already in 11.10.

---

### Post by CityAceE on 2012-01-25
Users of Ubuntu 11.10 can try Chainz Galaxy DEMO for free from Ubuntu Software Center.

---

### Post by CityAceE on 2012-02-01
Now added 7 Wonders: Magical Mystery Tour DEMO to Ubuntu Software Center.

---

### Post by RavanH on 2012-03-01
Just bought and installed Midnight Mysteries: Devil on the Mississippi

But it won't even start :(

Tried it on two machines. From terminal with ```
$ /opt/MM3/MM3
``` I get this message

```

./HotBox: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

On the other machine I get some message about OpenGL... No dice :confused:

---

### Post by RavanH on 2012-03-01
OK, after installing the package libgl1-mesa-glx:i386 (I'm on a 64bit machine) it still won't start but the libGL.so1 message has now changed to the same message on the other machine:

```
$ /opt/MM3/MM3
Lua script executedPanic error in file "/home/ubuntu/Shared/HotSource_v5/HotEngine/Common/OpenGL/OpenGLTexture.cpp", line 687:
  Failed to create OpenGL texture (error code: 0x500, size: 500x256 -> 512x256, format: 7)
Aborted

```

Any other dependencies this package is missing? I feel this is not going anywhere :(

---

### Post by Carterclan on 2012-03-02
I downloaded chainzgalaxy demo played it and liked it so decided to buy it. Now it wont start properly, at least it does not appear on screen. It is running as it is showing up in system monitor and I have to kill it from there.
As I say had no problem with the demo, Any ideas anyone?

---

### Post by Carterclan on 2012-03-03
In an effort to get this working I have tried a few things, and now seem  to be able to get the game working (though not how it is supposed to)
I un-installed  the game and deleted the save file .Chainz Galaxy from the home folder, then re-installed the game.
When starting the game it still did not appear however I was able to get to it via Alt&Tab. This however only worked twice.
On  the 3rd attempt the game was not showing in the Alt&Tab menu though  the game was showing as running in the system monitor.
Also on this attempt the Unity interface went haywire, the lense would  not show and all the icons in the launcher became squashed so I killed  the game from system monitor then logged out and back in again.

Seeing  as Unity went funny I turned off wobbly windows as I am aware that many  compiz affects do not work well with Unity and it was the only affect I  was using.
Once again I was able to get into the game via Alt&Tab but once  again not with every attempt and having to go into system monitor to  kill the process. This time it did not affect Unity

Next, once I  got the game up again I switched off full screen mode from the games  options menu. Now it appears consistent and I am able to get to the game  at every attempt via Alt&Tab only.

I realise that this may lead you to believe that I have insufficient system requirements so i have listed my system below.

I also must stress that no problems exist with the demo version 

OS: Ubuntu 11.10 32 bit
Memory: 3.0 GiB
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ × 2
Graphics: GeForce 9300 GE/PCI/SSE2/3DNOW!

---

### Post by RavanH on 2012-03-16
I have similar results with Midnight Mystery. With the open nouveau driver for my Nvidia graphics, it simply woould not work (see error in my earlier post) but after switching to the closed/proprietary nvidia driver, the game works but I have to use Alt+tab to bring it into visibility... Weird stuff.

Nice enough game though ;)

---

