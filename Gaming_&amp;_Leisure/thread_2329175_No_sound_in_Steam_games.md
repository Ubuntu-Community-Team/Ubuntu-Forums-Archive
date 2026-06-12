---
title: "No sound in Steam games"
date: 2016-06-28
forum: Gaming &amp; Leisure
---

### Post by Fred Le Rouge on 2016-06-28
Hi everyone!

Recently I started playing [Frozen Synapse]("http://store.steampowered.com/app/98200/") thanks to Steam but there is no sound when I launch the game... It happened to me before when I tried to install [Wolfenstein: Enemy Territory]("http://www.splashdamage.com/wolfet").
Somebody in the French Ubuntu Forum told me to install some packages but it did not solve my problem, as you can see below.

```
frederic@frederic-W55xEU:~$ sudo apt install libasound2:i386 libasound2-plugins:i386
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
libasound2:i386 is already the newest version (1.1.0-0ubuntu1).
libasound2-plugins:i386 is already the newest version (1.1.0-0ubuntu1).
frederic@frederic-W55xEU:~$
```

What should I do? Thank you for your help!

PS : I use Ubuntu 16.04, 64bits.

---

### Post by Liam_Murphy on 2016-06-28
Even if you're not an Arch user, the Arch wiki can be very helpful.

[https://wiki.archlinux.org/index.php/Steam/Troubleshooting#FMOD_sound_engine](https://wiki.archlinux.org/index.php/Steam/Troubleshooting#FMOD_sound_engine)

May have to do some wiki article jumping, but google is your friend.

---

### Post by Fred Le Rouge on 2016-06-28
I already searched on google but I did not find anything close to my problem. Most of the packages referenced on the Arch wiki are either already installed on my system or impossible to find.

---

### Post by mastablasta on 2016-06-29
perhaps the ldpreload command might work if oyu knew which libraries need to be loaded.

i had the same issue with wolfenstein and it was difficult to troubleshoot as there were no apparent errors reported. so in the end i gave up and booted into win7 to play it.

---

### Post by MikeCyber on 2016-06-29
ldd gamename should give infos about missing libs. Also simply running in a terminal gives a lot of infos.

---

### Post by Fred Le Rouge on 2016-06-29
@MikeCyber
You were right! I did ldd with Frozen Synapse and it said that libSDL-1.2.so.0 was missing.

I installed it by doing:
```

sudo apt-get install libsdl1.2debian:i386

```

I launched the game but still no sound. I tried:
```

sudo apt-get install --reinstall libsdl1.2debian

```

But it did not work either. Now I am stuck with this:
```

frederic@frederic-W55xEU:~/.steam/steam/steamapps/common/Frozen Synapse$ ldd FrozenSynapse 
    linux-gate.so.1 =>  (0xf7726000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf76f9000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf76dc000)
    libSDL-1.2.so.0 => /usr/lib/i386-linux-gnu/libSDL-1.2.so.0 (0xf7639000)
    libsteam_api.so => /home/frederic/.steam/steam/steamapps/common/Frozen Synapse/./libsteam_api.so (0xf7629000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf74b2000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf745d000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf7440000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7289000)
    /lib/ld-linux.so.2 (0x565f5000)
    libasound.so.2 => /usr/lib/i386-linux-gnu/libasound.so.2 (0xf7173000)
    libpulse-simple.so.0 => /usr/lib/i386-linux-gnu/libpulse-simple.so.0 (0xf716d000)
    libpulse.so.0 => /usr/lib/i386-linux-gnu/libpulse.so.0 (0xf7113000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf6fc8000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf6fb2000)
    libcaca.so.0 => /usr/lib/i386-linux-gnu/libcaca.so.0 (0xf6ee8000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf6edf000)
    libpulsecommon-8.0.so => /usr/lib/i386-linux-gnu/pulseaudio/libpulsecommon-8.0.so (0xf6e57000)
    libjson-c.so.2 => /lib/i386-linux-gnu/libjson-c.so.2 (0xf6e4a000)
    libdbus-1.so.3 => /lib/i386-linux-gnu/libdbus-1.so.3 (0xf6df0000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6dca000)
    libslang.so.2 => /lib/i386-linux-gnu/libslang.so.2 (0xf6c9e000)
    libncursesw.so.5 => /lib/i386-linux-gnu/libncursesw.so.5 (0xf6c69000)
    libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0xf6c45000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf6c2a000)
    libsystemd.so.0 => /lib/i386-linux-gnu/libsystemd.so.0 (0xf6b9c000)
    libwrap.so.0 => /lib/i386-linux-gnu/libwrap.so.0 (0xf6b92000)
    libsndfile.so.1 => /usr/lib/i386-linux-gnu/libsndfile.so.1 (0xf6b19000)
    libasyncns.so.0 => /usr/lib/i386-linux-gnu/libasyncns.so.0 (0xf6b11000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6b0d000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6b06000)
    libselinux.so.1 => /lib/i386-linux-gnu/libselinux.so.1 (0xf6ae0000)
    liblzma.so.5 => /lib/i386-linux-gnu/liblzma.so.5 (0xf6aba000)
    libgcrypt.so.20 => /lib/i386-linux-gnu/libgcrypt.so.20 (0xf6a0a000)
    libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xf69ef000)
    libFLAC.so.8 => /usr/lib/i386-linux-gnu/libFLAC.so.8 (0xf698f000)
    libvorbisenc.so.2 => /usr/lib/i386-linux-gnu/libvorbisenc.so.2 (0xf6903000)
    libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf68ea000)
    libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf6874000)
    libgpg-error.so.0 => /lib/i386-linux-gnu/libgpg-error.so.0 (0xf685e000)
    libogg.so.0 => /usr/lib/i386-linux-gnu/libogg.so.0 (0xf6855000)
    libvorbis.so.0 => /usr/lib/i386-linux-gnu/libvorbis.so.0 (0xf6829000)
frederic@frederic-W55xEU:~/.steam/steam/steamapps/common/Frozen Synapse$ 

```

---

### Post by MikeCyber on 2016-06-30
All seems there. Paste the output of the terminal when executing the app.

---

### Post by Fred Le Rouge on 2016-06-30
I cannot launch it:
```

frederic@frederic-W55xEU:~/.steam/steam/steamapps/common/Frozen Synapse$ ./FrozenSynapse 
[S_API FAIL] SteamAPI_Init() failed; no appID found.
Either launch the game from Steam, or put the file steam_appid.txt containing the correct appID in your game folder.
Erreur de segmentation
frederic@frederic-W55xEU:~/.steam/steam/steamapps/common/Frozen Synapse$ 

```

---

### Post by MikeCyber on 2016-06-30
Probably first launch steam in terminal and only paste the last output? Never tried but maybe some useful output.

---

### Post by Fred Le Rouge on 2016-06-30
It is the only thing I have when I launch the game through Steam:
```

frederic@frederic-W55xEU:~$ steam Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
[2016-06-29 10:05:24] Startup - updater built Jun 14 2016 23:23:08
[2016-06-29 10:05:24] Vérification de l'installation...
[2016-06-29 10:05:24] Verification complete
Unable to remove /home/frederic/.steam/CONFIG/SteamAppData.vdf!

Refresh rate: 60
Refresh rate: 60
Refresh rate: 60
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/frederic/.steam/ubuntu12_32/steam-runtime
Refresh rate: 60
Refresh rate: 60
Refresh rate: 60
Refresh rate: 60
Refresh rate: 60
Refresh rate: 60
Refresh rate: 60
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
[2016-06-29 10:06:40] Shutdown
frederic@frederic-W55xEU:~$

```

---

### Post by Fred Le Rouge on 2016-06-30
I thought the problem was more general than that... It was actually related to this game specifically... [http://ubuntuforums.org/showthread.php?t=2158542](http://ubuntuforums.org/showthread.php?t=2158542)
The solution was:
```

sudo ln -s libopenal.so.1 /usr/lib/i386-linux-gnu/libopenal.so

```

---

