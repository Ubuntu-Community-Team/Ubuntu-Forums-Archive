---
title: "How can I use Strigi ?"
date: 2008-11-02
forum: Desktop Environments
---

### Post by AKoine on 2008-11-02
Hi there,

I feel a bit stupid, but I can't work out how to use strigi.
I recently installed Kubuntu Intrepid (I was using gnome before, with beagle and the deskbar applet), installed strigi-client, checked in Nepomuk if strigi daemon was running (it says it's up), but can't find the way to use it ...

In the Konsole, "strigi-client" - or anything close to it I could think of - returns a "command not found" ...

Any thoughts ?

Cheers !

---

### Post by benerivo on 2008-11-02
Try Alt+F2 on the desktop and type strigiclient

---

### Post by AKoine on 2008-11-02
This would do it, thanks !

Unfortunately, I get a QDBus Error : I start it through the console, eventually get a strigiclient window after 10 or 15 sec, and then no way to type or click anything, the window is like frozen. If I reduce it and put it back on screen, it's all blank, and after a while I get this in the console :

```
QDBusError("org.freedesktop.DBus.Error.NoReply", "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.")
QDBusMessage(type=MethodCall, service="vandenoever.strigi", path="/search", interface="vandenoever.strigi", member="getStatus", signature="", contents=() )
```
And then I must kill it ...:(

---

### Post by benerivo on 2008-11-02
Can't help you with that error message, but when i open strigiclient, it is a very basic program that only allows you to choose which folders you want to be indexed. You can do exactly the same in the Nepomuk section of the KDE4 System Settings.


I haven't found much on the web yet that tells you how to use its search functions, but i'm not convinced that i have it fully installed. There are some statistics displayed that mention how many files have been indexed and what the size of the index is in MB. On mine it says it has indexed 0 files and the index is 0 MB, even though it was all over my hard drive for about half an hour. When i click on Find in Dolphin, it doesn't display any more info on the files than it did before.

---

### Post by AKoine on 2008-11-02
All right,

After a reboot, it seems to work. I get a fonctionnal window saying "Documents in queue 0
Documents indexed 0
Index size: 0MB"

Two buttons allowing me to stop the daemon and stop indexing, and, below, 2 directories (i.e. ~/ and ~/.kde dir) which I don't seem able to change (even if I click on the "add directory" button, and select my ~/Documents dir, it doesn't do anything).
And, obviously, when I type anything in the space at the bottom of the window, I don't get any match (not really surprising if 0 file are indexed ...).

Any solution ?

BTW, I'm not especially fond of Strigi, I'd be fine with tracker or beagle if there is a simple way to use these on KDE 4 ...

Thanks anyway

---

### Post by benerivo on 2008-11-02
I've logged out and back in, and now when i type a search at the bottom of strigiclient it's giving me results from my indexed folder. It's basic, but it works. It is still telling me i have 0 documents indexed and that the index is 0MB.

---

### Post by AKoine on 2008-11-02
Thanks for the info.
I doubt it'll work on my computer, since strigi daemon has been running for several days now, and that I have no results to my searches ...

I hope I'll find a solution: beagle saved my life several times when I was on gnome desktop ...

---

### Post by AKoine on 2008-11-03
I found a replacement : installing the package kio-beagle. It comes with a lot of gtk depencies though.

I'm still interested if someone knows a way to get strigi to work ...

---

### Post by AKoine on 2008-11-05
Ok,

As mentioned somewhere else, recoll seems to be pretty efficient too, and comes with very limited dependencies (on Kubuntu, at least). sudo apt-get install recoll. I think I'll use that one.

Hope this will help someone else ...

---

### Post by lorebett on 2008-11-13
I've just installed kubuntu 8.10 and started Nepomuk from the section of the KDE4 System Settings.

when I start strigiclient (by the way, why isn't there a menu item for this?) no document has been indexed and if I try to do something I see in the syslog file:

kernel: [ 1713.614391] strigidaemon[5259]: segfault at 0 ip 080526d0 sp b53d7e40 error 4 in strigidaemon[8048000+51000]

was anyone able to use strigi?

---

### Post by krazyd on 2008-11-13
strigi/nepomuk don't work in any useful way in kde 4.1.x. They'll be up and running in 4.2 though (already are in trunk I believe)

---

### Post by shadwstalkr on 2008-12-06
I don't understand why the Kubuntu maintainers are enabling things that simply don't work by default.  I think Strigi has been the default search engine in Kubuntu for three releases now, and has never worked correctly.

---

### Post by lorebett on 2008-12-07
I agree!
I never managed to have it working...

---

### Post by sheepdogj15 on 2008-12-07
from my understanding strigi is a "required" part of KDE so it can't be uninstalled without bad things happening. 

what bad things I don't know. 

KDE4 in general seems unfinished. it looks good, it works really well, but they need to bring back the customability that made 3.5 teh awesome. ...and fix broken parts like strigi.

---

### Post by lorebett on 2008-12-08
> **sheepdogj15 said:**
> from my understanding strigi is a "required" part of KDE so it can't be uninstalled without bad things happening. 


since it was not working I've uninstalled strigi, and nothing bad happened actually... :confused:

---

### Post by wecaoniddmab891 on 2008-12-08
is [jordan shoes](http://www.smkings.com) good enough for play basketball?

---

### Post by Ubuntiac on 2009-12-09
> **lorebett said:**
> I've uninstalled strigi, and nothing bad happened actually...


Notice that we never heard from lorebett on this thread again... 
That's why I'm not brave enough to uninstall core operating system components! ;)

---

### Post by lorebett on 2009-12-09
Actually I never had the chance to try strigi again... for the moment I'm pretty happy with beagle.

Is strigi still used in kde 4?

---

### Post by kch on 2010-04-07
> **benerivo said:**
> Try Alt+F2 on the desktop and type strigiclient

I have not a strigiclient

---

### Post by Ubuntiac on 2010-04-07
These days it seems to all be done in Dolphin with the search bar in the top right corner.

Still a bit hit and miss, but getting better. Just don't try to search for anything starting with a period like .jpg or .htaccess

---

### Post by lorebett on 2010-04-07
so do you think strigi is usable these days?

---

### Post by Ubuntiac on 2010-04-07
Generally, yeah. It's taken a long time to get there, and occasionally the process dies, but as long as you avoid periods at the start I'd say it's working. (a bold statement, I know! ;))

I should note that I'm referring to it working on Lucid, not Karmic... Only 22 days until Lucid goes wild though!

---

### Post by jetpeach on 2010-05-03
so how exactly _does_ it work? i don't see anything in dolphin that shoes a search? i tried control-f in dolphin, which brings up a find files dialog, and there is a "use index" check box i can click. when i use that, the searches still take a pretty long time.

strigi on the bottom right says it's idle and i believe it has indexed all my files, but i'm still not getting where the client actually is?

i'm running lucid, upgraded and strigi was installed and such. it used a simply massive amount of memory and cpu on one of my machines for basically an entire day and even now, a look at top shoes a ton of resources being used by stuff i can't even find out how to use! what is nepomukservices, virtuoso-t, and why do they need gigabytes of memory? i only have two gigs in this machine (it's now very slow because its disk caching the memory), is that simply not enough physical memory or KDE anymore?

ok, sorry for the rant, but can anybody answer how to use strigi?

from top
```

2127 jet       20   0 1681m 554m 2836 S    0 27.6   4:04.07 nepomukservices                                                                                                       
 1974 jet       20   0 1077m 327m  17m S    0 16.3  33:21.46 plasma-desktop                                                                                                        
 1689 root      20   0  372m 102m  10m S    0  5.1  34:51.14 Xorg                                                                                                                  
 2131 jet       39  19  585m  87m 3904 S    0  4.4  85:48.33 nepomukservices                                                                                                       
 2017 jet       20   0  161m  68m 2696 S    0  3.4 105:47.19 virtuoso-t 
2008 jet       20   0  465m  17m 2368 S    0  0.9  47:31.21 nepomukservices
2128 jet       20   0  216m 5476 1584 S    0  0.3   3:50.38 nepomukservices
2132 jet       20   0  172m 3864 1860 S    0  0.2   4:54.83 nepomukservices                                                                                                       
 2447 jet       20   0  146m 3660 2568 S    0  0.2   0:00.93 klauncher
2130 jet       20   0  278m 3416 1604 S    0  0.2   4:05.10 nepomukservices                                                                                                       
 1966 jet       20   0  310m 3332 1816 S    0  0.2   0:06.05 ksmserver                                                                                                             
 1977 jet       20   0  228m 3296 2044 S    0  0.2   0:05.00 knotify4
2005 jet       20   0  285m 2588 1312 S    0  0.1   0:03.16 nepomukserver

```
free -m showing how with all my physical memory eaten, my computer has turned into a 286...
```

             total       used       free     shared    buffers     cached
Mem:          2008       1982         26          0         34        164
-/+ buffers/cache:       1784        224
Swap:         5883       1247       4635

```

---

### Post by Ubuntiac on 2010-05-04
No, that's the older search interface that doesn't use Strigi at all if I remember correctly. To use strigi desktop search:


1. Go to System Settings -> Advanced Tab -> Desktop search and enable both Nepomuk and Strigi
2. Wait for it to say it's finished indexing (if you hover over the Nepomuk icon in the systray a tooltip should say "Indexing is idle.")
3. Right click in an open space to the right of the menu's in dolphin and enable "Search toolbar".
4. Search in the toolbar! (Or Kickoff, or Krunner) :)

---

### Post by jetpeach on 2010-05-04
wow, that is one slick search! really nice to search the _contents_ of PDF files as well!
thanks Ubuntiac for the specific description of how to enable the search toolbar, i clicked just a little too low (where the icons were) before when i tried and didn't see the option....
cheers

---

### Post by Ubuntiac on 2010-05-05
Yeah. Kind of ironic that you really need to search around to find the search toolbar... :)

---

