---
title: "Home network with Kubuntu and WinXP"
date: 2006-01-12
forum: General Help
---

### Post by nisukka on 2006-01-12
Hi!
I'm having problems getting my home network working. I have Kubuntu as a primary pc with internet connection via cable modem (eth1) and a secondary pc with WinXP (eth0). Pc's are connected with a cross-over cable.
I can't get the internet connection working in the WinXP machine. The pc's don't even ping each other.
I have tried to search for guides and tried to do as instructed but still no luck.
(On my primary pc I have also WinXP installed (dual-boot) and when using it, the internet is working on my secondary pc so there's no problems with bad cables etc.)

What should I try to do? Since the pc's don't ping each other, I guess I would have to start from there, but how?
And what about tcp/ip settings for both pc's?

Thanks in advance!
nisukka

---

### Post by drummer on 2006-01-12
One way of doing it is with the firewall program firestarter which has an internet connection sharing option built in. Firestarter is basically a front end to the IP tables as well as a soft firewall.

---

### Post by nisukka on 2006-01-13
Is Firestarter only for Ubuntu and not for Kubuntu. Or does it work properly in both?
I tried to install Firestarter via apt-get and I had some errors during install (can't remember what). It didn't create any startup icons for Firestarter, but I managed to start it from terminal. I switched the internet sharing setting on.
But anyway, my Kubuntu pc still doesn't share the internet connection.

---

### Post by drummer on 2006-01-13
hmm... firestarter should still work in kde even if it is meant for gnome, but maybe there's a kde specific program for this (anyone else know?). You could also try configuring IP tables directly, this might do the trick: [http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370) but I haven't tried this myself.

---

### Post by nisukka on 2006-01-13
I did exactly as instructed by the guide but still no luck.
When I try to ping my WinXp pc from my Kubuntu pc, I get this:
```
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
```

Any suggestions?
nisukka

---

### Post by drummer on 2006-01-13
never seen that error before, sorry.

Anyone else with ideas?? /me is not sure what to do next :S

---

