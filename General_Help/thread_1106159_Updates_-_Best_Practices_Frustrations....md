---
title: "Updates - Best Practices? Frustrations..."
date: 2009-03-25
forum: General Help
---

### Post by webkris on 2009-03-25
I've been running 8.10 on my workstation for about 4 months now. I've been running the same on my new Dell Mini for a week.

Initially when I setup 8.10 I changed the update manager to check for long term security updates only, and passed on the features updates. Certainly not going to do beta or pre-release updates. I installed 210MB of "critical" updates, restarted my PC and my mini - and had no issues. I was pleased that the machine came back up.

This seemed to be the way to go - until I started having problems with BlueTooth. In my attempt to get BlueTooth running - I installed the 24 or so features updates for my machine (long term releases only).

The first thing that was really frustrating is my icons have all changed. When I went into settings / appearance, it said something about Gnome manager not loading, etc. (I'm not going to get into it - in this post.) Just that it's really frustrating to update your computer only to have it be a total crap shoot.
Is your PC going to boot after a major kernel update?
Is your desktop going to look the same after a major update?
How about that feature you rely on - like wifi :p - that is now broken because you "updated".

**The question:**
What are your best practices when dealing with Ubuntu updates?
Do you always install? Do you pour over update changes making sure you need them? Do you get your machine running and then lock it down tight?

Help - I'm about to turn off update manager and throw away the key.

- Kris

---

### Post by cariboo on 2009-03-25
I would suggest that for some reason your updates didn't finish properly. Open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get install -f
```

then in the same terminal type:

```
sudo apt-get update && sudo apt-get upgrade
```

this should correct any problems.

Jim

---

### Post by kanikilu on 2009-03-25
I'm sure you'll get some varied responses, but I've never really been bitten by an update breakage...I usually glance over the updates to see what all is installing (mainly to see if I'll need to reboot), and install all. Perhaps haphazardly, I also do this on my home server (although the server installation generally sees a lot less updates because it doesn't have a lot of packages installed by default).

I'm always a little nervous when I see packages that affect hardware (xorg, alsa, etc) and new kernels, but so far haven't really ran into anything major...*knock on wood* 8-[

---

### Post by 3Miro on 2009-03-25
Ubuntu actually tests updates before releasing them. The odds of something being broken are small and usually happens with third party software and such (i.e. when no-Ubuntu software is involved). The only time I have experienced problems is when I am running beta versions of programs (then I expect for crap to happen).

---

### Post by UbuntuNerd on 2009-03-25
If you want to lock down programs go to "Synaptic Package Manger" and select the "install program" you want and on the top menus click Package > Lock Version. it should remain the same even if there is an update.
you can even lock the "Kernel" version if you want

---

### Post by webkris on 2009-03-25
> **cariboo907 said:**
> I would suggest that for some reason your updates didn't finish properly. Open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get install -f
```

then in the same terminal type:

```
sudo apt-get update && sudo apt-get upgrade
```

this should correct any problems.

Jim


Unfortunately - didn't fix it...
I get 0 updates and 0 not finished, etc.

Here is the 'unable to start manager' error I was talking about: [http://ubuntuforums.org/showthread.php?t=579167](http://ubuntuforums.org/showthread.php?t=579167)

**and** I'd love to get updates on the internet but:
[http://ubuntuforums.org/showthread.php?t=1106175](http://ubuntuforums.org/showthread.php?t=1106175)

**and** I just tried a wired connection and it won't negotiate.

headhitkeyboard

I do appreciate the help!
I'm going to go to Starbucks for my 'cup of FAIL' now...
- Kris

---

### Post by webkris on 2009-03-25
**UbuntuNerd**: That's good to know.

**Update:**
Okay - I restarted once. No help...
Then I **shut-down.**

Then I wanted to try some other suggestions.
Started her back up.
1. My "unable to start the settings manager" problem is gone.
2. My unable to connect to ethernet connection is resolved.
3. My weird WiFi cached password problem is still around.

So I guess shutting down is different then a restart?
For now - updates have redeemed themselves. :D
- Kris

---

