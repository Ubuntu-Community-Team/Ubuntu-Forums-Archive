---
title: "Sound disapeared. Got error: audiotestsrc wave=sine freq=512"
date: 2009-03-30
forum: General Help
---

### Post by abcuser on 2009-03-30
Hi,
using Ubuntu 8.10, I noticed that my sound does not work anymore. It was working without any problem two days ago.

I try to test the sound using System | Preferences | Sound | Test buttons and I get error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.


In the same window in the bottom at Default Mixer Tracks, Device - there is no selection at all. It looks like Ubuntu has lost my sound driver.

Is there any way to uninstall/install sound driver? Or any idea how to solve this problem?
Regards

---

### Post by fcuk112 on 2009-03-30
Some other people are experiencing this issue as well, including me.  No resolution as of yet, but you can get your sound back by going into a terminal (ctrl-alt-f2) and entering:
```

pkill -9 -u username

```

---

### Post by Aat on 2009-03-30
I had this problem too.

In my case it was related to bug [COLOR="Navy"][U][https://bugs.launchpad.net/bugs/292743]("https://bugs.launchpad.net/bugs/292743")
[/U][/COLOR]
The fix is:

Add the following line:

> options snd-hda-intel probe_mask=1

to /etc/modprobe.d/alsa-base

Hope this helps

---

### Post by abcuser on 2009-03-31
fcuk112, Aat, tried bout ideas and not working.

Any idea?

By the way, what is the info in your system in from System | Preferences | Sound | Device tab | Device data field? My is empty, so it looks like no sound driver was recognized.

---

### Post by abcuser on 2009-03-31
Hi,
solved the problem. I was right there was no sound driver...

I use VirtualBox software to virtualize Ubuntu on Windows XP host. I have reinstalled VirtualBox few days ago and I haven't notice that sound gone off. By default VirtualBox has Audio set to none, so Ubuntu does not see sound driver. Now I have set on VirtualBox settings:
Host Driver: Windows DirectSound
Controler: ICH AC97
and sound is on again.

Problem solved!
Regards

---

