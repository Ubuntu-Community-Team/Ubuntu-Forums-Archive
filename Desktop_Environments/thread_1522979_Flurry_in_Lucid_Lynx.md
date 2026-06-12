---
title: "Flurry in Lucid Lynx"
date: 2010-07-02
forum: Desktop Environments
---

### Post by minagica on 2010-07-02
Hi! My all time fave screensaver is Flurry. I had it back when I had Windows, I tried getting it now that I switched to Linux: I'm too much of a noob to succeed. I read that it was disabled because it wouldn't run well and that some updates fixed the problem but it hasn't been rereleased. And then someone on this forum ([http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6930123](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6930123) and [http://ubuntuforums.org/showthread.php?t=245158](http://ubuntuforums.org/showthread.php?t=245158)) said that if we have the old files we can just place them in the old folders and they will work. I must be missing something because Flurry is still not working for me. Could someone please help? Thanks so much!

---

### Post by brayanhabid on 2010-08-16
Hi. Flurry is my favorite screensaver. I use it on windows, mac and linux.

I was missing it in lucid (and i missed glines too, but that's already solved). So I just did some research, and I found out that there is a package called xscreensaver-gl-extra, which has some 60 to 70 screensavers, including flurry

so, you can do on a terminal window a

sudo apt-get install xscreensaver-gl-extra

it'll install the screensavers and a library (libgle3) needed to have them working. Copying the files from other installed versions doesn't always work, as you may or may not have the library installed.

---

