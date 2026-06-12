---
title: "SVGA in DOSBOX 0.72?"
date: 2009-06-11
forum: Gaming &amp; Leisure
---

### Post by DaGrimReefah on 2009-06-11
I've been trying to figure this one out... I recently installed "An Elder Scrolls Legend: Battlespire" but it runs like crap on DOSBOX 0.72 (through repositories), on my 2.5 GHz Celeron with 1 GB of RAM and an NVidia Geforce 6200. I want to run it using SVGA_S3 instead of just plain VGA, thinking maybe that will allow for better framerate. I changed my dosbox.conf accordingly:


```

[dosbox]
# language -- Select another language file.
# memsize -- Amount of memory DOSBox has in megabytes.
# machine -- The type of machine tries to emulate:hercules,cga,tandy,pcjr,vga.
# captures -- Directory where things like wave,midi,screenshot get captured.

language=
machine=svga_s3
captures=capture
memsize=63
```

Notice under "# machine", it doesn't even suggest "svga_s3" (like the Windows DOSBox.conf does.) I figured, oh well, I'll put "svga_s3" next to "machine" anyway. The game still starts, but it's because it defaults back to VGA automatically, and the error I get when running in terminal is:
```

DOSBOX:Unknown machine type svga_s3
```

Before I am asked, let me save you the inconvenience and say that I have already tweaked my dosbox.conf to play Battlespire as good as possible (including setting output to "opengl", "-freesize 300", "memsize 63", etc.) except when it comes to changing the machine type to "svga_s3" Am I missing something here?

---

### Post by rCXer on 2009-06-11
I don't think 0.72 has svga_s3.  You need DOSBox 0.73 although it isn't in the Ubuntu repositories yet.  A user named Grishka made 0.73 binaries which can be downloaded [here](https://launchpad.net/~thir/+archive/ppa). Just remember to regenerate "dosbox.conf" using "config -writeconf dosbox.conf" from the dosbox prompt.  I think it puts the file in "/home/YourUserName/". Alternativelly, [here](http://ubuntuforums.org/showthread.php?t=1171794) are instructions on how to build your own 0.73 in ubuntu. You may have to install sdl libraries e.g. libsdl1.2-dev.

---

### Post by DaGrimReefah on 2009-06-11
> **rCXer said:**
> I don't think 0.72 has svga_s3.  You need DOSBox 0.73 although it isn't in the Ubuntu repositories yet.  A user named Grishka made 0.73 binaries which can be downloaded [here](https://launchpad.net/~thir/+archive/ppa). Just remember to regenerate "dosbox.conf" using "config -writeconf dosbox.conf" from the dosbox prompt.  I think it puts the file in "/home/YourUserName/". Alternativelly, [here](http://ubuntuforums.org/showthread.php?t=1171794) are instructions on how to build your own 0.73 in ubuntu. You may have to install sdl libraries e.g. libsdl1.2-dev.

That's the answer I was looking for, although strangely enough the Google search description for DOSBox 0.72 for linux says it has SVGA support. Although now I am starting to think that was just the general description for DOSBox, lazily tacked on to the Linux version. Thanks!

---

### Post by Mike'sHardLinux on 2009-06-11
DaGrimReefah, I am not sure, but it sounds like you are misunderstanding what is SVGA. I am running DOSBox .72 and at this very moment, am running Windows 3.1 at a resolution of 1280 x 1024. That is beyond SVGA. SVGA is only 800x600.

---

### Post by CharmyBee on 2009-06-11
> **DaGrimReefah said:**
>  runs like crap on DOSBOX 0.72 (through repositories), on my 2.5 GHz Celeron
With that CPU, you can forget about DOSBox then. Try dosemu.

---

### Post by DaGrimReefah on 2009-06-15
> **Mike'sHardLinux said:**
> DaGrimReefah, I am not sure, but it sounds like you are misunderstanding what is SVGA. I am running DOSBox .72 and at this very moment, am running Windows 3.1 at a resolution of 1280 x 1024. That is beyond SVGA. SVGA is only 800x600.

Thanks for the responses. You're right, I did misunderstand, lol.

[QUOTE=CharmyBee]With that CPU, you can forget about DOSBox then. Try dosemu.[/QUOTE]

Haha, first time I've heard that, but OK, why not. Thanks for the suggestion!

---

### Post by CharmyBee on 2009-06-15
I suggested that since you're trying to do SVGA. Those are generally only 'smooth' for the multi-core setups, and even then it's not perfect.

---

