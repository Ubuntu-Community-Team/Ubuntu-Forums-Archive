---
title: "CD ripping in Banshee"
date: 2006-06-30
forum: Desktop Environments
---

### Post by zip_000 on 2006-06-30
OK, what gives...

I can't get CD ripping to work in Banshee in any form that is useful for my needs...

I need either mp3 or mp4 (aac), not ogg or any of the other options that it has.

The MP4 option doesn't seem to work at all, and from reading around on it, it doesn't look like it works for anyone (if someone gets this to work, please tell me how).

I can't figure out how to get MP3 to work for it either - I can get them to play (I think) but I want to rip my CDs

Can someone give me some directions on how to go about adding this? Or if not pointing me to a CD ripper that will rip to MP3 or MP4?

Keep in mind, I'm an idiot - so if you can, be as clear as possible.

(if I sound a little grumpy, I'm sorry - just frustrated and its late (for me anyway))

---

### Post by nosmada on 2006-11-27
Here is the answer straight from banshee ([http://banshee-project.org/Distributions/Ubuntu]("http://banshee-project.org/Distributions/Ubuntu")):

> Support for MP3, AAC and Other Formats

Note: You must enable the multiverse repository in Synaptic or by editing /etc/apt/sources.list. Be sure to run apt-get update afterwards. 
```
$ sudo apt-get install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly \
    gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly-multiverse \
    gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg
```

---

### Post by Terc on 2007-10-21
I believe he meant cd _ripping_ your posted method just enables playback.

Here you are (sorry for the bump, this page has a high rank on Google when searching for "banshee rip to mp3")

[http://ubuntuforums.org/showpost.php?p=2754375&postcount=5](http://ubuntuforums.org/showpost.php?p=2754375&postcount=5)

---

