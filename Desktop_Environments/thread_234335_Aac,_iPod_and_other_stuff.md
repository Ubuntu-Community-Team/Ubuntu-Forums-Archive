---
title: "Aac, iPod and other stuff"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Romu on 2006-08-11
Hi all,
I've read dozens of doc and wiki, installed faac and faad packages and gstreamer plug ins to encode and decode AAC format.

About gstreamer, I installed some plugins from 0.10 and some from 0.8, I don't know if this way raise the problem.

Sound juincer seems to rip and produces somes files with quite logical sizes, but I can't read them, I always (Totem, Banshee, or RythmBox) get the same issue "format not supported" or something like this.

Any idea ?

Thanks for the help.

---

### Post by netztier on 2006-10-09
> **Romu said:**
> Sound juincer seems to rip and produces somes files with quite logical sizes, but I can't read them, I always (Totem, Banshee, or RythmBox) get the same issue "format not supported" or something like this.

Same here. I configured Sound Juicer according to the "Restricted" and the "CD-Ripping" sections in the [Wiki]("https://help.ubuntu.com/community/Multimedia").

I produced files that XMMS plays, so I assume the'yre ok. But neither Totem, Rhythmbox nor gtkpod-aac seem to like them.

[LIST]
[*]Totem: "Could not determine type of stream"
[*]Rhythmbox: "The MIME type of the file could not be identified"
[*]gtkpod-aac: "Could not open '<path to file>' for reading, or file is not an mp4 file. The following track could not be processed (filetype is known but analysis failed): '<path to file>'
[/LIST]

I tried (re)installing all gstreamer-0.10 plugins, the base ones, the good ones, the bad and even the ugly ones from universe and multiverse. faac and faad, too. To no avail.

What next? How to make gstreamer decode AAC?

thanks and best regards

Marc

---

### Post by netztier on 2006-10-16
> **netztier said:**
> What next? How to make gstreamer decode AAC?

I've been able to cross-check this with my Ubuntu laptop, which has nothing but gstreamer-0.10 installed - with all plugins from universe and multiverse, that is.

I've been using .m4a files that were ecoded from CD with iTunes on a PowerBook running MacOS X 10.something. The gstreamer-based apps play them (rhythmbox, totem), Xine an Gxine, too, and of course mplayer and VLC, XMMS also. 

When I try to add them to gtkpod's database, it still shouts at me that the filetype was known, but the analysis did fail, but adds them anyway, transfers them to the iPod which will finally play them - not yet in audiobook format, I'll investigate that part later on.

So the fault must've been with the encoding/"packaging" done with the wiki-suggested gstreamer pipeline that does **not** work with gstreamer-0.10 only. See also this [thread]("http://www.ubuntuforums.org/showpost.php?p=1606504&postcount=11").

best regards

Marc

---

### Post by sinaen on 2006-10-23
the audiobook format is m4b not m4a.. it exist a good script that converts mp3 audio-books to m4b.

but i have the problem to edit the id3 tags on the aac/m4a and m4b files.. :(

[http://www.ubuntuforums.org/showthread.php?t=180073&highlight=audiobook+support](http://www.ubuntuforums.org/showthread.php?t=180073&highlight=audiobook+support)

here it is :)
hope you can use it in some way.

---

