---
title: "wine vs guildwar problems"
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by wittewol on 2007-07-24
well my problem is that guildwars seemes to work fine, but after about 10 seconds the window crashed 

can somebody help me i've been working it for days now. even the howto also found in this form doesn't work

the line i use = wine "C:\Program Files\Guild Wars\Gw.exe" -nosound -dx9 -noshaders -windowed -perf >/dev/null 2>&1

thxs
:confused:

---

### Post by ubuntu.daemon on 2007-07-24
[QUOTE=

the line i use = wine "C:\Program Files\Guild Wars\Gw.exe" -nosound -dx9 -noshaders -windowed -perf >/dev/null 2>&1
:confused:[/QUOTE]

no clue what that dev/null stuff is for, but what you need to do at least 


```
user@home:~Program Files$ wine Guild Wars\Gw.exe -opengl
```

thats probably why it is crashing honestly, why the nosound?  and wtf the dx9??  i didnt think that was an option for wine ....  just try what i gave u and get back to me with the results from xterm...

---

### Post by wittewol on 2007-07-24
when i do 

wine "C:\Program Files\Guild Wars\Gw.exe" -opengl

THIS HAPPENS
Guild wars starts to run in a separate window for about 4 secs and then the window/guildwar crashes
In the terminal this is seen and way more

fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x7d5a52f0, 260): stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b40020) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b40020) : stub

hope to get it fixed:)

---

### Post by lordhebe on 2007-07-24
There is no opengl mode for guild wars, so the -opengl flag should do nothing.

The -nosound flag shouldn't be necessary, as is the -noshaders. If you have an nvidia card (I had no luck trying this on an ati) you can use -dx9 for maximum graphical quality.


I would use this line:```
wine "C:\Program Files\Guild Wars\Gw.exe" -dx9
```

If your system locks up, use:

```
wine "C:\Program Files\Guild Wars\Gw.exe" -dx9 -dsound
```

---

### Post by wittewol on 2007-07-24
Thxs for the lines

but still the fixme lines and the games still dies after 4 sec.

with -dsound/-nosound it works a little bit longer :)

and i have an ati radeon

:popcorn:

---

### Post by ubuntu.daemon on 2007-07-25
here u go probably alot better support =P
[http://appdb.winehq.org/appview.php?iVersionId=7530]("http://appdb.winehq.org/appview.php?iVersionId=7530")

---

### Post by dorath on 2007-07-25
> **ubuntu.daemon said:**
> here u go probably alot better support =P
[http://appdb.winehq.org/appview.php?iVersionId=7530]("http://appdb.winehq.org/appview.php?iVersionId=7530")

/nod

But for the record, I'm using:```
wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -dx8 -windowed >/dev/null 2>&1
```

Runs fairly well.  **wittewo**, what happens when you run the game without any arguments at all?  Same thing?

---

