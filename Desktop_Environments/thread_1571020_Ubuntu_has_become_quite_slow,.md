---
title: "Ubuntu has become quite slow,"
date: 2010-09-09
forum: Desktop Environments
---

### Post by monk11 on 2010-09-09
I am running 9.10 (not upgraded to 10.x as there are known os level bug for some of the app I run). After taking upgrade of patches (that come automatically), system is darn slow. It runs smoothly after a fresh restart, but eventually becomes slower after say few hrs. Though it has 3gb ram, it sucks big time. "top" doesn't show any spike either. Is there a known issue as such?

---

### Post by bcz on 2010-09-09
You dont mention which programs you run or what processor you are using

IMHO the latest Firefox changes slow down the system badly when complex adds are displayed by various websites.  Previously the features to animate the adds did not work atall.  Now they seem to work (but not properly on my machine anyway) and make firefox annoying to use on medium speed hardware, because the overhead of viewing adds we dont want anyway is now much higher.  Scrolling the page so the adds disappear gets normal performance, but due to layout, this is not always possible

I  have installed new firefox add-ons recently and this might be the cause of the slowdown, rather than firefox itself

I dont know if this ia part of your problem

Am running 9.04 with latest updates, running heavy C compilation load, email and web browsing.  I only reboot about once a month and dont notice any degradation.  Could be a memory loop in a program you are running

Rgds Bill C

---

### Post by monk11 on 2010-09-09
Hey Bill:
Thanks for reply.

Processor: Intel(R) Core(TM)2 Duo CPU     T6670  @ 2.20GHz.
These are java programs on the line of hadoop (an open source map-reduce program); and are quite cpu intensive. Do you need other info?

