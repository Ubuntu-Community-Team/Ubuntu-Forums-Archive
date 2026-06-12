---
title: "swap like crazy"
date: 2005-10-13
forum: Desktop Environments
---

### Post by thomasmathiesen on 2005-10-13
My problem is that breezy swaps like crazy.

After running firefox and thunderbird, the swap usage increases. When it reaches 100%, the machine is just "stuck".

I have one machine running the final release, and two running RC1. All have the same problem. I've used the automated "fdisk" utility in the installer, so I haven't touched the size (etc) for swap.

Anyone else having these problems?

My hardware is 2 and 3 GHz machines with 256-1024 MB RAM.

Shouldn't be a problem.. but it is.

Cheers
/Thomas

---

### Post by ansorg on 2005-10-13
Do you have the Beagle Search index running on those machines? 

I made the experience in one Ubuntu and one Gentoo Installation that the beagle-daemon is gradually eating memory over time. 

Don't think that FF and TB alone could be the reason

Jens

---

### Post by thomasmathiesen on 2005-10-13
Nope.. not even installed beagle :(
Is there any kind of output that would help pasting in this thread?

---

### Post by snarkout on 2005-10-13
When you are deep in swap, take a look at top (from a teminal, run top) and see what's eating up memory.  Sounds like a major leak in some app you run on all 3 boxen though.

---

### Post by GeneralZod on 2005-10-13
Yes, please post the output of "top".  My money is on Firefox as it is full of memory leaks.  I have 512MB RAM, the same as swap, and a fast harddrive and on two separate occasions Firefox had consumed so much memory that it exhausted RAM and swap, and took *1 and a half minutes* of disk-thrashing to finally settled down after I closed it (closing tabs won't help; you have to close Firefox itself).  I always use Session Saver for situations like this; it makes closing and re-opening Firefox much less painful.

I've also seen Azureus eat up tons of RAM, but oddly enough it is X memory it seems to use, as if it's allocated tons and tons of images (xrestop reported it as using 250MB), so maybe you could look into this if you use Azureus at all.

---

### Post by thomasmathiesen on 2005-10-14
oki.. here's the top output (sorted on virtual memory), if firefox is running:

------------------------------------------------------------------------------------------------
up 38 min,  2 users,  load average: 0.29, 0.41, 0.36
Tasks:  78 total,   2 running,  76 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.4% us,  0.3% sy,  0.0% ni, 90.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1035964k total,  1023004k used,    12960k free,    12992k buffers
Swap:  1236964k total,   581368k used,   655596k free,   182368k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6976 root      15   0 1358m 702m 9948 S  3.7 69.4   2:24.67 Xorg
 8612 thomas    16   0  103m  27m  11m S  0.0  2.7   0:11.04 mozilla-thunder
 8642 thomas    16   0 98560  31m  14m S  4.3  3.1   1:11.25 firefox-bin
 9285 thomas    15   0 40312  16m 9892 S  1.3  1.6   0:01.90 gnome-terminal
 7480 thomas    15   0 38092 5532 4872 S  0.0  0.5   0:00.42 gnome-cups-icon
 7470 thomas    16   0 31008  10m 7880 S  0.0  1.0   0:01.43 nautilus
 7468 thomas    16   0 23436  11m 7728 S  0.0  1.1   0:03.58 gnome-panel
 7512 thomas    16   0 23036 7888 6164 S  0.0  0.8   0:00.35 clock-applet
 7508 thomas    15   0 21628 8752 6292 S  0.0  0.8   0:00.69 mixer_applet2
 7033 hplip     16   0 20808  836  832 S  0.0  0.1   0:00.00 hpiod
 7482 thomas    16   0 20336 9680 6468 S  0.0  0.9   0:04.58 wnck-applet
 7495 thomas    16   0 19716 7960 5696 S  0.0  0.8   0:00.37 trashapplet
 7478 thomas    15   0 19412 7696 6060 S  0.0  0.7   0:00.47 update-notifier
 7424 thomas    16   0 19300 5240 4604 S  0.0  0.5   0:00.44 gnome-settings-
 7369 thomas    16   0 18708 5484 5000 S  0.0  0.5   0:00.37 x-session-manag
 7514 thomas    16   0 18708 7276 5700 S  0.3  0.7   0:07.55 multiload-apple
 7506 thomas    16   0 18552 7028 5528 S  0.0  0.7   0:00.21 notification-ar
------------------------------------------------------------------------------------------------

Here's an output (minutes later), after shutting down firefox. See that Xorg is using 1358MB when using firefox, and reduces to 347MB when firefox has been shutdown.

------------------------------------------------------------------------------------------------
top - 09:55:46 up 39 min,  2 users,  load average: 1.34, 0.75, 0.48
Tasks:  78 total,   1 running,  77 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.0% us,  0.3% sy,  0.0% ni, 95.6% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1035964k total,   380932k used,   655032k free,    13468k buffers
Swap:  1236964k total,   178208k used,  1058756k free,   171548k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6976 root      15   0  347m  97m 9956 S  1.3  9.6   2:37.25 Xorg
 8612 thomas    16   0  103m  23m  11m S  0.0  2.3   0:11.12 mozilla-thunder
 9285 thomas    15   0 40312  16m 9892 S  2.7  1.6   0:02.58 gnome-terminal
 7480 thomas    15   0 38092 5532 4872 S  0.0  0.5   0:00.44 gnome-cups-icon
 7470 thomas    15   0 31008  10m 7884 S  0.0  1.0   0:01.44 nautilus
 9327 thomas    15   0 25000  15m   9m S  0.0  1.5   0:01.90 gedit
 7468 thomas    15   0 23436  11m 7732 S  0.0  1.1   0:03.74 gnome-panel
 7512 thomas    16   0 23036 7888 6164 S  0.0  0.8   0:00.37 clock-applet
 7508 thomas    15   0 21628 8752 6292 S  0.0  0.8   0:00.70 mixer_applet2
 7033 hplip     16   0 20808  836  832 S  0.0  0.1   0:00.00 hpiod
 7482 thomas    15   0 20444 9724 6468 S  0.0  0.9   0:04.92 wnck-applet
 7495 thomas    15   0 19716 7960 5696 S  0.0  0.8   0:00.38 trashapplet
 7478 thomas    16   0 19412 7696 6060 S  0.0  0.7   0:00.49 update-notifier
 7424 thomas    15   0 19300 5244 4608 S  0.0  0.5   0:00.46 gnome-setting
------------------------------------------------------------------------------------------------


It takes about 1minute to shut down firefox after it has started to swap like crazy.

I have the same problem on all my machines. It may be because I am using Egroupware for my email, and it refreshes every 2 minutes (or so..). However, Opera can handle it well.. and I've been using Hoary and Warty, and had no problems at all.

I'll try anything you tell me to, so just shoot :)

---

### Post by thomasmathiesen on 2005-10-14
Ok. Using Opera instead now.. but swapping seems to be a problem (still).. but it takes more time before it starts swapping like crazy. Here's a top output, where swap is pretty high

-----------------------------------------------------------------------------------------------------
top - 11:53:32 up  2:37,  2 users,  load average: 1.53, 0.89, 0.57
Tasks: 104 total,   1 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.0% us,  0.7% sy,  0.0% ni, 91.0% id,  0.3% wa,  0.0% hi,  0.0% si
Mem:   1035964k total,  1003172k used,    32792k free,    12156k buffers
Swap:  1236964k total,   661216k used,   575748k free,   256796k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6976 root      15   0 1253m 544m  12m S  2.7 53.9  16:48.98 Xorg
 9350 thomas    15   0 87796  36m  11m S  0.0  3.6   1:05.19 opera
12160 thomas    15   0 52716  11m 9828 S  0.0  1.1   0:00.16 kio_http
-----------------------------------------------------------------------------------------------------

See the Xorg? Is that normal? It kills me at times..

---

### Post by GeneralZod on 2005-10-14
[QUOTE=thomasmathiesen]
See the Xorg? Is that normal? [/QUOTE]

Seems pretty high to me, although I only have 512MB RAM so I'm not sure how big it should be with 1GB....

See if xrestop is installed (run it from a terminal) - if not, 

```

sudo apt-get install xrestop

```

should install it.  Post the results here, please, and we'll see what's gobbling up all your RAM :)

---

### Post by CospeFogo on 2005-10-14
[QUOTE=GeneralZod]...My money is on Firefox as it is full of memory leaks...[/QUOTE]

I bet on that too. Plenty of problems of this nature here, yet I keep using it because I can't get used to Opera.

---

### Post by thomasmathiesen on 2005-10-14
Here's the output from xrestop (when swapping is going mad):

------------------------------------------------------------------------------------------------------
xrestop - Display: localhost:0
          Monitoring
 28 clientPixmaps: 1539239K total, Other:     110K total, All: 1539350K total

res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier
3a00000   232   36    1 5007   82   917622K      9K 917631K   ?   Network infrastructure - Wiki - Mozilla Firefox
1200000   138   37    1  971   49   177519K      6K 177525K  7470 Desktop
0e00000   125   23    1  758   41   140962K      5K 140968K  7468 Bottom Expanded Edge Panel
3c00000    99   35    1  525   75    89285K      5K  89291K   ?   Inbox for [email]tmathiesen@visualitylife.com[/email] - Mozilla Thunderbir1a00000    23   20    0  443   33    82651K      1K  82653K  7468 wnck-applet
2000000    12   20    0  105   15    19493K      1K  19495K  7468 mixer_applet2
2a00000    46   21    1   80   47    19395K      3K  19399K   ?   thomas@linprofs: ~
0c00000    13   21    2   82  691    15393K     18K  15412K  7463 metacity
1400000    10   20    0   76   12    14247K   1008B  14248K  7468 hook-notifier
2400000    16   25    0   69   17    11825K      1K  11826K  7468 multiload-applet-2
1e00000   124   24    1  608  248    10068K     10K  10078K   ?   Editing Road Warrior - Edit - Wiki - Opera 8.5
2600000     8   21    0   51   14     9377K      1K   9378K  7468 clock-applet
2200000     9   20    0   50   11     9189K    960B   9190K  7468 notification-area-applet
3400000    22   21    1   48   22     8636K      2K   8639K  7468 Gaim
1c00000     5   20    0   41    8     7503K    792B   7504K  7468 trashapplet
2800000     0    0    0    1    0     5120K      0B   5120K   ?   <unknown>
0600000     2    2    0    2   10      384K    336B    384K  7369 gnome-session
1000000     4   20    0    2    6      187K    720B    188K  7472 gnome-volume-manager
4600000     3   20    0    2    4      187K    648B    187K 11707 evolution-exchange-storage
1600000     3   20    0    2    4      187K    648B    187K  7480 gnome-cups-icon
0a00000     1  103    1    0  917        0B     24K     24K   ?   screensaver
0800000     4    1    0    0  487        0B     11K     11K  7424 gnome-settings-daemon
0200000     0    1    1    0    0        0B      1K      1K   ?   <unknown>
3e00000     2    1    0    0    4        0B    168B    168B 10353 kdesu
1800000     2    1    0    0    3        0B    144B    144B  7484 notification-daemon
2c00000     1    1    0    0    0        0B     48B     48B   ?   xrestop
------------------------------------------------------------------------------------------------------

Regarding opera; try konquerior.. I see that my swap go crazy when I run either of these apps:

Gaim
Firefox
Thunderbird

Good alternatives are
Kopete
Konquerior
Kmail

/T

---

### Post by trey on 2005-10-15
To free up most of your memory being stuck in gnome bloat/feature land

1) open terminal
2) type:  killall gam_server

