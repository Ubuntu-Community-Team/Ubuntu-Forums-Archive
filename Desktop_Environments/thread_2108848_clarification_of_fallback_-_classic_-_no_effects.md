---
title: "clarification of fallback - classic - no effects"
date: 2013-01-25
forum: Desktop Environments
---

### Post by aspergerian on 2013-01-25
Not sure if this post might be better in Community Cafe. 

I tried Unity, fallback, then Mint. Finally settled upon Xubuntu and achieved a 10.04-like top and bottom bar. Several threads mention "no effects". What are differences (if any) among fallback, classic, and no effects? If there are differences, which of the three is likelier to have longevity?

A different thread offered "Been running for quite some time now with Gnome - No Effects. Very happy. If Canonical persists with Unity, this solution will be permanent for me."
[http://ubuntuforums.org/showthread.php?p=12473796#post12473796](http://ubuntuforums.org/showthread.php?p=12473796#post12473796)

Xubuntu is working for me, but I'm wondering about 10.04-like options for Ubuntu.

---

### Post by kansasnoob on 2013-01-26
Beginning with 11.10 Ubuntu began using Gnome 3. Up through version 3.6 Gnome includes "gnome-session-fallback" which presented a DE similar to Gnome 2. If a user installed the fallback session they'd be presented with both GNOME Classic and GNOME Classic (No effects) sessions.

The standard Classic session uses the Compiz window manager whereas the Classic (no effects) session uses the Metacity window manager. I've made quite a few notes about the latter here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

But be sure to notice what I said about Quantal and the future of the "classic mode" here:

[http://ubuntuforums.org/showpost.php?p=12417104&postcount=183](http://ubuntuforums.org/showpost.php?p=12417104&postcount=183)

I also opened a discussion here:

[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)

Things are changing rather quickly. SolusOS has forked the "fallback-session" into [the Consort DE]("http://ubuntuforums.org/showthread.php?t=2105950"), and [MATE is moving ever closer to being added to the repos]("http://ubuntuforums.org/showpost.php?p=12468127&postcount=54"). And it's impossible to tell exactly what the new GNOME classic mode will look and perform like :D

I personally plan on keeping my production machines on 12.04 since it's supported until April 2017. By then I'll undoubtedly have decided which way to go ;)

---

### Post by kansasnoob on 2013-01-26
Aha ........ almost as good as a time machine :D

If you scroll down here you can see an early impression of the new "classic mode":

[http://blogs.gnome.org/mclasen/2013/01/25/gnome-3-7-at-the-halfway-mark/](http://blogs.gnome.org/mclasen/2013/01/25/gnome-3-7-at-the-halfway-mark/)

But I doubt that will appear as an option in Ubuntu until 13.10 or beyond :)

---

### Post by aspergerian on 2013-01-26
> **kansasnoob said:**
> If you scroll down here you can see an early impression of the new "classic mode":
[http://blogs.gnome.org/mclasen/2013/01/25/gnome-3-7-at-the-halfway-mark/](http://blogs.gnome.org/mclasen/2013/01/25/gnome-3-7-at-the-halfway-mark/)
But I doubt that will appear as an option in Ubuntu until 13.10 or beyond :)

kansasnoob,

Thank you for the replies. My current Xubuntu has kernel 3.2.0-36, which seems a goodly machine distance from the forthcoming Ubuntu 3.7. One of my goals is to keep my desktop uncluttered with buttons that (for me) are better confined to narrow top- and bottom bars on a netbook with 11.6" screen. My other concern is that Unity and fallback slowed my computer (Acer 1410 with 4g ram).

---

### Post by kansasnoob on 2013-01-27
I'll bet Compiz is a bit heavy if these specs are right:

[http://support.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire1410-11.6/Aspire1410sp9.shtml](http://support.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire1410-11.6/Aspire1410sp9.shtml)

Is there something in particular about Xubuntu that you dislike?

Xubuntu 12.04 is a 3 year LTS and 12.04.2 is bringing a new hardware stack including the Quantal kernel:

[http://www.phoronix.com/scan.php?page=news_item&px=MTI3MjY](http://www.phoronix.com/scan.php?page=news_item&px=MTI3MjY)

[https://bugs.launchpad.net/ubuntu/+source/linux-lts-quantal/+bug/1097919](https://bugs.launchpad.net/ubuntu/+source/linux-lts-quantal/+bug/1097919)

Watch for the release notes here:

[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)

I'm sure they'll include instructions on how to install the Quantal-LTS kernel safely w/o the need for a re-installation.

---

### Post by aspergerian on 2013-01-27
> **kansasnoob said:**
> I'll bet Compiz is a bit heavy if these specs are right:
[http://support.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire1410-11.6/Aspire1410sp9.shtml](http://support.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire1410-11.6/Aspire1410sp9.shtml)
Is there something in particular about Xubuntu that you dislike?


Kansasnoob,

Thank you again. I'm learning to like Xubuntu, which works well with the programs I use - especially since I got the desktop to be akin to 10.04 Ubuntu's.
[http://ubuntuforums.org/showthread.php?t=2098800](http://ubuntuforums.org/showthread.php?t=2098800)

My Acer 1410 has 11.6" screen, Intel Core 2 SU3500; 1.4 ghz, 800 mhz FSB; 4G ram.

---

