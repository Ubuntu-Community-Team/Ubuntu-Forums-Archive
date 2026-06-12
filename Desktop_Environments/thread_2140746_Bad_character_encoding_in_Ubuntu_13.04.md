---
title: "Bad character encoding in Ubuntu 13.04"
date: 2013-04-30
forum: Desktop Environments
---

### Post by play3man on 2013-04-30
I have Ubuntu 13.04 from release, fresh installation. System language is Slovak and character encoding is everywhere correct except numbers in Skype and VLC (only in settings, subtitles are encoded correctly)

In Skype are like this:

[&#1633;&#1641;:&#1633;&#1635;:&#1633;&#1635;]
[&#1633;&#1641;:&#1633;&#1635;:&#1634;&#1639;]
[&#1633;&#1641;:&#1633;&#1635;:&#1636;&#1635;]
[&#1633;&#1641;:&#1633;&#1636;:&#1635;&#1635;]

And in VLC

&#1638; or &#1639;

So it is the same encoding like in Skype... 

Here is a terminal output

play3man@play3man-Extensa-5630:~$ locale
LANG=sk_SK.UTF-8
LANGUAGE=sk:en
LC_CTYPE="sk_SK.UTF-8"
LC_NUMERIC=sk_SK.UTF-8
LC_TIME=sk_SK.UTF-8
LC_COLLATE="sk_SK.UTF-8"
LC_MONETARY=sk_SK.UTF-8
LC_MESSAGES="sk_SK.UTF-8"
LC_PAPER=sk_SK.UTF-8
LC_NAME=sk_SK.UTF-8
LC_ADDRESS=sk_SK.UTF-8
LC_TELEPHONE=sk_SK.UTF-8
LC_MEASUREMENT=sk_SK.UTF-8
LC_IDENTIFICATION=sk_SK.UTF-8
LC_ALL=
play3man@play3man-Extensa-5630:~$

---

### Post by play3man on 2013-05-01
Nobody knows how to fix it?

---

### Post by dankojoffrey on 2013-05-17
I had same issue with qbittorrent, clementine and others...  system language is english as well as keyboard, but some apps shows up in slovak...

Output:
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=sk_SK.UTF-8
LC_TIME=sk_SK.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=sk_SK.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=sk_SK.UTF-8
LC_NAME=sk_SK.UTF-8
LC_ADDRESS=sk_SK.UTF-8
LC_TELEPHONE=sk_SK.UTF-8
LC_MEASUREMENT=sk_SK.UTF-8
LC_IDENTIFICATION=sk_SK.UTF-8
LC_ALL=

I had different language settings (english) and regional settings (slovak). I changed slovak to english, logged out and in and now it works fine... Maybe something wrong with slovak translation...

---

### Post by uwabaki on 2013-06-02
yes, had the same issue, changing regional settings to english fixs it

---

### Post by Inoki on 2013-06-15
A bug report has been filed to fix this: [https://bugs.launchpad.net/ubuntu-translations/+bug/1191241](https://bugs.launchpad.net/ubuntu-translations/+bug/1191241)

---

### Post by tomasz_svk on 2013-06-18
Workaround here: [https://bbs.archlinux.org/viewtopic.php?pid=1215057](https://bbs.archlinux.org/viewtopic.php?pid=1215057)

---

### Post by Inoki on 2013-06-19
> **tomasz_svk said:**
> Workaround here: [https://bbs.archlinux.org/viewtopic.php?pid=1215057](https://bbs.archlinux.org/viewtopic.php?pid=1215057)
That won't help it, as I don't have any locale.gen file on my computer. Adding this line into terminal: "sudo gedit /etc/default/locale.gen" only brings up a blank file. Searching for it manually also.

---

### Post by Inoki on 2013-06-23
This [**workaround**]("http://askubuntu.com/questions/310990/borked-encoding-in-ubuntu-13-04-for-slovak-language") fixed it for me.

---

