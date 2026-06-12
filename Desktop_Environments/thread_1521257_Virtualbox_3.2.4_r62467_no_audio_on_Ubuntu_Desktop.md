---
title: "Virtualbox 3.2.4 r62467 no audio on Ubuntu Desktop (Lucid Lynx) 10.04 LTS"
date: 2010-06-30
forum: Desktop Environments
---

### Post by 3L33T on 2010-06-30
I'm posting this here for posterity.  I hope it helps out someone who is having same issue.


Problem:  No audio and no audio device recognized in Windows XP SP3 running inside VirtualBox 3.2.4 r62467 hosted on a HP ML150 G6 with Ubuntu 10.04 LTS and Sound Blaster Audigy SE sound card.

Solution: Modified VM VirtualBox machine --> settings --> audio --> audio controller --> ICH AC97.   

The default setting was Sound Blaster 16.  I left the Host Audio Driver setting to PulseAudio.

Now, audio output and mic inside the windows XP VM is working.  Tested and confirmed using Skype v 4.2.0.169

Cheers!

---

### Post by 3L33T on 2011-02-28
UPDATE:

Just want to update this thread with the latest info regarding my running Ubuntu 10.04LTS configuration on HP ML150 G6 server since there is no official support from HP with Lucid Lynx (10.04 LTS).

I'm now running a Windows 7 32-bit guest o/s on VirtualBox v 3.2.12 r68302.


```
 root@lucidlynx:~# uname -a
Linux lucidlynx 2.6.32-28-generic-pae #55-Ubuntu SMP Mon Jan 10 22:34:08 UTC 2011 i686 GNU/Linux

```

```

root@lucidlynx:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

```

```

Skype (BETA) version 2.1.0.81

```

[

---

### Post by mercmobily on 2012-01-06
Posterity says THANK YOU!

---

