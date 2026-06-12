---
title: "Possible memory/swap problem?"
date: 2006-01-23
forum: Desktop Environments
---

### Post by PerfectSelf on 2006-01-23
This is the second time this problem has occured over the past couple of days. I was in Firefox 1.5 both times - not sure if there's a correlation - but here it is:

Originally, after having spent some time (usually an hour or more) working and browsing through various programs, Ubuntu started to become a big sluggish and slow to respond. It was nothing too serious at first, but when I browsed to a rather graphics-intensive page on a particular forum, the system became terribly slow. A minute or more would pass by before simple commands such as clicking to minimize a window would execute. A similar deal happened today except I had many tabs opened in Firefox along with OpenOffice Writer going. I checked my system resources: 100% CPU usage, user memory and used swap were both sitting around 100%. I eventually had to do a hard reboot.

I run Ubuntu on my laptop which is a couple of years old and has 512 MB RAM. The swap file is 619.6 MB and was set by the system during partitioning.

This is all the info I can think of to put down at the moment. Any help or advice is appreciated.

---

### Post by GeneralZod on 2006-01-23
Several apps have done this to me, namely, Azureus (contains some kind of image memory leak that makes xorg take up progressively larger and larger amounts of RAM until the system becomes unusable) and - dum-dum-dum! - Firefox! Once, Firefox damn near crashed my system when I hadn't even used it for a few days - I left my machine on while I went back home to visit my Mum, ssh'd in a few times over the next few days, and every thing was fine.  A few days later, I tried again and it took ages to connect and ages to type when I finally logged in.  I ran "top" and 30 seconds later got some output.  Firefox was taking up a huge amount of RAM, kswapd was taking up 100% CPU, and all my swap and RAM were full.  I managed to type "killall firefox-bin" and, a minute later, everything was back to normal and swap and RAM usage had halved.

So the moral of this story is to close Firefox regularly (I use the SessionSaver extension to remember all my tabs, so this is pretty painless) and don't leave it running when you go away for a few days! ;)

---

### Post by PerfectSelf on 2006-01-23
I gave that a shot. I closed out Firefox completely along with any other application I was running at the time. After letting things just sit for several minutes on the desktop, I checked memory usage again. No changes. Memory was still maxed.

---

### Post by kaamos on 2006-01-23
have you tried using top or gnome-system-monitor to see whick applications are eating the resources?

---

### Post by PerfectSelf on 2006-01-23
I was able to pull out a 'top' before I had to reset the desktop this time. Firefox is definitely eating up some memory, but I also noticed Xorg was sitting around 60 in the %MEM column.

---

### Post by GeneralZod on 2006-01-24
[QUOTE=PerfectSelf]I was able to pull out a 'top' before I had to reset the desktop this time. Firefox is definitely eating up some memory, but I also noticed Xorg was sitting around 60 in the %MEM column.[/QUOTE]

You can install and use xrestop to find out what is making xorg take up so much memory.  Are you running Azureus at all? As I mentioned earlier, that has been known to inflate xorg to enormous size.

---

### Post by lasermike026 on 2006-01-25
I'm having the same problem.  When I've been using firefox for an extended period of time, firefox and Xorg gobbles up memory and swap.  When I kill firefox, Xorg releases memory.

---

### Post by lasermike026 on 2006-01-25
what do we think?

top - 17:07:26 up 7 days,  3:58,  5 users,  load average: 0.89, 0.74, 0.45
Tasks: 115 total,   5 running, 109 sleeping,   0 stopped,   1 zombie
Cpu(s): 19.7% us, 25.1% sy,  0.0% ni, 55.2% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    508748k total,   500564k used,     8184k free,      796k buffers
Swap:  1048568k total,   758060k used,   290508k free,    57280k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6803 root      16   0  265m 117m 5568 R 25.3 23.7  18:51.34 Xorg
13540 user1  15   0  191m  88m  22m R  1.0 17.8   1:08.03 firefox-bin
 7484 user1  17   0  449m  46m 1456 S  3.3  9.4   3:45.85 gconfd-2
 3986 user1  15   0  264m  43m 8392 S  0.7  8.7   1:15.45 evolution-2.4
 3994 user1  15   0  209m  41m 4468 S  2.0  8.4   1:13.97 evolution-excha
13801 root      15   0 44136  29m  16m S  0.0  5.9   0:05.82 synaptic
12278 user1  15   0 48212  16m 9796 S  0.0  3.2   2:45.53 gaim
23570 user1  16   0 27296  10m 6044 S  0.0  2.0   0:07.18 gedit

xrestop - Display: localhost:0
          Monitoring 35 clients. XErrors: 0
          Pixmaps:  131532K total, Other:     205K total, All:  131737K total

res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier
3400000   590  100    1 1091   75   117255K     18K 117274K   ?   Mozilla Firefox
1e00000     0    0    0    1    0     5120K      0B   5120K   ?   <unknown>
4000000    94   86    1   18   56      863K      6K    870K   ?   Synaptic Package Manager

---

### Post by lasermike026 on 2006-01-26
memory hogs:
gconfd-2
evolution-exchange connector
firefox
Xorg

---

