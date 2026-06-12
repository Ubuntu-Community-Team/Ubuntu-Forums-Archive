---
title: "CoD problem"
date: 2006-08-21
forum: Gaming &amp; Leisure
---

### Post by underworld288 on 2006-08-21
I got the game install fine its just when I go to start the game an error message pops up saying "Call of Duty couldn't write a file. The hard drive is probably full.". I don't know how much space is left on the drive but I just installed it two days ago and its a 60GB so it shouldn't be full. Any help?

thanks

---

### Post by den benne on 2006-08-21
perhaps a permission issue?

---

### Post by underworld288 on 2006-08-21
ok then how would i fix that?

---

### Post by underworld288 on 2006-08-22
ok i fixed that by just typing "sudo codsp" in the terminal but now it says "Miles sound system initialization failed. The single player game does not        
work properly without sound. Make sure you have your sound card's latest 
drivers and DirectX installed." then another window pop up and gives me this...

...loading 'fxshaders/weaponfx.shader'
----- finished R_Init -----

------- Miles sound system initialization -------
Attempting 44 kHz 16 bit stereo sound
couldn't initialize 2D provider: waveOutOpen() failed.
----- CL_Shutdown -----
RE_Shutdown( 1 )
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...deleting GL context: success
...releasing DC: success
...destroying window
...resetting display
...shutting down QGL
...unloading OpenGL DLL
-----------------------
Hunk_Clear: reset the hunk ok
Miles sound system initialization failed.
The single player game does not work properly without sound.
Make sure you have your sound card's latest drivers and DirectX installed.

any suggestion?
thanks

---

### Post by underworld288 on 2006-08-22
i almost forgot here is what is says in the terminal....

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x16b658) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16af10)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:keyboard:RegisterHotKey ((nil),0,0x00000001,9): stub
fixme:wgl:wglMakeCurrent (0x2f0,0x176090)
fixme:wgl:wglMakeCurrent GWOEX failed
fixme:wgl:wglMakeCurrent worg is 0.0nGWEEX failed
fixme:wgl:wglMakeCurrent wext is 1.1n make current for dis 0x7c03b760, drawable 0x3c00002, ctx 0x7c213530
fixme:wgl:wglMakeCurrent ((nil),(nil))
fixme:keyboard:UnregisterHotKey ((nil),0): stub

---

### Post by den benne on 2006-08-22
I'm no expert, so sorry I can't help

have you tried installing it via the loki-installer:
[http://www.liflg.org/?catid=7&gameid=1](http://www.liflg.org/?catid=7&gameid=1)

---

### Post by underworld288 on 2006-08-22
that is how i installed it

---

### Post by Scythe!? on 2006-08-22
Can CoD run natively!?

---

### Post by underworld288 on 2006-08-22
no you need wine, and the loki installer

---

### Post by Cyraxzz on 2006-08-22
I would like to know this as well, i sometimes get these size problems when runing game on whine.

---

