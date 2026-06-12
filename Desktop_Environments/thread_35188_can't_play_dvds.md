---
title: "can't play dvds"
date: 2005-05-18
forum: Desktop Environments
---

### Post by tom_d on 2005-05-18
I can't get dvds to play, I tried totem,gxine,and mplayer. Using Totem the error message states Totem can not play dvd //.  Using gxine xine engine failed to start no demuxer found ,and Mplayer doesn't try to  open. I have downloaded all the codecs,libs. that I know to download.  WHAT IS A DEMUXER and where do I get one.        thanks in advance   tom_d

---

### Post by defkewl on 2005-05-18
Download libdvdcss2.deb first :)

---

### Post by jeremy on 2005-05-18
or apt-get it from the Marillat repos.

---

### Post by tom_d on 2005-05-18
I installed libdvdcss 2 , win32codecs. before I downloaded gxine , and mplayer .  thanks

---

### Post by SNo0py on 2005-05-18
[QUOTE=tom_d]I installed libdvdcss 2 , win32codecs. before I downloaded gxine , and mplayer .  thanks[/QUOTE]

And does it work now or is it still broken?

---

### Post by tom_d on 2005-05-18
no it still doesn't play, not sure why it doesn't.   using other Linux distros I can play dvds with xine, mplayer without any problems.

---

### Post by SNo0py on 2005-05-19
[QUOTE=tom_d]no it still doesn't play, not sure why it doesn't.   using other Linux distros I can play dvds with xine, mplayer without any problems.[/QUOTE]
Yeah, I'm sorry to say, but I have the same issue with Ubuntu - great Distro, but why the he** can't I play my DVD's or videos using ogle or mplayer? Even with the same settings as in Gentoo? No difference, same system, same DVD, same file? Why?

---

### Post by @jens on 2005-05-19
[QUOTE=tom_d]no it still doesn't play, not sure why it doesn't.   using other Linux distros I can play dvds with xine, mplayer without any problems.[/QUOTE]

Correct device? Open xine->become "master of the universe"->look at audio and video. /dev/cdrom or dev/cdrom1 should match your drives. Look at /etc/fstab.
hth
Regards,
@Jens (just watching "The Pianist" in Ubuntu...)

NB: make sure that all ATAPI drives use dma:
E.G.:
# hdparm -d1 /dev/hdx (x= your cdrom device, i.e: hdc when master on the 2. IDE, hdd, when slave on the 2. IDE)

---

### Post by tikal26 on 2005-05-19
I don't know if you are willing to try kaffeine, but it has work so far for me I have being able to play my DVD's wit no problem. I also read in the how to's  instructions on how to make mplayer work for all of us who had not make it work you need to dowload the add on cd. go look for it that solve my mplayer problems, but before that I used kaffeine

---

### Post by tom_d on 2005-05-20
Thanks everyone, I finally have it playing DVDs using gxine. I didn't  get it until I read @jen.  I opened gxine , to file, then I checked dvd and it worked.  thanks again @jen   tom_d :grin:

---

### Post by bruizer on 2005-05-20
@jens post worked for me to get DVD playing in Totem, however, I still find it very choppy. XINE works like a champ again! Thanks @jens and everyone else!

---

### Post by SNo0py on 2005-05-31
Aaarg... ogle is driving me crazy:

> WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshot'
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshotWithSPU'
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Couldn't find device name.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Couldn't find device name.
No accelerated IMDCT transform found

Any ideas?

---

### Post by weeroona on 2005-05-31
This is my output from ogle:
> 
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshot'
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshotWithSPU'
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Using libdvdcss version 1.2.8 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000129
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000283fc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00029ffd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002105b9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002114a5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00211b33
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
No accelerated IMDCT transform found
SNDCTL_DSP_GETCHANNELMASK: Invalid argument
##!-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+WARNING[ogle_mpeg_ps]: dvdreadblocks only got 7, wanted 87
FATAL[ogle_mpeg_ps]: dvdreadblocks failed
ctrl: ipc_rmid: Invalid argument


xine, totem, and ogle all play the 9sec. MGM-dvd sequence before they show an error dialog box or die.

---

### Post by weeroona on 2005-06-01
Last night, I ended up installing VLC. That gave me an error message that when I googled it, a bboard post said that the error related to the region code on dvd players. the dvd checks for multiple regions codes and if more than one exist, it won't allow playback. The work around suggested is to start at title 1, chapter 1 rather than 0,0. This worked in VLC. I then ejected that dvd and inserted the one I wanted to watch and Ubuntu autoplayed it with Totem successfully. This doesn't make complete sense to me. I think I must have been figeting unmethodically with enough stuff that I fixed the problem before I tested to see if it was working.

---

### Post by sprucio on 2006-04-01
I'm having the same problem with the dvdreadblocks error. Has anyone had any success?

---

### Post by aresgoddess on 2006-04-06
[QUOTE=defkewl]Download libdvdcss2.deb first :)[/QUOTE]

ok, so i did that, and i don't know if it was the package (used synaptic), my comp, Totem or a combo, but I was able to play a Region Two dvd on Totem when my comp has only played Region One dvds before...You don't know how happy I am that you posted this. :KS \\:D/ [-o< =D> 8-) Thank you so much!!!

---

