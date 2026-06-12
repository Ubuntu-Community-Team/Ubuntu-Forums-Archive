---
title: "WoW installation problem"
date: 2006-12-30
forum: Gaming &amp; Leisure
---

### Post by Ozcu on 2006-12-30
So, I just installed World of Warcraft for my linux (Im using Kubuntu( by followin[these](https://help.ubuntu.com/community/WorldofWarcraft)steps. I have followed instructions EXACTLY and then I type those first two lines (which are avove) to Konsole:


```
osmo@osmo-laptop:~$ cd '/home/osmo/.wine/drive_c/World of Warcraft'
[email]osmo@osmo-laptop:~/.wine[/email]/drive_c/World of Warcraft$ wine wow.exe
Xlib:  extension "GLX" missing on display ":0.0".
err:opengl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c230000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c230000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbef04,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
fixme:dbghelp:sffip_cb NIY on 'E:\build\buildWoW\WoW\bin\Wow.pdb'
[email]osmo@osmo-laptop:~/.wine[/email]/drive_c/World of Warcraft$

```

Then it just "stubs(?)"

Then it Launches Wowerror.exe or somtehing, which looks like this:
[img]http://koti.mbnet.fi/viikuna/upload/uploads/Wowitus.png[/img]
(Dont care about cropping, cba cropping it anymore 8) )

Then nothing happens. I would really apriciate your help

- Ozcu

---

### Post by Sammi on 2006-12-30
I am by no means an expert, but this line makes me think your grafics drivers aren't installed right:
```
Xlib:  extension "GLX" missing on display ":0.0".
```Try reinstalling them. What card do you have?

---

