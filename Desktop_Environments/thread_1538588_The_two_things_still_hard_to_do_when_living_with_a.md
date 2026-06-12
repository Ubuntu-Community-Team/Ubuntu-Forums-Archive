---
title: "The two things still hard to do when living with a legacy machine"
date: 2010-07-25
forum: Desktop Environments
---

### Post by romis on 2010-07-25
So I've gotten to the point where I find GNU/Linux a whole lot of fun to put on various different types fo computers that today's proprietary software couldn't even come close to supporting. I'm talking about so-called "legacy" machines. With about a 10 GiB hard drive  (usually even less) and 256 MB of RAM (or less) I can get Xfce or LXDE environments up and running smoothly.

Except for two aspects, as to a lesser extent a third. Namely, playing videos, and looking at photos (copied from a digital camera, so they're full resolutionn), and in some cases also playing lossless audio.

Sure, there are so-called light-weight alternatives to the heavy and bulky GNOME and KDE viewers, but the only thing lightweight about them is that they themselves use low resources in their interface - the same cannot be true for their processing.

Take, for example, [Ristretto]("http://goodies.xfce.org/projects/applications/ristretto"), the image viewer for Xfce. When introducing it, they [noted]("http://blog.xfce.org/2008/03/ristretto-a-lightweight-image-viewer/") quite correctly that "there is no such thing as a lightweight image viewer" because decompressing the images and such requires CPU power and RAM - something which are not always plentifully available on legacy systems.

And videos are the biggest pain - it seems purely impossible to watch anything of high quality on legacy machines, even in a "lightweight" media player.

So it's for that that I've attempted to come up with a solution.

In Thunar, Xfce's file manager, you are allowed custom action (see [here]("http://thunar.xfce.org/pwiki/documentation/custom_actions")) and I thought if I could make it easy for the user to right click a video and to click on an option "Make this video playable under low requirements" or something it could help. Sure, it would take a while, because after all, you're still processing the video, but it would eventually convert it down to something watchable.

So after a few hours I came up with this:

```
ffmpeg2theora %n -o %n-smaller && zenity --info --text="Done."
```

Which will convert a given video file to ffmpeg2theora's default qualities, which are (according to "man ffmpeg2theora") 5 for video (scale of 0 to 10) and 1 for audio (scale of -2 to 10). My hope is this is low enough quality to be playable, but not too low so as to look terrible.

Of course my lack of experience, the script above is functional, though by no means elegant. Customizing or changing the values at will requires re-hardcoding, so I'm wondering if perhaps anyone could offer some advice as to a better way to accomplish what I'm looking for, for all of the three things - photos, audio, and video.

For photos, I am trying to get it so the user can select a bunch of photos and for their to be a "scale down" command, which copies the original ones into a directory called "original backups" in the same folder, and scales the given photos by a percentage. Or do you think it would be better to keep the same size but lower quality? Probably ImageMagick is the way to go here?

For audio, likely the solution is to convert to a format like Ogg with medium to low quality, possibly through the "soundconvert" program. Important to use Ogg because some input formats will be lossless, and others may not have as many encoding options.

So does anyone have any ideas as to how to better attack this and maybe can help me out with scripting?

Thanks.

---

### Post by nemilar on 2010-07-25
All of these conversions would be taking place on the low-quality machine, which means that the conversions themselves would be slow (and it would be sucking up power (processing power and electrical power) the entire time.

At some point it's necessary to just junk the old hardware and move on.

---

### Post by linux18 on 2010-07-25
1) Do you have any benchmark test to show which is the lightest weight codec?
2) could I see the hardware specs of the computer your testing on?
3) transcoding takes a long time, its more of a dedicated program that supports scheduling and running in the background than a context menu option.
despite these concerns, I love the idea. When I had my 850mhz celeron without a video card i could get better fps on openarena than youtube vids ( althought that was/is adobe's fault ) or dvd's ( more like a powerpoint presentation ) good work!

---

### Post by jerrykenny on 2010-07-25
For videos i used to find mplayer managed on older hardware whereas other players would be a bit choppy.

For photos, konqueror has the excellent ability html slideshows from any folderfull of photos. I used to use this ability to create webpages for a sports club website. . . . That your viewing them locally still makes them usefull inasmuch as you have a real nice presentation, and sensibly sized images.

---

### Post by Joe of loath on 2010-07-25
VLC is the best player on my celeron 433mhz. Audio uses around 10% (Compared to aqualung or deadeef which use ~60%). Videos I haven't checked, but I'm going to assume the performance difference will be similar.

---

### Post by romis on 2010-07-25
Thanks for your responses everyone. I'll address everything (hopefully) one by one. Regarding the oft-noted "It'll still take a while and use lots of power to the conversion" I know this, but the way I'm premising the idea, is that users will be willing a one-time long wait for essentially unlimited access to their videos or photos or audio later. Obviously not ideal, but if you want to do it, you'll deal - I mean there's no alternative and it's really not like some crazy "evil" feature or deal-breaker in my opinion like "Oh, I can't watch high quality videos whenever I want, I'm not going to do anything on my computer then."

Another issue I have with the script I posted, is there's no progress, really. Zenity does have [a progress dialog]("http://library.gnome.org/users/zenity/stable/zenity-progress-options.html.en"), but it seems to be for different purposes, namely to look pretty, not necessary to read into from some other program like ffmpeg2theora, though maybe I'm wrong. I have an idea that I should add the showing of the terminal command during this, so that at least displays some sort of progress happening. Thoughts?

Ok, now on to the responses and my responses to them.

> **nemilar said:**
> All of these conversions would be taking place on the low-quality machine, which means that the conversions themselves would be slow (and it would be sucking up power (processing power and electrical power) the entire time.

At some point it's necessary to just junk the old hardware and move on.

I agree that the conversion would take a long time, but if there was a decent way to do it at least the user would have access to their media *eventually*. I don't think junking old hardware is quite a good idea, since obviously it works with the vast majority of tasks under a lightweight environment quite well. And what about devices like netbooks or cell  phones that can run GNU/Linux? They also have lower specs, does that mean we shouldn't be putting GNU/Linux on them? Seems like a silly argument that just because something isn't a GiB of RAM that they're not worth anything.

> **linux18 said:**
> 1) Do you have any benchmark test to show which is the lightest weight codec?
2) could I see the hardware specs of the computer your testing on?
3) transcoding takes a long time, its more of a dedicated program that supports scheduling and running in the background than a context menu option.
despite these concerns, I love the idea. When I had my 850mhz celeron without a video card i could get better fps on openarena than youtube vids ( althought that was/is adobe's fault ) or dvd's ( more like a powerpoint presentation ) good work!

1) I've got no particular benchmark, but in my experience Ogg varieties (at lower qualities) seem to work pretty well. Theora always gets FUD for not being HD, but that's exactly what I want.

