---
title: "Dreamweaver 8 via Wine or Crossover"
date: 2006-07-20
forum: Desktop Environments
---

### Post by MishMich on 2006-07-20
I have installed a trial version of crossover office, & couldn't get past an error on trying to install dreamweaver via the cdrom.  I have a legit copy of dreamweaver 8 with licence key - but I could not do an install  from cd.  So, I tried installing wine emulating 2000 - and tested it with basic windows programs, and it seemed to work OK.  Still no joy installing from cd.  So went online.  I went through a hack for pulling it over from the xp pc via ftp - put all the various directories over and copied the relevant registry entries over, converting from unicode to ascii on the way.  Dreamweaver loads, and I get a box saying something went wrong with installation, try again. Click that, and Dreamweaver closes.  I can still work with draemweaver with the box open & Dreamweaver in front, but feel a bit insecure while that box is still haning about.  Anybody got any info on how to get this working properly?

Screen output as follows:

$ wine /home/****/.wine/drive_c/Program\ Files/Macromedia/Dreamweaver\ 8/Dreamweaver.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f7d0,0x00000000), stub!
fixme:ole:CoRegisterMessageFilter stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
err:x11drv:X11DRV_CreateWindow invalid window height -2
fixme:imm:ImmSetCandidateWindow (0x7fd678f0, 0x7fb9ebc0): stub
fixme:imm:ImmReleaseContext (0x600f2, 0x7fd678f0): stub
fixme:imm:ImmReleaseContext (0x600f2, 0x7fd678f0): stub
fixme:imm:ImmReleaseContext (0xc0072, 0x7fd678f0): stub
fixme:imm:ImmReleaseContext (0xc0072, 0x7fd678f0): stub
fixme:mlang:fnIMLangFontLink_GetStrCodePages
fixme:mlang:fnIMLangFontLink_GetStrCodePages
fixme:mlang:fnIMLangFontLink_GetStrCodePages
fixme:mlang:fnIMLangFontLink_GetStrCodePages
fixme:mlang:fnIMLangFontLink_GetStrCodePages
fixme:mlang:fnIMLangFontLink_GetStrCodePages
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:imm:ImmReleaseContext (0xc0072, 0x7fd861e0): stub
fixme:imm:ImmReleaseContext (0xc0072, 0x7fd861e0): stub
fixme:imm:ImmReleaseContext (0xc0072, 0x7fd861e0): stub
fixme:imm:ImmReleaseContext (0xc0072, 0x7fd861e0): stub

The only other thing I need to work via Wine/Crossover Office is EndNote with Word.

If I can get this working, and decide to upgrade my newer XP-PC to ubuntu (as I like it so much), can I just transfer everything across in the .wine directory tree to the new machine for everything to work OK?

Mish

---