I found that gam_server was using over 289MB of actual RAM and I'd only been using the system withour relogging in or reboot for 1.5 days.  I did however use Nautilus a lot with file previews.  When I turned previews back to Local Files Only, it greatly reduced used RAM from gam_server.  I then just killed it (it will respawn) and got a boatload of RAM back.

---

### Post by thomasmathiesen on 2005-10-15
Doesn't help. Found out that OpenOffice give me the same problem. I'm wondering if there is something really wrong with the memory handling somewhere in Ubuntu.. The more KDE apps I use, the less problems I see, so I am wondering if it's Gnome 2.12

---

### Post by thomasmathiesen on 2005-10-15
Smells like I have found the problem.... themes!

I always use a GTK and Metacity theme called something like "RPanther". Changing back to the original (ugly brown ;) ) theme, I no longer have a swap problem!

That's why KDE apps has been ok on my machine, while Gnome apps has been killing me..

Here's some tip on how to solve swap problems in Gnome 2.12:
[http://www.opensubscriber.com/message/ubuntu-devel%40lists.ubuntu.com/2210395.html](http://www.opensubscriber.com/message/ubuntu-devel%40lists.ubuntu.com/2210395.html)

---

### Post by karl.william on 2005-10-15
I don't know, I just installed Kubuntu on this machine, and I have exactly the same problem, well, not exactly, havn't got my swap full yet, but it hogs all of my memory! the longer I have the machine going, the more memory it hogs :/

---

### Post by thomasmathiesen on 2005-10-15
1. Try switching to the default theme (icons etc.) if you have changed that to something else. 

2. Use konquerior instead of firefox

3. Use kmail instead of thunderbird.

I am not used to kubuntu, but I reckon you use a couple of Gnome apps there as well. It smells like this is a Gnome problem.. (sad to say).

/T

---

