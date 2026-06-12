---
title: "Yuri's Revenge"
date: 2006-07-28
forum: Gaming &amp; Leisure
---

### Post by frying_fish on 2006-07-28
Does anyone else on here have Yuri's revenge installed and working under wine, I have managed to get it installed, but now when it loads it crashes out with an internal error.

I might also add that this is infact further than it manages to get in windows where it just breaks before even finishing to load the game.

If anyone has any ideas they will be appreciated

---

### Post by jordilin on 2006-07-28
What kind of error do you get. tip: launch the game in the command line. Secondly, take a look at system logs such as /var/log/messages.

---

### Post by frying_fish on 2006-07-28
> **jordilin said:**
> What kind of error do you get. tip: launch the game in the command line. Secondly, take a look at system logs such as /var/log/messages.

Ok, /var/log/messages has nothing in it,

The actual message in game is

"Yuri's revenge has encountered an internal error and is unable to continue"

the output from the terminal is:
```


wine .wine/drive_c/Westwood/RA2/RA2MD.exe
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7fd7f2b0) : stub, emulating 64MB for now, returning 64MB
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd7ec30)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:keyboard:RegisterHotKey (0x10026,1,0x00000007,77): stub
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd80760)->(0x10026,00000011)fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd56cf8,0x7fb9d284,e8,0,0x7237007c,0x7fd54d1c,0x72370058): stub
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file tsun.dbg ("")
err:seh:setup_exception stack overflow 88 bytes in thread 000b eip 7ff8ffb6 esp 7fa90fa8 stack 0x7fa91000-0x7fba0000

```

To where it crashes out, doesn't seem to mean much to me.

---

### Post by jordilin on 2006-07-28
> **frying_fish said:**
> 
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd7ec30)->((nil),00000008 )

It seems, there is a problem with the Direct Draw implementation. I'm afraid this will be quite hard to fix or just impossible.

---

### Post by gtr225 on 2007-06-20
I tried installing it under Cedega, I get Red Alert 2 to install but when I try Yuri's Revenge, it says Red Alert 2 not detected.

---

