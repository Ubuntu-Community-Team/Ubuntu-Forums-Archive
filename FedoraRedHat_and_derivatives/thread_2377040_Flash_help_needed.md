---
title: "Flash help needed"
date: 2017-11-08
forum: Fedora/RedHat and derivatives
---

### Post by sports fan Matt on 2017-11-08
So I divided my partition in two with Gnome CentOS as the second option but can't seem to get flash to work in either chromium or Firefox.  I was trying to view a Twitch stream.  On Firefox, I can hear audio from Iheart radio though.  

Here is what I've tried.
# rpm -ivh [http://linuxdownload.adobe.com/adobe-re](http://linuxdownload.adobe.com/adobe-re) ... noarch.rpm
# rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux
yum update
# yum install flash-plugin nspluginwrapper alsa-plugins-pulseaudio libcurl
sudo yum install flash-plugin alsa-plugins-pulseaudio libcurl

Any ideas are welcome.

just an update.  Flash works on Youtube and audio and videos play.  I can hear sound on Twitch but can see no video.

---

### Post by ajgreeny on 2017-11-08
Flash is not needed and most people do not use flash for youtube any more but html5; are you sure your system is really using flash for them?

---

### Post by sports fan Matt on 2017-11-08
I'm honestly not sure. I would think that if html did not work, I wouldn't be able to hear audio or see video in Firefox or Chrome?

---

### Post by ajgreeny on 2017-11-08
Right click in a youtube video window and tell us what you see; if using flash you will see something about **flash settings**, if html5 you will see other items in a simple menu, including, at the top "**copy video URL**"

---

### Post by sports fan Matt on 2017-11-08
I do see "copy video url"

---

### Post by ajgreeny on 2017-11-08
So as I expected you are using html5 for youtube; nothing to do with flash.

I do not know CentOS so am unable to give you more info about how to install it, but I presume you have looked at the CentOS forums; [https://www.centos.org/forums/](https://www.centos.org/forums/)

What did you find there?

---

### Post by sports fan Matt on 2017-11-08
Basically the same things we walked through except instead of sudo, they use yum to install. If I'm thinking right, if I can hear the audio but not see the video, it's something to do with the video playback I'm assuming ?.

---

