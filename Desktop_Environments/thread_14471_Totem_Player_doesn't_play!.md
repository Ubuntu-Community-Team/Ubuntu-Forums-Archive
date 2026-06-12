---
title: "Totem Player doesn't play!"
date: 2005-02-07
forum: Desktop Environments
---

### Post by robtotheb on 2005-02-07
Made the mistake of wiping my computer and reinstalling Ubuntu at the weekend.  After hours of trying the tutorials and HOWTO's to get totem to play avi's xvid mpegs etc Im out of ideas.  It just comes up with the message - "Failed to open; reason unknown"

Got it working before so why not now?

---

### Post by Razvan on 2005-02-07
mhhh...i dont like totem anyway

i use mplayer

---

### Post by subjectdenied on 2005-02-07
sudo apt-get intall totem-xine (package totem uses the gstreamer-backend which doesn't work with some windows-media without installing some plugins)
  
  download the win32-codecs vom [www.mplayer.hu]("http://www.mplayer.hu")  (and copy them to /usr/lib/win32) or add the marillat-repository to your apt-sources and get the package with apt-get
  
 totem isn't able to play all files at the moment, but if you get the gst-ffmpeg plugin (apt-get install ffmpeg) you should be able to play some win32-media-files with the gstreamer-version of totem

---

### Post by robtotheb on 2005-02-07
get this when i apt totem-xine

"Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  totem-xine: Depends: dbus-1 (>= 0.22+cvs.200412122010) but 0.22-1ubuntu2 is to be installed
              Depends: libatk1.0-0 (>= 1.9.0) but 1.8.0-1ubuntu2 is to be installed
              Depends: libgconf2-4 (>= 2.9) but 2.8.1-0ubuntu1 is to be installed
              Depends: libgcrypt11 but it is not installable
              Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
              Depends: libgnomevfs2-0 (>= 2.9.2) but 2.8.2-0ubuntu1 is to be installed
              Depends: libgnutls11 (>= 1.0.16) but it is not installable
              Depends: libgpg-error0 (>= 1.0) but 0.7-1 is to be installed
              Depends: libgtk2.0-0 (>= 2.6.0) but 2.4.10-1ubuntu1 is to be installed
              Depends: libhowl0 (>= 0.9.8-1) but it is not installable
              Depends: libnautilus-burn1 but it is not installable
              Depends: libnautilus-extension1 (>= 2.9.1) but it is not installable
              Depends: libpango1.0-0 (>= 1.8.0) but 1.6.0b-0ubuntu1 is to be installed
              Depends: libstartup-notification0 (>= 0.8) but 0.7-0ubuntu1 is to be installed
              Depends: libtasn1-2 (>= 0.2.8) but 0.2.7-2 is to be installed
              Depends: libxml2 (>= 2.6.17) but 2.6.11-3ubuntu1.1 is to be installed
E: Broken packages"

I already have the win32-codecs installed.

---

### Post by robtotheb on 2005-02-07
I haven't found a way to install mplayer that works!

---

### Post by rohandhruva on 2005-02-08
Install from CVS source

---

### Post by brainstuff on 2005-02-08
[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

All you need! Follow it to the letter, but replace the older filenames with the latest versions that you'll no doubt want to be getting from here:

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

cheers
brain

*proud to have conquered fear of the terminal through the installation of  mplayer*

---

### Post by robtotheb on 2005-02-08
Had already installed it.  When I try to play some thing I get the message Error opening/initializing the selected video_out (-vo) device.

---

### Post by brainstuff on 2005-02-08
Complete guesswork going on windoze experience, but it sounds like it's not happy with the video driver or some other application is using the video overlay?

---

### Post by Jad on 2005-02-08
got this problem before, solved with gxine
sudo apt-get install gxine
Don't forget the codex

---

### Post by robtotheb on 2005-02-09
cant install that 

"The following packages have unmet dependencies:
  gxine: Depends: libsmjs1 but it is not installable
E: Broken packages"

---

