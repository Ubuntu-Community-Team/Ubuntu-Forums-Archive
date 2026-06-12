---
title: "codecs"
date: 2008-10-11
forum: Fedora/RedHat and derivatives
---

### Post by mr.farenheit on 2008-10-11
whats the easiest free alternative to installing audio and video codecs in fedora?

---

### Post by mthei on 2008-10-12
[http://rpm.livna.org/rlowiki/](http://rpm.livna.org/rlowiki/)


However, as much as I love Fedora, I found that some of Livna's packages such as some XMMS plugins and VLC were very buggy since Fedora 8. However, it's the best repository offered until RPMFusion comes out.

---

### Post by exploder on 2008-10-15
Look on the Fedora forum, there are two different scripts that will install all of the codecs and some additional fixes. Getting multimedia working in Fedora is real easy now.

---

### Post by Antman on 2008-10-20
Sorry, missed this thread. Here is the contents of my script to give all of my Fedora boxes: Media Codecs, Flash, MS Fonts, and a little extra.
```
rpm -ivh http://rpm.livna.org/livna-release-9.rpm
rpm -Uvh http://linuxdownload.adobe.com/adobe-release/adobe-release-i386-1.0-1.noarch.rpm
yum -y install yum-fastestmirror gstreamer-plugins-bad gstreamer-plugins-bad-extras gstreamer-plugins-ugly gstreamer-ffmpeg flash-plugin libflashsupport nautilus-open-terminal unrar wget libdvdcss mplayer
cd /tmp/
wget http://corefonts.sourceforge.net/msttcorefonts-2.0-1.spec
yum -y install rpm-build cabextract
rpmbuild -bb msttcorefonts-2.0-1.spec
rpm -ivh /usr/src/redhat/RPMS/noarch/msttcorefonts-2.0-1.noarch.rpm --nodeps
cd /tmp/
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
tar xfvj all-20071007.tar.bz2
mkdir /usr/lib/codecs/
cp all-20071007/* /usr/lib/codecs/
ln -s /usr/lib/codecs/ /usr/lib/win32
```

---

