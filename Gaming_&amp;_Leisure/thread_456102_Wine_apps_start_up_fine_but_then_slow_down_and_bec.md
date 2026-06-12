---
title: "Wine apps start up fine but then slow down and become useless"
date: 2007-05-27
forum: Gaming &amp; Leisure
---

### Post by rumo_orbis on 2007-05-27
I have tried several games using wine (Jagged Alliance, Fallout 2, Moorhuhn Kart) and all of them work perfectly. I can start them and they run perfectly. But then after some time they start to lag and the sound becomes distorted. I tried all kinds of options in the winecfg and nothing changed anything. I tried I think all options there were in the audio and graphics tab.
nothing helped. 

i use xubuntu feisty and the newest version of wine.

can anyone help? thanks. rumo.

---

### Post by rumo_orbis on 2007-05-29
bump

---

### Post by hikaricore on 2007-05-29
You might want to launch them from a terminal and wait til they start slowing down, watch for errors in the terminal from wine.  It is normal to have many errors when running wine in a terminal window, but if you see something specific when it starts to slow down, it may help further diagnose the issue.

It sounds like some kinda memoy leak to be honest.  What kinda hardware are you running on?

---

### Post by rumo_orbis on 2007-05-31
i was thinking of a memory leak too... but i have no idea really, especiall with linux :).
i ran two different games for errors: the first was Moorhuhn Kart XXL which is a 3D racing game. I got tons of errors, most of them concerning graphics. i can't show you the whole log as its far too long, but those 3 kinds of errors occured:
```
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet

err:dsound:DSOUND_MixOne underrun on sound buffer 0x4ae3a80

fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1574 < primary_done=1578)
```

i couldnt really tell exactly when it started to be unplayable, its more of a gradual process.

then i tested jagged alliance 2, which is old and 2d. much less errors, the log is as follows:
```
*****@*****-laptop:~$ wine '/home/*****/.wine/drive_c/Program Files/Jagged Alliance 2 Gold/ja2.exe'
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x170948) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x170118)->(0x10028,00000011)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1f01f8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1f01f8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1f01f8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1f01f8

```

they have one error in common, the dsound one. what does it mean? do you know how i could fix it?

my system is a dell inspiron 8600... i dont actually know my specs (whats the command for looking that up?). i have a graphics card with fglrx driver and it runs well. 1 gig of memory. i ran beryl without problems, so i think that shouldnt be the problem, especially as those games arent really demanding.

thanks for any help. rumo.

---

### Post by graigsmith on 2007-05-31
it's probably ati's driver that's causing all the problems.

when i last used it on my x800 about a week or 2 ago.. it froze my whole system. so it wouldn't surprise me if it wasn't all that stable.

---

### Post by Ferrat on 2007-05-31
Sound more like a memory leak problem

How did you install wine? from deb or did you build it yourself?
What sound do you use with wine? OSS, ALSA, E ? 
Do you have other wine apps running?
Any other program using the sound driver or grafic driver?

I know that when I used to run WoW using the OSS driver caused sound to crack when there was more grafics or alot of sounds, using AOSS or just running with ALSA fixed this.

---

### Post by YokoZar on 2007-05-31
Try switching off Beryl and see if things don't improve.

---

