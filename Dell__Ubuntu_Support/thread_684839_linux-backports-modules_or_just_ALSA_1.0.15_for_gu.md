---
title: "linux-backports-modules or just ALSA 1.0.15 for gutsy?"
date: 2008-02-01
forum: Dell  Ubuntu Support
---

### Post by Sempfinger on 2008-02-01
Hello,

While trying to fix my microphone problem on a vostro 1400, I found this bugreport:

[http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963]("http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963")

and especially:

> However, the complete fix, including built-in microphone support, is in linux-backports-modules which contains ALSA 1.0.15

What I want to do is either installing the linux-backports-modules with ALSA 1.0.15 included, or just installing ALSA 1.0.15. I do not know which one is better, though.

I found a HOWTO for the ALSA 1.0.15 install:

[http://help.ubuntu.com/community/HdaIntelSoundHowto]("http://help.ubuntu.com/community/HdaIntelSoundHowto")

I could jump right in and follow the instructions, but since I am not that experienced and do not know what I would be doing with the kernel headers, the best thing to do is get advice.

There is a Caveats section in this HOWTO:

> Overwriting packaged files and adding unmanaged files by running sudo make install may break upgrades. A better way is to create a backport by using the build scripts from your current alsa source packages. This would also allow you to undo the changes if they don't work, by simply downgrading back to the original package version.

and we are back to linux-backports-modules (?). I am confused and have no idea

recommendations/explanations are highly appreciated

kind regards

---

### Post by andyvich on 2008-02-07
Hey hows it going.

Here is what I did on my 1400 and it works great.  I have it in a post i put up here [http://ubuntuforums.org/showthread.php?t=681135&highlight=1400](http://ubuntuforums.org/showthread.php?t=681135&highlight=1400)

Hope that gets it working for you

---

### Post by Sempfinger on 2008-02-07
just a few minutes ago I typed

```
uname -a

Linux vostro 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```


```
sudo aptitude install linux-backports-modules-2.6.22-14-generic
```

no error messages... reboot

now I have no sound:

```
cat /proc/asound/card0/codec#* | grep Codec

cat: /proc/asound/card0/codec#*: No such file or directory
```

what went wrong? can someone help me?

--- Edit ---

after a few reboots and adding 'options snd-hda-intel probe_mask=1 model=3stack' to /etc/modprobe.d/alsa-base, the kernel was able to load the snd_hda_intel module.

Alsamixer prints its version as 1.0.14, although the backports package should contain 1.0.15... But after running alsamixer from the terminal I saw that somehow the alsamixer options had changed and now I can perfectly redord via mic and play back sound!

thanks andyvich! you led me on the right track!

I wish I knew what made it work in the end...

---

