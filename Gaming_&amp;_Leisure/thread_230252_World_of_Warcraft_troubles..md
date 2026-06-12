---
title: "World of Warcraft troubles."
date: 2006-08-05
forum: Gaming &amp; Leisure
---

### Post by Taiden on 2006-08-05
So, when I make a new character it loads just fine and everything works. When I log into an already created character, it crashes. Here is the log from the terminal of everything that is happening, from launching, to crashing. If you guys have any ideas of what might be causing this, let me know. Thank you!

```

greybox@greybox:~$ wine media/Downloads/Frostwire/World\ of\ Warcraft/WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cf90000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cf90000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f388,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f628,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f628,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x33f098,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33e428,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e480,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  1030
  Current serial number in output stream:  1030

```

---

### Post by Taiden on 2006-08-07
bump it up. hopefully someone knows what is up.

:)

---

### Post by sgtBiafra on 2006-08-08
Seems like the infamous mini-map crash. A recent patch (1.9 or 1.10 don't remember which) changed how the mini-map is rendered and that subsequently broke WoW under WINE.

If you still want to play without the mini-map (it's a bit more annoying to find things and you lose out on gathering nodes sometimes), you can grab one of several mods that hides the mini-map. These typically load during log-in so they prevent this crash.

Perhaps someone has come up with a replacement mini-map as well. I wonder if any of those full mod packages has one that works under WINE. Maybe someone will post their experiences.

---

