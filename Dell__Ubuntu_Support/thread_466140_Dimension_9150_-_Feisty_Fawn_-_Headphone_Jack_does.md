---
title: "Dimension 9150 - Feisty Fawn - Headphone Jack does not work"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by jcbodnar on 2007-06-06
Just installed 7.04. Sound works out of my main speakers but when I plug headphones into the front jack sound continues from the main speakers and I get no audio from the headphones.

I'm using a Dell Dimension 9150 desktop.

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 16
```

According to alsamixer the chip is a SigmaTel STAC9221 A1.

```
$ dpkg -l 'alsa*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                  Version                               Description
+++-=====================================-=====================================-==========================================================================================
un  alsa                                  <none>                                (no description available)
ii  alsa-base                             1.0.13-3ubuntu1                       ALSA driver configuration files
ii  alsa-oss                              1.0.12-1                              ALSA wrapper for OSS applications
ii  alsa-utils                            1.0.13-1ubuntu5                       ALSA utilities
```


Per several threads on headphone jack issues I added the following to /etc/modprobe.d/alsa-base and rebooted:

options snd-hda-intel model=dell

I also tried:

options snd-had-intel model=ref

Neither has worked. I previously had Fedora Core 5 installed on this machine and the headphone jack worked fine.

---

### Post by Ek0nomik on 2007-06-06
Here are a few links that may get you started:

[http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html](http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html) (Find "Headphones" and you will find the relevant section)

[http://ubuntuforums.org/showthread.php?p=2775938](http://ubuntuforums.org/showthread.php?p=2775938)

[http://ubuntuforums.org/showthread.php?t=452526](http://ubuntuforums.org/showthread.php?t=452526)

---

### Post by jcbodnar on 2007-06-08
Setting options snd-hda-intel model=stack3 got it working for me. Thanks!

---

