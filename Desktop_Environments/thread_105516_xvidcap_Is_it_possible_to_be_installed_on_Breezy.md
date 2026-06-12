---
title: "xvidcap: Is it possible to be installed on Breezy ?"
date: 2005-12-18
forum: Desktop Environments
---

### Post by kurtkraut on 2005-12-18
Hi,

I intend to do some video tutorials with audio. Xvidcap is the onliest tool that I found that allow an audio narration of the screen capture.

I've downloaded xvidcap using these sources to download xvidcap [1] and  libavcodec1 [2]:

deb [http://www.jarre-de-the.net/computing/debian/](http://www.jarre-de-the.net/computing/debian/) stable main **[1]**
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main **[2]**

The program is installed and can be runned with no errors prompted. But when I click on the RECORD button, the program closes immediatly.

Any suggestions ? I really need a screen capture tool with audio and none of previous posts about xvidcap contains a way of installing it on Breezy. Istanbul doesn't fit for me because it messes audio.


Thanks in advance

---

### Post by ranf on 2005-12-18
It doesn't look like there is much happening with the development of xvidcap.

I just tried `istanbul' which does at least screen capture movies. No audio as it looks.

---

### Post by jannol on 2006-01-04
you start xvidcap instead, gvidcap does not work atm.

to record audio you need to change a few lines in ~/.xvidcap.scf

find and edit >

file: frm-%04d.mpeg

codec: MPEG4

audio: 1

audio_in: /dev/audio

or whatever your sound wrapper is

audio_rate: 44100

does not work with other than 22050 or 44100, at least for me

audio_bits: 64000

or whatever quality you want

audio_channels: 2

I haven't tested mic but with ex

cat "some mp3" | xvidcap --audio_in -

I can include music to the recording

---

### Post by patrick295767 on 2006-06-15
[QUOTE=kurtkraut]Hi,

I intend to do some video tutorials with audio. Xvidcap is the onliest tool that I found that allow an audio narration of the screen capture.

I've downloaded xvidcap using these sources to download xvidcap [1] and  libavcodec1 [2]:

deb [http://www.jarre-de-the.net/computing/debian/](http://www.jarre-de-the.net/computing/debian/) stable main **[1]**
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main **[2]**

The program is installed and can be runned with no errors prompted. But when I click on the RECORD button, the program closes immediatly.

Any suggestions ? I really need a screen capture tool with audio and none of previous posts about xvidcap contains a way of installing it on Breezy. Istanbul doesn't fit for me because it messes audio.


Thanks in advance[/QUOTE]
  
my best advice: to get my debs
Look into my multimedia.sh signature 
there is the automatic installation of xvidcap (via script) = 100% working ! :-)
and new linux users aimt
  

otherwise, the installation is written there:
[http://patrick295767.sitesled.com/data/how_to_record_your_x11_screen.htm](http://patrick295767.sitesled.com/data/how_to_record_your_x11_screen.htm)
(to record screen, look into multimedia.sh)  

Greetz

Cheers

---

