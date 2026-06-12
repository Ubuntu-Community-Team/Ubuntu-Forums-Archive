---
title: "Cabrio FE"
date: 2013-07-15
forum: Emulators
---

### Post by ZarathustraDK on 2013-07-15
I've finally gotten the son of a gun that is Cabrio FE working, except I'm not juuuust there yet :) I've have the following issues, any input would be appreciated:

- Video-previews are choppy and only renders top half part of the video, with a strange flicker on the rest.

- I really miss some docs on the different parameters you can set in the config.xml. The standard options turns my full hd-screen into 640x480 when launching a rom (which is good), but then it doesn't reset when exiting (which is bad bad bad). Even worse, if the rom is bad or some other error occurs during launch, then my monitor starts going "This resolution not supported" in which case I need to cold-boot.

- How do I change to the horizontal carrousel theme instead of the default vertical theme?

Seems like we're only a destined few left who use Cabrio FE :( A pity, it's very nice frontend once you get it to do what you want.

---

### Post by naxil on 2013-12-15
i can't install or compile cabrio FE u can helpme? my ubuntu 12.04 have new lib (the deb askme for version 52 but i have version 53)
libavcodec52 (>= 4:0.6-1~)|libavcodec-extra-52 (>= 4:0.6-1~)

---

### Post by Sergio Benjamim on 2014-06-09
Hey, I managed to make a package for Cabrio FE, for ubuntu 12.04, 13.10, 14.04 (and linux mint 13, 16 and 17 as well). Take a look at my PPA:

[https://launchpad.net/~sergio-br2/+archive/cabrio](https://launchpad.net/~sergio-br2/+archive/cabrio)

This version is based in [Fred git fork]("https://github.com/fredbcode/cabrio"), which has a video-loop option, uses libavcodec53 and some bug fixes (i.e. it is much more update thant the package from cabrio website). There is a group to discut about bugs and issues: [https://groups.google.com/forum/#!forum/cabrio-fe-dev](https://groups.google.com/forum/#!forum/cabrio-fe-dev)

Known issues in 14.04:

- Video makes a horrible noise (someone needs to update a deprecated function in video.c, avcodec_decode_audio3() to avcodec_decode_audio4() from libav/ffmpeg library, take a look at [https://groups.google.com/forum/#!topic/cabrio-fe-dev/Gagu5D4t8Kc](https://groups.google.com/forum/#!topic/cabrio-fe-dev/Gagu5D4t8Kc))


In the portuguese forum, me and other nice guy are talking about this front end, we have some config examples and tips (if you understand portuguese :), i can translate something to here): [http://ubuntuforum-br.org/index.php/topic,113252.0.html](http://ubuntuforum-br.org/index.php/topic,113252.0.html)

---

