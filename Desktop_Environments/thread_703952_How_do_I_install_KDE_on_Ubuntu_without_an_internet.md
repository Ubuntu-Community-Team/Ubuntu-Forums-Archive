---
title: "How do I install KDE on Ubuntu without an internet connection?"
date: 2008-02-21
forum: Desktop Environments
---

### Post by deepblue_tiano on 2008-02-21
Hello I am using ubuntu 7.10 Gutsy Gibbon.. How to install KDE desktop in my box i dont have internet connection in our home so i downloaded kubuntu 7.10 to get the KDE installer but when i type in terminal sudo apt-get install kubuntu-desktop no luck it cannot found.. I've already added the kubuntu installer as a repository..Is that mean that the package is not in kubuntu? I really appreciate your help guys..thanks

---

### Post by aysiu on 2008-02-21
If it's the Desktop CD, you can't add Kubuntu without an internet connection.

If it's the Alternate CD, then ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` should work.

---

### Post by deepblue_tiano on 2008-02-21
What do you mean by that desktop cd? Desktop edition of kubuntu or ubuntu? I am Using ubuntu desktop version of ubuntu.. I have installers of kubuntu also desktop version

---

### Post by aysiu on 2008-02-21
> **deepblue_tiano said:**
> What do you mean by that desktop cd? Desktop edition of kubuntu or ubuntu? I am Using ubuntu desktop version of ubuntu.. I have installers of kubuntu also desktop version
If you look at [the Kubuntu download page](http://ubuntu.media.mit.edu/ubuntu-releases/kubuntu/gutsy/), there are various types of CDs. The relevant ones in this discussion are the Desktop CD and the Alternate CD, bolded below: > Name	Last Modified	Size	Type
Parent Directory/	 	-  	Directory
source/	2007-Oct-11 14:01:23	-  	Directory
.htaccess	2007-Oct-18 03:53:28	2.9K	application/octet-stream
FOOTER.html	2007-Oct-18 03:53:28	0.1K	text/html
HEADER.html	2007-Oct-18 03:53:28	3.3K	text/html
MD5SUMS	2007-Oct-18 03:53:37	0.2K	application/octet-stream
MD5SUMS.gpg	2007-Oct-18 03:53:37	0.1K	application/octet-stream
kubuntu-7.10-alternate-amd64.iso	2007-Oct-16 17:57:05	693.7M	application/x-iso9660-image
kubuntu-7.10-alternate-amd64.iso.torrent	2007-Oct-18 03:53:23	27.3K	application/x-bittorrent
**kubuntu-7.10-alternate-i386.iso**	2007-Oct-16 17:58:02	697.4M	application/x-iso9660-image
kubuntu-7.10-alternate-i386.iso.torrent	2007-Oct-18 03:53:28	27.4K	application/x-bittorrent
kubuntu-7.10-desktop-amd64.iso	2007-Oct-16 18:28:15	696.6M	application/x-iso9660-image
kubuntu-7.10-desktop-amd64.iso.torrent	2007-Oct-18 03:51:12	27.4K	application/x-bittorrent
**kubuntu-7.10-desktop-i386.iso**	2007-Oct-16 18:28:32	697.1M	application/x-iso9660-image
kubuntu-7.10-desktop-i386.iso.torrent	2007-Oct-18 03:51:17	27.4K	application/x-bittorrent You can use the Alternate CD to add Kubuntu to Ubuntu. You *cannot* use the Desktop CD to add Kubuntu to Ubuntu.

---

### Post by deepblue_tiano on 2008-02-21
Oh I see.. I didnt know about the alternate cd before.. Even i am using ubuntu desktop version i install kde using that alternate cd?

---

### Post by aysiu on 2008-02-21
> **deepblue_tiano said:**
> Oh I see.. I didnt know about the alternate cd before.. Even i am using ubuntu desktop version i install kde using that alternate cd?
Well, I guess the question is--do you want to *install* Kubuntu over (i.e., in place of) your current Ubuntu installation, or do you want to *add* Kubuntu on top of your current Ubuntu installation?

If it's the former, you can use the Desktop CD. If it's the latter, you have to use the Alternate CD... or a fast internet connection.

---

### Post by deepblue_tiano on 2008-02-21
sorry forget that question..in case of  XFCE desktop, can I also install it in my ubuntu? Do i need to download an alternate cd of xubuntu which i believe xubuntu uses XFCE?

---

### Post by aysiu on 2008-02-21
> **deepblue_tiano said:**
> sorry forget that question..in case of  XFCE desktop, can I also install it in my ubuntu? Do i need to download an alternate cd of xubuntu which i believe xubuntu uses XFCE?
Yes, same deal for Xubuntu.

If you want to add it to your existing installation, you need the Xubuntu Alternate CD.

If you want to replace your existing installation, you can use either the Xubuntu Alternate CD or the Xubuntu Desktop CD.

---

### Post by deepblue_tiano on 2008-02-22
Thank you bro.. Where you from? and how long your using ubuntu? Another question bro is installing a nvidia driver  and codecs for ubuntu.. coz now i cant play mp3's and movies,...

---

### Post by aysiu on 2008-02-22
> **deepblue_tiano said:**
> Thank you bro.. Where you from? and how long your using ubuntu? Another question bro is installing a nvidia driver  and codecs for ubuntu.. coz now i cant play mp3's and movies,...
I'm from the US, and I've been using Ubuntu for a little over two and a half years.

I'll be honest with you--Ubuntu without an internet connection is pretty painful. You might find [APTonCD](http://aptoncd.sourceforge.net/) useful, or, if you need a lot of proprietary codecs, you might want to download [Linux Mint](http://linuxmint.com/).

---

### Post by deepblue_tiano on 2008-02-22
Yes i know that..but it was challenging... I just want to try linux environment...Linux mint is another operating system of linux?

---

### Post by deepblue_tiano on 2008-02-26
Hello aysiu..thanks ive intalled KDE in my ubuntu.. But something change, when you open your computer loader is kubuntu not ubuntu..Is that possible that it only change is the desktop when is select session for kde..but not the loading image which is kubuntu? and How can reinstall my ubuntu without formating its ext3 and swap partition?

---

