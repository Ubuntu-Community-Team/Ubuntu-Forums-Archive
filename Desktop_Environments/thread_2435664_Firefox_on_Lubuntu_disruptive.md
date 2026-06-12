---
title: "Firefox on Lubuntu disruptive"
date: 2020-01-24
forum: Desktop Environments
---

### Post by cam17 on 2020-01-24
While using Lubuntu19.04 when ever I use Firefox it crashes  over a few minutes of play the entire system. I tried another browser and it worked. But when I open firefox usually for youtube  it crashes the system even if no video is playing and Firefox is left open and dormant.  This appears to be a Lubuntu problem as it does not occur in Ubuntu. This has been going on for a couple of months. It did operate correctly before.  Is there any correction ?

---

### Post by TheFu on 2020-01-24
[https://www.omgubuntu.co.uk/2020/01/ubuntu-19-04-end-of-life](https://www.omgubuntu.co.uk/2020/01/ubuntu-19-04-end-of-life)
Not worth troubleshooting on a EoL OS.

However, firefox has changed some of the default security settings which prevent video and audio. These were added for privacy. I found them a few weeks ago after a new firefox release was pushed out. I'd never seen any of those privacy settings before.  Sorry, but I don't recall exactly which settings had to be changed. I was following a guide at mozilla.org - I think.

---

### Post by Autodave on 2020-01-24
Are you using any ad blockers?  If so, disable all of them and try *uBlock.*

---

### Post by cam17 on 2020-01-24
> **Autodave said:**
> Are you using any ad blockers?  If so, disable all of them and try *uBlock.*  I already use ublock. I tested it with everthing turned off and the problem still persists. Firefox with no add ons and open will eventually crash Lubuntu.

---

### Post by TheFu on 2020-01-24
LUbuntu didn't have pulse-audio last time I checked, but firefox on Linux requires pulse-audio. Could that be part of the issue?
What do the system logs show?

---

### Post by guiverc on 2020-01-24
TheFu has already stated Lubuntu 19.04 is EOL, so I'd *release-upgrade* asap.

[https://lubuntu.me/lubuntu-19-04-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-19-04-end-of-life-and-current-support-statuses/)
[http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)

FYI:  Lubuntu uses pulseaudio, using the `puvucontrol-qt` Qt variant, even Lubuntu 18.04 uses pulseaudio though used the GTK control.

---

### Post by cam17 on 2020-01-25
You say it is outdated but I received and update today Jan-25-2020 from my Public IP address of 104.158.49.18.

Does Lubuntu warn of a pending update?

---

### Post by cam17 on 2020-01-25
> **guiverc said:**
> TheFu has already stated Lubuntu 19.04 is EOL, so I'd *release-upgrade* asap.

[https://lubuntu.me/lubuntu-19-04-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-19-04-end-of-life-and-current-support-statuses/)
[http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)

FYI:  Lubuntu uses pulseaudio, using the `puvucontrol-qt` Qt variant, even Lubuntu 18.04 uses pulseaudio though used the GTK control.

I am using 19.10 and there is no difference in Firefox performance. It crashes while playing pluto.tv and Youtube but not other sites. 

The reason I think it is Lubuntu is if I close Firerfox while it is running or about to slow down the system says it is not responding.

---

### Post by springshades on 2020-01-26
Do you know if you're having a full kernel panic or just a graphical freeze? If it's just your window manager freezing, then you might be able to get to a console by Ctl+Alt+Fx where Fx is just trying F1, F2, F3, F4... to see if one of them gives you a console. That may help you to debug the crash.

You may want to disable or enable hardware acceleration in Firefox to see whether it is a video card driver issue.

I can't imagine that an adblocker could cause a kernel panic, but a combination of a sketchy video driver and a misbehaving browser plugin (such as Flash) has done my system in on many occasions. Those sites should be using HTML5 by default, but sometimes they have settings that override that. Such as if you sync your settings between browsers.

I can tell you that I run Firefox in Lubuntu 19.10 (clean install) on a newer machine without issues.

---

### Post by guiverc on 2020-01-26
Any update you got from 25-Jan (on 19.04) was probably delayed getting to you, because your chosen mirror is behind (some are hours behind, some days, some so far back it's beyond the counter - [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)). 

Yes you are prompted to upgrade to 19.10 (from 19.04; would have occurred 4-8 days 19.10's release) however there is an answer you can give that causes this question to never be asked again, which means that first warning was also the last warning (which would have been about 3 months ago now so users usually don't remember it).


Using firefox to stream youtube videos is something I do in normal Lubuntu testing, and on 19.04 I used laptops that had as little as 1GB of ram without trouble, by 19.10 cycle I no longer used less than 2gb of ram. I have 17 boxes I use for testing, though only 12 were used for 19.10, so I'd look at what addon's you've added.  You mentioned pluto.tv; I've never used it sorry.

You also said it crashes eventually; I don't know how long you mean  (in the first post you said only minutes though). I've left youtube streaming in the background for ~6 hours without issue (in my testing) though usually I move to the next box in testing within 5 minutes of streaming (a minute in small window, a minute in maximized window, minute with f11, minute after fullscreen, then media keys & repeat on other display if one is present on test box, streaming can be left on as I write notes on iso.qa.ubuntu.com, or just start loading `pcmanfm-qt` or whatever's next).  I do often test using 'ublock origin', 'ghostery', and 'privacy badger', but never any others.  On my own machines, I won't use any google site in firefox (I use chromium only for google sites) so I've only used firefox to stream videos during testing.

Are you using the default deb install package?
What do you see if you `sudo apt-cache policy firefox`?
Do you have a firefox snap installed?  (`snap list` to view your installed snaps)
or have you installed firefox another way?

---

