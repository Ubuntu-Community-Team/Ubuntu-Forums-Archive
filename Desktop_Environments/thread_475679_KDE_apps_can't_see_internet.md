---
title: "KDE apps can't see internet"
date: 2007-06-16
forum: Desktop Environments
---

### Post by Rhapsody on 2007-06-16
I've recently seen a strange problem where KDE apps (Konqueror, KTorrent, KAudioCreator) are all entirely unable to see any sort of internet connection. As you can probably tell, my internet connection actually works fine, and I'm posting this using Firefox.

Somewhat strangely, Amarok seems partly unaffected. If I insert an audio CD and load it in Amarok, it quite happily fetches the names of the album, artist, and tracks (something KAudioCreator can't so, as it insists it can't access the CDDB). But if I try to use the Context menu to access Wikipedia for more information, it doesn't work.

I'm beginning to think something is quite broken within KDE on my system, as I also have [problems](http://ubuntuforums.org/showthread.php?t=474600) with my refresh rate resetting itself when I start each session in KDE. I've recently reformatted and reinstalled everything on my root partition (which is separate from my home partition) so the problem with this must lie in /home somewhere.

This is quite frustrating, as this PC is working almost completely for the first time ever, but these problems are holding it back.

---

### Post by bailout on 2007-06-17
I have noticed the same problem with konq, not tried anyother programs. I use Opera but occasionally if a site doesn't like opera I used to use knq but now it comes up with an error msg for every site.

---

### Post by Blowfly on 2007-06-19
Methinks it's Konqueror, et al that are broken, as all my"commercial"  browsers work fine, and I predict if I could import Internet Explorer into the OS, it would work fine too.

There seems to be no answer for this, whether you look in Ubuntu or Konqueror sites.

It's really an intellectual exercise, I guess. No one would use Konqueror over Firefox anyway, but the question begs the developers of Konqueror: why didn't you make this to work?

---

### Post by ^master^ on 2007-06-19
I am aslo facing this kinda problem. Konqueror is not browsing the web. Messenger, Adept, Opera, Firefox all are working fine. This is strange and I have no idea how to solve this problem. I have installed Kubuntu 2 times but problem still exist.

---

### Post by bailout on 2007-06-19
I have just seen a thread on the kubuntu forums about this. Apparantly, and this works for me, if you run konq as root then it will connect. Obviously this isn't a solution but it may hint at what is wrong. For some reason kde apps run as user don't seem to allowed to connect but third part programs can. This can't be affecting everyone though :confused:

