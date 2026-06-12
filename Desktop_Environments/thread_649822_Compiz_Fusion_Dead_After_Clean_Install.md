---
title: "Compiz Fusion Dead After Clean Install"
date: 2007-12-25
forum: Desktop Environments
---

### Post by family on 2007-12-25
Before my clean install of Ubuntu, Compiz Fusion worked great. Not one single crash.
However, now, no matter what I do (uninstall everything compiz related, remove old repos,  then reinstall with new repos) CF will just not work.
Lspci:
```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)

```
Terminal output says;
```

compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```
I tried Alberto Milone's Envy... No go.
I never had to configure XGL or AIXGL last time. I just installed ccsm and couple plugins, and it worked.

Can anyone point me to older versions of Compiz Fusion (and no, Beryl has never worked for me)..? Thank-you.

Anyone think if I try to compile CF myself it will work? Or just create a mess?

---

### Post by TidusBlade on 2007-12-25
Maybe try install "xserver-xgl" package from Synaptic?

---

### Post by family on 2007-12-25
*smacks forehead*
il try installing everything xgl-related i can find :)

edit>>> why is that not a dependency for compiz-core???

---

### Post by family on 2007-12-25
I'm installing xserver-xgl and 180 other things (updates)... I cant compiz --replace yet because its updating too :(.
Anyone know of Compiz Fusion alternatives? I know beryl doesnt work for me, but what about Matisse (I think that's a Mandriva thing..). Are there any others?

---

### Post by TidusBlade on 2007-12-25
Not sure why it idint, but I am using Compiz Fusion without that... but may help ro something? And what graphics card do you have?

---

### Post by family on 2007-12-25
I'm not positive, I heard lspci was good for this hardware stuff so I put it in my first post.
I'll check around and edit this post if I find it.

edit> pretty sure it is 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

---

### Post by family on 2007-12-25
I found a very good thread;
[http://ubuntuforums.org/showthread.php?t=527749](http://ubuntuforums.org/showthread.php?t=527749)

---

### Post by TidusBlade on 2007-12-25
Not sure how Compiz works with Intel cards, only had a 3 day experience with that and I forgot it, but it should work okay.

---

### Post by family on 2007-12-25
Yeah, the xserver-xgl package was already installed. Patching my xorg.conf resulted in a minor catastrophy (but I got to recovery mode). xserver-xorg-driver-i810 video thing was installed already...
Again, anybody know of alternatives or legacy versions of CF?

---

### Post by family on 2007-12-26
Ok... This has gone on long enough.
I don't think this is a problem with compiz-core. I followed Forlong's Guide the first time i installed CF, but this time I used the CF package from the Gutsy repos. I tried the Feisty compiz-core package and followd the same guide again. No luck.
I know I have the correct drivers, since I have never needed restricted ones and my Xorg has never failed me (except for that one time I edited it... =p). 
Can someone please tell me what I should do to get it back?

---

