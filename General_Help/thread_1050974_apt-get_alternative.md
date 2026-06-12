---
title: "apt-get alternative?"
date: 2009-01-26
forum: General Help
---

### Post by Barnicle on 2009-01-26
I'm trying to run 'apt-get update', but I'm getting 'failed to fetch' errors. This has happened before, because it's obviously dependent on it's source list. Anyway, I was wondering what you guys would recommend as an alternative? Also, in regards to apt-get, is there any solution to get around this error? I already modified my source list to use archive, instead of ca.archive.

Thanks.

---

### Post by Archimedes0212 on 2009-01-26
I know, at least for me, that when I run the apt-get command, it needs super user privileges. Try running the command:

sudo apt-get update

You will be prompted for your root password and then the command should work perfectly fine.

---

### Post by albinootje on 2009-01-26
> **Archimedes0212 said:**
> I know, at least for me, that when I run the apt-get command, it needs super user privileges. Try running the command:

sudo apt-get update

You will be prompted for your root password and then the command should work perfectly fine.

Indeed, and if you get errors, please post them (completely) here.

---

### Post by Barnicle on 2009-01-26
I am sudo when running the update. These are the errors:

[IMG]http://i2.photobucket.com/albums/y11/barnicle/apt-get.jpg[/IMG]

---

### Post by Archimedes0212 on 2009-01-26
It almost looks like you don't have a connection to the internet (but I think I can disregard this idea)

---

### Post by albinootje on 2009-01-26
> **Barnicle said:**
> I am sudo when running the update. These are the errors:


Thanks.

I get a 404 in Firefox for this [http://archive.ubuntu.com/dists/hardy-updates/universe/source/](http://archive.ubuntu.com/dists/hardy-updates/universe/source/) already.

p.s. please try to copy & paste error messages whenever possible, that makes things much easier for the readers here to double-check or test things via copy&paste too.

---

### Post by Barnicle on 2009-01-26
I am able to ping the outside world with no problem on the machine. I will do that next time, it's just I'm running a virtual console, and it won't let me copy so I can paste :(

---

### Post by albinootje on 2009-01-26
> **Barnicle said:**
> I am able to ping the outside world with no problem on the machine. I will do that next time, it's just I'm running a virtual console, and it won't let me copy so I can paste :(

Okay, but there's something wrong with your /etc/apt/sources.list

Here's the relevant part of mine :
```

deb http://nl.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://nl.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy universe
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://nl.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

# deb http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by albinootje on 2009-01-26
You can use other mirrors, instead of 
[http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/)
e.g. these :
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
[http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/)
[http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/)

Maybe the canadian mirror had a temp. problem.

---

### Post by Barnicle on 2009-01-26
I used ca. and nl. and I'm still getting errors. I will try the other ones suggested, but in the meantime, what is a good alternative to apt-get?

Just by clicking those links, I can see that they are down. I think that the source list is just unable to connect. I don't think it's anything wrong on my end, that's why I want to see if there is an alternative to apt-get.

---

### Post by albinootje on 2009-01-26
> **Barnicle said:**
> I used ca. and nl. and I'm still getting errors. I will try the other ones suggested, 

Can you post your /etc/apt/sources.list ?
And if you don't need the deb src lines, comment them out.
Do you have bzip2 installed ?
> 
but in the meantime, what is a good alternative to apt-get?

Just by clicking those links, I can see that they are down. I think that the source list is just unable to connect. I don't think it's anything wrong on my end, that's why I want to see if there is an alternative to apt-get.

You can use aptitude instead of apt-get. But imho you really need to solve this problem at the root.

---

### Post by Barnicle on 2009-01-26
I just blew away the machine cause I thought that I didn't do a proper OpenSSH install. That did not solve the issue. I did an apt-get update on another machine, and it ran successfully.

Here is a copy of my source list:
```
#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Yes, I do have bzip2 installed, but that seems to be causing some issues, as seen in the error. Here are the errors I'm getting (sorry about the screenshot, I can't copy/paste in my virtual console):

[IMG]http://i2.photobucket.com/albums/y11/barnicle/apt-get-1.jpg[/IMG]

---

### Post by albinootje on 2009-01-26
I just tested your lines from /etc/apt/sources.list, and they are fine.
Can you post (screenshots) the output of :
```

ifconfig -a
route -n
cat /etc/resolv.conf
ping -c4 ping.xs4all.nl
ping -c4 62.108.1.65
free -m

```

---

### Post by wirelessmonkey on 2009-01-26
Can you ping archive.ubuntu.com from that machine?
If not, can you ping its IP (91.189.88.31)?


I'm wondering if you're seeing a DNS issue.

---

### Post by Barnicle on 2009-01-26
Ok, so it seems as though changing the sources to FTP from HTTP worked! It's weird though cause the apt-get worked on my other machine with basically the same configurations.

Pinging archive.ubuntu.com works.

---

### Post by oldos2er on 2009-01-26
"what is a good alternative to apt-get?"

 Every package manager in Ubuntu uses the same sources.list. You can change servers via Synaptic or Software Sources.

---

### Post by Barnicle on 2009-01-26
I think the real problem here is that my virtual machine settings for networking need to be configured differently. I tried pinging my virtual machine, but didn't get a response. I think this is why my apt-get wasn't working.

---

