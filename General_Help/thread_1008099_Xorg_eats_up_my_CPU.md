---
title: "Xorg eats up my CPU"
date: 2008-12-11
forum: General Help
---

### Post by Piraja on 2008-12-11
Dear all,

my desktop machine's an old Compaq Evo D 510, 2 GHz, 512 MB RAM, Ubuntu Intrepid installed on an external USB hard drive partition.

CPU usage is quite high, often 100 %. Firefox uses often a lot of it, but it is actually Xorg that climbs to the top of top most of the time.

I happen to know the Intel driver has serious [bugs]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/284461") at the moment, problems with the integrated i845 G graphics card, for instance, which is indeed what my box has.

Here's the output of "sudo lshw -C Video":

```
**sudo lshw -C Video**
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

And here's an example of top output:

```
Tasks: 134 total,   1 running, 133 sleeping,   0 stopped,   0 zombie
Cpu(s): 53.3%us, 12.2%sy,  0.0%ni, 33.6%id,  0.0%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:    506120k total,   500056k used,     6064k free,     4272k buffers
Swap:  1052248k total,    58988k used,   993260k free,   116544k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5018 root      20   0  252m  37m 8792 S 37.6  7.6  62:24.28 Xorg               
29392 pprasane  20   0  232m 105m  26m S 12.5 21.3   6:02.74 firefox            
 5742 pprasane  20   0 31036 3616 2792 S  3.0  0.7   1:26.88 pulseaudio         
28481 pprasane  20   0 86440 5004 2576 S  3.0  1.0   1:12.42 mocp               
 5772 pprasane  20   0 22104  12m 8332 S  2.6  2.4   0:29.60 metacity           
31202 pprasane  20   0 21248 3680 2380 S  2.6  0.7   0:31.02 conky              
19146 pprasane  20   0  106m  30m  14m S  2.0  6.1   0:49.98 gnome-terminal     
 5777 pprasane  20   0 58396  28m  14m S  1.7  5.8   0:50.57 gnome-panel        
 5848 pprasane  20   0 21588 4964 4188 S  1.3  1.0   0:35.34 gnome-screensav    
31061 mpd       20   0 13428 3236 2052 S  0.7  0.6   0:01.26 mpd                
31331 pprasane  20   0  2416 1164  884 R  0.7  0.2   0:11.64 top                
 5780 pprasane  20   0 93956  35m  15m S  0.3  7.2   2:02.81 nautilus           
    1 root      20   0  1880  788  588 S  0.0  0.2   0:01.94 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:20.92 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0 
