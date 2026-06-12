---
title: "Kaffeine Media Player?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-02-18
I was wondering if anyone here used Kaffeine media player on their Ubuntu system? I removed Totem and downloaded the "esential codec pack" from the "Mplayer" site per suggested from Kaffeine. I just don't know where to move the codecs after I unzip them.

---

### Post by Perfect Storm on 2006-02-18
I will recommend VLC or Mplayer as mediaplayer.

To get the codecs.

```
gedit /etc/apt/sources.list
```

add:
[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]


```
sudo apt-get update
sudo apt-get install w32codecs
```

---

### Post by CarlosinFL on 2006-02-18
No, I am not asking for Media player suggestions. Kaffeine uses Xine front end with Mplayer codecs...it's all the same. Please - I am only asking for help with where to the codecs are to be moved to once unpacked.

---

### Post by Perfect Storm on 2006-02-18
As shown above will install the codecs.

---

### Post by CarlosinFL on 2006-02-18
Just for kicks I tried your suggestion and was unable to find Mplayer...???

Tried CLI and also GUI synaptic. I even tried "g"mplayer and still found nothing...?

```
carlos@notebook:~$ sudo apt-get install mplayer
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer
```

---

### Post by Perfect Storm on 2006-02-18
```
sudo apt-get install mplayer-386
```

There's also -586 and -686 if you want it to fits your computer spec.

Oh by the way you need multiverse enable in the sourcelist

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

---

### Post by CarlosinFL on 2006-02-18
Is there a way I can tell Ubuntu to open Mplayer anytime it needs to play a common video file like .wmv, mpeg, mpg, avi, mov, etc etc etc...?

---

### Post by Perfect Storm on 2006-02-18
Yep, if you want mplayer to play all your .mov as an example, you right click on a .mov and click **properties**. Now go to **Open with** tab.
Click the **add** button and pick **Use a custom command** and write in its command box:

```
gmplayer
```

Now you can choose it in the **Open with** Selector.

---

### Post by CarlosinFL on 2006-02-18
Thanks - that did the trick!

I keep getting this error however...?

[IMG]http://img500.imageshack.us/img500/4931/mplayer1kb.png[/IMG]

---

### Post by Perfect Storm on 2006-02-18
Try with this:

```

sudo apt-get install gsfonts-x11 msttcorefonts
sudo fc-cache -f -v
```

If that doesn't work do this:

```

sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/share/mplayer/subfont.ttf
```

Skins for mplayer: [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

Also please post the output when writting this in the terminal:

```
gmplayer
```

To get mplayer to play browser stuff:

```
sudo apt-get install mozilla-mplayer
```

---

### Post by CarlosinFL on 2006-02-18
Mplayer seems to be working for .mpg files but when I try to play something that is embedded in the browser, I seem to be missing a plugin or something.

I installed "mozilla-mplayer" which I assume installed fine since it returned no errors but I still see this:

[IMG]http://img226.imageshack.us/img226/6629/screenshot6ik.png[/IMG]

I have a .mpg file on my "Desktop" which does play fine but it will not pull down from the browser.

---

### Post by Perfect Storm on 2006-02-19
[http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)

```
cd Desktop
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb 

```

---

