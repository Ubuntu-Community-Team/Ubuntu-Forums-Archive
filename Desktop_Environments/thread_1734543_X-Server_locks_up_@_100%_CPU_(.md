---
title: "X-Server locks up @ 100% CPU :("
date: 2011-04-20
forum: Desktop Environments
---

### Post by frikker on 2011-04-20
Hi everyone. Over the past two weeks my laptop has started locking up at random. I thought maybe it was a thermal issue, because I have an upgraded hard drive (put in 2 years ago) and once a month or so I might get a heat related lockup. I keep my fans running at high speed and the laptop elevated now and don't typically have an issue.

The freezing has started to become a daily occurrence now, and yesterday it locked up three times. I am able to move my mouse (unlike thermal lockups where everything goes down) but unable to click anything. The entire display freezes, and my cpu monitor doesn't continue to update.

I finally ssh'd into my laptop and was surprised to see it responding just fine. htop showed that my X-server was at 100%. When I killed it, X restarted automatically and promped me to log in. Everything is fine after this until the next lockup.

When I don't have access to ssh I have to hard-shutoff the laptop. That can't be good on this 5 year old macbook.

I have done my system updates in the past two weeks that may have triggered this, but I don't remember anything specifically. I've tried all versions of my kernel that are installed but nothing has helped.

I have the intel video and have not had problems with it up until now.

2$ uname -a
Linux macbook 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

3$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Can anyone suggest something to try? I'm not sure how to go back to older versions of the the video drivers, but I'm not even sure if that is the issue. I did add the following to /etc/apt/sources.lst after the lockups started occuring:
```

# X
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main #X-Updates PPA
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main #X-Updates PPA

```and did a full update, but this hasn't helped.

I'm running Ubuntu 10.04 LTS

Thank you. Hopefully this doesn't lock up before I post it.

---

### Post by IanWood on 2011-04-20
> **frikker said:**
> Hi everyone. Over the past two weeks my laptop 
When I don't have access to ssh I have to hard-shutoff the laptop. That can't be good on this 5 year old macbook.

.

See [http://ubuntuforums.org/showthread.php?t=1625119](http://ubuntuforums.org/showthread.php?t=1625119) 

You may not have to ssh onto it. I use ctrl-alt-F1 to log into my own machine when a similar thing happens to my machine. 

I don't know why it happens but this method can be used to fix it.

---

### Post by frikker on 2011-04-20
Thanks. I've tried with no luck with the alt+f1, but i'll try again. I also don't have a sysReq key on this keyboard so i can't raise any skinny elephants.

that link looks promising. thanks!

---

### Post by frikker on 2011-04-20
It has been suggested that perhaps it is Java that is messing up X. Now that I think about it, I have been doing a lot more Java programming in the last week. I always use Eclipse when I'm not doing Java, as well.

I haven't had a lockup today so far and I don't have eclipse open. Perhaps this is the issue?

It has been suggested to add "-Dsun.awt.disablegrab=true" to my VM params to see if this helps. We'll see.

---

### Post by IanWood on 2011-04-21
I am a Java developer and always have some Java programs running. I have also noticed that X locks up when I start a Java program sometimes. 

Also, its ctrl-alt-F1 not just alt-F1 that I use to log in again to my machine. 

I will give that arg a whirl, seems a good idea.

Cheers

Ian

---

### Post by frikker on 2011-04-21
Hmm. So the issue seems to happen less often without java running, but it still has locked up on me twice today compared to about 5 times yesterday with eclipse up.

Any other suggestions? I'd hate to do a complete re-install. I also don't have access to cntrl+alt+f1, but that might be because my macbook's function key might not work with with X hanging, it works fine otherwise.  although i think what is happening is that all keyboard input is locked up, including cntrl+alt+f1

should i try rolling back intel-video drivers? is there a log file i can examine, perhaps? dmesg doesn't help much from what i can tell.

---

