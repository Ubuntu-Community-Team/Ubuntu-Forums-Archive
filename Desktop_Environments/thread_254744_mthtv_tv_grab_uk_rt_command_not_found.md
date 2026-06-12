---
title: "mthtv: tv_grab_uk_rt: command not found"
date: 2006-09-10
forum: Desktop Environments
---

### Post by rasti121 on 2006-09-10
Hi,

on ubuntu 6.06, KVER=2.6.15-26-amd64-generic, I did apt-get install mythtv. when I try to create channel for UK TV (from mythtv-setup) I get in terminal window:

new DataDirect_config source == 1
2006-09-10 18:31:17.683 Please wait while MythTV retrieves the list of available channels
sh: tv_grab_uk_rt: command not found
2006-09-10 18:31:17.745 tv_grab_uk_rt --config-file '/home/rasti/.mythtv/tv.xmltv' --configure
2006-09-10 18:31:17.746 exited with status 32512

when I check it, file doesn't exist. I spent couple of hours trying to figure out how to get the file, but following all guides/docs it seems that file is installed implicitely with mythtv, I also apt-get remove and install mythtv couple of times without any success.

Any more ideas how to get around this will be appreciated.

---

### Post by FakeOutdoorsman on 2006-09-10
I did a google search of "[exited with status 32512]("http://www.google.com/search?sourceid=navclient-ff&ie=UTF-8&rls=GGGL,GGGL:2006-32,GGGL:en&q=%22exited+with+status+32512%22")" and found a few forums that might have your answer.
[URL="http://www.hauppauge.co.uk/board/showthread.php?t=5932"]
tv_grab_uk_rt is a file of no size[/URL]

[mythtv-setup probs]("http://forums.dvbowners.com/lofiversion/index.php/t2631.html")

---

### Post by rasti121 on 2006-09-10
Found it... if anybody ever needs it
You must install this package which doesn't come with mythtv to support xml feeds:


apt-get install xmltv-util

---