### Post by towsonu2003 on 2006-01-26
firefox has a well known memory leak bug when you let it open for a long time and / or access multimedia rich pages. there is a chance this won't be fixed even in firefox 2.0. xorg's memory will go up with firefox using more memory. try apt-getting xrestop and looking at the memory usages from within X (type xrestop in a terminal).

---

### Post by lasermike026 on 2006-01-26
Ok, I found these instructions from here...
[http://fusion94.org/archives/2005/07/firefox_memory.html](http://fusion94.org/archives/2005/07/firefox_memory.html)

I'm trying them now.  We'll see how it goes.  i used 16384k (16mb) as my int value

1)Type about:config into the location bar and press enter
2)Right click any line to bring up a sub-menu
3)Choose "new">"integer"
4)paste this into the dialogue that appears: browser.cache.memory.capacity
5)Next click Okay
6)Specify the amount in kb (about 60000 should do) in the next dialogue that appears
7)Restart Firefox and happy surfing.

---

### Post by lasermike026 on 2006-01-26
I also found referrences to a plugin called fasterfox.  There is an option in fasterfox to set your browser.cache.memory.capacity.  The plugin seems to have some other cool features too.  You can get it at [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)

---

### Post by lasermike026 on 2006-01-26
Could it be that Ubuntu really needs 1gig of memory to perform well, especially when running firefox and evolution?

---

### Post by towsonu2003 on 2006-01-26
[QUOTE=lasermike026]Could it be that Ubuntu really needs 1gig of memory to perform well, especially when running firefox and evolution?[/QUOTE]
I don't think it could be the case, from a logical perspective. If you are designing an OS for a wide audience, you can't count on the audience having such high tech parts... especially in linux, which is famous for nicely running old systems. than you'd be labeled as a bad distro all over the place. both of the programs would go down as well. 

I suppose what ubuntu needs for good performance is 256MB RAM + 500MB Swap. 

personally, my ram usage is between 150MB (just launched firefox) and 350MB (firefox leaked memory for about 8 hours AND a couple of java and multimedia rich content rendered) and no swap usage. not sure about evolution as I don't use it. with a leaked firefox memory + evolution, I'd say you would go up to 500MB if evolution leaks memory too (which is NOT an optimal thing at all) but not higher. restarting firefox from time to time should save you some headaches. 

some evolution users might help us out here about their average memory usage.

you can monitor your memory usages running xrestop in a terminal + top in another and taking a look at them every 30 minutes. that should give u a nice idea about what goes wrong when you do something or another. This is just a diagnostics suggestion, not something you do normally running linux / ubuntu / anyotherdistrohere.

PS. did those steps helped you fixing the memory leak?

---

### Post by lasermike026 on 2006-01-27
Well, it looks like reducing memory cache capacity and fasterfox has improved the issue of a growing firefox.  Maybe fasterfox should be added to ubuntu's firefox by default.

Evolution seems to have a significant memory leak.  In a 24 hour period is sucked up about 1 gig of memory and 1 gig of swap.  But I think the evolution thing is a minor issue.

gconfd-2 on the other hand is bothering me.  This daemon has sucked up a bunch of memory.  I've killed and restarted it which helps.  I don't know what this daemon does but I'm looking into it.

What is gconfd-2?

---

### Post by lasermike026 on 2006-01-27
I think i'm going to try xfce until they fix this thing.

---

### Post by lasermike026 on 2006-02-02
ok, so I sart using to xfce desktop and evolution emailer.  Process gconfd shows up again and it sucks up memory.  I think the gconfd is tied to evolution.  I'm using thunderbird and i don't see the memory problem with gconfd.  I'm back using gnome desktop.

---

### Post by towsonu2003 on 2006-02-02
[QUOTE=lasermike026]ok, so I sart using to xfce desktop and evolution emailer.  Process gconfd shows up again and it sucks up memory.  I think the gconfd is tied to evolution.  I'm using thunderbird and i don't see the memory problem with gconfd.  I'm back using gnome desktop.[/QUOTE]
may be it's time for you to search in bugs and file one if there is none?

---

### Post by nauticalthinker on 2006-03-31
To answer the question about "What is gconfd-2?"

Well, it stands for Gnome Config Daemon.  It similar to the windows registry system, but for Gnome.  

I too have recently discovered a memory leak associated with using Breezy.  The culprit was gconfd-2.  I'm a net admin for a small company, and we use Exchange 2003 as our mail server (not my choice btw).  I refuse to conform to using Windows, so Linux is my OS of choice.  Using Evolution-Exchange works amazing well, but have had trouble since trying out Breezy.  My version of gconf is 2.12.0, so maybe I/we should attempt to upgrade that to the test version (2.14.0 I believe).  This is something I may try today.  I'll report back my findings.

---

### Post by nauticalthinker on 2006-04-03
Okay...So, I didn't actually update gconfd-2, but did update some things associated to gconfd-2.  In KDE I used the Adept Updater utility to update my system.  It updated libc6 and a few other components, but I suspect that libc6 was the key.  Gconfd-2 needs libc6 to operate.  This was done the day of my previous post, and so far I've not experienced any swap or memory problems since.  I'm still watching things though.  In TOP, gconfd-2 runs around 10% mem as opposed to what it was before ( 50% Mem + ).  Hope this helps.  If I discover otherwise, then I'll be sure to post it.  :cool:

---

