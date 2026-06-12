---
title: "Bus Error showing up a lot"
date: 2009-05-04
forum: General Help
---

### Post by lemcoe9 on 2009-05-04
So this has been REALLY frustrating. There are a bunch of applications that are not starting, and when I try to start them via command line, I get "Bus Error". No more, no less. This happens with the repo versions of VLC and Amarok. I have gotten the same error with other applications, but I can not remember them off hand.

I think this may be a problem with Xubuntu in itself, but I'm not sure.

Can anyone offer some help?

Thanks in advance,

David

---

### Post by lemcoe9 on 2009-05-04
Please can someone help? I NEED to have Amarok and VLC.

---

### Post by emyr42 on 2009-08-13
New install of U9.04 Jaunty, all updates.
VLC installed from repositories.
I'm using the FGLRX driver for my ATI HD3870.

```
emyr@emyr-desktop:~$ vlc
VLC media player 0.9.9a Grishenko
[[COLOR=DarkGreen]00000001[/COLOR]] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[[COLOR=DarkGreen]00000001[/COLOR]] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[[COLOR=DarkGreen]00000001[/COLOR]] main libvlc debug: translation test: code is "en_GB"
Bus error
emyr@emyr-desktop:~$ 

```

---

### Post by emyr42 on 2009-08-13
Also happens with rhythmbox, when trying to open the preferences menuitem.

---

### Post by Pablo_F on 2011-04-02
I am bumping this old thread because I have had this issue with xubuntu 10.10 in an Acer Aspire One netbook. 

This might have to do with pulseaudio and this bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/470073](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/470073)

So, if you encounter this problem, check:

ls -la /dev/shm

If there are several pulse-shm-xxxxxx, you need to:

rm -f /dev/shm/pulse-shm*

and the bus error problem is gone, hopefully. 

I use the scripts around jackd in qjackctl to automate disabling pulseaudio and clean /dev/shm before starting the jack server. There could be other solutions aswell.

Cheers, Pablo

---

