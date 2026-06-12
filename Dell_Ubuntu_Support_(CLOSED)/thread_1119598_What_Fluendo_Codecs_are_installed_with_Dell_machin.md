---
title: "What Fluendo Codecs are installed with Dell machines"
date: 2009-04-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by notbitmonk on 2009-04-08
I bought a Dell Inspiron 530 from Dell last week.  Service was lighting fast since I placed the order Tuesday and Thursday I received the computer.  It boots in less than 30 seconds and works flawlessly.  When I went to try multimedia, DVD playback was great with nice sound and no stuttering using LinDVD from Corel.  Windows Media files were good too with nice playback.  I tried to play a downloaded Quicktime movie encoded with H.264 and that's were things went wrong.  After asking Dell and Fluendo (Fluendo was the one to answer because Dell said that they do not provide support to Ubuntu even though the packages were bought by Dell and installed by Dell and I was not asking for support just merely what codecs Dell had bought) here is the answer from Fluendo:
[INDENT]The codecs included in this Dell offer are :
[LIST]
[*]WMV decoder
[*]WMA decoder
[*]ASF demuxer
[*]MP3 decoder
[/LIST]
So the only files that will be decoded are Windows Media files that you downloaded on your hard drive (no streaming support like MMS) and MP3 tracks.
If you really want complete codec support you would need to buy the Complete codec pack from [http://www.fluendo.com](http://www.fluendo.com)
[/INDENT]
Whoever buys a Dell computer and can not watch H.264 or the other formats now knows that there is no problem with the computer, they just need to buy the additional codecs from Fluendo.  I havn't bought the other codecs yet (have to buy the Complete Bundle though) but I have to say that the codecs above are good.  Besides, those codecs are the only legal way to play those formats in the US and its territories.  This post is merely informative as it took me a while to find out what was happening with the codecs in my computer.

---

### Post by superm1 on 2009-04-08
> **notbitmonk said:**
> I bought a Dell Inspiron 530 from Dell last week.  Service was lighting fast since I placed the order Tuesday and Thursday I received the computer.  It boots in less than 30 seconds and works flawlessly.  When I went to try multimedia, DVD playback was great with nice sound and no stuttering using LinDVD from Corel.  Windows Media files were good too with nice playback.  I tried to play a downloaded Quicktime movie encoded with H.264 and that's were things went wrong.  After asking Dell and Fluendo (Fluendo was the one to answer because Dell said that they do not provide support to Ubuntu even though the packages were bought by Dell and installed by Dell and I was not asking for support just merely what codecs Dell had bought) here is the answer from Fluendo:[INDENT]The codecs included in this Dell offer are :
[LIST]
[*]WMV decoder
[*]WMA decoder
[*]ASF demuxer
[*]MP3 decoder
[/LIST]
So the only files that will be decoded are Windows Media files that you downloaded on your hard drive (no streaming support like MMS) and MP3 tracks.
If you really want complete codec support you would need to buy the Complete codec pack from [http://www.fluendo.com](http://www.fluendo.com)
[/INDENT]Whoever buys a Dell computer and can not watch H.264 or the other formats now knows that there is no problem with the computer, they just need to buy the additional codecs from Fluendo.  I havn't bought the other codecs yet (have to buy the Complete Bundle though) but I have to say that the codecs above are good.  Besides, those codecs are the only legal way to play those formats in the US and its territories.  This post is merely informative as it took me a while to find out what was happening with the codecs in my computer.
Hi!
Thanks for the informative post.  I'd like to add a few comments.  The codec pack that ships with the mini 9 & 12 is not necessarily identical to the pack with the 530, XPS1330, Studio 15 etc.  There may actually be more codecs available in that pack. (They are billed differently, so I figured I'd mention this)

---

### Post by notbitmonk on 2009-04-09
If there are different codecs shipped with the various model provided by Dell, this might be a good place to post what codecs are included with each model.  The codecs package in my Inspiron (my daughter's actually) 530n as checked through Synaptic is:
[INDENT]**gstreamer0.10-fluendo-plugins-offline version 0.10.6-1**[/INDENT]
I went to Synaptic and did a search for Fluendo, there was just one package installed.
The full Fluendo package contains the following codecs:
[LIST]
[*]Windows Media Audio Decoder (Windows Media 7, 8, 9, 10, Pro, Lossless and Speech)
[*]Windows Media Video Decoder (Windows Media 7, 8, 9 and VC1)
[*]Windows Media ASF Demuxer
[*]Windows Media MMS Networking
[*]MPEG2 Video Decoder
[*]MPEG4 Part 2 Video Decoder
[*]DivX 3.11 Alpha ;-) Video Decoder
[*]H.264/AVC Video Decoder
[*]MPEG2 Program Stream and Transport Stream demuxer
[*]MPEG4 ISO Demuxer
[*]MP3 Audio Decoder
[*]AAC Audio Decoder
[*]LPCM Audio Decoder
[/LIST]
The price (2009-04-09) is €28.00 which is equivalent to $37.14 ([http://finance.yahoo.com/currency-converter](http://finance.yahoo.com/currency-converter)).  I know that is very tempting to download the ugly plugins and not pay but I urge you to PAY.  This is a good set and this company is dedicated to Linux.  We can not let it go the same way that Loki and other companies went.  Also, Ubuntu sells PowerDVD for Linux in their web page for $50 ([http://shop.canonical.com/index.php?cPath=19&currency=USD](http://shop.canonical.com/index.php?cPath=19&currency=USD)).

---

