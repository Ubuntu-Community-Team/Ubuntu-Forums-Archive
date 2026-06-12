---
title: "VLC Skin Error"
date: 2009-02-28
forum: General Help
---

### Post by SableSlayer on 2009-02-28
The other day, I decided, I wanted to change the skin on VLC. Upon doing so, the skin I selected was very shitty and didn't have the option to switch back to the old one or new others ones. So I deleted the skin hoping it would just prompt for a new skin to load, and it did just that. Except now it wont load any new skins. It errors out every time I try any skin, even the default.

This is the Error it gives me everytime i try and load the new skin
> 
sableslayer@XeN-desktop:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000405] skins2 interface error: cannot find the skins DTD
[00000413] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000413] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000405] skins2 interface error: failed to parse /tmp/vlt27YcpE/askin/theme.xml
[00000405] skins2 interface error: error while parsing /tmp/vlt27YcpE/askin/theme.xml
[00000418] xml xml error: XML parser error (line 1) : Document is empty

[00000405] skins2 interface error: failed to parse /home/sableslayer/Desktop/ASkin.vlt
[00000405] skins2 interface error: cannot load the theme, aborting
[00000409] main generic error: object is not attached
sableslayer@XeN-desktop:~$ 
 

I removed it with 
> sudo apt-get --purge remove vlc

and then reinstalled it. It still prompts for a new skin which, it errors upon loading.

Any help would be greatly appreciated!

---

### Post by mc4man on 2009-02-28
Start vlc from the terminal with this, will reset to an almost fresh install

```
vlc --reset-config
```

---

### Post by SableSlayer on 2009-02-28
It worked perfectly. Thanks your awesome!

---

### Post by mc4man on 2009-03-01
If your looking for different skins try to find ones that say 'for vlc 0.9 or later'
Though you can always recover from a bad choice as you did above

---

### Post by SableSlayer on 2009-03-01
Well I thought it would definably be current since it was from the VLC website.

Im running version 0.9.4 but i think ill just keep the skin i have now, its not all that bad :P

---

### Post by mohamedansari05 on 2009-04-10
I had the same problem
Thanks it worked for me too :)

---

