---
title: "Re-encoding video podcasts for the iPod"
date: 2009-03-25
forum: General Help
---

### Post by achinton on 2009-03-25
Sorry if this isn't the right place to post this, but wasn't sure where it should go.

OK, so I want to be able to download a video podcast and copy the files across to my ipod. Simple enough, but the problem is I need to re-encode the video into an appropriate format so my ipod will play it. Is there a podcatcher available that will perform a command on all video files before uploading them to the ipod, for instance? I know exactly what ffmpeg command will work, I just want to automate the process, so it's not such a pain.

Anyway, I wasn't aware of such a program, so I set about trying to do it through cronjobs. My problem there is getting [ipod-encoder]("http://sourceforge.net/projects/ipod-encoder/") to work. I can't seem to make its folder processing and "fake" podcast generating mode work. I keep getting "no such file or folder" errors. If I could make it work, then I could download the podcast with bashpodder, generate a fake rss feed of re-encoded video files, point my podcatcher at that, and I'd be away.

Sorry for that complicated explanation! Anyone have any ideas?

---

### Post by saidinesh5 on 2009-03-25
Floola : 
its the one software, which i used to properly maintain my bro's ipod nano...it does the conversions of videos to the ipod format, and writes them to the ipod's database...well just check the website out here..i havent ever used podcasts thingy, but it says it can handle podcasts n stuff.. till now this is the best ipod management tool i ve seen

[http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

all the best :)

---

### Post by mb_webguy on 2009-03-25
Handbrake is great for encoding videos for use on an iPod, but it's just a converter.  You'd have to use something else to download the podcasts, and then something like gtkpod to put the videos on the iPod.

---

### Post by achinton on 2009-03-25
Thanks for pointing me towards Floola, it looks like a pretty good program in general.

Unfortunately, in the case of the particular video podcast I'm trying to get working, it seems to be incorrectly determining that the files don't need re-encoding, and transferring them straight on.

Sigh.

---