```

Is there anything to be done? From time to time more than 50 % of CPU usage goes to Xorg... Thanks in advance,

regards,

Piraja

---

### Post by kerry_s on 2008-12-11
that sounds like and looks like normal behavior from what i can see in your screen shot. your using heavy theming and conky, transparency, all that takes resources, xorg just happens to have to do the heavy lifting. everything you see on the screen is done through xorg, unless it's staying at 100% it's doing it's job.

---

### Post by Piraja on 2008-12-11
OK, thanks a lot, I thought as much. 

I was just wondering about the CPU usage because I'm not for instance using Compiz (it is actually blacklisted due to the Intel driver bug) on this machine &#8212; the transparency is just pseudo transparency &#8212; and I have significantly lower CPU and RAM usage on my second oldish machine, an Acer Travelmate 2350 laptop with a 1,3 GHz processor and 768 MB RAM; I'm even using Compiz ("Normal visual effects") without problems on it.

What is more, I'm using rather low-resource applications, such as Music on Console, which you can see in the screenshot. I have been experimenting also with a MPD-Ario-Lyricsdownloader-Conky constellation, but that is relatively resource-hungry.

So I'm wondering whether the Intel driver bug has anything to do with this; and a second thing is the fact that I'm running Ubuntu on an external USB hard disk drive &#8212; I suppose also this has its effects on performance, doesn't it?

I could certainly cut down on custom theming on this old desktop... Would you think the fancy dark themes affect performance significantly, compared with the default Human theme for instance?

---

### Post by Piraja on 2008-12-11
All right: I tuned down my desktop. Changed the dark theme and transparent Gnome panel to the default Human theme. I made a very basic conky setup. Now the CPU usage seems to have dropped drastically, at least with Firefox and MOC running; it varies between ca. 8% and 40% now, instead of 40-100%.  I suppose this is one of the lessons to learn with older hardware.

---

### Post by philinux on 2008-12-11
Yep if you bought or could buy a graphics card it would do the donkey work.

---

### Post by Piraja on 2008-12-11
I know... But the funny thing is that Ubuntu's been running pretty smoothly in spite of the regular 100% peaks of CPU usage. It doesn't crash, just slows down a bit for a moment. Windows wouldn't tolerate such behaviour on an old machine like this, I think...

---

### Post by liuji_dragon on 2008-12-11
I'm having the same issue, but my machine is much higher end.  Runing 32bit Hardy (upgrading to Ibex now) on a Dell M1730 - Core2Duo Extreme Edition at OC'd to 3.4Ghz, 4 gigs of ram, 160 gig hard drive, dual NVidia SLI 8700GT (running in single gpu mode, SLI tends to make Compiz stutter).  Running Gnome with Compiz enabled and a few effects and I'm constantly getting between 40 to 100% CPU usage from Xorg.  Absolutely nothing else is running.  

Does Compiz really suck up that much from Xorg?  My desktop environments with less powerful hardware dont have these issues...

---

### Post by Piraja on 2008-12-11
With your specs, that's more than a mild surprise. 

It would be interesting to know an estimate of how much different features affect Xorg's performance (by features I mean true or pseudo transparency in windows and panels, desktop background image size, theme attributes such as dark vs. light, etc.). 

As I'm writing this, I'm having 100% CPU usage all the time and 98% RAM usage: I'm using abcde right now and it's encoding wav files to mp3 with lame, and I noticed that lame sucks up quite a chunk (75% vs. Firefox's ca. 13-18%). Yet, I'm encountering no problems.

BTW, I did "abcde -o mp3,ogg"; in a moment I can make a comparison between the resource-greediness of the two encoders...

---

### Post by Piraja on 2008-12-11
> **Piraja said:**
> BTW, I did "abcde -o mp3,ogg"; in a moment I can make a comparison between the resource-greediness of the two encoders...
I'm quoting myself... The result of the comparison is: Wow! Oggenc uses less resources than lame, and seems faster too.

Words of explanation: **[B]abcde**[/B] is "a better cd encoder", namely a command-line cd ripper that can output into mp3, ogg, flac (did I forget some format?). The fact that "I did abcde -o mp3,ogg" means that I ripped a cd and chose both mp3 and ogg as output.

---

### Post by Piraja on 2008-12-11
I didn't give up on making a-my-kind-of-desktop... Just made a little less fancy "basic" Conky (on the right), but still using also another Conky for Lyricsdownloader (on the left) and some other candy stuff. In any case, it seems that Xorg's not at the top of the pops.. I mean the *top of top* any longer.

One thing I must repeat [oh darn, I did not say this already, as I later realized]: with Hardy, I could even use Compiz also on this desktop machine; with Intrepid it doesn't work, due to the Intel driver bug. And since the issue with CPU usage doesn't seem to be limited to my low-end hardware (see post #7), this might be a more considerable issue than it first seemed, I think. So I'm definitely not marking this thread as "SOLVED".

The background photo's by [.robbie](http://www.flickr.com/photos/rtv/2395920004/).

---

### Post by fragos on 2008-12-12
It may show up in Xorg but it is called by other applications using the display. Open idle windows use more CPU than when they are minimized. My TV card is a major CPU hog and shows up as Xorg. Every 30 seconds I get a peek of close to 100% CPU but it drops back down to average about 25% CPU.

---

### Post by Piraja on 2008-12-13
Thanks fragos, good points. Mine was not to blame the Xorg package; actually saying "Xord eats up my eye candy!" was just a bad joke. That is, I realize that it's not actually Xorg's fault.

---

### Post by Piraja on 2008-12-18
I must say I have learned a lot through paying attention to the Conky output lately and also through the conversation in this thread — so, thanks for that. 

For instance, I did not realize how much the open windows affect CPU usage. A moment ago I used my favourite synchronization application Grsync (GUI frontend for rsync) to sync my home user directory with another hard disk drive. CPU usage was pretty much 100% all the time, but the percentage varied a great deal between Xorg and Grsync (plus rsync) depending on whether the Grsync window was maximized or not. Whenever I minimized the Grsync window, the number one position of Top changed from Xorg to Grsync, i.e. the latter gained more resources than when the application window was maximized.

This taught me also a lesson on the advantages of using different workspaces, which were actually rather unclear to me previously. Nice!

---

### Post by Arjunanda on 2009-02-15
Hi,

This thread has been very helpful also for me. I was experiencing extreme sluggishness and Xorg eating upto 75% of CPU, as well as Firefox competing of the same cake.

Updating to Firefox 3.1b2 seem to have solved one half of the problem, but the issue with Xorg remains. I uninstalled compiz to make sure it is not the cause, but this did not help.

In my situation, Xorg eats up all CPU time for a period of several minutes and desktop becomes unresponsive. After some time it retunrs back to normal. I have no idea what is the cause for this.

Please see below my TOP listing.

```

