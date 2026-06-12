---
title: "amule: Connection Lost."
date: 2006-07-07
forum: Desktop Environments
---

### Post by zrothe on 2006-07-07
This started about 2 weeks ago, just out of the blue. I hadn't changed anything to my knowledge. Heres what im seeing:

> 2006-07-06 18:56:13: Connecting
2006-07-06 18:56:13: Servers: Trying to connect
2006-07-06 18:56:13: AICH Thread: Syncronization thread started.
2006-07-06 18:56:13: AICH Thread: Masterhashes of known files have been loaded.
2006-07-06 18:56:13: AICH Thread: No new files found.
2006-07-06 18:56:13: AICH Thread: Terminated.
2006-07-06 18:56:13: Connecting to BiG BanG 10 (80.239.200.109 - 80.239.200.109:3000)
2006-07-06 18:56:13: Read 0 Kad contacts
2006-07-06 18:56:14: Credit file loaded, 2401 clients are known

2006-07-06 18:56:14: - This is aMule CVS using wxGTK2 v2.6.1 (Unicoded) (Snapshot: Mon Jan 9 07:02:13 CET 2006) based on eMule.
2006-07-06 18:56:14: Running on Linux 2.6.15-25-386 i686
2006-07-06 18:56:14: - Visit [http://www.amule.org](http://www.amule.org) to check if a new version is available.

2006-07-06 18:56:14: Loading ipfilter.dat files.
2006-07-06 18:56:14: Loaded 0 IP-ranges from 'ipfilter.dat'. 0 malformed lines were discarded.
2006-07-06 18:56:14: Loaded 0 IP-ranges from 'ipfilter_static.dat'. 0 malformed lines were discarded.
2006-07-06 18:56:14: Loading server.met file: /home/aaron/.aMule/server.met
2006-07-06 18:56:14: 199 servers in server.met found
2006-07-06 18:56:14: Found 4 part files
2006-07-06 18:56:14: External connections disabled in config file
2006-07-06 18:56:14: MuleUDPSocket: Created Server UDP-Socket at port 4665
2006-07-06 18:56:14: MuleUDPSocket: Created Client UDP-Socket at port 4672
2006-07-06 18:56:14: Found 9 known shared files
2006-07-06 18:56:14: Servers: Trying to connect
2006-07-06 18:56:14: Connecting to Bidonkey 2k (213.251.133.199 - 213.251.133.199:4661)
2006-07-06 18:56:14: Connected to BiG BanG 10 (80.239.200.109:3000)
2006-07-06 18:56:14: Connected to Bidonkey 2k (213.251.133.199:4661)
2006-07-06 18:56:33: Lost connection to Bidonkey 2k (213.251.133.199:4661)
2006-07-06 18:56:33: Connection lost
2006-07-06 18:56:33: Lost connection to BiG BanG 10 (80.239.200.109:3000)
2006-07-06 18:56:33: Connection lost
2006-07-06 18:56:37: Connection attempt to BiG BanG 10 (80.239.200.109:3000) timed out.
2006-07-06 18:56:37: Servers: Trying to connect
2006-07-06 18:56:37: Connecting to DonkeyServer No3 (62.241.53.17 - 62.241.53.17:4242)
2006-07-06 18:56:38: Connected to DonkeyServer No3 (62.241.53.17:4242)
2006-07-06 18:56:39: Connection attempt to Bidonkey 2k (213.251.133.199:4661) timed out.
2006-07-06 18:56:39: Servers: Trying to connect
2006-07-06 18:56:39: Connecting to BiG BanG 1 (80.239.200.99 - 80.239.200.99:3000)
2006-07-06 18:56:40: Connected to BiG BanG 1 (80.239.200.99:3000)
2006-07-06 18:56:57: Lost connection to DonkeyServer No3 (62.241.53.17:4242)
2006-07-06 18:56:57: Connection lost
2006-07-06 18:56:59: Lost connection to BiG BanG 1 (80.239.200.99:3000)
2006-07-06 18:56:59: Connection lost


What I've done so far:

-I deleted the preferences file and started that from scratch.
-Double checked my router settings.
-Turned on DMZ for my ip on my router.

Not sure what is going on here. Any help would be very much appreciated, thanks.

---

### Post by zrothe on 2006-07-08
> **zrothe said:**
> This started about 2 weeks ago, just out of the blue. I hadn't changed anything to my knowledge. Heres what im seeing:




What I've done so far:

-I deleted the preferences file and started that from scratch.
-Double checked my router settings.
-Turned on DMZ for my ip on my router.

Not sure what is going on here. Any help would be very much appreciated, thanks.

I tried reinstalling, to no avail. I think this might be an external problem.

---

### Post by quedigg on 2006-07-08
actually the same problem here ! ,it's not an external problem,try another server rather thaan Edonkey server 1,2

---

### Post by zrothe on 2006-07-10
I tried numerious different servers, it finally connected to one, but it had low population, none of my downloads would continue.

---

### Post by zrothe on 2006-07-12
> **zrothe said:**
> I tried numerious different servers, it finally connected to one, but it had low population, none of my downloads would continue.

bumps

---

### Post by alican timur on 2007-08-22
same problem here. did this problem get solved?

---

### Post by Sukarn on 2007-11-12
Doesn't seem to have been solved. I'm having the same problem. Someone please report here if you get it working.

---

### Post by Ux64 on 2007-11-15
Nope, it seems that aMule is broken. At least it's Kad seems to be loosing contact all the time even if I take fresh nodes.dat from my eMule.

Luckily eMule runs just fine with Wine. I would use aMule if it wouldn't be this badly broken.

I have to check out [aMule forums]("http://forum.amule.org/").

Thread about [aMule's Kad]("http://forum.amule.org/index.php?topic=11992.0").

---

### Post by Sukarn on 2007-11-16
> **Ux64 said:**
> Nope, it seems that aMule is broken. At least it's Kad seems to be loosing contact all the time even if I take fresh nodes.dat from my eMule.

Luckily eMule runs just fine with Wine. I would use aMule if it wouldn't be this badly broken.

I have to check out [aMule forums]("http://forum.amule.org/").

Thread about [aMule's Kad]("http://forum.amule.org/index.php?topic=11992.0").


Thanks for the link to the thread about aMule's Kad.

Weirdly, aMule has a habbit of quitting suddenly without any warning when I update the Kad nodes. I guess I'll just use eMule with wine.

---

### Post by planejason on 2008-02-05
I just tried the svn version posted [[COLOR="Blue"]_here_[/COLOR]]("http://www.mediafire.com/?1ogcqmibz2m") by [[COLOR="Blue"]_this guy_[/COLOR]]("http://forum.amule.org/index.php?topic=13700.0"), and can report that they have fixed the KAD problem in version 2.2.  I installed the .deb file from the command line because I wanted to see if there were any errors reported but there were not other than missing dependencies because I uninstalled 2.1.3 first.  I went this route because I'm not confident enough yet to build it from the cvs source.  You could probably just let the package manager take the .deb file from the bowser instead of doing all this if you don't like command lines.  It is important to uninstall the non working version before installing this one.  If you want to wait for the official release it looks like they are getting close.  Meanwhile, I'm back to amule again :mrgreen:

[[COLOR="Blue"]_amule site(which seems to be down right now)_[/COLOR]]("http://www.amule.org/")

[[COLOR="Blue"]_Link to cvs source_[/COLOR]]("http://www.hirnriss.net/?area=cvs")

---

### Post by mad_max0204 on 2008-02-12
There is a nice solution for this.

I had the same problem. I set the server.met ur to [http://www.gruk.org/server.met.gz](http://www.gruk.org/server.met.gz) and it worked like a charm :D

---

### Post by Ux64 on 2008-02-18
I have to admit that these aMule problems lead to network transition which I have been putting of for years.

Now I happily use [**Deluge Torrent**]("http://deluge-torrent.org/") and I have forgotten whole **ED2K** already.

I also uninstalled **Wine** because I don't need it anymore. eMule was last Windows application that I were using.

---

### Post by Sukarn on 2008-02-18
> **Ux64 said:**
> I have to admit that these aMule problems lead to network transition which I have been putting of for years.

Now I happily use [**Deluge Torrent**]("http://deluge-torrent.org/") and I have forgotten whole **ED2K** already.

I also uninstalled **Wine** because I don't need it anymore. eMule was last Windows application that I were using.

I still use wine, mainly to compile and check whether the applications I code work correctly on a windows system because I don't have a seperate windows installation anymore to test my applications before I pass them on in my friend circle.

I use torrents as well as the emule network. Which of them I use depends on what I'm looking for.

I must admit, I have not tried running emule in wine. I shall try that soon and see how well it runs. If it runs fine in wine, I'll get rid of amule because that is obviously causing more trouble than its worth if emule runs in wine.

---

### Post by Ux64 on 2008-02-29
> **Sukarn said:**
> I shall try that soon and see how well it runs. If it runs fine in wine, I'll get rid of amule because that is obviously causing more trouble than its worth if emule runs in wine.

It runs just fine, and it's better than aMule.

---

### Post by Sukarn on 2008-03-01
eMule in wine seems to fail while trying to connect to some servers, and then it just crashes within a few seconds of opening it.
I don't have time to debug this problem right now. I've got important exams going on.
I shall look into this once I have some spare time. I just came online today for a while after having an exam today.

---

### Post by Darth Arturito on 2008-03-25
Had the same problem. I solved it this way:

I added an official server list:

```
http://www.gruk.org/server.met.gz 
```

I remembered that I had emule running on windows and I have opened two ports for

**eMule**
```

TCP - 4663

UDP - 4673
```

and I realized that aMule needs:

**aMule**
```

TCP - 4662

UDP - 4672
```

Silly thing but that was the first time ever I had a problem with aMule. Great piece of software. :-) 
Hope that helps anyone.

---

### Post by Ux64 on 2008-06-08
> **Darth Arturito said:**
> **aMule**
```

TCP - 4662

UDP - 4672
```


Ports are freely configurable, so that's not the real cause.

---

