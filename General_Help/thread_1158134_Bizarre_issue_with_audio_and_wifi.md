---
title: "Bizarre issue with audio and wifi"
date: 2009-05-13
forum: General Help
---

### Post by kappa962 on 2009-05-13
I just upgraded to 9.04, and now a few minutes after booting up, the audio will stop working, *simultaneous with the wifi dying*. The wifi still sees all the networks, it just can't log in. The audio still puts out sound, but it is extremely choppy, on and off several times per second. Kind of like a machine gun sound. I am clueless as to how to troubleshoot this issue.

Everything worked fine before with 5.10, 6.04, 6.10, 7.04 and Xubuntu 7.10.

I tried "sudo /etc/init.d/alsa-utils reset" and got this curious result:

```
 * Resetting ALSA...
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'

```

Any ideas?

---

### Post by kappa962 on 2009-05-13
anybody?

---

### Post by kappa962 on 2009-05-14
Anybody have any ideas at all?

---

### Post by BZF on 2009-05-14
[SIZE=1][COLOR=Blue]make sure you have all the updates and drivers ready and installed, that should help[/COLOR][/SIZE]

---

### Post by kappa962 on 2009-05-14
That's the first thing I did after installing 9.04.

---

### Post by petrus4 on 2009-05-14
> **kappa962 said:**
> 
Any ideas?

ALSA is a royal pain in the rear end.  It has been giving me trouble intermittently ever since I installed about a month ago.  I'm currently compiling a custom kernel as I write, and the main reason why is in order to compile OSS v4 with it.

When I've finished doing a few things, I'm going to be writing a HOWTO about how to get the garbage out of Ubuntu and make it into hopefully a semi-tolerable system which doesn't crash and have hardware dying constantly.

---

### Post by kappa962 on 2009-05-14
Ok, your mention of compiling a custom kernel got me thinking that this sounds like a kernel problem, so I tried switching to the realtime kernel. So far no problems. Audio and wifi are both still functional after an hour, which would never have been the case before. Hopefully the problem is fixed.

---

