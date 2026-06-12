---
title: "Rpm"
date: 2006-04-21
forum: Desktop Environments
---

### Post by catgate on 2006-04-21
Hello,
I am trying to get to grips with Linux. I have been messing with it on and off for a few years. I was "brought up" on DOS and migrated to M$ Windows when it came out and I must say I prefer GUI to command line, and I think this is why I have never been totally happy with making a switch. The Linux commands are so much different to the DOS commands that I find it very arduous to remember them. However I was recently recommended to try Breezy Badger and so here I am. 
I wish to instal a Speedtouch DSL modem and downloaded a "driver" package from Speedtouch's web site. It is a .rpm package but the Badger says it will not play. Can some fount of knowledge please help me? How do I go about getting it on, as they say? (in language that is understandable to a BOF)
Thanks
:confused:

---

### Post by Joey French on 2006-04-21
You want to use a package called alien, it converts .rpm packages (redhat package management) to .deb (debian, what ubuntu is based on) for you. So, for example in the command line, you would type something like 

```
sudo alien -i /whatever/the/package/is/called.rpm
```

I have not used alien in a long time, so someone else should chime in and give the proper syntax for you. DON'T use the command above, I am not certain it will work for you, but that's generally how it goes. Alternatively, you can search the forums for alien to get a feel for it. Installing alien involves opening Synaptic, searching for alien, then "Apply Changes". 

Good luck!

---

### Post by louis_nichols on 2006-04-21
converting a packag from rpm to deb is as simply as

sudo alien <package-name>.rpm

nothing else required.

---

