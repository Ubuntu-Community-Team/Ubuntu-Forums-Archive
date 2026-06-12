---
title: "PSone emulation under Ubuntu"
date: 2005-10-23
forum: Gaming &amp; Leisure
---

### Post by snooo on 2005-10-23
Quick question: has anyone managed to get PSone emulation going under Ubuntu breezy? I have tried the executables availible for ePSXe, only to find that the plugins provided at [http://www.pbernert.com/html/gpu.htm](http://www.pbernert.com/html/gpu.htm) give me this complaint and cause a segmentation fault:

"libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
"

Is there a way to get around this? Can I set up a symlink to fool the binary into thinking the library is there? Or is it permanently screwed? In case anyone was wondering, I cant seem to get it going under Wine....

---

### Post by snooo on 2005-10-23
After following the instructions at: [http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/#epsxe](http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/#epsxe) i've managed to get rid of the last error. Yet I'm still getting segmentation faults, although this time they seem unexplained. Has anyone any experience of getting ePSXe working and how did they do it?

---

### Post by jamyskis on 2005-10-23
I haven't personally tried ePSXe under Linux, but I would suggest from the errors that you point out that might be worth downgrading your compiler (either gcc or g++) to 3.3 or 3.4 and the version of libcstd++ associated with them) and compiling with that. This is based on experience, as I know that GCC 4.0.2 causes some very weird results with the C++ standard library.

---

### Post by snooo on 2005-10-25
i got it working eventually by playing with the paths... but the software is a badly designed buggy peice of crap anyway. and it doesnt help that my ATI drivers seem to crash the PC every so often. I guess its windows for emulation, for now. :-/

---

### Post by rpgcyco on 2005-10-25
> but the software is a badly designed buggy peice of crap anyway.

Yeah, the Linux version of ePSXe, is not as polished as the Windows version. That's for sure. Though I did have it working fine in Ubuntu.

Have you tried PCSX? I ran both in Ubuntu before I went to Arch.

> and it doesnt help that my ATI drivers seem to crash the PC every so often.

That blows. :( Unfortunately, I do not know anything about their drivers, so I can't help on that front. :(

- Rpg Cyco

---

### Post by aminalshmu on 2005-10-25
i remember getting that error. i think it was the eternal SPU plugin. symlink didn't work. the plugin is pretty screwed up. epsxe itself works pretty well in linux for me. i have to use 1.5.2 for chrono cross and some other games, but between that and 1.6.0 i can run pretty much anything. pete's plugins work flawlessly.

try removing any instances of the eternal SPU plugin from the epsxe plugins and cfg folders. any other problems with it i will be glad to help troubleshoot.

---

### Post by dryandplain on 2005-10-25
Don't give up hope, [Alucard is waiting for you!]("http://i24.photobucket.com/albums/c35/dryandplain/sotn.png")

I was able to get things working well with this Debian PCSX tutorial:
[http://eric.halo43.com/linux_psx_emu.php](http://eric.halo43.com/linux_psx_emu.php)

---

### Post by rpgcyco on 2005-10-25
The Eternal SPU plugin works fine, it's just built with a very old version of GCC.

Installing the package **libstdc++2.10-glibc2.2** fixed the problem up good for me. :)

```
sudo apt-get install libstdc++2.10-glibc2.2
```

There was recently a BETA version of Eternal 1.5 released. No support for Linux at the moment (I don't think), but hopefully it will support it in the future.

- Rpg Cyco

---

### Post by janga on 2005-11-03
I am using P.E.Op.S. OSS Audio Driver 1.6 with ePSXe, and it works very well. Sometimes, the sound is a bit laggy, but it works!

---

### Post by arcanistherogue on 2005-11-03
Hey, anyone know a good PSone controller to PC adapter for linux?  Will the ones on lik sang work?  

I wanted this, and If they ahve a working emulator that lets me play my games on teh computer I want to have my controller with it too :D

And is there a n64 one too?

---

### Post by dolny on 2005-11-04
[QUOTE=dryandplain]Don't give up hope, [Alucard is waiting for you!]("http://i24.photobucket.com/albums/c35/dryandplain/sotn.png")

I was able to get things working well with this Debian PCSX tutorial:
[http://eric.halo43.com/linux_psx_emu.php](http://eric.halo43.com/linux_psx_emu.php)[/QUOTE]

Worked for me - but what do I write in the input configuration ( /dev/js0 by default) to change it to keyboard?

OK /dev/kbd1, 
nevermind

---

### Post by Biased turkey on 2005-11-04
[QUOTE=rpgcyco]The Eternal SPU plugin works fine, it's just built with a very old version of GCC.

Installing the package **libstdc++2.10-glibc2.2** fixed the problem up good for me. :)

```
sudo apt-get install libstdc++2.10-glibc2.2
```

There was recently a BETA version of Eternal 1.5 released. No support for Linux at the moment (I don't think), but hopefully it will support it in the future.

- Rpg Cyco[/QUOTE]
So far, I was able to run EPSXE with Fedora core2, fedoracore3 and Debian.
I couldn't run it with Ubuntu but as I remember, Fedora included some "legacy" c compiler packages.
I'l try to install the libs you mentions.
Yes, EPSXE linux version is not as good as the windows counterpart, but it still works nicely.
Imho what's missing is a **decent** controller plugin.
Pete's plugins are very good, that guy did a fantastic job for EPSXE in both Windows and Linux version
[http://www.pbernert.com/](http://www.pbernert.com/)

---

### Post by dolny on 2005-11-04
Can you play your games using CDs under PCSX? I only saw 'run exe' or 'run <something>' and I don't know how to run a game from a CD :|

---

### Post by BoyOfDestiny on 2005-11-04
[QUOTE=dryandplain]Don't give up hope, [Alucard is waiting for you!]("http://i24.photobucket.com/albums/c35/dryandplain/sotn.png")

I was able to get things working well with this Debian PCSX tutorial:
[http://eric.halo43.com/linux_psx_emu.php](http://eric.halo43.com/linux_psx_emu.php)[/QUOTE]

Nice. I'm a big castlevania fan (both emulated and I own a lot of the carts... and the cd for this one too :) )

However, the english voice acting for Symphony of the Night... It would be awesome to keep the voices japanese and have the text be english...

Anyway why the rant...enjoy this spoof. It primarily uses sound bytes from the game (mostly unmodified).

[http://www.videogamedc.com/Fan_Flicks/Symphony_of_the_Night__Alterna/symphony_of_the_night__alterna.html](http://www.videogamedc.com/Fan_Flicks/Symphony_of_the_Night__Alterna/symphony_of_the_night__alterna.html)

P.S I know the animation is silly, but the voice acting kills the mood anyway...

---

### Post by Biased turkey on 2005-11-05
[QUOTE=rpgcyco]The Eternal SPU plugin works fine, it's just built with a very old version of GCC.

Installing the package **libstdc++2.10-glibc2.2** fixed the problem up good for me. :)

```
sudo apt-get install libstdc++2.10-glibc2.2
```

There was recently a BETA version of Eternal 1.5 released. No support for Linux at the moment (I don't think), but hopefully it will support it in the future.

- Rpg Cyco[/QUOTE]

Just tried that, got an ( strange ) error message:
 undefined symbol: XftDrawSetClipb
is it an xorg message ?

---

### Post by rpgcyco on 2005-11-06
That *is* strange. I have not encountered that error message before.

> **Xft**DrawSetClipb

Xft, is that short for X Font server or something? I know the Eternal SPU plugin has a different interface [in terms of the way it looks] than ePSXe itself [GTK1] and GTK2 programs. I don't know what it could be called, however.

- Rpg Cyco

---

### Post by Biased turkey on 2005-11-22
[QUOTE=rpgcyco]That *is* strange. I have not encountered that error message before.



Xft, is that short for X Font server or something? I know the Eternal SPU plugin has a different interface [in terms of the way it looks] than ePSXe itself [GTK1] and GTK2 programs. I don't know what it could be called, however.

- Rpg Cyco[/QUOTE]

I have it working now. I switched to libgpuPeteXGL2.so.2.0.7 for the video plugin and activated the No ATI render texture extension option.
I can play Granturismo2 at least with the keybord. The only thing left wil be to add the joystick plugin.
I'm almost there.
Thanks again for the help.

To Snoo: great link about how to have EPSXE running with Linux.

---

