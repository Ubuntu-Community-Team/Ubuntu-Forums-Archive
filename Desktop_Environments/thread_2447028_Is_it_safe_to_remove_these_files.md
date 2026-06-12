---
title: "Is it safe to remove these files?"
date: 2020-07-11
forum: Desktop Environments
---

### Post by yapidumoac on 2020-07-11
The following packages were automatically installed and are no longer required:

  atomicparsley fonts-freefont-ttf freepats libaom0 libaribb24-0 libavresample4 libavutil56 libbasicusageenvironment1 libcgi-fast-perl
  libcgi-pm-perl libclass-method-modifiers-perl libcodec2-0.8.1 libcodec2-0.9 libcommon-sense-perl libde265-0 libdirectfb-1.7-7
  libdvbpsi10 libebml4v5 libev-perl libfcgi-perl libfluidsynth2 libgroupsock8 libinstpatch-1.0-2 libio-socket-socks-perl
  libjs-prettify libkate1 liblept5 liblilv-0-0 liblivemedia62 libmatroska6v5 libmfx1 libmicrodns0 libminizip1 libmjpegutils-2.1-0
  libmojo-server-fastcgi-perl libmojolicious-perl libmpcdec6 libmpeg2encpp-2.1-0 libmplex2-2.1-0 libmysofa1 libofa0
  libopenmpt-modplug1 libplacebo4 libpocketsphinx3 libpostproc55 libprotobuf-lite10 libproxy-tools libqt5x11extras5 librabbitmq4
  libresid-builder0c2a librole-tiny-perl libsdl-image1.2 libserd-0-0 libsidplay2 libsord-0-0 libsoundtouch1 libsphinxbase3
  libsratom-0-0 libsrt1 libsrt1-gnutls libsrtp2-1 libswresample3 libswscale5 libtesseract4 libtinyxml2-6a libupnp6
  libusageenvironment3 libusrsctp1 libvidstab1.1 libvlc-bin libvlc5 libvlccore9 libvo-aacenc0 libwildmidi-config libwildmidi2
  libx265-179 libx265-192 libxcb-xv0 libxml-libxml-perl libxml-namespacesupport-perl libxml-sax-base-perl libxml-sax-expat-perl
  libxml-sax-perl libxml-simple-perl libzbar0 linux-headers-4.15.0-101 linux-headers-4.15.0-101-generic linux-headers-4.15.0-106
  linux-headers-4.15.0-106-generic linux-image-4.15.0-101-generic linux-image-4.15.0-106-generic linux-modules-4.15.0-101-generic
  linux-modules-4.15.0-106-generic linux-modules-extra-4.15.0-101-generic linux-modules-extra-4.15.0-106-generic
  ungoogled-chromium-common ungoogled-chromium-sandbox vlc-bin vlc-data vlc-l10n vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba
  vlc-plugin-skins2 vlc-plugin-video-output vlc-plugin-video-splitter vlc-plugin-visualization

Use 'apt autoremove' to remove them.

---

### Post by Frogs Hair on 2020-07-11
Did this message follow and update and do you have any 3rd Party PPA's installed? PPA's and non Ubuntu repositories can cause autoremove problems.Old kernels show up as auto-removable on my system so I don't think that's  unusual it's the other packages I would be cautious about.

---

### Post by yapidumoac on 2020-07-11
> Did this message follow and update and do you have any 3rd Party PPA's installed?

Yes, there are a number of third party PPAs. Think I should do a recent full back-up. Or a total new install.

---

### Post by ajgreeny on 2020-07-11
And have you uninstalled some applications which were previously installed as .debs, such as the PPA version of get_iplayer which has now disappeared, and have now replaced them with either a snap version, or manually installing it as shown at the get-iplayer site [https://github.com/get-iplayer/get_iplayer/wiki/unix?](https://github.com/get-iplayer/get_iplayer/wiki/unix?)

Snaps contain all the dependencies needed for an application in the snap package as I understand it, so anything that was installed as a dependency of the .deb version will no longer be needed, assuming nothing else requires it.

---

### Post by yapidumoac on 2020-07-11
> And have you uninstalled some applications which were previously installed as .debs ..

Yes, various apps .. I'll do a full install .. thanks for the quick responce ...

---

### Post by GhX6GZMB on 2020-07-11
Is it safe? In my painful experience: no. When you get an autoremove list as big as you have, something has gone seriously wrong. You've apparently removed something else before which has broken a lot of dependencies.

---

### Post by yapidumoac on 2020-07-11
> Is it safe? In my painful experience: no. When you get an autoremove  list as big as you have, something has gone seriously wrong. You've  apparently removed something else before which has broken a lot of  dependencies.

Yes some app complained about the wrong python version. I tried manually correcting that and broke Synaptic. Then &#8220;Software Updater&#8221; wiped out a lot of my manually installed apps.

---

### Post by ajgreeny on 2020-07-12
This is one good reason for using the terminal or synaptic when carrying out these operations in my opinion; you get good warnings about everything that is going to happen before it happens so can stop, if you wish to, and think again, or ask questions as you have here.

I don't think I have ever used the software-updater, always using synaptic when I was new to Ubuntu, and now generally the terminal, though even when using synaptic I always set it to show actions inn the terminal window.
I find synaptic most useful when searching for specific packages that are not seen in the software-centre, gnome-software, or whatever it's now called.

---

### Post by yapidumoac on 2020-07-16
> This is one good reason for using the terminal or synaptic when carrying out these operations ..

Curiously enough, I just did &#8216;apt-get update&#8217;, &#8216;apt-get upgrade&#8217;,&#8216;apt-get dist-upgrade&#8217; and the original errors have disappeared. Except for this:

&#8220;E: The repository 'http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu bionic InRelease' is no longer signed.&#8221;

As someone above mentioned, get-iplayer is moving to a snap package.

---

