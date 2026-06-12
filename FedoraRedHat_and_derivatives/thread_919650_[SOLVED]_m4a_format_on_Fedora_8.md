---
title: "[SOLVED] m4a format on Fedora 8"
date: 2008-09-14
forum: Fedora/RedHat and derivatives
---

### Post by motoperpetuo on 2008-09-14
Does anyone know what I need to install to get .m4a files (the native iTunes format) to play on Fedora 8? I use Mint on my main computer now, so I haven't really had to worry about multimedia codecs in a while, but I decided to install Fedora on an old computer in an attempt to get familiar with it, and I can't even find any information on how to get .m4a files to play.

I got them playing on Ubuntu some time ago, but I don't remember what I did. I'm guessing it would be a different package on Fedora anyway, because Fedora is rpm-based, correct?

Better yet, is there something for Fedora that just installs all the common multimedia codecs?

---

### Post by Antman on 2008-09-14
> **motoperpetuo said:**
> 
Better yet, is there something for Fedora that just installs all the common multimedia codecs?
If you really must play proprietary codecs in Fedora; first enable the Livna and Adobe repos.
As Root:
```
rpm -ivh http://rpm.livna.org/livna-release-9.rpm
rpm -Uvh http://linuxdownload.adobe.com/adobe-release/adobe-release-i386-1.0-1.noarch.rpm
```
Then install these tidbits:
```
yum -y install yum-fastestmirror gstreamer-plugins-bad gstreamer-plugins-bad-extras gstreamer-plugins-ugly gstreamer-ffmpeg flash-plugin libflashsupport nautilus-open-terminal unrar
```
To also get the MS Codecs do this (also as root):
```
cd /tmp/
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
tar xfvj all-20071007.tar.bz2
mkdir /usr/lib/codecs/
cp all-20071007/* /usr/lib/codecs/
ln -s /usr/lib/codecs/ /usr/lib/win32
```
This is stuff from my media setup script I made to install codecs and such on all of my Fedora boxes after a fresh install.
Enjoy... :guitar:

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Here is what "apt-cache show" says about the version medibuntu has of amarok :

"""
 This package is built with Itunes AAC-LC (.m4a) support enabled.
 Therefore, it is in Medibuntu as it might violate patents.
"""

So for ubuntu, as I have medibuntu enabled and am using amarok, I guess I automagically have m4a support.

So I guess the answer would be fedora specific and you should ask a fedora specific forum.

Edit: oh, he asked in a fedora section of the ubuntu forums it seems.

---

### Post by motoperpetuo on 2008-09-14
hey, that worked great, antman. i am now listening to music that i foolishly ripped to m4a years ago, before i knew that it was a stupid format.

one question, is it all the gstreamer plugins that provide m4a support? (i'm still learning here.)

---

### Post by Antman on 2008-09-14
> **motoperpetuo said:**
> hey, that worked great, antman. i am now listening to music that i foolishly ripped to m4a years ago, before i knew that it was a stupid format.

one question, is it all the gstreamer plugins that provide m4a support? (i'm still learning here.)
Yes I **think** (can't recall for sure) that the gstreamer stuff gives you m4a support. I normally just install all the other stuff just to give my fedora media boxes full codec capabilities.

---

