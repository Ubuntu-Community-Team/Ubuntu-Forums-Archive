---
title: "Video/Multimedia"
date: 2005-12-10
forum: Desktop Environments
---

### Post by slrafal on 2005-12-10
This is in regards to watching videos in firefox. I went through all the tutorials on installing mplayer(works), and installing these codecs(?) and I still cannot watch trailers on apple.com.

I have done two things:

1) copied the codecs and everything into /usr/lib/win32
 - since this did nothing

2) I installed w32 codecs in .deb file format and still no success.

What am I missing?

---

### Post by amohanty on 2005-12-11
1. Undo everything you did.

2. Install totem-xine (worked for me withouth any hitches - so I use it)
```
sudo apt-get install totem-xine
```
NOTE: This will prompt you to remove totem-gstreamer - say Yes

3. In a terminal:
```
sudo apt-get install mozplugger gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg flashplayer-mozilla
``` 

4.Add the plf repost to your /etc/apt/sources.list (add to the end)
> deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

5. update repos
```
sudo apt-get update
```

6. Then in a terminal just do the following:
```
sudo apt-get install w32codecs libdvdcss2
```

7. Register the plugins
```
gst-register-0.8
```
You will have to do this for every user.

6. Comment out the plf repos. Add a '#' charachter to the lines you added to /etc/apt/sources.list in Step (4)

7. Redo step (5)

You should be ready to go.

HTH

---

### Post by slrafal on 2005-12-11
Thanks for the attempt, but it did not work. I don't know how tha hell to fix this annoying issue.

---

### Post by Hairy_Palms on 2005-12-11
totem plugin is broken follow my howto on howto get mplayer plugin
[http://www.ubuntuforums.org/showthread.php?t=76946](http://www.ubuntuforums.org/showthread.php?t=76946)

---

### Post by ShiftyPowers on 2005-12-11
worked like a charm, thank you

---

### Post by slrafal on 2005-12-13
I don't know what I'm doing wrong, but it still does not work?

---

