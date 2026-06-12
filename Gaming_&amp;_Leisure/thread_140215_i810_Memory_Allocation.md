---
title: "i810 Memory Allocation"
date: 2006-03-05
forum: Gaming &amp; Leisure
---

### Post by Grey on 2006-03-05
I am having a problem with my i915GM video card.  I am running Dapper Drake at the moment, but I was having the same problem on Breezy.  The problem is that the video card never steals more than 8MB of main memory for video memory.  This is fine for a lot of things, but it restricts my abilities in even the most basic 3D Graphics.  The Lava Lamp screensaver does not even render the entire lamp.

So my question is, does anyone know of any way of making sure that the video card steals memory when it's supposed to?  Or barring that, at least uses a good chunk at boot?  I have this line in my xorg.conf, which I believe in theory allocates a maximum of 256MB to the video card:

```

        VideoRam        262144

```

---

### Post by ximok on 2006-03-06
Ah, you are on the right track for memory allocation, but there is a trick about the i810 driver.  It can't do 3d rendering in 24 bit color.  At max, it'll do it in 16 bit color.   So, what you do is set your defaultdepth to 16, not 24.

You can test your result by running ```
 glxinfo |grep render 
```
if you get a "YES" then you are set and ready to go.  If you get a "No" you haven't got your settings right yet.  You shouldn't need to steal more than 16-32 megs for any of the screensavers.

Once glxinfo tells you that it is rendering, then you should see very beautiful results with the graphics.  Remember, you have to restart your X server for your settings to take effect.

---

### Post by Grey on 2006-03-06
No, I'm pretty sure that 3D Acceleration is working.  (I'm running in 24-bit though).  It's just that it doesn't request enough memory to actually be useful.  I experience things like missing textures, and in some cases, missing models which is usually indicative of a lack of video memory.  If it helps, here's my glxinfo:

```

grey@Maria:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225

```

---

### Post by syg00 on 2006-03-06
Start [here](http://www.geocities.com/stomljen/). I used the 885resolution on a Dell laptop successfully.

---

### Post by Grey on 2006-03-06
That's just for setting your graphics card to a non-native resolution though, is it not?  My laptop works just fine at my LCD's native resolution.  Or is there something I'm missing?

---

### Post by syg00 on 2006-03-06
Mutter, bloody grumble ...
Sorry - wrong link. Try [this](http://www.chzsoft.com.ar/855patch.html) for some relevant info on my problem. May be helpful.

---

### Post by az on 2006-03-30
[QUOTE=Grey]I am having a problem with my i915GM video card.  I am running Dapper Drake at the moment, but I was having the same problem on Breezy.  The problem is that the video card never steals more than 8MB of main memory for video memory.  This is fine for a lot of things, but it restricts my abilities in even the most basic 3D Graphics.  The Lava Lamp screensaver does not even render the entire lamp.

So my question is, does anyone know of any way of making sure that the video card steals memory when it's supposed to?  Or barring that, at least uses a good chunk at boot?  I have this line in my xorg.conf, which I believe in theory allocates a maximum of 256MB to the video card:

```

        VideoRam        262144

```[/QUOTE]

I think your card can dynamically allocate ram, if it is available.

If you have less than 128 megs of ram, you get nothing.

If you have 256 mregs of ram, I think it can allocate up to 64 megs.

If you have more ram, if can go up to 96 megs of ram.

It does this on-the-fly.

I think.

---

