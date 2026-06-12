---
title: "WoW troubles.... in Dapper Drake"
date: 2007-02-16
forum: Gaming &amp; Leisure
---

### Post by dopefishlives on 2007-02-16
I am trying to get World of Warcraft working on my PC and I seem to be having endless challenges with it... so much so I'm afraid I may be tempted back to Win XP for this system due to so many other challenges I've had related to its hardware.

System:
Dell Latitude D610
1.6GHz Pentium M
512MB DDR RAM
ATI Radeon X300 Mobility

Running Ubuntu 6.06, FGLRX video driver and WINE 9.30

The installer worked perfectly from disc 1 through disc 4, even ran the game initially through the cenimatics. As soon as they were over however both WoW and WINE closed. I checked the WoW 'error' folder and found this:

==============================================================================

World of WarCraft (build 5595)



Exe:      C:\Program Files\World of Warcraft\WoW.exe

Time:     Feb 16, 2007  9:29:44.892 PM

User:     dopefish

Computer: dopefish-laptop

------------------------------------------------------------------------------



This application has encountered a critical error:



ERROR #132 (0x85100084) Fatal Exception

Program:	C:\Program Files\World of Warcraft\WoW.exe

Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000000



The instruction at "0x00000000" referenced memory at "0x00000000".

The memory could not be "read".





WoWBuild: 5595

------------------------------------------------------------------------------



----------------------------------------

    x86 Registers

----------------------------------------



EAX=001924F0  EBX=7DEC909C  ECX=7DEB60A0  EDX=00000028  ESI=00000030

EDI=00000000  EBP=0034C5A0  ESP=0034C524  EIP=00000000  FLG=00010206

CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B





----------------------------------------

    Stack Trace (Manual)

----------------------------------------



Address  Frame    Logical addr  Module



00000000 0034C5A0 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe

7DE556E8 0034C6B0 0001:000346E8 c:\windows\system32\wined3d.dll

7DE3C680 0034C710 0001:0001B680 c:\windows\system32\wined3d.dll

7DEE0E85 0034C740 0001:0000FE85 c:\windows\system32\d3d9.dll

005A0C80 0034C774 0001:0019FC80 C:\Program Files\World of Warcraft\WoW.exe

0058A408 0034C790 0001:00189408 C:\Program Files\World of Warcraft\WoW.exe

0058A41B 0034C7B8 0001:0018941B C:\Program Files\World of Warcraft\WoW.exe

0070AF2C 0034C84C 0001:00309F2C C:\Program Files\World of Warcraft\WoW.exe

0070826E 0034FBC8 0001:0030726E C:\Program Files\World of Warcraft\WoW.exe

0076CCEE 0034FCA0 0001:0036BCEE C:\Program Files\World of Warcraft\WoW.exe

0046F91F 0034FCC4 0001:0006E91F C:\Program Files\World of Warcraft\WoW.exe

00764FA7 0034FCE8 0001:00363FA7 C:\Program Files\World of Warcraft\WoW.exe

00763A0C 0034FCF4 0001:00362A0C C:\Program Files\World of Warcraft\WoW.exe

0044263E 0034FDBC 0001:0004163E C:\Program Files\World of Warcraft\WoW.exe

004246A0 0034FDF0 0001:000236A0 C:\Program Files\World of Warcraft\WoW.exe

0042105F 0034FE60 0001:0002005F C:\Program Files\World of Warcraft\WoW.exe

00420BE1 0034FE78 0001:0001FBE1 C:\Program Files\World of Warcraft\WoW.exe

0040410E 0034FF08 0001:0000310E C:\Program Files\World of Warcraft\WoW.exe

7B86D59F 0034FFE8 0001:0004C59F c:\windows\system32\kernel32.dll



----------------------------------------

    Stack Trace (Using DBGHELP.DLL)

----------------------------------------



