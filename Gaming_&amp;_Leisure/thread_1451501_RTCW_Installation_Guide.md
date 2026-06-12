---
title: "RTCW Installation Guide"
date: 2010-04-10
forum: Gaming &amp; Leisure
---

### Post by quadomatic on 2010-04-10
**Update:** Sound fixed

I figured I'd post this here in case there was anyone else going through old games they have which are capable of native linux installation, but are so old they have problems getting libraries to work.

Things you'll need:

1. Legit copy of RTCW
2. WINE
3. Latest RTCW Installer, get it from id's ftp here: [ftp://ftp.idsoftware.com/idstuff/wolf/linux/wolf-linux-1.41b.x86.run](ftp://ftp.idsoftware.com/idstuff/wolf/linux/wolf-linux-1.41b.x86.run)
4. libstdc++2.10-glibc2.2_2.95.4-27, get it here: [http://ftp.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb)
5. et-sdl-sound, get it here: [http://nullkey.ath.cx/et-sdl-sound/et-sdl-sound.tar.gz](http://nullkey.ath.cx/et-sdl-sound/et-sdl-sound.tar.gz)

Run the linux installer, and let it install to whichever directory you wish.

Launch the Windows installer in WINE, let it install, then copy all the .pk3 files from the Windows installation folder to the "main" folder where the linux installer installed RTCW to. Don't overwrite any files when copying.

Here's the tricky part: RTCW's binaries need libraries which haven't been available since dapper. On 32-bit installations, I imagine one could simply install the deb downloaded above, but I DON'T KNOW for sure since I use 64-bit.

For 64-bit users:

Put the deb in a folder by itself. cd to that folder and run:

```

dpkg -x libstdc++2.10-glibc2.2_2.95.4-27_i386.deb .
cd usr/lib
sudo cp * /usr/lib32

```

Now, when you run the RTCW binaries, it should work!

Fixing sound: RTCW uses OSS by default, but you'll probably need ALSA. Extract the et-sdl-sound.tar.gz file and copy the extracted et-sdl-sound.so to the RTCW root directory. Then, copy and past the following into a empty document file at the root of the RTCW directory:

```

export ETSDL_SDL_LIB="libSDL-1.2.so"
export SDL_AUDIODRIVER="alsa"
LD_PRELOAD="${LD_PRELOAD}:/home/aneesh/Games/rtcw/et-sdl-sound.so" ./wolfsp.x86 $*

```

To make an executable for multiplayer, simply change ./wolfsp.x86 to ./wolf.x86

Run chmod +x against this newly created script, and run it. You should now have a fully functioning Return to Castle Wolfenstein running natively!

---

