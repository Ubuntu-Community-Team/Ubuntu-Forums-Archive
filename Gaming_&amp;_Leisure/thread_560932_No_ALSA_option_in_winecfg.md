---
title: "No ALSA option in winecfg"
date: 2007-09-27
forum: Gaming &amp; Leisure
---

### Post by lckeeper1 on 2007-09-27
Hey all,

I just complied wine-0.9.45 from the source, and applied the patches so I could play the ETQW. Unfortunately, when I run winecfg and click the audio tab, there is no option for ALSA sound. I was previously using the wine .deb from synaptic and it was fine. The only sound option I have is OSS.

Also, when I click the audio tab, it says that alsa is in the registry, though it is an unknown driver, and do I want to remove it from the registry.

I would quite like to keep the patched version so as to play ETQW and I have another patch in there for WoW. Is this version just bonked, and I have to recomplie, or is there another way to get the ALSA driver in there, even though it's still in the registry. Thanks in advance.

---

### Post by tbroderick on 2007-09-27
Did you install the alsa dev pacakges before compiling? Check if libasound2-dev and either lib32asound2-dev or lib64asound2-dev. If not, install the dev packages and recompile.

---

### Post by Big_Rog on 2007-10-01
I compiled the .46 source for the hang-on-exit bug and somehow killed my alsa support as well.  I have just installed (and reinstalled) the pre-comp binary for .46 and it didn't pick alsa back up.  I do have the dev for libasound2 installed, but i can't find the lib32 dev in synaptic.  i've also reinstalled the alsa base packages but that hasn't helped either.  Alsa was present and functional prior to my diy-compile.

my major impetus for this is to get the in-game voice chat working, but the stuttering sound and glitch every few seconds is driving me crazy to boot.

---

