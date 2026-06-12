---
title: "gnome-subtitles &quot;don't know how to handle video/x-h264&quot;"
date: 2014-05-02
forum: Desktop Environments
---

### Post by landry-soules-cn on 2014-05-02
I've recently installed Kubuntu 14.04, and I'm unable to use one of my favorite programs : gnome-subtitles.
It opens subtitles OK, but won't play any movie, which make it useless for editing subtitles...
I get the following message :  "don't know how to handle video/x-h264"
Yet I can play video files without any problem, and I have installed the whole gstreamer plugins family, so I'm out of solution. Please help !

---

### Post by enzideout on 2014-05-02
You may need to install ubuntu-restricted-extras.

---

### Post by landry-soules-cn on 2014-05-02
Thanks for your suggestion, but I have [COLOR=#000000]**ubuntu-restricted-extras** already installed.[/COLOR]

---

### Post by fliewatuet on 2014-05-25
The gstreamer0.10-ffmpeg package is missing, see:

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1275556")

You'd have to install it from a ppa:

```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg
```

---

### Post by ahendriks on 2014-05-26
First, thx for the answer!!!

Second, is this PPA trustworthly?
I would like to use gnome subtitles in 14.04, but try not to use any untrusty APT sources...

---

### Post by fliewatuet on 2014-05-27
[QUOTE=ahendriks;13033851
Second, is this PPA trustworthly?
I would like to use gnome subtitles in 14.04, but try not to use any untrusty APT sources...[/QUOTE]

I think this has everybody to decide for himself, you can read some stuff about this repository here:

[https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

A nice side effect of installing gstreamer0.10-ffmpeg is that now firefox can play again youtube html5 videos.

---

### Post by mc4man on 2014-05-27
> **ahendriks said:**
> First, thx for the answer!!!

Second, is this PPA trustworthly?
I would like to use gnome subtitles in 14.04, but try not to use any untrusty APT sources...

You can simply add the ppa, install the plugin, then remove the ppa. As far as that package there as been about 28k downloads, I've gotten no complaints. The likihood of the plugin being updated down the road isn't great though if I find or am presented with a security patch for the internel libav source used would certainly apply it.

As far as the other packages, yours or anybody's choice. All have been tested to some extent by me, some I use regularly (ffmpeg, mpv, mplayer, vlc, smtube, youtube-dl, ect. Those are updated weekly or so & are pre-tested in a proposed ppa first.
Not all are described though some additional info can be found by going to "View package details" > expanding a package entry & ck. the Changelog

If there is any issue or suggestion to improve a package then a lauchpad email & I'll address as possible...

Edit: Firefox 30 should be available soon & it has support for the 1.0 gstreamer libav plugin. Currently packages are in 14.10 -proposed, they can be installed in 14.04 or one can wait.

---

### Post by sampayu on 2014-09-20
If you don't want to add that repository, no problem: you can head straight to the [URL of that repository]("http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/pool/main/g/gstreamer0.10-ffmpeg/"), then download [gstreamer0.10-ffmpeg_0.10.13-5ubuntu1~trusty2_i386.deb]("http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/pool/main/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1~trusty2_i386.deb") (if your system is **32 bits**) or download [gstreamer0.10-ffmpeg_0.10.13-5ubuntu1~trusty2_amd64.deb]("http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/pool/main/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1~trusty2_amd64.deb") (if your system is **64 bits**).

After that, install the package using [GDebi]("https://launchpad.net/gdebi"): run GDebi, then select **File**, then **Open**, then select the .DEB package that you've just downloaded, hit the **Open** button and then the **Install Package** button. GDebi will ask for the superuser password. Provide that password and hit Enter / Return. The package will be installed. Now try running Gnome Subtitles again.

If you don't have GDebi yet, you can install it by running this command in the shell terminal:
```
sudo apt-get install gdebi
```

If you don't want to install GDebi and/or prefer to install the DEB package directly in the shell terminal, all you have to do is to run [dpkg]("https://wiki.debian.org/Teams/Dpkg"). For instance, assuming that you downloaded the 32 bits package and put it into **/home/bogus/Download/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1~trusty2_i386.deb**, in order to install it via dpkg all you have to do is to run this command:
```
sudo dpkg -i /home/bogus/Download/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1~trusty2_i386.deb
```

...and you're good to go: just try running Gnome Subtitles again and openning a video for playback.

---

### Post by noup on 2014-10-16
Hi guys,

Just to let you know, I've added a 14.04 build for Gnome Subtitles 1.3 to the project PPA:
```
ppa:pedrocastro/ppa
```

Hope this helps. Please tell me if you run into any issue.

Cheers
Pedro

---

### Post by sampayu on 2014-10-17
Hi, Pedro, thank you! It worked.\\:D/

To the other users (mostly the GNU/Linux beginners / basic users), here's the step-by-step shell commands in order to uninstall your former version of Gnome Subtitles and use the PPA above to install the newest version (nowadays it's version **1.3**) of Gnome Subtitles:

**1**) Uninstall your previous version of Gnome Subtitles:
```
sudo apt-get remove gnome-subtitles gstreamer0.10-ffmpeg
```

**2**) Add the Pedro Castro's PPA:
```
sudo apt-add-repository ppa:pedrocastro/ppa
```

**3**) Install the current version of Gnome Subtitles:
```
sudo apt-get update && sudo apt-get check && sudo apt-get install gnome-subtitles
```

---

### Post by jan4 on 2014-11-06
> **sampayu said:**
> Hi, Pedro, thank you! It worked.\\:D/

To the other users (mostly the GNU/Linux beginners / basic users), here's the step-by-step shell commands in order to uninstall your former version of Gnome Subtitles and use the PPA above to install the newest version (nowadays it's version **1.3**) of Gnome Subtitles:

**1**) Uninstall your previous version of Gnome Subtitles:
```
sudo apt-get remove gnome-subtitles gstreamer0.10-ffmpeg
```

**2**) Add the Pedro Castro's PPA:
```
sudo apt-add-repository ppa:pedrocastro/ppa
```

**3**) Install the current version of Gnome Subtitles:
```
sudo apt-get update && sudo apt-get check && sudo apt-get install gnome-subtitles
```

Excellent! This worked like a charm :) Kudos!!

---

### Post by sampayu on 2014-11-06
> **jan4 said:**
> Excellent! This worked like a charm :) Kudos!!

Glad it worked. You're welcome.:)

---

