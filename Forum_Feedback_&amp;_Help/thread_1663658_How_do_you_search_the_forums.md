---
title: "How do you search the forums?"
date: 2011-01-09
forum: Forum Feedback &amp; Help
---

### Post by e_james on 2011-01-09
Can anyone suggest how to search these forums for a compound word or phrase such as "ubuntu-desktop" without getting lots of unwanted results containing only one of the words?

Is it even possible?

---

### Post by wojox on 2011-01-09
I would just search from Google:

```
ubuntuforums:ubuntu-desktop
```

---

### Post by e_james on 2011-01-10
wojox

Thanks for the suggestion but the google search is only marginally better than the forum search and does not allow me to select posts rather than threads (I think).

In the case of the search term "ubuntu-desktop", I was intending to research the relationship between gstreamer, pulseaudio and ubuntu-desktop which is giving me and others some problems when trying to playback divx / mp3 video files in ubuntu 10.10 and / or 10.04. I would prefer to avoid reading through 10 or 20 pages of posts in a thread containing the word "desktop" until I am sure that it does not contain "ubuntu-desktop". I could put the question in a new thread in the multimedia forum but I expect that the answer has already been written if I can just find it.

---

### Post by wojox on 2011-01-10
> **e_james said:**
> wojox

Thanks for the suggestion but the google search is only marginally better than the forum search and does not allow me to select posts rather than threads (I think).

In the case of the search term "ubuntu-desktop", I was intending to research the relationship between gstreamer, pulseaudio and ubuntu-desktop which is giving me and others some problems when trying to playback divx / mp3 video files in ubuntu 10.10 and / or 10.04. I would prefer to avoid reading through 10 or 20 pages of posts in a thread containing the word "desktop" until I am sure that it does not contain "ubuntu-desktop". I could put the question in a new thread in the multimedia forum but I expect that the answer has already been written if I can just find it.

Have you installed Medibuntu Repository AND the medibuntu keyring?

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

And codecs

```
sudo apt-get install non-free-codecs libdvdcss2 gxine libxine1-ffmpeg vlc mplayer mencoder
```

You should have no problem playing any files now.

---