2) Yeah absolutely. I ran the System Profiler (the package name "hardinfo"), great program btw.
> 
Processor
Processor
Name	Pentium III (Katmai)
Family, model, stepping	6, 7, 2 (Pentium III/Pentium III Xeon/Celeron)
Vendor	Intel Corp.
Configuration
Cache Size	512kb
Frequency	451,00MHz
BogoMIPS	903,00
Byte Order	Little Endian
Features
FDIV Bug	no
HLT Bug	no
F00F Bug	no
Coma Bug	no
Has FPU	yes
Capabilities
fpu	Floating Point Unit
vme	Virtual 86 Mode Extension
de	Debug Extensions - I/O breakpoints
pse	Page Size Extensions (4MB pages)
tsc	Time Stamp Counter and RDTSC instruction
msr	Model Specific Registers
pae	Physical Address Extensions
mce	Machine Check Architeture
cx8	CMPXCHG8 instruction
sep	Fast System Call (SYSENTER/SYSEXIT)
mtrr	Memory Type Range Registers
pge	Page Global Enable
mca	Machine Check Architecture
cmov	Conditional Move instruction
pat	Page Attribute Table
pse36	36bit Page Size Extensions
mmx	MMX technology
fxsr	FXSAVE and FXRSTOR instructions
sse	SSE instructions
up	
Memory
Memory
Total Memory	126448 kB
Free Memory	2824 kB
Buffers	4872 kB
Cached	43184 kB
Cached Swap	7128 kB
Active	85344 kB
Inactive	19128 kB
High Memory	0 kB
Free High Memory	0 kB
Low Memory	126448 kB
Free Low Memory	2824 kB
Virtual Memory	369452 kB
Free Virtual Memory	348452 kB
Dirty	2120 kB
Writeback	0 kB
AnonPages	54016 kB
Mapped	20220 kB
Slab	6096 kB
SReclaimable	2596 kB
SUnreclaim	3500 kB
PageTables	1068 kB
NFS_Unstable	0 kB
Bounce	0 kB
WritebackTmp	0 kB
CommitLimit	432676 kB
Committed_AS	175316 kB
VmallocTotal	901112 kB
VmallocUsed	5612 kB
VmallocChunk	894452 kB
HugePages_Total	0
HugePages_Free	0
HugePages_Rsvd	0
HugePages_Surp	0
Hugepagesize	4096 kB
PCI Devices
PCI Devices
Host bridge	Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
PCI bridge	Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
ISA bridge	Intel Corporation 82371AB/EB/MB PIIX4 ISA
IDE interface	Intel Corporation 82371AB/EB/MB PIIX4 IDE
USB Controller	Intel Corporation 82371AB/EB/MB PIIX4 USB
Bridge	Intel Corporation 82371AB/EB/MB PIIX4 ACPI
Multimedia audio controller	Ensoniq ES1370 [AudioPCI]
Ethernet controller	Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
VGA compatible controller	ATI Technologies Inc Rage 128 RF/SG AGP

