---
title: "Kubuntu gets freezed ..."
date: 2011-01-02
forum: Desktop Environments
---

### Post by gaurang on 2011-01-02
Hi All,
I don't know why but my Kubuntu system gets freeze after some period of usage. I believe it is random because I don't see any fixed time period or any software. But my knowledge is yet limited in Ubuntu, so what are the places I can check if it has any h/w or s/w issues ??

Just to let you guys know, Originally I had only Ubuntu installed. But I installed Kubuntu just few days ago along with Ubuntu using,
**sudo apt-get install kubuntu-desktop**


Any reply is really appreciated ...

Thanks,
-Gaurang

---

### Post by R33D3M33R on 2011-01-03
Do you have desktop effects enabled? Did you check the logs for errors?

---

### Post by gaurang on 2011-01-03
Hi,
Thanks for reply ... And Yes Desktop Effects Were Enabled ...
do you think it can be the reason ??
Also I checked at Syslog.1 in my log folder and I found few entries as follows (for most recent HANG event )...

```

Jan  2 22:32:27 Ltl-Devil pulseaudio[2012]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 56.
Jan  2 22:32:27 Ltl-Devil pulseaudio[2012]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.

```
After above message (which I think could be reason for blackouts), I get following error ...
```

Jan  2 22:48:53 Devel kernel: [ 1043.180129] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jan  2 22:48:53 Devel kernel: [ 1043.180296] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 160191 at 160190)
Jan  2 22:48:53 Devel kernel: [ 1043.180632] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
Jan  2 22:48:53 Devel kernel: [ 1043.180641] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000


```

and this repeats number of times till end of log and next entry is for restart (which I did after machine got froze) ...

-Gaurang

---

### Post by R33D3M33R on 2011-01-03
This could be your bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/659826](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/659826)

Try to update your KDE to latest version with Kubuntu PPA: [https://launchpad.net/~kubuntu-ppa/+archive/ppa](https://launchpad.net/~kubuntu-ppa/+archive/ppa)

---

### Post by gaurang on 2011-01-03
Hmm sounds like solution ... because the BUG shows kind of similar error as mine (since I am on Intel machine too)...

But it is strange that I have booted my machine into Kubuntu since this morning and it has not yet frozen !!! I did update though (not sure if they are related) ...

I think, I will wait for it to get freeze again if so then I will surely follow your solution ...

Thanks for your reply bro.

-Gaurang

---

