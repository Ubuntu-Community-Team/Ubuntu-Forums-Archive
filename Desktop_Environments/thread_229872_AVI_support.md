---
title: "AVI support"
date: 2006-08-05
forum: Desktop Environments
---

### Post by PokerFacePenguin on 2006-08-05
I have somehow managed to break my AVI support.  I redownloaded the w32codec package and dpkg'd it again.  I can play .wmv, but no avi files.  Although I have used it before, I am not too into installing automatix or similiar just to get this going.  There is no telling what else that might break.  I had it working fine and then I upgraded to dapper.....somewhere along the way it got hosed.  

Anybody got a suggestion as to why the w32codec package plays .wmv and not AVI?  my /usr/lib/codecs has these files:
> -rw-r--r-- 1 root root   61952 2001-04-10 15:39 acelpdec.ax
-rw-r--r-- 1 root root   38912 2002-01-06 18:00 alf2cd.acm
-rw-r--r-- 1 root root  118784 2004-03-24 01:21 aslcodec_dshow.dll
-rw-r--r-- 1 root root   77824 2004-03-24 01:21 aslcodec_vfw.dll
-rw-r--r-- 1 root root   88064 2001-01-21 19:49 asusasv2.dll
-rw-r--r-- 1 root root   35840 1999-09-09 13:12 asusasvd.dll
-rw-r--r-- 1 root root  150016 2000-08-02 01:28 ativcr2.dll
-rw-r--r-- 1 root root   95292 2001-02-14 18:00 atrac3.acm
-rw-r--r-- 1 root root   62808 2006-07-23 06:56 atrc.so.6.0
-rw-r--r-- 1 root root   92160 2004-07-04 12:19 AvidQTAVUICodec.qtx
-rw-r--r-- 1 root root   69632 2001-05-03 09:30 avimszh.dll
-rw-r--r-- 1 root root  114688 2001-05-03 09:30 avizlib.dll
-rw-r--r-- 1 root root   76800 2001-04-18 05:54 BeHereiVideo.qtx
-rw-r--r-- 1 root root  312832 2002-04-20 19:58 CLRVIDDC.DLL
-rw-r--r-- 1 root root  135168 2002-04-20 19:52 clrviddd.dll
-rw-r--r-- 1 root root   41724 2006-07-23 06:56 cook.so
-rw-r--r-- 1 root root   74548 2006-07-23 06:56 cook.so.6.0
-rw-r--r-- 1 root root   11776 2003-09-09 00:18 ctadp32.acm
-rw-r--r-- 1 root root   81920 2002-04-21 05:22 CtWbJpg.DLL
-rw-r--r-- 1 root root   62956 2006-07-23 06:56 ddnt.so.6.0
-rw-r--r-- 1 root root   88464 1996-08-14 06:41 DECVW_32.DLL
-rw-r--r-- 1 root root  287744 2000-12-29 14:58 divxa32.acm
-rw-r--r-- 1 root root  239616 2000-12-21 16:34 divx_c32.ax
-rw-r--r-- 1 root root  412160 2001-01-24 04:28 divxc32.dll
-rw-r--r-- 1 root root  434176 2001-08-28 16:36 divxdec.ax
-rw-r--r-- 1 root root  520192 2001-08-28 16:26 divx.dll
-rw-r--r-- 1 root root   56492 2006-07-23 06:56 dnet.so.6.0
-rw-r--r-- 1 root root  200080 2006-07-23 06:56 drv2.so.6.0
-rw-r--r-- 1 root root  299560 2006-07-23 06:56 drv3.so.6.0
-rw-r--r-- 1 root root  335164 2006-07-23 06:56 drv4.so.6.0
-rw-r--r-- 1 root root  318400 2006-07-23 06:56 drvc.so
-rw-r--r-- 1 root root   66372 2006-07-23 06:56 dspr.so.6.0
-rw-r--r-- 1 root root   33280 2000-08-23 20:00 huffyuv.dll
-rw-r--r-- 1 root root  391680 2000-08-01 16:41 i263_32.drv
-rw-r--r-- 1 root root  199680 2004-06-02 12:37 iac25_32.ax
-rw-r--r-- 1 root root  110592 2000-03-09 14:15 iccvid.dll
-rw-r--r-- 1 root root  307200 2001-05-03 09:29 icmw_32.dll
-rw-r--r-- 1 root root   19456 2001-03-29 19:16 imaadp32.acm
-rw-r--r-- 1 root root   98304 2000-12-17 19:32 imc32.acm
-rw-r--r-- 1 root root  199168 2000-07-13 23:52 ir32_32.dll
-rw-r--r-- 1 root root  739328 1997-07-07 05:32 ir41_32.dll
-rw-r--r-- 1 root root  755200 2000-03-09 14:17 ir50_32.dll
-rw-r--r-- 1 root root  225280 2001-11-03 18:40 ivvideo.dll
-rw-r--r-- 1 root root   90112 2002-11-30 17:55 jp2avi.dll
-rw-r--r-- 1 root root  300544 2000-12-21 16:40 l3codeca.acm
-rw-r--r-- 1 root root   83456 2001-01-02 19:44 l3codecx.ax
-rw-r--r-- 1 root root  245760 2004-03-22 18:57 LCMW2.dll
-rw-r--r-- 1 root root  338432 2002-04-21 14:13 LCodcCMP.dll
-rw-r--r-- 1 root root   81920 2004-03-22 18:57 LCODCCMW2E.dll
-rw-r--r-- 1 root root   33040 2002-04-21 05:09 lhacm.acm
-rw-r--r-- 1 root root  204800 2004-11-14 16:02 lsvxdec.dll
-rw-r--r-- 1 root root  422912 2002-11-12 03:53 m3jp2k32.dll
-rw-r--r-- 1 root root  264704 2001-09-03 07:08 m3jpeg32.dll
-rw-r--r-- 1 root root   53760 2001-05-09 21:51 m3jpegdec.ax
-rw-r--r-- 1 root root  263680 2001-10-11 06:34 mcdvd_32.dll
-rw-r--r-- 1 root root   98304 2001-04-01 23:57 mcmjpg32.dll
-rw-r--r-- 1 root root   57344 2004-02-14 15:10 mi-sc4.acm
-rw-r--r-- 1 root root  254272 1999-06-26 09:31 mpg4c32.dll
-rw-r--r-- 1 root root  262416 2001-05-10 18:04 mpg4ds32.ax
-rw-r--r-- 1 root root   17920 2000-07-30 00:36 msadp32.acm
-rw-r--r-- 1 root root   10752 1999-05-05 17:22 msg711.acm
-rw-r--r-- 1 root root   25088 1999-05-05 17:22 msgsm32.acm
-rw-r--r-- 1 root root  167696 2001-06-26 11:53 msh261.drv
-rw-r--r-- 1 root root  424960 1999-04-15 14:10 msms001.vwp
-rw-r--r-- 1 root root   79872 2001-10-11 09:10 msnaudio.acm
-rw-r--r-- 1 root root   28672 1999-05-05 16:22 msrle32.dll
-rw-r--r-- 1 root root   76112 2001-12-07 08:27 msscds32.ax
-rw-r--r-- 1 root root   30208 2001-03-23 13:30 msvidc32.dll
-rw-r--r-- 1 root root  218624 1999-04-15 14:10 mvoiced.vwp
-rw-r--r-- 1 root root   49664 2002-04-20 21:30 nsrt2432.acm
-rw-r--r-- 1 root root   45056 2001-11-16 14:10 pclepim1.dll
-rw-r--r-- 1 root root  225552 2001-01-29 03:08 qdv.dll
-rw-r--r-- 1 root root   34304 1996-12-15 18:00 qpeg32.dll
-rw-r--r-- 1 root root  225280 2002-11-08 14:04 qtmlClient.dll
-rw-r--r-- 1 root root  563200 2003-05-27 06:42 QuickTimeEssentials.qtx
-rw-r--r-- 1 root root  904704 2003-05-27 06:42 QuickTimeInternetExtras.qtx
-rw-r--r-- 1 root root 4544512 2003-05-27 06:42 QuickTime.qts
-rw-r--r-- 1 root root  299008 2002-04-20 21:32 rt32dcmp.dll
-rw-r--r-- 1 root root   13239 2003-12-03 16:29 scg726.acm
-rw-r--r-- 1 root root   60772 2006-07-23 06:56 sipr.so.6.0
-rw-r--r-- 1 root root  131072 2002-09-09 14:01 sp5x_32.dll
-rw-r--r-- 1 root root  175616 2002-04-23 09:51 tm20dec.ax
-rw-r--r-- 1 root root   21256 2006-07-23 06:56 tokf.so.6.0
-rw-r--r-- 1 root root   57552 2006-07-23 06:56 tokr.so.6.0
-rw-r--r-- 1 root root  110592 2002-04-21 08:38 tsccvid.dll
-rw-r--r-- 1 root root   16144 2002-04-05 17:00 tsd32.dll
-rw-r--r-- 1 root root    9488 2002-04-20 20:55 tssoft32.acm
-rw-r--r-- 1 root root  573440 2004-12-19 11:51 tvqdec.dll
-rw-r--r-- 1 root root  241664 2001-07-03 10:01 ubv263d+.ax
-rw-r--r-- 1 root root  118784 2002-04-21 11:35 ubvmp4d.dll
-rw-r--r-- 1 root root   28672 2003-10-29 10:40 ultimo.dll
-rw-r--r-- 1 root root   76800 1996-11-12 04:12 VDODEC32.dll
-rw-r--r-- 1 root root   82432 2003-08-18 12:52 vdowave.drv
-rw-r--r-- 1 root root   76800 2002-03-12 08:22 vgpix32d.dll
-rwxr-xr-x 1 root root  316500 2006-07-23 06:56 vid_3ivX.xa
-rwxr-xr-x 1 root root    6444 2006-07-23 06:56 vid_cvid.xa
-rwxr-xr-x 1 root root    3056 2006-07-23 06:56 vid_cyuv.xa
-rwxr-xr-x 1 root root   71220 2006-07-23 06:56 vid_h261.xa
-rwxr-xr-x 1 root root  112288 2006-07-23 06:56 vid_h263.xa
-rwxr-xr-x 1 root root  107572 2006-07-23 06:56 vid_iv32.xa
-rwxr-xr-x 1 root root  187252 2006-07-23 06:56 vid_iv41.xa
-rwxr-xr-x 1 root root   86944 2006-07-23 06:56 vid_iv50.xa
-rw-r--r-- 1 root root  211968 2003-03-28 10:03 ViVD2.dll
-rw-r--r-- 1 root root  122880 2001-05-03 09:34 vivog723.acm
-rw-r--r-- 1 root root  155648 2005-04-10 12:06 vmnc.dll
-rw-r--r-- 1 root root   56320 1999-04-15 10:10 voxmsdec.ax
-rw-r--r-- 1 root root  462848 2001-09-22 09:17 vp31vfw.dll
-rw-r--r-- 1 root root  466944 2004-04-27 18:39 vp4vfw.dll
-rw-r--r-- 1 root root  372736 2004-04-27 18:40 vp5vfw.dll
-rw-r--r-- 1 root root  438272 2004-02-12 03:39 vp6vfw.dll
-rw-r--r-- 1 root root  626688 2006-05-11 14:21 vp7vfw.dll
-rw-r--r-- 1 root root   49152 2003-04-09 18:49 vssh264core.dll
-rw-r--r-- 1 root root  421888 2003-04-09 18:49 vssh264dec.dll
-rw-r--r-- 1 root root   98304 2003-04-09 18:49 vssh264.dll
-rw-r--r-- 1 root root  454656 2005-05-03 10:23 vsshdsd.dll
-rw-r--r-- 1 root root  706696 2003-04-09 18:48 vsslight.dll
-rw-r--r-- 1 root root  167936 2003-04-09 18:48 vsswlt.dll
-rw-r--r-- 1 root root  409720 2002-10-29 11:03 wma9dmod.dll
-rw-r--r-- 1 root root  410216 2002-10-28 09:11 wmadmod.dll
-rw-r--r-- 1 root root  773368 2004-08-10 19:44 wmsdmod.dll
-rw-r--r-- 1 root root  486504 2004-04-27 18:43 wmspdmod.dll
-rw-r--r-- 1 root root  278800 2001-05-01 03:46 wmv8ds32.ax
-rw-r--r-- 1 root root  807032 2002-11-20 16:03 wmv9dmod.dll
-rw-r--r-- 1 root root 1181944 2004-10-18 03:33 wmvadvd.dll
-rw-r--r-- 1 root root  807528 2002-10-28 09:12 wmvdmod.dll
-rw-r--r-- 1 root root  262416 2001-04-01 23:30 wmvds32.ax
-rw-r--r-- 1 root root  126464 2004-07-02 18:36 wnvplay1.dll
-rw-r--r-- 1 root root   93184 2004-07-02 18:36 wnvwinx.dll
-rw-r--r-- 1 root root 1184984 2006-05-20 11:16 wvc1dmod.dll
-rw-r--r-- 1 root root   81920 2006-04-24 20:17 zmbv.dll


---

### Post by benfindlay on 2006-08-24
Don't know much technical about your problem, but I do know that a media player like video lan controller (vlc) comes with all its own codecs built in, and is free. Its very basic, easy to use but also VERY functional. So if you're not particular about which specific prog you use to play video files, I'd recommend giving it a go!

---

### Post by z_pod on 2006-08-24
check if this entry is in /usr/lib:
lrwxrwxrwx  1 root  root         6 2006-04-24 16:37 win32 -> codecs

---

### Post by masnevets on 2006-08-24
Are you using totem? If so, are you using gstreamer or xine for your codecs?

---

