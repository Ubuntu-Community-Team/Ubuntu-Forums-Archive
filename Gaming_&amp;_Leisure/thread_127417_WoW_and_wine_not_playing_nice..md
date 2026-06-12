---
title: "WoW and wine not playing nice."
date: 2006-02-08
forum: Gaming &amp; Leisure
---

### Post by RonJohnson on 2006-02-08
I have started getting this error after I downloaded and installed the patch. The install, initial movie and login to system worked. Next time I tried to run WoW I got the following output and error.

```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c2b0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c2b0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0eedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0ee58,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x20022): stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  682
  Current serial number in output stream:  682

```

Here is a copy of my config.wtf
```

SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1920x1200"
SET gxRefresh "60"
SET hwDetect "0"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "450.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "-1"
SET readEULA "-1"

```

I have a GeForce FX Go 5200 with the latest nVidia drivers. If you need any other data please let me know.

---

### Post by sornen on 2006-02-10
I was getting this problem with the latest patch.  It seems to do with blizzard harvesting information about your pc.

[http://forums.gentoo.org/viewtopic-t-246098-postdays-0-postorder-asc-start-225.html](http://forums.gentoo.org/viewtopic-t-246098-postdays-0-postorder-asc-start-225.html)

I fixed the problem by changing the directory

.wine/drive_c/Program\ Files/World\ of\ Warcraft/WDB

to read only.

---

### Post by RonJohnson on 2006-02-10
Well that helped get past the error. Now I'm having other issues with wow :cry: Now when WoW starts the system hangs. I can alt-tab and switch to the app but it'll take a few minutes to even give me the screen. When the screen does come up the mouse doesn't move. The audio is also very choppy. :-k 

I have tried the Cedega TimeDemo and I'm not impressed with their software at all. For them wanting me to pay them to use I'd rather get what seems like better results with wine. I just need to get wine working again...

Thanks for the help sornen

---

### Post by johso on 2006-02-11
The WDB folder is some kind of cache right? So if you can't write to it, then it seems quite logical that it would slow down the game, doesn't it? Have you tried to delete all it's contents, make it writable and then launch the game?
You're sure that your video driver hasn't been reset in the meantime, or something like that? It has happened to me before.

And I agree with you on the Cedega matter. I tried it out, and I couldn't even get Half-Life 2 working (which they are 'fully supporting'). There not real how-to. I'm sure that I could have made it work if I just tried long enough, but seriously, that's not what a program you eventually will pay for is worth.

---

### Post by RonJohnson on 2006-02-11
I figured out the problem that I was having with mine. For some reason I can only run the game if I'm running 1024x768. Any higher and the game craps out. I'd like to eventually fix this but I'm up and running!!!

Thanks for the suggestions guys. I appreciate the help.

---