user@ananda:~$ top

top - 16:15:56 up  5:39,  3 users,  load average: 1.97, 1.36, 1.06
Tasks: 126 total,   3 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s): 75.8%us, 19.1%sy,  0.0%ni,  0.0%id,  0.0%wa,  5.1%hi,  0.0%si,  0.0%st
Mem:   1284088k total,   892964k used,   391124k free,    39840k buffers
Swap:  1590424k total,    10764k used,  1579660k free,   403184k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
20529 root      20   0  295m  28m 8316 S 38.8  2.3   0:38.79 Xorg               
21140 user      20   0  300m 109m  27m R 17.1  8.8   0:55.39 firefox-bin        
21242 user      20   0  102m  23m  13m R 15.0  1.9   0:03.58 gnome-terminal     
20896 user      20   0 78064  34m  12m S 11.4  2.7   0:14.58 skype              
20799 user      20   0 13768 4552 3588 S  4.8  0.4   0:01.58 at-spi-registry    
 4797 chipcard  20   0  4660 1224  928 S  3.9  0.1   3:18.04 chipcardd4         
 4873 haldaemo  20   0  6316 2888 2260 S  3.3  0.2   1:09.28 hald               
21267 user      20   0  2416 1148  876 R  3.0  0.1   0:02.84 top                
20863 user      20   0 22436 9428 7716 S  1.2  0.7   0:00.88 multiload-apple    
 1266 root      15  -5     0    0    0 S  0.6  0.0   0:06.60 ata/0              
 1770 root      15  -5     0    0    0 S  0.6  0.0   0:11.56 scsi_eh_0          
 2638 root      15  -5     0    0    0 S  0.6  0.0   0:12.50 b43                
 4988 root      20   0  3440 1040  888 S  0.6  0.1   0:13.68 hald-addon-stor    
20780 user      20   0  8208 5116 2276 S  0.6  0.4   0:00.98 gconfd-2           
20806 user      20   0 23684  14m 9580 S  0.6  1.2   0:01.58 metacity           
20856 user      20   0 22324 3320 1804 S  0.6  0.3   0:01.10 gnome-screensav    
    1 root      20   0  1740  536  456 S  0.0  0.0   0:01.50 init               


```

---

### Post by Cannaregio on 2009-02-25
Heya, I notice that you are still allowing [COLOR="Blue"]chipcard[/COLOR] to run.
This is nonsensical. All debian distros (so ubuntu too) ship with the chipcard deamon running per default even if one user on a million actually has any need for that. 
This not only violates all sound & holy GNU/Linux principles, but almost 4% of a GNU/Linux running CPU represents *de facto* ten thousand of kw wasted worldwide :-)

So kill it for good. As everyone and his aunt should do.

```
sudo apt-get remove chipcard
```

One parasite less, one!

Cheers!

---

### Post by Arjunanda on 2009-02-25
Thanks Cannaregio, chipcard-tools removed. And that process also disappeared.

---

### Post by fragos on 2009-02-25
> **Cannaregio said:**
> Heya, I notice that you are still allowing [COLOR="Blue"]chipcard[/COLOR] to run.
This is nonsensical. All debian distros (so ubuntu too) ship with the chipcard deamon running per default even if one user on a million actually has any need for that. 
This not only violates all sound & holy GNU/Linux principles, but almost 4% of a GNU/Linux running CPU represents *de facto* ten thousand of kw wasted worldwide :-)

So kill it for good. As everyone and his aunt should do.

```
sudo apt-get remove chipcard
```

One parasite less, one!

Cheers!

I'm runnning Ubuntu 8.10 and couldn't find any element of chipcard running.

---

### Post by Wush.S.H on 2009-02-25
I have never encountered such a problem. I have a machine of E5200 and G43 chipset, the cpu usage is below 10% when no application is opened.

---

### Post by jjpcexpert on 2009-02-25
Well my CPU:
Intel Celeron 530 1.73 GHz CPU
And RAM: 1GB DDR-2 or 3 SODIMM (So Dim) - It is a netbook
And Swap: Wubi=0.9GiB and RAM is quite underloaded, even when loads of apps are running.
And (GP)GPU: Mobile Intel 965 Express Chipset Family, Compiz running fine. ](*,)
Get a 965 graphics chipset if the problem bothers you, it will make the CPU a CPU again instead of a GPU aswell.

---

### Post by Arjunanda on 2009-02-25
I think that may have got in at some stage - I have been updating since Dapper if I can remember correctly.

Btw, just today there was update to adobe-flash player. Let's see if the performance clutch got fixed.

---

