---
title: "Max bitrate on a VBR mp3 file?"
date: 2006-03-16
forum: Desktop Environments
---

### Post by hashimoto on 2006-03-16
Dear fellow coffee grinders,

Does anybody know how to tell the maximum and minimum bitrates of a VBR mp3 file? What nice piece of software could do that?

Background for the question:
I have a iRiver ifp-899 player that does random rebooting every now and then. It could be a harware failure but I also have a theory that it could be caused by too high bitrates in VBR mp3 files (iFP supports max 320 bitrate). 

I have some files that seem to cause the reboot more regularly and they are all VBR mp3 files. Reboot seldom happens at the same point of time in a piece, but still. So it could be a kind of memory overflow or something. So, before I send my unit back for guarantee repair/change (and possible embarrass myself and cause extra cost) I want to test the theory.

---

### Post by MichaelZ on 2006-03-16
Hello,

May be FFMPEG could be useful for you:

[http://ffmpeg.sourceforge.net/index.php]("http://ffmpeg.sourceforge.net/index.php")

Best wishes,
Michael

---

### Post by hashimoto on 2006-03-17
Thanks, I'll take a glance during weekend.

---

### Post by Velvet Elvis on 2006-03-17
This is for debian sid but I can can personaly attest to it working in breezy.

[http://rarewares.soniccompression.com/debian/packages/unstable/encspot_2.01-1_i386.deb](http://rarewares.soniccompression.com/debian/packages/unstable/encspot_2.01-1_i386.deb)

this is typical of the output it will give you

```

joe@zara:/media/hda5/music/Morphine-Like_Swimming$ encspot 04.Early_To_Bed.mp3
04.Early_To_Bed.mp3
-------------------

Bitrates:
------------------------------------------------------------
 32     |                                               1.0%
128     ||||||||||||||||||||||||||||||||               27.3%
160     ||||||||||||||||||||||||||||||||||||||||       33.7%
192     ||||||||||||||||||                             15.3%
224     |||||||||||                                     9.8%
256     |||||||||                                       7.8%
320     ||||||                                          5.1%
------------------------------------------------------------

Type                : mpeg 1 layer III
Bitrate             : 176
Mode                : joint stereo
Frequency           : 44100 Hz
Frames              : 6796
Length              : 00:02:57
Av. Reservoir       : 77
Emphasis            : none
Scalefac            : 5.8%
Bad Last Frame      : no
Sync Errors         : 0
Encoder             : Lame 3.96

Lame Header:

Quality                       : 77
Version String                : Lame 3.96
Tag Revision                  : 0
VBR Method                    : vbr-old / vbr-rh
Lowpass Filter                : 19000
Psycho-acoustic Model         : nspsytune
Safe Joint Stereo             : yes
nogap (continued)             : no
nogap (continuation)          : no
ATH Type                      : 4
ABR Bitrate                   : 128
Noise Shaping                 : 1
Stereo Mode                   : Joint Stereo
Unwise Settings Used          : no
Input Frequency               : 44.1kHz

--[ EncSpot Console 2.0 ]--[ http://www.guerillasoft.com ]--



```

---

### Post by hashimoto on 2006-03-17
This seems to be exactly what I was looking for. Thanks a lot!

---

### Post by stoeptegel on 2006-03-17
Max bitrate of mp3 is 320 kbit/s, and that shouldn't be the problem. 
I have heared that some players break their neck over VBR and ABR streamed files. They just can't handle it well.

---

### Post by hashimoto on 2006-03-19
stoeptegel, thanks! 

Turned out that VBR in itself was the problem. I re-encoded some of the problem causing files with CBR (from the VBR file) and have not had a problem after that. I've been listening the whole day yesterday without a single reboot (my poor ears). I didn't embarrass myself, then.

---

