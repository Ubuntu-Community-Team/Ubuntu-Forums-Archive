---
title: "Sound card help in Wine"
date: 2006-07-08
forum: Gaming &amp; Leisure
---

### Post by disk11 on 2006-07-08
I'm trying to play Red Alert 1 using wine, but the performance is really slow, I think due to my sound card not being configured right in winecfg.  Here's the output I get:
```
******@ubuntu:~$ wine /cdrom/autorun.exe
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7fd8cc48) : stub, emulating 64MB for now, returning 64MB
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd8c5b0)->(0x10030,00000011)fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_ASYNC flag right now.
err:ntdll:RtlpWaitForCriticalSection section 0x7fd63b2c "WINEALSA_mmap_crst" wait timed out in thread 000f, blocked by 0000, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7fd63b2c "WINEALSA_mmap_crst" wait timed out in thread 0010, blocked by 0000, retrying (60 sec)

```

I have a onboard Realtek ALC650, using the 0.9.16~winehq0~ubuntu~6.06-1 package of wine.  I only have the ALSA box checked in the audio tab of winecfg, and trying various other sound card drivers didn't help.  Any advice?

---

### Post by vem0m on 2006-07-09
type winecfg in terminal to mess with your sound settings however it look like more of a GFX problem to me. do you have 3d Acceleration enabled? E.G proper drivers installed? also check and make sure its reading all your avialible Video card ram as the output looks like its only using 64 MB, is that all your card has? hoep this helps

---

### Post by disk11 on 2006-07-14
> **vem0m said:**
> type winecfg in terminal to mess with your sound settings however it look like more of a GFX problem to me. do you have 3d Acceleration enabled? E.G proper drivers installed? also check and make sure its reading all your avialible Video card ram as the output looks like its only using 64 MB, is that all your card has? hoep this helps

I have all the proper boxes in the grpahics tab of winecfg enabled, and I've got the newest nvidia drivers installed via synaptic, but I'm still having the same problems.  Could it be a simlink being messed up due to an older driver?

The VRAM is not being reported right, I have a Leadtek GF4 ti4400 with 128MB of RAM.

---

### Post by disk11 on 2006-07-16
I uninstalled nvidia-glx and linunx-restricted modules and reinstalled them and also installed anything with "xlib" in it and I got Red Alert to work.  In gameplay however, it was very choppy.  Here's the output:
```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7fdaab98) : stub, emulating 64MB for now, returning 64MB
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd6de18)->(0x10030,00000011)fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_ASYNC flag right now.
matt@ubuntu:~$ err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6d6b0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6d6b0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6d6b0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6d6b0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6d6b0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6d6b0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6d6b0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6dc38
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6dc38
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd654b8
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd6da60
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd6de18)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

So I have some video related errors but a ton of sound buffer underruns.  Any thoughts?

---

### Post by Amaroq on 2007-03-02
I have no idea. I'm getting sound buffer underrun errors as well with a game I'm trying to get running under wine. I was hoping to find an answer around here, but alas my search continues.

There is a bug about the sound buffer underrun filed with winehq though.

---

