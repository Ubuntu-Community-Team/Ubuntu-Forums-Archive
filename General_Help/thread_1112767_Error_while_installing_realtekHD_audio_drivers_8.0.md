---
title: "Error while installing realtekHD audio drivers 8.04"
date: 2009-04-01
forum: General Help
---

### Post by clone11 on 2009-04-01
I'm installing my audio drivers now but i'm running in to a problem on step 3 it says to do sudo make, When i do that it outputs this
```
chris@chris-desktop:~/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11$ sudo make
make dep
make[1]: Entering directory `/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11'
make[2]: Entering directory `/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/acore'
copying file alsa-kernel/core/info.c
/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/chris/Desktop/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11'
make: *** [include/sndversions.h] Error 2

```

---

### Post by Sinkingships7 on 2009-04-01
I have NEVER successfully installed the Linux version of the Realtek audio drivers. I don't remember the name, but the driver requires some package that isn't in production anymore. Without it, you will be unable to compile the source.

Funny thing: my name is Chris also.

EDIT: My above words are my experience with the Realtek HD drivers, which I just realised might not be what you're talking about.

---

### Post by clone11 on 2009-04-01
Well what would you recomend doing, right now my audio is barely working correctly, it cuts out stero does not work. Is there any open source audio that would support my chipset?

---

### Post by clone11 on 2009-04-01
bump

---

### Post by clone11 on 2009-04-01
I have got them to compile and install now the problem i'm running in to is this.
```
Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
snd-ALC883
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx  
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss
```
Am i supposed to put all that in my moduels file like this?
```
	
snd-ALC883
#ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-ALC883    
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss
```

---

### Post by clone11 on 2009-04-01
I went ahead and added that to my mod file without putting the snd-ALC883 at the top and my audio is still messed up, i can't play stero, and mono lags what ever app is outputting the sound

---

### Post by Lunx on 2009-04-01
Sorry I'm not technically experienced enough to offer advice, but there are a couple of useful threads I've been using to get a few problems ironed out.

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Hopefully you may find what you need there, or at least a starting point for further digging

---

### Post by clone11 on 2009-04-01
I tried that my audio sounds correct now, but when I load up runescape if it's on mono or stero it does the samething it lags and then plays again lags plays again.

---

### Post by clone11 on 2009-04-01
Bump any fix for my last problem?

---

### Post by clone11 on 2009-04-01
bump

---

### Post by Sinkingships7 on 2009-04-01
I know this sounds dumb, but are you sure your volume is up? That was my first problem when I thought my sound wasn't working right.

---