I also think it is because of firefox, because there were bunch of firefox related updates that I installed and I used it like (2-3 windows with 10-12 tabs in each of them: don't know if it is heavy). Initially youtube was one of them but the "great" npviewer flash program forced me to quit watching it. but still "top" says its load not more than 7-10%. 

Is there any better option for firefox? Any sugestions.

---

### Post by inkrypted on 2010-09-09
To check and make sure it is Firefox slowing down your computer try an alternative browser such as Opera. I really doubt that Firefox would bog your entire system down especially with your specs.

---

### Post by monk11 on 2010-09-12
i am quite sure there is a memory leak in firefox 3.6.8 that i am using. I started it, and keep checking the mem status free -m, and it kept on decreasing gradually; from 2GB of free mem to 1GB of free mem in approx 1 hr.
and yes, i was checking the buffer/cache line.

---

### Post by monk11 on 2010-09-13
Oh! Ubuntu sucks, and it does big time now! While running it on a 2.2 GHz processor with 3Gb of Ram, I bet it is running even slower than windows vista on a 1 GB RAM m/c. And all credit is to memory consumption, that seems to be leaving only 20-40 MB free... rest all is consumed in some mystique processes. I know about its disk cache policy etc, and it shows to be using caching heavily, but God knows what it is caching. All my process, all of them, are running so slowly that I am regretting my decision of removing Windows 7 and installing this piece of crappy os. I know my language is not decent, but it is really very frustrating to sit on my system anymore.

free -m:
             total       used       free     shared    buffers     cached
Mem:          2885       2864         20          0          1        191
-/+ buffers/cache:       2671        213
Swap:         8346       1067       7278

/proc/meminfo:
MemTotal:        2954364 kB
MemFree:           24352 kB
Buffers:            1048 kB
Cached:           196148 kB
SwapCached:       124904 kB
Active:           666412 kB
Inactive:         185512 kB
Active(anon):     639044 kB
Inactive(anon):   160568 kB
Active(file):      27368 kB
Inactive(file):    24944 kB
Unevictable:           0 kB
Mlocked:               0 kB
.................

Can someone help me in sorting this? or is it just a wonderful feature in ubuntu now?

---

### Post by 3Miro on 2010-09-13
List of things that you can check:

1. Go to System -> Admin -> System Monitor (or was it Prefs -> SM) and check the memory usage for the individual processes. You should be able to see what is taking up all that RAM. Depending on what it is, you can stop/remove/disable/fix the problem.

2. If you have trouble figuring out what is causing the problem, start closing apps and wait for couple of seconds after each closed app to see which one will free memory in the System Monitor. You cannot close system apps, but you will be able to narrow it down if it is a browser or media player or something like that.

3. Install FireFox flash block add-on, this will only show flash apps that you decide. This is the only way I can go to some very flash incentive web-pages. (flash by the way is entirely Adobe's fault and has nothing to do with Linux)

4. I have never used Opera, but Google-Chrome work way better than firefox (and also has flash block).

Basically if everything is OK after a fresh install, you simply have a rogue process that you have to find and eliminate (thought it is simpler said than done).

---

### Post by infamous-online on 2010-09-13
You could also try out Google Chrome for Ubuntu, or Opera as someone else suggested.

---

### Post by freshminted on 2010-09-13
I am also new to Linux, and have found that Open Office slows steadily so that saving files can become a long operation. When used in Windows XP (apologies to those who hate that OS), Sun's version of OPen Office ran without a hitch. Have I done something that has caused this or is it commonplace? I do run just OO without other programmes open in the background.):P

---

### Post by 3Miro on 2010-09-13
> **freshminted said:**
> I am also new to Linux, and have found that Open Office slows steadily so that saving files can become a long operation. When used in Windows XP (apologies to those who hate that OS), Sun's version of OPen Office ran without a hitch. Have I done something that has caused this or is it commonplace? I do run just OO without other programmes open in the background.):P

Hi, freshminted and welcome to the forum. Here, it is considered impolite to hijack someone else's thread with your unrelated problem. You should start a new thread, give the system that you are running (ubuntu/kubuntu/xubuntu 10.04, 9.10 ... ) and describe exactly what the problem is and what happens. Then people will help you. This thread is to help the the one who started it (monk11) with his problem.

---

### Post by finny388 on 2010-09-13
RAM will always appear to be fully in use because Ubuntu uses it as a cache for disk data, then releasing it to programs when requested. Faster to use RAM first rather than resorting to the slower swap file.

So RAM will almost always show 98-99% usage.

---

### Post by Taiji on 2010-09-13
> **monk11 said:**
> I am running 9.10 (not upgraded to 10.x as there are known os level bug for some of the app I run). After taking upgrade of patches (that come automatically), system is darn slow. It runs smoothly after a fresh restart, but eventually becomes slower after say few hrs. Though it has 3gb ram, it sucks big time. "top" doesn't show any spike either. Is there a known issue as such?


Ubuntu is getting bloated.

I am looking forward to Linux Mind Debian Edition, though I think its still a little buggy for my primary OS at this point.....Debian original + Mint adding codecs and adding to its ease of use seems to be a whole lot faster than Ubuntu. The interface is almost the same, but a few things are done differently.

---

### Post by Taiji on 2010-09-13
> **finny388 said:**
> RAM will always appear to be fully in use because Ubuntu uses it as a cache for disk data, then releasing it to programs when requested. Faster to use RAM first rather than resorting to the slower swap file.

So RAM will almost always show 98-99% usage.


I really wish that live CD sessions would use my SWAP first. This causes the RAM to run out and my session to end, even if I have 10GB of swap.

Are there any tricks to mounting a /tmp partition and getting a live session to use that instead of ram?

---

### Post by monk11 on 2010-09-13
FYI:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by God Of Atheism on 2010-09-15
I have a similar problem. After running the computer for a day or so, top sees nearly all memory as used and the computer slows to a crawl. Part of it might be disk caching, but in that case, the disk caching does not work as it should since it apparently fails to release memory. Using gnome system monitor I see a lot less used ram, but still it increases over time while the amount used by programs is far less. Memory leaks seem a likely explanation especially since the final lockup in firefox usually occurs when seeing some flash. Typical applications running the last week when this occurs:
Firefox 3.6 (now .9) with noscript, flashblock, adblock and various other plugins.
Audacious2 and pulse audio
usually at least one bash terminal, often with top running
often a few pdfs open with evince
often some text file open in gedit
gnome system monitor

All of the applications together maybe get to 2 GB, but top sees nearly 4 GB used (I have 4 GB in my machine).

Is there a good way to monitor memory use over time? For example, I left my computer on overnight, and when in the evening maybe 2.5 GB was seen as used by top, by morning this had grown to 3.5 GB. This does look like a memory leak, the thing is, which program is the culprit? The only programs actually doing anything, updating recources used, were gnome system monitor and top. Firefox and audacious were still open, but not doing anything, maybe I also had evince and/or gedit open, but again neither doing anything.

Using 9.10 amd64 btw, cpu is athlon II 245.

---

### Post by monk11 on 2010-09-15
what about the free -m command output. can you post that here.

In my case, I did found some programs (that i had installed). They were consuming memory (but top was not showing their consumption). After wiping them off, it is much better.

---

### Post by God Of Atheism on 2010-09-17
> **monk11 said:**
> what about the free -m command output. can you post that here.

In my case, I did found some programs (that i had installed). They were consuming memory (but top was not showing their consumption). After wiping them off, it is much better.

             total       used       free     shared    buffers     cached
Mem:          3962       3916         46          0        330       2423
-/+ buffers/cache:       1162       2800
Swap:         9538          0       9538

---

### Post by monk11 on 2010-09-17
> **God Of Atheism said:**
> total       used       free     shared    buffers     cached
Mem:          3962       3916         46          0        330       2423
-/+ buffers/cache:       1162       2800
Swap:         9538          0       9538

So, you indeed have 2.8 Gigs free RAM. Your system seems perfectly OK as far as memory consumption is considered. See the link I pasted just above your first message.

---

### Post by God Of Atheism on 2010-09-17
> **monk11 said:**
> So, you indeed have 2.8 Gigs free RAM. Your system seems perfectly OK as far as memory consumption is considered. See the link I pasted just above your first message.

I read that link earlier, but I encountered problems with the computer slowing to a crawl.

---

### Post by God Of Atheism on 2010-09-25
Now I notice the following:

1. Things are down to a crawl again
2. Top displays firefox as having 7741M virtual memory. I left firefox running overnight, it was downloading some files, but yesterday evening it has less than 1G real memory and no virtual memory. It seems something with caching goes wrong.
3. Initially nautilus and gnome also were slow, but it seems back to normal (for some value of normal).

---

### Post by yossman on 2010-09-25
i'm thinking a problem i've been fighting on and off for days here, to do with memory cache, is related to the issues on this thread (and others).  

if i ask nautilus to copy a directory tree containing 8GB and 1066 files from a windows network share mounted with smbfs, and i watch memory usage using top, the 'cached' memory count consumes all RAM i have within a matter of minutes, which didn't particularly worry me since that's what cache is basically designed to do; however, having filled up all my RAM, it then proceeds to start to move pages from cache to swap, and then i immediately get OOM problems -- the kernel out of memory killer, which then starts zapping processes seemingly at random until i'm left with an unusable desktop.

to add insult to injury, i see gnome-session now depends on nautilus -- so now i can't even use gnome-session and uninstall nautilus in favour of a different file manager to try to get around this problem.

is it too much to ask for some sort of cache control mechanism for nautilus? failing that, how about a gnome-session version that doesn't depend on nautilus?  if gnome-session requires nautilus now, why not combine that into a new package, something like 'gnome-session-nautilus', and have a version of gnome-session that doesn't require nautilus?  is there a way for me to affirmatively say that this is the fault of nautilus and not some other sub process that isn't directly mentioned in top?  ultimately i'd like to continue using nautilus, but not if it's going to be this massive a performance / stability problem.

i have already told nautilus to disable all previews on files, stop drawing the desktop, and cease showing volumes -- none of which has solved this problem.

this is pretty much a show stopper for me, and for any other people i'm trying to help switch to ubuntu from windows (a hobby of mine).  8GB and 1000 files is not a huge amount anymore compared to previous years, and i can't be telling people to avoid copying "large numbers of files" when using their computers, that's ridiculous. :confused: 

i think this bug may be related:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/174809](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/174809)

(note the bug was first filed in 2007.. sigh..)

edit: OK, doing further test copies shows that if i do local disk to local disk copy, the problem isn't nearly as bad, it doesn't kill any tasks.  if i use the smb:// nomenclature in nautilus to access the windows share, that also seems to work OK, no tasks killed.  mounting the share via smbfs and using that mount point to do the copying appears to trigger the never-ending upward RAM usage..  sorry this appears to be in the wrong thread now. ;-)

yossman

---

