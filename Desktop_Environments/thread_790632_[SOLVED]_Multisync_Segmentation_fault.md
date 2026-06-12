---
title: "[SOLVED] Multisync Segmentation fault"
date: 2008-05-11
forum: Desktop Environments
---

### Post by ArtPulse on 2008-05-11
Hey there! I've been googling about this but yet I can't find an answer...

I have a Sony Ericsson k750, and I wanted to be able to sync my Evolution 2 (in Ubu 8.10) with my mobile and otherwise. So everyone talked about nothing but multisync, so I apt-get installed it.

I've configured it, following:
[https://wiki.ubuntu.com/MultisyncHowto](https://wiki.ubuntu.com/MultisyncHowto)

When I pressed Sync, it crashed. Then I went to console to start it, and I get this:

artpulse@px0:~$ multisync 
plugin_API_version
short_name
long_name
plugin_init
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/artpulse/.multisync/1/remotesettings
[evo2-sync] DEBUG: end: load_palm_state
[evo2-sync] DEBUG: end: sync_connect
Segmentation fault

=( what's up? I don't think I've configured it wrong, there are not many ways to do it wrong actually :S...
I was trying to use Bluetooth to communicate...

anyone? =(

---

### Post by ArtPulse on 2008-05-11
Further investigation proved how unpatient I am xP thing is after 20 minutes I got tired, but after posting I kept researching for other 10 and made my way out ;) This Ubuntu forum thread says it all:

[http://ubuntuforums.org/showthread.php?t=646889](http://ubuntuforums.org/showthread.php?t=646889)

The "official" one does not work, at least for me and the author xD

byeee!

---

