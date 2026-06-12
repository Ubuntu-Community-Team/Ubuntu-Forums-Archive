---
title: "Debian Etch: Flash Sound and Latency"
date: 2007-06-24
forum: Debian
---

### Post by shae on 2007-06-24
I tried Debian Etch and absolutely loved it.  I would still be using it if I could figure out how to configure flash correctly.  I used ESD for sound mixing and while I could figure out how to enable sound, it laged far behind the video.  Does anyone else know how to fix this problem?  I tried google, but then I might have missed something.  

Thank you very much ahead of time.

---

### Post by kerry_s on 2007-06-24
> **shae said:**
> I tried Debian Etch and absolutely loved it.  I would still be using it if I could figure out how to configure flash correctly.  I used ESD for sound mixing and while I could figure out how to enable sound, it laged far behind the video.  Does anyone else know how to fix this problem?  I tried google, but then I might have missed something.  

Thank you very much ahead of time.

alsa is better than esd> 
[B]su
apt-get install alsa-base alsa-utils[/B]
then while your still in terminal as root>
**alsaconf**
**exit** <to switch back to the user
then adjust the settings>
**alsamixer**

flash is just> apt-get install flashplugin-nonfree

make sure you have> **main contrib non-free **
at the end of your repos, to have access to all the software.

---

### Post by shae on 2007-06-25
I used this:

```
sudo apt-get install gnome-audio libesd-alsa0 alsa-oss esound-clients
```

and in /etc/iceweasel/iceweaselrc

```
FIREFOX_DSP="aoss"
```

To fix it.  Thanks guys.

---

