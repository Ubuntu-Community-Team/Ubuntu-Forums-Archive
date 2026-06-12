---
title: "Epsxe No Sound On Ubuntu 10.10"
date: 2010-11-22
forum: Emulators
---

### Post by axelord on 2010-11-22
Dear friends at Ubuntu Forum,

I`m getting no sound from Epsxe on Maverik, seems to be a problem with the SPU Plugin (as it seems its not kicking in when lauching the game). All my plugins are latest version and were working just fine on 10.04. Has anyone figured that out already? any help is more than welcome!

P.S: Games are emulating just fine, only sound isnt working. Also, tried to compile the OSS sound plugin for ALSA but returns an error regardind a wrong pentium -m parameter...(my processor is a AMD PhenonII x4 965) :-(

---

### Post by Darent on 2010-12-14
Same problem here... don't mess with the plugins because it's not the reason, if you look the terminal output say something about "not loading libcanberra-gtk-module.so" so its a problem related with the sound libraries of the system, not the emulator. Reinstalling libcanberra doesn't solve it. 

The only solution i've found is running the epsxe 1.7 for windows under wine, it works well, but my system is not enough powerfull to run it smooth (ubuntu emulating windows emulating a psx...), but give it a try.

If you found a solutions, please post it here :) Good luck!

---

### Post by WINGZERO619 on 2010-12-16
I'm currently running ePSXe 1.6.0 using WINE.  Graphics and sound currently work without issue.  For my sound plugin, I am using the Eternal SPU Plugin 1.41.  It's pretty much in the default setting with the exception of checking off one more option, "Enable XA sound (Select to enable XA sound in MDEC).  I am running all this on an Acer Aspire Timeline X 1830T-68U118.  Hope the sound plugin info helps.

---

### Post by Buttink on 2010-12-17
have you tried

```
padsp ./epsxe
```

Assuming you have an OSS plugin.

---

### Post by dmatos88 on 2010-12-19
> **Buttink said:**
> have you tried

```
padsp ./epsxe
```Assuming you have an OSS plugin.

It really fix the no sound problem, thanks.

---

### Post by Darent on 2010-12-19
Hi, thanks a lot! it worked for me too. The sound is working, except for the cdda (no soundtrack in wip3out for example), but i think that's a diferent problem.

Funny but the 1.7 running under wine works better than the 1.6 linux...

---

### Post by axelord on 2011-03-19
It indeed solves the problem. Thanks guys.

---

### Post by z-itou16 on 2011-04-23
Buttink,

THANK YOU SO MUCH! Can you imagine I even tried to compile using ALSA and it worked but not fluently.

Using wrapper was brilliant and truly helpful.

Many thanks

---

### Post by Je Et on 2011-05-28
> **Buttink said:**
> have you tried

```
padsp ./epsxe
```Assuming you have an OSS plugin.


Had been trying everything to get the sound to work and **padsp ./epsxe** worked like a charm. Exactly what does that do? Again... many thanks!

---

### Post by moebius444 on 2011-06-06
```

padsp ./epsxe

```

i confirm that this works in kubuntu 11.04

---

### Post by adrianj2012 on 2011-07-19
I hope I'm posting in the right place (still somewhat new), but whenever I try the command 
```
padsp ./epsxe
```I get this:
```
exec: 88: ./epsxe: Permission denied
```Running with sudo before it makes no difference.
Any thoughts? If it helps, the sound plugin I'm using is P.E.Op.S. OSS Audio Driver 1.9
Thanks in advance!

---

### Post by Darent on 2011-07-20
Probably epsxe is not marked as executable, in the directory where epsxe is, run:

chmod +x epsxe

(you'll need sudo only if epsxe is installed system-wide, not if it's in your home)

After that, you should be able to run it with your command:

padsp ./epsxe
Usually in linux when you download an executable the system doesn't trust it and doesn't allow it to run until you change its permissions with chmod +x

Good luck!

---

### Post by adrianj2012 on 2011-07-24
Thanks, Darent! Changing the permissions did the trick! Now to tweak the sound plugin to get it exactly how I want it... thanks again, everyone!

---

### Post by Possum93 on 2012-03-14
No Sound!
 
 
I have just installed Ubuntu 10.10 on a multi-boot system and my sound card doesn't even show up. There is sound on the other operating systems, but not on Ubuntu 10.10. I have an Realtek ALC260 sound card not sure what to try next any suggestions, thought about reinstalling because prior to updates it worked.

---

### Post by hackedhacker on 2013-02-24
> **Buttink said:**
> have you tried

```
padsp ./epsxe
```Assuming you have an OSS plugin.
This solved mine...
thanks...

---

