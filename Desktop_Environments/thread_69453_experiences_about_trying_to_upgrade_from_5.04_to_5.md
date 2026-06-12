---
title: "experiences about trying to upgrade from 5.04 to 5.10: failed because of firefox"
date: 2005-09-26
forum: Desktop Environments
---

### Post by beewer on 2005-09-26
Hi.

I tried to upgrade my Kubuntu 5.04 to 5.10 yesterday. I had problems trying to upgrade my firefox to 1.07 in my 5.04 but I managed to do upgrade by uninstalling firefox and then reinstalling it.

I started my editing sources.list, apt-get update apt-get dist-upgrade (yes, I killed kdm before dist-upgrade). Everything went ok until dist-upgrade stopped on firefox. I don't have exact error message but problem had something to do with dpkg and depedencies.

I'm sorry that I don't have exact error message but my  system was in a mixed state and I couldn't do copy-paste and decided to leave it because it was already so late.

I tried to apt-get remove mozilla-firefox but it didn't work, maybe because dist-upgrade was not run fully. Error message said that I should run "apt-get install -f". At the moment apt-get install -f is running at that Kubuntu machine. I will post more of my experiences later.

---

### Post by beewer on 2005-09-26
Ok, with "apt-get install -f" things get bit further. But after message Setting up kubuntu-desktop (0.52) I get following error message:
Errors were encountered while processing:
postfix
lsb-core
lsb-graphics
lsb-cxx
lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)

After this I did apt-get update and apt-get dist-upgrade once more and got following error message:
Errors were encountered while processing:
/var/cache/apt/archives/firefox_1.0.7-0ubuntu15_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

And dist-upgrade stopped and I system stays in mixed up state :???: 

Any ideas how to proceed?

---

### Post by beewer on 2005-09-27
Ok, googled a bit and decided to purge problematic packages with dpkg

dpkg --purge postfix
dpkg --purge mailx
dpkg --purge mutt
dpkg --purge lsb-core
dpkg --purge lsb-graphics
dpkg --purge lsb-cxx
dpkg --purge lsb

After this apt-get dist-upgrade went ok. After it I installed packages listed above and mozilla-firefox and mozilla-mplayer

apt-get install mozilla-firefox
apt-get install mozilla-mplayer

And everything seemed to went ok. 

Unfortunately I cannot test KDE since I wasn't physically at the place. But I will test it this evening.

---

### Post by beewer on 2005-09-27
It seems that my Kubuntu 5.10 box works now pretty ok. I have two video cards, agp geforce 256 and pci s3. I had to remove s3, because othervise Kubuntu tried to use it as default video card instead of geforce. 

After removal of s3 I ran dpkg-reconfigure xserver-xorg.

I still have some error messages at boot but everything seems to work.

---