3) Yeah I, as a rule, never install Flash or recommend it - not just because it's proprietary - it doesn't work. Period. Even the free software re-implementations like Gnash are still more memory efficient than Adobe's whatist. Non-Adobe-Flash ways to access YouTube and Pandora already exist, so that fits the major needs of quite a lot of people. HTML5 will fill in the gap, except on sites like Hulu which rely on the RTMP - a proprietary protocol, essentially DRM, and I avoid DRM everywhere else, why should Hulu be any exception?

> **jerrykenny said:**
> For videos i used to find mplayer managed on older hardware whereas other players would be a bit choppy.

For photos, konqueror has the excellent ability html slideshows from any folderfull of photos. I used to use this ability to create webpages for a sports club website. . . . That your viewing them locally still makes them usefull inasmuch as you have a real nice presentation, and sensibly sized images.

I'll give MPlayer a quick look. Konqueror is very big though hard-drive wise, and I'm sure RAM-usage wise too. Plus tons of KDE and Qt deps is not fun. It's a little bit better with some GNOME-y apps, because XFCE already uses GTK+. I guess the HTML slideshow option is pretty cool, but can it be invoked from the command line and/or installed separately? Because then I wouuld just set it up as a context menu - you right click a folder or select a whole bunch of photos and have "make these photos into an HTML slide show" 

> **Joe of loath said:**
> VLC is the best player on my celeron 433mhz. Audio uses around 10% (Compared to aqualung or deadeef which use ~60%). Videos I haven't checked, but I'm going to assume the performance difference will be similar.

If that is true that is terrific, because VLC is also extremely functional (sometimes in lightweight computing you have to fight between software that's super functional vs. software that's super light. The only issue  I have with VLC is it's still, interface-wise, way too complicated for most users. Still, I use VLC for scripting pretty often. Side note, hey doesn't VLC also transcode between audio and video formats? Is that efficient at all and can it be used from the commandline?

---

### Post by Joe of loath on 2010-07-25
> **romis said:**
> 
If that is true that is terrific, because VLC is also extremely functional (sometimes in lightweight computing you have to fight between software that's super functional vs. software that's super light. The only issue  I have with VLC is it's still, interface-wise, way too complicated for most users. Still, I use VLC for scripting pretty often. Side note, hey doesn't VLC also transcode between audio and video formats? Is that efficient at all and can it be used from the commandline?

I'm afraid I can't say anything about the transcoding, as I've never had a need for it. I do know, however, that (almost?) all of its functions are available through the CLI, as I've had boxes playing music and being controlled via SSH from the other side of the house. There were LOTS of functions there.

---

### Post by romis on 2010-07-26
> **Joe of loath said:**
> I'm afraid I can't say anything about the transcoding, as I've never had a need for it. I do know, however, that (almost?) all of its functions are available through the CLI, as I've had boxes playing music and being controlled via SSH from the other side of the house. There were LOTS of functions there.

Just tried VLC, it is sadly not light enough to solve my problem - namely that the file is still high quality. I still need a way to convert a given video to low enough quality to make it playable in anything at all.

---

