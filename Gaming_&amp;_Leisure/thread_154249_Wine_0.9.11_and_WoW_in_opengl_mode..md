---
title: "Wine 0.9.11 and WoW in opengl mode."
date: 2006-04-02
forum: Gaming &amp; Leisure
---

### Post by Zer0d on 2006-04-02
The game runs great on the new wine version but the mouse does not work properly i cant target enemyes and so on.( Right mouse key ) Here is the output:

```
root@zer0d:~/Desktop/WoW# wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7ca80000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7ca80000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f448,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6e8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f158,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not suppor ted on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9e4d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9e530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

What can i do about this?

---

### Post by trorion on 2006-04-02
[QUOTE=Zer0d]The game runs great on the new wine version but the mouse does not work properly i cant target enemyes and so on.( Right mouse key ) Here is the output:

What can i do about this?[/QUOTE]

There is a patch called wine-wow-fixes.patch which you may need to patch into wine before compiling.  I'll try it out.

By the way, 0.9.6 doesn't work in dapper...

---

### Post by trorion on 2006-04-02
well...
When I compile wine from CVS it won't open a window (gives an error as if X isn't running) so I can't tell you if it will run WoW or not.

---

### Post by Zer0d on 2006-04-03
Ok thanks im gonna look for the patch now :)

---

### Post by dragge on 2006-04-03
I'm using the latest wine and i think it boosted my fps with around 10.
I installed from winehq repo using apt and ofc, the "mouse bug" are still not fixed in the source so u need to patch it with the wow_patch.

---

### Post by Zer0d on 2006-04-05
I t runs great on the new wine :) the only problem i have is the right mouse key not working. I have read all the threads about the problem and tryed to patch it. But how do i do this in wine 0.9.11?

---

### Post by Zer0d on 2006-04-05
[QUOTE=trorion]There is a patch called wine-wow-fixes.patch which you may need to patch into wine before compiling.  I'll try it out.

By the way, 0.9.6 doesn't work in dapper...[/QUOTE]

I have tryed the patch with wine 0.9.11 but i only got some errors. I also tryed to patch the old version and it worked nice. But i need to use the new one ;)

---

### Post by Toxicity999 on 2006-04-05
Well... look at what the patch changes in each source (old version and new...) check for any differences and patch it manually. 'Course this would only work if its not another part of the program making it screwy... in essence I'm saying try to update the patch file for this version if at all possible. and if it works, have fun.

---

### Post by Zer0d on 2006-04-06
[QUOTE=Toxicity999]Well... look at what the patch changes in each source (old version and new...) check for any differences and patch it manually. 'Course this would only work if its not another part of the program making it screwy... in essence I'm saying try to update the patch file for this version if at all possible. and if it works, have fun.[/QUOTE]

Ok I'm gonna try that out. What language is the script file made in? Nice to know so I can start learning the way it works :)

---

