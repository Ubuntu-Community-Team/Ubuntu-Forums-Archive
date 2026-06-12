---
title: "Update to OpenGL 2.1 with ATI for Savage 2?"
date: 2008-12-27
forum: Gaming &amp; Leisure
---

### Post by black_whispers on 2008-12-27
Hi,

Installed Savage 2, and when I came to run it, it decided not to launch.

Terminal returns:
```
Savage2 - Fatal Error: OpenGL 2.1 not available.
Savage2 - Fatal Error: Segmentation Fault

Segmentation fault

```

I saw a different topic about this problem but with an Intel card, but with lspci you can see I don't have the same problem (in the other topic, the problem is that intel doesn't support openGL 2.

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
```

I know my hardware is up to scratch to play. Using IBM Thinkpad (T30).

Because I have an ATI card, I suspect that I can upgrade OpenGL to fix this problem, or I need better drivers for my card.
How do I do that? 

Any help greatly appreciated.

Thanks

Joe

---

### Post by itix on 2008-12-28
After some digging on my brothers computer which has savage2 installed I managed to find how to check the OpenGL version. Execute the command *glxinfo* in the terminal and somewhere in the immense rubble of information there will be the OpenGL version. His is OpenGL 2.1.2 Nvidia somethingish.

The latest proprietary ATI drivers should contain the latest OpenGL and they should be found under Administration => Hardware Drivers.

If not so, try google. I'm afraid I can't be of any more help than that.

---

### Post by black_whispers on 2008-12-29
Hi there.

glxinfo returns a load of info, inside which I find:
```

GLX version: 1.2
OpenGL version string: 1.3 Mesa 7.0.3-rc2

```
Again I noticed at the bottom,
```
Segmentation fault

```
What does this mean? It was returned when I tried to run Savage2.

Obviously I need to upgrade my openGL version.

I clicked through to Hardware Drivers under administration, but get the following notice;
No proprietary drivers are in use on this system.

I will check google for the latest drivers, and get back to you. Thanks itix for helping to validate that I need to upgrade openGL.

Thanks

Joe

---

### Post by itix on 2008-12-29
I was wondering what segmentation fault meant too, and now I know; [http://www.linuxquestions.org/questions/linux-newbie-8/what-does-segmentation-fault-mean-149530/](http://www.linuxquestions.org/questions/linux-newbie-8/what-does-segmentation-fault-mean-149530/)

1.2 won't do. To play Savage 2, wee need to swap the numbers.

I suspect that you, like me, can't find sh*t about how the hell one might upgrade ATI Radeon M7 to OpenGL 2.1. I Found a bunch of different forum threads, some of them in my native language Swedish which were somewhat helpful if your screen by any chance happens to be upside down, but they too had 1.2.

I wonder if it is possible. It should be since 2.1 has been around since early 2006. I mean... we had barely discovered fire by then ;)

---

### Post by curvedinfinity on 2008-12-29
Hey, perhaps there is a way to run savage 2 with a lower OpenGL specification, but if there isn't, you're out of luck! Your OpenGL version is tied directly to the hardware of your graphics card, so if you're running a laptop, the only way to upgrade the OpenGL version is to buy a whole new laptop.

---

### Post by curvedinfinity on 2008-12-29
> **itix said:**
> I was wondering what segmentation fault meant too, and now I know;

It just means the game crashed. On a more technical level, there was an unhandled exception, which can stem from a wide variety of causes. It probably has something to do with accessing memory incorrectly. :)

---

### Post by itix on 2008-12-29
Oops. Ouch.

Seams there will be no Savage 2 then. 
If you happen to come by sweden and Gnosjö, I bet my brother will lend you his computer ;)

I wonder why the hell ATI has not updated their OpenGL support since 1.2. Dinosaurs used 1.2 on their computers...

---

### Post by black_whispers on 2008-12-29
Thanks everyone for your help.

I guess I am stuck with no gaming.

What I don't understand though, is that when I was running Windows XP, I could run new openGL games (which I guess would require openGL 2), but can't when I switch to Ubuntu.

Meh, will just have to look for another MMORPG game that is older, or save up and buy a new laptop.

Thanks everybody (You have all been thanked.).

Joe

---

### Post by Melcar on 2008-12-29
You're using the default open source driver, which only supports opengl1.2-1.3.  The latest proprietary ATI drivers do not support that chip you have, so you will have to install the older drivers.
I think this version should work:

[http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html]("http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html")

However, since it's an old driver it is very likely to not be able to install on new kernels.

---