I have since upgraded from version 1.02 of WoW and am now running 1.12 but there has been no change... also when I try to add the 'SET OpenGL' command to the config.wtf WoW will crash but not in the same fashion and an error log is not generated. It only pops up the message '3D acceleration not supported', I click OK and it closes WINE.

I snooped around WINE-HQ/appsDB but had no luck with anything listed there.

Thanks,
_Kris

---

### Post by wowgamer on 2007-02-16
Well i am a fellow wow player myself :)  and one thing you could do is Download the game from one of the many private servers that have the link and then install through the download.

---

### Post by dopefishlives on 2007-02-17
What benifit would I have of downloading a questionable/illegitimate version of the game from an online resource when I have a full legal copy that was successfully updated by the Blizzard patch software?

It just seems that would introduce more troubles than it would resolve.

_Kris

---

### Post by Motoxrdude on 2007-02-17
Install WoW in windows and then take those install files and copy them to your ubuntu partition. Run the .exe and see if it plays.
Or
> cd /WoW direcotory
wine wow.exe -opengl
I think the exe was called "wow" but i can't remeber exactly, but i think you get what i mean.

---

### Post by Praill on 2007-02-18
Alright, I've had a lot of troubles with wine myself and I have just got it working now after several weeks of research, trial and error, and frustration. Here's what I found out.

Wine 0.9.30 is perfectly cable of running WoW (without patching) if you compile it from source, resolving ALL dependencies and WARNING messages it displays during the configure. Don't install wine from the package manager because its not the newest version. And once again.. resolve ALL dependencies and warnings before you compile.
The only editing of wine you'll need to do is add a registry entry for openGL, and change it to WindowsXP in winecfg. But these should only affect perfomance.

I would guess the reason why you can't get WoW to work is because either a)wine was compiled without all the neccessary dev packages, or b) your card isnt supporting 3d acceleration correctly.

If youre certain wine is installed resolving all dependencies and warnings then ATI's website has a proprietary linux driver you can try, or you can get the fglrx package from synaptic (I have it and it works fine).
To install either driver you can follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
It's written with Edgy in mind, but should work just as well with Dapper.

The above site will tell you how to install your video card with 3d capability, and how to check to make sure it has 3d capability.
However, with an ATI card, WoW will still have problems. After weeks I finally found the problem.
You have to edit your xorg.conf file (sudo gedit /etc/X11/xorg.conf) after the driver has been installed correctly.. and look for the following lines:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Then you need to append this section so it looks like this:
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
        Option "Capabilities" "0x00000800"
        Option "UseFastTLS" "off"
        Option "KernelModuleParm" "locked-userpages=0"	
EndSection

I don't know what any of these options do, or mean, but I know it worked for me (and im running an x series ati card too.. x1400). Whenever messing with your xorg file make sure you save a backup so you can restore the backup if X wont start afterwards.

If you manage to get WoW to boot up you can go here:
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
to maximize performance. It will tell you about the registry entries you have to create, and a couple of DLL's some people might have to get.

Good luck.
Let me know if this works for you.

---

### Post by hikaricore on 2007-02-18
Praill, sorry you had so much trouble... but you are aware that there are almost biweekly  ubuntu/debian releases of Wine on the official site right?

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

or to simpily download the package:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Praill on 2007-02-21
Thanks for your concern.
Yes, I'm aware of the deb packages available. But since wine will readily install with minimum functionality I find it safer to install from source so you can resolve all required and recommended dependencies.

---

### Post by justin whitaker on 2007-02-21
Gentlemen, did you try Crossover yet? I just bought it after installing WoW and TBC with it....flawless, at least for me. YMMV. Download a trial and give it a shot!





Toons: 
Mateotg, Blackhand, Gamers With Jobs Alliance.
ToroMateo, Blackhand, GWJ Horde

---

### Post by Praill on 2007-02-28
Why?
I got it working with wine and it was alot more fun than Crossover just working :)

---

