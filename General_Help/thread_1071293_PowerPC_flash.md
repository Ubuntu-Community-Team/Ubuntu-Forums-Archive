---
title: "PowerPC flash"
date: 2009-02-16
forum: General Help
---

### Post by injector2 on 2009-02-16
before I start to get flamed, let me start by saying that i'm not a linux expert but I know enough to survive, with that said, i finally managed to install Linux onto my PS3 after running Hardy on my laptop for a month to get used to the commands before even touching the PS3.

the install went fine, it took some tinkering to kboot to get the resolution but that's another story, as many of you know PSUbuntu run on the PPC platform, which is where the problem lays, Adobe flash under linux only supports x86 and x64 not PPC, i know Gnash and swfDEC work under PPC but they don't support hulu which is one of the big ones.

I was looking at the Adobe site and they have a PPC version of flash but it's for a Mac, it's a dmg file, converting the dmg file is not a problem, my question is once i get it converted where do I start? theoretically Mac is unix based and should be somewhat compatible with Linux? <-- this will get me flamed but i need to learn

---

### Post by injector2 on 2009-02-16
well i went ahead and mounted the file and looked at the files in it to see if i could make anything out of them

```

lgp@lgp-laptop:~$ sudo modprobe hfsplus
[sudo] password for lgp: 
lgp@lgp-laptop:~$ sudo mount -t hfsplus -o loop /home/lgp/Desktop/flash.iso /home/lgp/Desktop/folder/

lgp@lgp-laptop:~$ cd Desktop/
lgp@lgp-laptop:~/Desktop$ cd folder/
lgp@lgp-laptop:~/Desktop/folder$ ls
Adobe Flash Player.pkg

lgp@lgp-laptop:~/Desktop/folder$ cd Adobe\ Flash\ Player.pkg/

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg$ ls
Contents  Icon?

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg$ clear
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg$ ls
Contents  Icon?

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg$ cd Contents/
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents$ ls
Archive.bom  Archive.pax.gz  Info.plist  PkgInfo  Resources

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents$ cd Resources/
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources$ ls
Adobe Flash Player.bom     ICVersionValidator.awk
Adobe Flash Player.info    MacOSXVersionCheck.sh
Adobe Flash Player.pax.gz  package_version
Adobe Flash Player.sizes   postflight
Archive.sizes              preflight
background.tif             RemoveUserFPInstall.applescript
CloseFPClients.app         Welcome.rtf
Description.plist

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources$ cd CloseFPClients.app/
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app$ ls
Contents

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app$ cd Contents/
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents$ ls
Info.plist  MacOS  PkgInfo  Resources

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents$ cd MacOS/
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents/MacOS$ ls
CloseFPClients

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents/MacOS$ cd ..
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents$ cd Resources/
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents/Resources$ ls
English.lproj  FP128.icns  greyBackground.png

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents/Resources$ cd English.lproj/
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents/Resources/English.lproj$ ls
CBLocalizable.strings  CFPCMain.nib

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents/Resources/English.lproj$ cd CFPCMain.nib/
lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents/Resources/English.lproj/CFPCMain.nib$ ls
classes.nib  info.nib  keyedobjects.nib

lgp@lgp-laptop:~/Desktop/folder/Adobe Flash Player.pkg/Contents/Resources/CloseFPClients.app/Contents/Resources/English.lproj/CFPCMain.nib$ 



```

---

### Post by Alterax on 2009-02-16
No flames, I promise.

Unfortunately, converting the DMG file won't do much good; it's a binary that leans heavily on Apple's proprietary APIs, which I doubt will ever be ported to Ubuntu.

You may be able to use gnash for this--it's in the software repositories as a third-party Flash reader and plugin--but I'll just say (as a ppc user on my laptop) that it's still not fully functional, so I'm not sure if it'll do Hulu or not.

It is, however, worth a try.

---

### Post by zoggnoff on 2011-04-05
I looked into doing this very same thing but was not able to convert the dmg to img for mounting even though i am pretty sure i did all the steps correctly. kudos

can anyone say, but please omit any obvious comment about not being legal to do it, how and what one would decompile to source to rebuild for use on a linux ppc64? and how messy would this be and where would one start?

---

