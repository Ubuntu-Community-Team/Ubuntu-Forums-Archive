---
title: "Sound - Dell Mini 10(1010): HDA Intel MID"
date: 2011-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JWColeman on 2011-12-26
```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```

I tried to do this but it told me that it cannot find the package 'linux-restricted-modules-2.6.32-21-generic.

I got that from this post: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Can anyone help me get this package installed, I'm pretty sure it's what I need, although I could be wrong.

---

### Post by mikewhatever on 2011-12-27
The package you are looking for doesn't exist, so helping you to install it would require real magic. The howto you've been following says:
> 
Open a terminal and type

find /lib/modules/`uname -r` | grep snd

**You should see a large list of items come up. If you don't, it means that the install process did not install the sound modules for you. To fix this, type in the terminal window:**

sudo apt-get install linux-restricted-modules-`uname -r` linux-generic

Don't you get anything from 'find /lib/modules/`uname -r` | grep snd'???

The howto is obviously incorrect. There are linux-backport-modules, for example, 'linux-backports-modules-alsa-lucid-generic', which is sound related, but 'linux-backports-modules-alsa-2.6.32-22-generic' is the oldest, as the 2.6.32-21 kernel is too outdated.

---

