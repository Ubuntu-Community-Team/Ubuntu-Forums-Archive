---
title: "Installed Amarok - says &quot;No suitable input plugin&quot;"
date: 2008-12-15
forum: General Help
---

### Post by terry@softreq.com on 2008-12-15
Not sure where or how I'm supposed to get a suitable input plugin.   :sad

---

### Post by EdThaSlayer on 2008-12-15
You should say a bit more.

For example, what "file" were you trying to play?

There is(or was) an issue with Amarok 1.5 where playing an mp3 file gets that result. It was overcome by playing Amarok in root(using sudo) but that isn't recommended.

---

### Post by terry@softreq.com on 2008-12-15
Sorry, I figured it out - I just had to double click on the track, rather than clicking once, and then hitting the Play button. 

There's a lot of Shoutcast streams - much better than Itunes in that regard.

---

### Post by mc4man on 2008-12-15
Install libxine1-ffmpeg and amarok can handle just about anything but wma lossless. 
For that install w32codecs

---

### Post by terry@softreq.com on 2008-12-15
should I use terminal mode to install those: libxine1 and w32codecs?

Don't know how to do it (only had ubuntu for 1 day but learning fast - wow, awesome!)

---

### Post by mc4man on 2008-12-15
for libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

For w32codecs you need to either add the appropriate medibuntu repo for your install and then the key file or do a direct download and install.

You didn't post what version of ubuntu your using, Intrepid or Hardy, makes a difference for the medibuntu repo. (worth adding for hardy, less so for intrepid

---

### Post by terry@softreq.com on 2008-12-15
I have ubuntu 8.10

---

### Post by mc4man on 2008-12-15
For w32codecs go here and  click on on i386, if you get an option to open with Gdebi do so. If not download to desktop and then d. click on the .deb to install.

[http://packages.medibuntu.org/intrepid/w32codecs.html](http://packages.medibuntu.org/intrepid/w32codecs.html)

---

