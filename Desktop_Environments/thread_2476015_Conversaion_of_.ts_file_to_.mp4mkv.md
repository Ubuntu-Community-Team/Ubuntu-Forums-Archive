---
title: "Conversaion of .ts file to .mp4/mkv"
date: 2022-06-14
forum: Desktop Environments
---

### Post by johnaaronrose on 2022-06-14
On Ubuntu 20.04, I've tried "ffmpeg  -i input.ts -c:v libx264 -c:a aac output.mp4 " & "ffmpeg -i input  -c:v copy -c:a aac output.mkv". Both give "input.ts: could not find  codec parameters". I've tried vlc but it creates a 161 byte output.mp4  and does nothing more. The input.ts file shows N/A for Video & Audio  codecs. Attached is o/p from Terminal:
[ATTACH]290604[/ATTACH]

---

### Post by deadflowr on 2022-06-14
Probably has to do with this: [https://trac.ffmpeg.org/wiki/Encode/AAC#:~:text=FFmpeg%20supports%20two%20AAC%2DLC,licensed%20code%20is%20also%20included.]("https://trac.ffmpeg.org/wiki/Encode/AAC#:~:text=FFmpeg%20supports%20two%20AAC%2DLC,licensed%20code%20is%20also%20included.")

---

### Post by TheFu on 2022-06-14
> **johnaaronrose said:**
> On Ubuntu 20.04, I've tried "ffmpeg  -i input.ts -c:v libx264 -c:a aac output.mp4 " & "ffmpeg -i input  -c:v copy -c:a aac output.mkv". Both give "input.ts: could not find  codec parameters". I've tried vlc but it creates a 161 byte output.mp4  and does nothing more. The input.ts file shows N/A for Video & Audio  codecs. Attached is o/p from Terminal:
[ATTACH]290604[/ATTACH]

For 720p conversions, with 
ffmpeg version 4.4.2-0ubuntu1~18.04.sav1.3
I use:
```

MAP="-map 0"
QUAL="19"
PRESET="-preset superfast -strict experimental"
AUDIO="-c:a libvorbis -q:a 6 -qscale:a 6"
FF_OPTS="$MAP -vcodec libx264 -crf $QUAL -vf scale=-1:720 $PRESET $AUDIO"
nice ffmpeg -y -i "$IN" $FF_OPTS  "$OUT"

```

The $IN and $OUT are set in other parts of the script.
This is for quick conversion and not for archival storage.

To have AAC as the audio codec (yuck!), use 
AUDIO="-c:a aac"

I typically move the .ts into an .mkv container first, just to handle the lack of correct length times that .ts has here.
superfast is the preset that doesn't use tooo much storage and runs fast enough. use **medium** if you are willing to trade CPU/time for smaller.  Other presets are:
    ultrafast
    superfast
    veryfast
    faster
    fast
    medium – default preset
    slow
    slower
    veryslow

Some poorly create TS files cannot be handled by ffmpeg.  I used to run into that more, before I started shoving the files into .mkv containers first.

---

### Post by johnaaronrose on 2022-06-15
@TheFu I just tried "ffmpeg -i input.ts output.mkv" to convert to mkv but still get "input.ts: could not find codec parameters.
I don't care much about the quality; I just want to be able to play the video on my "dumb" tv from a USB stick / SSD.
I'm doing this because my Humax PVR went kaput and I want to retrieve some recordings from it: I've copied the.ts files from it to my PC's SSD after taking the HD out of the Humax and reading it on my PC using a suitable Drive Enclosure.
PS in Nautilus Properties->Audio/Video both Audio & Video Codecs are shown as N/A.

---

### Post by ajgreeny on 2022-06-15
@johnaaronrose.
It might be interesting to see what **mediainfo** tells us about the codecs used in your errant .ts files though if nautilus can't figure it out maybe mediainfo will also have problems.

---

### Post by johnaaronrose on 2022-06-15
mediainfo shows:
john@desktop:~$ mediainfo input.ts
General
Complete name                            : input.ts
Format                                   : BDAV
Format/Info                              : Blu-ray Video
Format profile                           : No PAT/PMT
File size                                : 2.82 GiB
FileExtension_Invalid                    : m2ts mts ssif

---

### Post by TheFu on 2022-06-15
Bluray is often encrypted.

I decided years ago that I'd never use bluray nor allow it in my house.  It is *broken by design.*
I used to use a TiVo. It recorded media into .TS containers. They were encrypted.  When pulling recorded shows off the TiVo, we had to use some TiVo software to remove that encryption.  Could the Humax be similar?  

[https://groups.google.com/g/uk.tech.digital-tv/c/1tHU-9wpdRA](https://groups.google.com/g/uk.tech.digital-tv/c/1tHU-9wpdRA) says some files are encrypted in a specific Humax PVR.

---

### Post by pantazi on 2022-06-15
If your Humax is an HDR FOX T2 then HD video is encrypted. Lots of info on this at Hummy.tv forum.

---

### Post by johnaaronrose on 2022-06-16
Humax is HDR-2000T. I've posted on hummy.tv an appropriate question [https://hummy.tv/forum/threads/how-to-copy-from-hard-disk-in-hdr-2000t-to-an-mp4-file-on-my-pc.10644/](https://hummy.tv/forum/threads/how-to-copy-from-hard-disk-in-hdr-2000t-to-an-mp4-file-on-my-pc.10644/)

---

### Post by johnaaronrose on 2022-06-16
@TheFu I looked at the above web site but it didn't help. I've just found another web site [https://www.howtogeek.com/240487/how-to-play-dvds-and-blu-rays-on-linux/](https://www.howtogeek.com/240487/how-to-play-dvds-and-blu-rays-on-linux/) which shows how to 'deencrypt' blue ray disks. However, it didn't help with .ts files as vlc just did nothing with them. It may only work if one has a blue ray disk which I don't have. So I would need s/w to create a blue ray disk!

---

### Post by johnaaronrose on 2022-06-16
Humax experts on hummer.tv say that the box itself does the encryption, probably using Mac Address & Serial Number (which I do have) but they don't know how though they've worked out how to de-encrypt for Humax Fox boxes. So it looks like end of road for me on this topic.

---

### Post by TheFu on 2022-06-16
I read somewhere that if the DVR has a USB port on the front, that copying the files through that method would remove the encryption.  

Test that with NTFS and/or FAT32 just to see if it actually works.  

Long term, if this is your intent, you'll want to use an externally powered USB external storage drive. External drives that spin that don't have external power are usually 80% slower than those with power. On a spinning HDD, NTFS would likely be the best choice to move content off the DVR.  It is very likely that port will be limited to USB2 speeds, so throwing an SSD at it won't make it any faster. Plus, using an SSD for video storage isn't cost effective or necessary.

I have a 250G used WD-Blue drive ($9 about 5 yrs ago) connected to a USB2 docking port that I use to move video from a specific device to linux for storage.  My device can record at 1080i, but I force it to 720p to save storage.  I don't have any 4K capable displays here so higher resolutions don't make any sense to me, yet.  Last year, got a new 1080 projector, so 4K for movies ain't gonna happen for 5+ yrs.

---

### Post by johnaaronrose on 2022-06-16
Not able to use the DVR as it's kaput. I took the HD out of the DVR. I was able to copy the files (there are only 4 programmes of which 1 is still on BBC iPlayer) on the HD to my PC's SSD (using separate SATA data & power cables with a powered converter gizmo - for both sizes of hd - with USB output - £8+ from Amazon) but not able to play / convert to mp4. 
Perhaps due to being over 70 - I can't even tell the difference between HD & 4K! Current main TV is dumb and is only HD.

---

### Post by TheFu on 2022-06-16
Das ist kaput?  That changes everything.

I have poor eyesight too. 'Only HD' is more that sufficient for me.  If I ever get a smart TV, it won't be connected to any network, except for yearly firmware updates.  I keep IoT (really IoS) stuff on a separate network, nowhere near anything important.  
[https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/](https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/) > FBI recommends that you keep your IoT devices on a separate network

...
The FBI says owners of IoT (Internet of Things) devices should isolate this equipment on a separate WiFi network, different from the one they're using for their primary devices, such as laptops, desktops, or smartphones.

I consider smartphones, tablets, and Windows computers to be IoS devices too.

---

### Post by pantazi on 2022-06-16
> **johnaaronrose said:**
> Humax is HDR-2000T. I've posted on hummy.tv an appropriate question [https://hummy.tv/forum/threads/how-to-copy-from-hard-disk-in-hdr-2000t-to-an-mp4-file-on-my-pc.10644/](https://hummy.tv/forum/threads/how-to-copy-from-hard-disk-in-hdr-2000t-to-an-mp4-file-on-my-pc.10644/)

Saw that and you were given the information by the resident guru, tough luck!

---

### Post by pantazi on 2022-06-17
> **TheFu said:**
> I read somewhere that if the DVR has a USB port on the front, that copying the files through that method would remove the encryption.  

Test that with NTFS and/or FAT32 just to see if it actually works.  



No, that doesn't work. On the Humax HDR FoxT2, where a lot of customisation is available, the Custom Firmware is used to remove the encoding encryption flag before copying to USB.
Sadly for the OP that option is not available for his model.

---