[http://kubuntuforums.net/forums/index.php?topic=3084031.0](http://kubuntuforums.net/forums/index.php?topic=3084031.0)

---

### Post by Rhapsody on 2007-06-21
> **bailout said:**
> I have just seen a thread on the kubuntu forums about this. Apparantly, and this works for me, if you run konq as root then it will connect. Obviously this isn't a solution but it may hint at what is wrong. For some reason kde apps run as user don't seem to allowed to connect but third part programs can. This can't be affecting everyone though :confused:

[http://kubuntuforums.net/forums/index.php?topic=3084031.0](http://kubuntuforums.net/forums/index.php?topic=3084031.0)
Confirmed for me. Konqueror run with superuser privileges was able to connect to web sites. As a regular user, it failed to connect to the same sites.

Additionally, starting Amarok with superuser privileges also seemed to work, where as it won't start at all usually.

At least I'm getting closer to the root of problem it seems.

Edit: Unfortunately, the command at the end of that topic did nothing. All of the files had correct ownership to begin with.

---

### Post by bailout on 2007-06-21
I have the problem on my desktop pc but my laptop works fine. I haven't tried the command at the end of that post yet as it seemed a bit speculative. Also until trying konq as root to test this I have never run as root so that isn't the cause of the problem.

---

### Post by Rhapsody on 2007-06-21
> **bailout said:**
> I have the problem on my desktop pc but my laptop works fine.
Similar experience here. My last PC never had problems like this. It's only my new one that exhibits these problems.

> **bailout said:**
> I haven't tried the command at the end of that post yet as it seemed a bit speculative.
It really did nothing in my case. Every single line of output said "retained", meaning the command hadn't changed a thing.

> **bailout said:**
> Also until trying konq as root to test this I have never run as root so that isn't the cause of the problem.
I've done several sudo and kdesu commands in the past, including running some applications as root. But then that *needs* to be done at some points. I've never actually logged in as root though.

---

### Post by kuja on 2007-06-21
I vote for hitting with a broader hammer, rather than just the ~/.kde directory, why not chown -R $USER:$USER ~

---

### Post by bailout on 2007-06-22
The major difference between my desktop and laptop that I can think of is the network connection. They are both wireless but the laptop uses a intel chip which works quite happily with knetworkmanager whereas the desktop uses a ralink chip which won't work at all with knetman and hence I control it via the command line (sudo dhclient rausb0). 

How are other people who have the problem connecting?

---

### Post by Rhapsody on 2007-06-22
I'm connecting in exactly the same way as I did with my old PC. My ADSL 'thing' (no idea what to call it, looks like a green stingray) was just transferred from my old PC to the new one. Same firmware, same account.

---

### Post by bailout on 2007-06-22
So you connect directly to the modem with a cable rather than wireless? I did wonder whether it was me connecting to the net via a 'sudo' command.

In summary for me I can connect with third party apps, Opera and openwengo. I can connect with Adept (needs root password anyway), konq when run as root. I can't connect with konq or amarok running as user.

There must be some way in linux to control users access to the internet. I wonder if this system has somehow got messed up.

---

### Post by Rhapsody on 2007-06-24
> **bailout said:**
> So you connect directly to the modem with a cable rather than wireless?
Yep. I've got a wireless thing here, but I've never used it. Also, even the wireless equipment can be used with an ethernet cable, which I'll probably do if I ever use it.

> **bailout said:**
> I did wonder whether it was me connecting to the net via a 'sudo' command.
Prior to me using 'kdesu konqueror', I'd never done that myself.

> **bailout said:**
> In summary for me I can connect with third party apps, Opera and openwengo. I can connect with Adept (needs root password anyway), konq when run as root. I can't connect with konq or amarok running as user.
Same here. I can connect using Firefox or Irssi, and I can connect with anything if I use the root password. Amarok usually doesn't work at all, but 'kdesu amarok' works perfectly.

> **bailout said:**
> There must be some way in linux to control users access to the internet. I wonder if this system has somehow got messed up.
Well it seems mine has as well. I've looked at the 'broader hammer' solution, but I'm a bit reluctant to hit the whole system with it. This install is only a couple of weeks old, so that's hardly likely to be the problem, and everything in .kde is correct, so where else could the problem possibly be?

---

### Post by bailout on 2007-08-15
Finally solved this by following advice in this thread on the kubuntu forums.

[http://kubuntuforums.net/forums/index.php?topic=3084031.0](http://kubuntuforums.net/forums/index.php?topic=3084031.0)

It seems the problem is knetworkmanager. Once I had closed that I could connect with konqueror :) I don't use knetworkmanager anyway as it doesn't work with my wireless adapter.

---

### Post by Rhapsody on 2007-08-23
Wow. I just killed KNetworkManager by closing the icon in my panel, and that seemed to fix everything. Konqueror can connect, Amarok starts. I haven't tried much else, but I presume they were all linked to this. How the hell did KNetworkManager cause so much trouble?

---

### Post by Rhapsody on 2007-08-25
After 24 hours, the Amarok problem is back for some reason. Exactly the same symptoms as before. All other problems remain fixed, only this one has returned. KNetworkManager is not active.

---

### Post by kuja on 2007-08-28
If possible, try removing knetworkmanager altogether and see if it fixes the problem. 

```
sudo apt-get --purge remove knetworkmanager
```

and then reboot

---

### Post by fca_neo on 2007-09-28
I had the same problem (konqueror could not access the internet) and doing sudo conqueror changed nothing. What solved my problem was simply closing knetworkmanager.

while knetworkmanager is closed konqueror works fine.

I hope this helps somebody. 

Cheers,
Carlos

---

