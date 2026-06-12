---
title: "Enemy-Territory 2.60"
date: 2006-01-25
forum: Gaming &amp; Leisure
---

### Post by Mikecore on 2006-01-25
I just tried installing ET three time and no luck. It starts the game and I can even hear the startup sounds but the screen goes black and never come back. 

anybody else have this problem?

---

### Post by Perfect Storm on 2006-01-26
Any output errors when you run it through the terminal? Did you setup your 3D card?

---

### Post by Mikecore on 2006-01-26
Im sorry I was drinking last night when I posted this. 
Yes my video card is setup correctly i have dri enable and working.
There was no error messages ! just a blank screen.

I googled last night and the only thing I could come up with was on MAC's systems 
they were having a similar problem. and they found that ET was shutting off the monitor somehow. I will look into it today after work. Thanks

---

### Post by Mikecore on 2006-02-04
Well i have been working on this problem and i think im geting closer.

I realized that on my toshiba satellite M55 that my native screen res is 1280x768
and in my xorg.conf that was the only res setup. So I edited my config file and added
1024x768 abd 800x600. 

in my perfs I can now choose between 1280x768 and 1024x768 but not 800x600?

next I found that ET was trying to start up in 800x600 mode for I added an autoexec.cfg file with a startup mode of 1024x678. And set my screen to 1024x768
this should have worked but it didn't. Im still stuck with a running game and no screen.

---

### Post by Mikecore on 2006-02-04
here is the X failure 

```

RE_Shutdown( 1 )
X Error of failed request: BadValue (integer parameter out of range for operatio n)
  Major opcode of failed request: 135
  Minor opcode of failed request: 10
  Serial number of failed request: 1445


```

---

### Post by Mikecore on 2006-02-10
Ok well I figured out why the other screen resolutions will not work. my VBIOS is hosed up and it only shows that I can run in two resolutions. 1280x768 and 1024x768. ( has to do with being a widescreen laptop and the i810 driver ) 

So now the next trick is to try to start ET with a screen res of 1024x768.

I cant just edit the "et config file " cause until you setup a profile one is not genterated. So I will have to look into trying to start ET in a set Resolution mode.

---

