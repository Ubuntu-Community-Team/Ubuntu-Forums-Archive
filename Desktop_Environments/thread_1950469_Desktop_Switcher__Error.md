---
title: "Desktop Switcher  Error"
date: 2012-03-31
forum: Desktop Environments
---

### Post by cbennett926 on 2012-03-31
Desktop Switcher displays the correct boxes and windows, however it only shows a blue screen as a background and not the actual background. :(

---

### Post by cbennett926 on 2012-03-31
Ok, so I don't know exactly what I did. I uninstalled CCSM and reset the desktop as well as unity, I then rebooted, and all is back to normal.

---

### Post by sparhawkthesecond on 2012-05-10
Hi, how did you reset the desktop/Unity?

Cheers.

---

### Post by cbennett926 on 2012-05-10
> **sparhawkthesecond said:**
> Hi, how did you reset the desktop/Unity?

Cheers.


Hello,

You can open a terminal using ctrl-alt-T

or find it under accessories depending on what version of Ubuntu you are using, else you can hit the super key and begin typing terminal.

From there type

```


unity --reset


```

Tell me how that works for ya!

---

### Post by sparhawkthesecond on 2012-05-10
Thanks, I'm actually seeing another bug [here](http://ubuntuforums.org/showthread.php?p=11923045#post11923045) (and some other bugs that are possibly unrelated!), so I'll see if that can be resolved first, but if not, I'll try your hint. Is that also what you meant by resetting the "desktop"? Also, I presume uninstalling ccsm is unnecessary?
Cheers!

---

### Post by cbennett926 on 2012-05-10
> **sparhawkthesecond said:**
> Thanks, I'm actually seeing another bug [here]("http://ubuntuforums.org/showthread.php?p=11923045#post11923045") (and some other bugs that are possibly unrelated!), so I'll see if that can be resolved first, but if not, I'll try your hint. Is that also what you meant by resetting the "desktop"? Also, I presume uninstalling ccsm is unnecessary?
Cheers!


Are you running 11.10 or higher? CCSM has some very known issues with Unity and normally causes more problems than it's worth (at least to my knowledge so PLEASE correct me if I'm wrong :) ) 

I recommend unninstalling CCSM, and that is also how I reset the desktop, however you could uninstall the unity-desktop and re-install it doing this:

```


sudo apt-get update sudo apt-get install --reinstall ubuntu-desktop sudo apt-get install unity


```

However I would use that as a last straw!

All the best,

Cody

---

### Post by sparhawkthesecond on 2012-05-10
> **cbennett926 said:**
> Are you running 11.10 or higher? CCSM has some very known issues with Unity and normally causes more problems than it's worth (at least to my knowledge so PLEASE correct me if I'm wrong :) )
I'm running 12.04 (I'm waiting for my 50 beans before I can put that in my profile :(). I was using ccsm as per advice for 11.10. Googling a [bit]("http://askubuntu.com/questions/125328/will-ccsm-work-better-with-12-04/125329#125329") [more]("http://askubuntu.com/questions/29553/how-can-i-configure-unity/101415#101415") supports what you say! On that advice, I think I might try resetting it in the next few days. I did an upgrade to 12.04 from 11.10, and I'm actually considering a clean reinstall, since a few other things have broken (e.g. hibernation works 10% of the time). It's just irritating to reinstall, since I'll have to not only recover /home/ but all my new packages, and my udev files, and /usr/local/bin, etc. etc. etc.

> **cbennett926 said:**
> I recommend unninstalling CCSM, and that is also how I reset the desktop, however you could uninstall the unity-desktop and re-install it doing this:

sudo apt-get update sudo apt-get install --reinstall ubuntu-desktop sudo apt-get install unity

[/code]
I presumed that ccsm was just a front-end to the settings, so I imagined that uninstalling it would not reset settings to the default? Anyway, I'll give it a try and see how I go.

Thank you for your advice!

---

### Post by sparhawkthesecond on 2012-05-10
Oops. I tried this, as it looked promising.
1) open ccsm
2) Click preferences
3) click "reset to defaults"
This prevented unity from working at all! So then ```
$ unity --reset
``` fixed it.

---

