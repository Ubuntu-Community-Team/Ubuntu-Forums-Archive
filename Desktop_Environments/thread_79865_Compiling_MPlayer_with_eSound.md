---
title: "Compiling MPlayer with eSound"
date: 2005-10-21
forum: Desktop Environments
---

### Post by bored2k on 2005-10-21
```
Enabled optional drivers:
    Input: ftp network tv-v4l2 tv-v4l edl tv matroska mpdvdkit2 vcd dvb
    Codecs: qtx libavcodec real xanim dshow/dmo win32 faad2(internal) libmpeg2 liba52 mp3lib tremor(internal) libmad
    Audio output: oss mpegpes(dvb)
    Video output: xvidix cvidix md5sum pnm png mpegpes(dvb) fbdev xv x11 xover tga
    Audio filters:
  **Disabled optional drivers:**
    Input: vstream tv-bsdbt848 live555 cdda dvdread smb
    Codecs: opendivx x264 xvid libdv amr_wb amr_nb faac musepack libdts libtheora twolame toolame liblzo gif
    Audio output: sgi sun alsa jack polyp **esd** arts dxr2 nas dsound win32 sdl

```Anyone know a way around this? I've been told it needs esound-devel, but Ubuntu does not have this.

---

### Post by hw-tph on 2005-10-21
Try **sudo apt-get install libesd0-dev**.
Also, you know you can create a Debian package from the source using the debian/rules script in the Mplayer source package?

Untar it, cd to the debian/ subdirectory and edit the rules file to your liking. I usually only remove "--enable-runtime-cpudetection" since I don't need it and it seems to have a hit on performance on my machine.

Anyway, cd to the Mplayer directory and run **fakeroot debian/rules binary** to create a deb! You may need to install fakeroot and/or some dependancies (development packages).


H&#229;kan

H&#229;kan

---

