---
title: "ffmpeg: where is mp3 and xvid encoders"
date: 2006-01-16
forum: General Help
---

### Post by kwaanens on 2006-01-16
I can't seem to make avi-files that go with my iAudio X5 60 gig portable player.

How do I fix mp3 and xvid encoding with ffmpeg?

```
$ ffmpeg -formats
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  RoQ             Id RoQ format
 DE ac3             raw ac3
 DE alaw            pcm A law format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dc1394          dc1394 A/V grab
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 D  flic            FLI/FLC animation format
 DE flv             flv format
 DE gif             GIF Animation
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image           image sequence
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 DE imagepipe       piped image sequence
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2 QuickTime/MPEG4 format
  E mp2             MPEG audio layer 2
 D  mp3             MPEG audio
  E mp4             mp4 format
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             nut format
 DE ogg             Ogg Vorbis
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shn
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 DE yuv4mpegpipe    YUV4MPEG pipe format

Image formats (filename extensions, if any, follow):
 DE gif    gif

Codecs:
 D V    4xm
 D V D  8bps
 D V D  aasc
 DEA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_swf
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 DEV D  asv1
 DEV D  asv2
 D V D  camtasia
 D V D  cinepak
 D V D  cljr
 D V D  cyuv
 D A    dts
 DES    dvbsub
 D S    dvdsub
 DEV D  dvvideo
 DEV D  ffv1
 DEVSD  ffvhuff
 D A    flac
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEA    gsm
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 DEA    mp2
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V D  qdraw
 D V D  qpeg
 D V D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 D A    roq_dpcm
 D V D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 D A    shorten
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 D V    theora
 D V D  truemotion1
 D V D  ultimotion
 D V    vc9
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vqavideo
 D A    wmav1
 D A    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
 DEV D  zlib

Supported file protocols:
 file: pipe: udp: rtp: tcp: http:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
Motion estimation methods:
 zero(fastest) full(slowest) log phods epzs(default) x1

Note, the names of encoders and decoders dont always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported for example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats its even
worse
```

I know it should be possible, because a Debian unstable user that tried to help me has it. (With more or less the same version of ffmpeg)

- Ketil

---

### Post by RAOF on 2006-01-23
Hm.  Are you compiling ffmpeg from CVS, or using the Ubuntu package?  If you're using the Ubuntu package, the answer is to compile from CVS.  The Ubuntu package has neither xvid nor mp3 encoding enabled.

To compile from cvs from CVS, I'd suggest that the output of "./configure --help" would be of interest.  Particularly the options
```
  --enable-xvid            enable XviD support via xvidcore [default=no]
  --enable-mp3lame         enable MP3 encoding via libmp3lame [default=no]

```

You'll need to have the xvid & lame libraries installed first, of course.  You can sudo apt-get install liblame-dev libxvidcore-dev

---

### Post by kwaanens on 2006-01-23
No one interested in this?

- Ketil

---

### Post by cvmostert on 2006-10-15
> **kwaanens said:**
> No one interested in this?

- Ketil

I beleive they all use mencoder for xvid and mp3lame

---

### Post by Georges on 2006-11-19
just that I tried to use mencoder to do an xvid/mp3 avi from my photo camera's mjpeg/raw-audi MOV. And the result is horrific A/V desynchronization.
I tried transcode, and besides it's not putting the audio into the video file, after the avimeger I also got again A/S desync.

So now I do mpeg4/mp2 using ffmpeg and sync is ok.

I do not plan to compile ffmpeg. Why do I have to?
Why does transcode and mencoder come with mp3, but not ffmpeg. This is completely illogic. Ubuntu should just put ffmpeg into the same repositories as the other video conversion programs and then there should be no problem to add the codecs. But no, *they* want to show that patents and licenses are bad. Result: frustrated users.

Isn't there a ubuntu-repository delivering a working ffmpeg version? I could not find one.

Georges

---

### Post by RAOF on 2006-11-19
My repository has an all-extras-enabled, recent SVN FFmpeg build.

Also, you don't need XVID enabled to encode to mpeg4 (which is just what XVID is, an mpeg4 encoder).

Edit: It might be important to note that my repository pretty much only contains AMD64 builds :)

---

### Post by ILIJA on 2006-11-19
My repository has an all-extras-enabled, recent SVN FFmpeg build too

---

### Post by geofffox on 2006-12-04
I am looking for an FFMPEG package with mp3 enabled for my Pentium 4 machine (32 bit).  Ilija, I can't find any Ubuntu packages on your site.  The other site mentioned in a previous response is 64 bit only.

I have tried three times tonight (following instructions on other sites) to compile this myself.  No luck!  So, any help will be appreciated.

Geoff

---

