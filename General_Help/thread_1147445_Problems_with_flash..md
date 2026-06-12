---
title: "Problems with flash."
date: 2009-05-03
forum: General Help
---

### Post by JamieLeece on 2009-05-03
I'm new to linux and really liking it so far except for one problem I've been having. I can't get flash to work properly. I've looked it up online and tried pretty much everything I've found but It still runs very poorly. I can start flashmovies playing, but they load slowly, and once I can click start the sound starts up but the video stays frozen for a few seconds till it suddenly jumps ahead to a different motionless screen with the sound playing on in the background. When I first installed Ubuntu I tried to use Gnash with firefox, maybe that's the problem. I just can't figure out how to get firefox to stop using gnash and try something else.

---

### Post by codeseer on 2009-05-03
> **JamieLeece said:**
> I'm new to linux and really liking it so far except for one problem I've been having. I can't get flash to work properly. I've looked it up online and tried pretty much everything I've found but It still runs very poorly. I can start flashmovies playing, but they load slowly, and once I can click start the sound starts up but the video stays frozen for a few seconds till it suddenly jumps ahead to a different motionless screen with the sound playing on in the background. When I first installed Ubuntu I tried to use Gnash with firefox, maybe that's the problem. I just can't figure out how to get firefox to stop using gnash and try something else.

What version of Ubuntu and are you running 32-bit or 64-bit?

Edit:

You can determine this information by typing the following in the Terminal and pressing the Enter key. The Terminal can be accessed by clicking the Applications menu, Accessories, Terminal.

```
lsb_release -a;uname -a
```

---

### Post by delcypher on 2009-05-03
Try , exiting firefox and typing these commands into a terminal
```
sudo apt-get remove gnash 
#hopefully this next one is unnecessary, but just in case
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get install flashplugin-nonfree

```

Start firefox and try now. Your problem might also be caused by no proper graphics drivers.

---

### Post by JamieLeece on 2009-05-04
I'm running 32bit and here's the results of:
lsb_release -a;uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty
Linux Motel-1 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

I tried: 
sudo apt-get remove gnash 
#hopefully this next one is unnecessary, but just in case
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get install flashplugin-nonfree
It didn't help. Flash is still just as slow as ever. Some things won't even run at all. I was asked to install nvidia drivers when I started up ubuntu for the first time after installing, and I've got the Nvidia Xserver Settings menu under administration. Other graphical things like games and movies run just fine. The problem seems to be with flash.

---

### Post by codeseer on 2009-05-04
> **JamieLeece said:**
> I'm running 32bit and here's the results of:
lsb_release -a;uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty
Linux Motel-1 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

I tried: 
sudo apt-get remove gnash 
#hopefully this next one is unnecessary, but just in case
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get install flashplugin-nonfree
It didn't help. Flash is still just as slow as ever. Some things won't even run at all. I was asked to install nvidia drivers when I started up ubuntu for the first time after installing, and I've got the Nvidia Xserver Settings menu under administration. Other graphical things like games and movies run just fine. The problem seems to be with flash.

Since the lsb_release command didn't work, I don't know which version of Ubuntu you have (32-bit or 64-bit).

Do you?

---

### Post by JamieLeece on 2009-05-04
I already said 32bit.

"I'm running 32bit and here's the results of:"
lsb_release -a;uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty
Linux Motel-1 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by codeseer on 2009-05-04
> **JamieLeece said:**
> I already said 32bit.

"I'm running 32bit and here's the results of:"
lsb_release -a;uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty
Linux Motel-1 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Oh... lol, I just woke up. Give me a sec and I'll post you a 'howto' that I compiled.

---

### Post by codeseer on 2009-05-04
Download the '.deb for Ubuntu' of Flash from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

...then close firefox and...

Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

...then install from the .deb and restart Firefox.

---

### Post by JamieLeece on 2009-05-04
Looks like that did the trick. Everything seems to be working just fine now. Thanks for all the help.

---

