---
title: "Fujitsu fi-60f Scanner not working after few minutes"
date: 2014-02-06
forum: Desktop Environments
---

### Post by karikalan2 on 2014-02-06
In my machine I have loaded Ubuntu 12.04 LTS in which i have attached  Fujitsu fi-60f scanner. It  works fine for  first few minutes with  simple scan tool or xsane tool. After few minutes the scanner is not  recognized . The error  message displayed is " scanner not found attach  the scanner "  Only if I resart my machine the scanner is recognized. 

I have Configured SANE for scanner.

My mother board Chip set detail is Intel HM 76.

Can any one help me to over come this issue and make the scanner always recognizable.

Thanks in advance.

Karikalan

---

### Post by Kirboosy on 2014-02-06
If no one has already told you let me be the first to say, Welcome to the forums! :D

What packages have you installed in order to get to your current semi-working buggy state?

There is a package I found called [sane-epjitsu]("http://manpages.ubuntu.com/manpages/karmic/man5/sane-epjitsu.5.html") that looks like it supports your scanner. I'm not sure if its still in the repo but one can only hope.

```
sudo apt-get install sane-epjitsu
```

I also found this thread on [Fixing a Fujitsu Snapchat]("http://ubuntuforums.org/showthread.php?t=1461915") scanner. I know its a different scanner model but perhaps since its the same manufacturer similar steps can be taken. I would like to direct your attention to [post 8]("http://ubuntuforums.org/showthread.php?t=1461915&p=11448844&viewfull=1#post11448844") in particular.

Hope that helps!
~Caboose

---

