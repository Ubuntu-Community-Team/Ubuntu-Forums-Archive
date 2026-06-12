---
title: "Compiz Memory Leak"
date: 2007-10-18
forum: Desktop Environments
---

### Post by jsgarvin on 2007-10-18
I realize that there are a few other threads on the same subject, but I think that this might be different and apply to a broader audience.

With a recent install of Gutsy, I've seen Compiz (as enabled and configured by default now) gradually uses more and more memory.  With a little testing, I've found I can reproduce it very easily.  Having the "Window Decoration" plugin enabled seems to greatly exacerbate the problem, I don't believe it's the source of the problem.

It appears to me that whenever a window or menu opens, Compiz take a little more memory, but when that window/menu closes, that memory doesn't free up.  This can be very easily demonstrated  by...
[LIST]
[*]Run 'top' in a terminal window and use Shift-M to sort by memory.  Find 'compiz.real' in the list.
[*]Open an application. See the memory compiz uses go up.
[*]Close the application. See that the compiz memory does *not* go down.
[*]Re-open the application. See the compiz memory go up further.
[*]Rinse, Lather, Repeat.
[/LIST]

For a slight more disturbing demonstration.

[LIST]
[*]Make sure the 'Window Decoration' plugin is enabled.
[*]Click "Applications" in the menu on your task bar to open that menu.
[*]Move your mouse back and forth over 'Applications' -> 'Places' -> 'System' -> 'Places' -> 'Applications' causing each menu to automatically open and close repeatedly.
[*]Notice the compiz memory usage gradually go up, and up, and up.
[/LIST]

I think I would find it difficult to believe that I'm the only person seeing this.  I've tried turning off different plugins to see if it's one of them.  As I said above, the Window Decoration plugin makes it much worse, but I suspect it's not the "Window Decoration" plugin's responsibility to free up consumed memory when windows and menus are closed, so I think the problem is actually more fundamental than any one plugin.

the fact the Compiz (and the Window Decoration plugin) are enabled by default on new Gutsy installs, I think I would consider this a pretty significant issue. "Normal users" will just notice hat after a while their machine starts to really crawl and eventually freeze up unless they reboot frequently.

---

### Post by frenkel on 2007-10-18
You might want to read this: [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by jsgarvin on 2007-10-18
I realize that Linux manages memory much differently than lesser OS's by keeping certain frequently accessed info cached in memory. That was the most detailed description I've seen of exactly what is going on and why though, so thanks for the link.

However, I don't believe that's what's happening here.  If it was, my second example above wouldn't have resulted in compiz taking up more and more memory simply by re-opening the "Applications" menu repeatedly.  Sure, a little memory would have been necessary the first time, but if it were caching that, then the next time it should have pulled that info from the memory cache, not eat up even more memory every time the menu opens again.

---

### Post by rrdharan on 2007-10-19
There's definitely a *massive* memory leak in the Compiz as released with Gutsy.

Frenkel, it's not just an issue of uncommitted virtual memory. I just had to power cycle my system because Compiz was using 1.7GB of *RESIDENT* memory (not just address space), and the machine locked up when I tried to kill it. 

This is pretty sad, considering compiz is supposedly one of the big new features of Gutsy. It must be a late regression as part of the Gutsy squeeze - I didn't see this when running compiz-fusion on Feisty.

---

### Post by olavjunior on 2007-10-19
I've had the same problem ever since I started using gutsy beta. So I did a fresh install oping this memory leak was caused by the fact it was a beta. But it's still the same, so I have to to a metacity --replace and then compiz --replace to free up memory. 

I hope someone will fix this, cause as you said, this makes new users just think ubuntu is sluggish and slow, cause system gets unusable after a couple of hours...

EDIT: I've done your "test", and I'm experience the exact same problem. So the trick will be to not close windows then.... all right...

---

### Post by z0phi3l on 2007-10-19
Must be something else, I ran the test and compiz real stays at 36mb and compiz at less than a meg

---

### Post by olavjunior on 2007-10-19
Well, that doesn't mean that it's not compiz doing this though... It might be the new nvidia-drivers..? Or compizs cooperation with these. I had compiz fusion running smoothly on Feisty.

---

### Post by gnuts on 2007-10-19
hello, gutsy clean install, amd64. I can not replicate your results. compiz.real remains at 1.5% opening and closing windows and moving across apps, places, and system menus with window decorator on. hope you get you situation resolved!

---

### Post by cuby on 2007-10-20
Hello.
The same here. 
With 7.04 my memory usage usually was bellow  300MB (I have 1GB) with the 3D stuff activated, but with gutsy it's usually above 600MB.
I was intrigued, investigated a little and found compiz.real using more than 300MB of resident memory (it is not shown by default in the system monitor).
This is a major problem because it really grows with time.
I think I'm going to report a bug...

---

### Post by cuby on 2007-10-20
Ok... it's confirmed.
There is a bug. See:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/151168]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/151168")

---

### Post by 23meg on 2007-10-25
I have the same issue with NVIDIA hardware; most likely a driver bug. 

nvnews.net thread: [http://www.nvnews.net/vbulletin/showthread.php?p=1420886](http://www.nvnews.net/vbulletin/showthread.php?p=1420886)

A workaround is to restart Compiz. All window positions are retained.

---

### Post by hoogland on 2007-10-25
another quick fix is to install xserver-xgl:

sudo apt-get install xserver-xgl

This seems to work for me on a laptop with an NVIDIA 7400 videocard. Now let's hope the devs at NVIDIA get a chance to fix the bug in their driver soon!

---

### Post by Spenzer4Hire on 2007-11-04
I've got 3 systems running 7.10.  All are nVidia with DE enabled.  The only one exhibiting the aforementioned memory leak is my only system running AMD64.  Is anyone seeing this in 32 bit Ubuntu?

---

### Post by Spenzer4Hire on 2007-11-05
Nevermind, answered my own question.  My AMD64 rig is the only one using nvidia-glx-new.

---

### Post by ironcamel on 2007-11-11
Nvidia claims they have fixed this bug and the fix will be present in the next driver release:
[http://www.nvnews.net/vbulletin/showpost.php?p=1442530&postcount=15](http://www.nvnews.net/vbulletin/showpost.php?p=1442530&postcount=15)
In the meantime, the work around I use is to run this once after I boot up:
<ALT><F2> compiz --replace --indirect-rendering

---

### Post by zippy028 on 2007-11-12
I haven't experienced this issue. current uptime is over 4 days and I haven't even noticed a slow down. I looked at top and I see Firefox using twice the memory of Compiz.real. Firefox at 7.7% or about 78MB and Compiz.real at 3.3% or 33MB use.

---

### Post by wormkid on 2007-12-06
My Gutsy crashes with compiz!!

compiz itselft doesn't take much memory.
but, with compiz, as I run and close applications, system memeory usage goes up and up.
finaly, it takes over 90% of my 2G ram and even I close all application, system memory doesn't go down under 50%.

sometimes, at that memory leaked moment, gnome doesn't show up after <ctrl><alt><backspace> + login. I have to reboot.

I wondered "is this realy caused by compiz?" and now turned off compiz and memory is under 50% for 2 days.(with compiz, I have to reboot or restart compiz everyday)

there's something with compiz or with nvidia.
I updated nvidia driver but it did no help.

I miss compiz's useful functions, and wish it solved soon.

---

### Post by kasulstyls on 2007-12-06
i just wanted to say I am also noticing a memory leak.  I tried the compiz --replace and releases the space on my ram.  Thanks for the quick tip!

---

### Post by wormkid on 2007-12-10
I tested something on my desktop Gutsy.

first, just off visual effects.
1. check starting memory. (16% mycase)
2. open about 100 bash terminals.
3. check memory (about 22%)
4. close all terminals.
5. check memory (16% again)

second, turn on compiz and check off all plugins (with no effects but just compiz itself)
1. check starting memroy (22% mycase)
2. open about 100 bash terminals again.
3. check memory (about 33%)
4. close all terminals.
5. check memory (27%)

is it only on my desktop's problem? compiz.real itself doesn't takes memory much but system memory does.

each application takes a little bit memory leak and finaly memory is full and crashes under compiz.

anybody has same problem?

---

### Post by RFScheer on 2007-12-10
Yes my system has been suffering this problem since Gutsy release and I've been doing the ```
compiz --replace --indirect-rendering
``` at startup for the past month or more, hoping the problem would be solved.

---

### Post by olavjunior on 2007-12-14
Isn't there updated nvidia-drivers yet?

And what's the thing with the --indirect-rendering. Does it slow the system down or affect the performance or something? Haven't tried it much yet

---

### Post by FuturePilot on 2007-12-14
The --indirect-rendering tells Compiz not to use the GPU. Instead you composite on the CPU. The drawbacks to this are that Compiz will use *a lot* more CPU resources since it's not being passed off to the GPU. Also Sync to VBlank is ignored which may result in some unsightly tearing.

---

### Post by DeadTaco on 2007-12-14
I am echoing olavjunior's question as well:  Are the new Nvidia drivers out?  What's the best way to check on that?

My system locked up solid at 100% processor usage for the fourth time this week, warranting a full hard reset.  Talk about frustrating.  Should I just uninstall compiz somehow?

---

### Post by kubug on 2007-12-17
OK, I had the same problem. It actually too 95% of main mem and added some 500meg of swap. Talk about sloooooooooow.

I think I have this fixed with the latest BETA driver from nvidia. I open applications and the memory clears up now.

Can somebody else please confirm that the BETA drivers (169.04) fix this?

---

### Post by LukePH on 2007-12-23
the leak is still there (using latests updates), this really needs to be fixed,

it's always leaking when compiz is on, and I've had my system lock-up from it using all my ram. It leaks so bad, I have to restart compiz pretty often.

---

### Post by kubug on 2007-12-24
Hi Luke,

are you using the latest BETA drivers from nvidia?? They are not included in the restricted drivers package. 

You'd have to download and install them, but it's not too difficult with nvidia.

---

### Post by olavjunior on 2007-12-27
I've just installed the beta drivers (169.04) and it looks good so far :)
exited! 

But the nvidia-installation proses is nothing I would suggest to noobs. It's a pity ubuntu doesn't support such updates through the restricted manager.

---

### Post by coreSOLO on 2007-12-29
nope sorry, I installed 169.07 and the issue persists. mem reaches close to 95% in a hour :(

I had to ultimately turn off compiz. Can a plugin be the cause here???

---

### Post by kubug on 2007-12-29
I know this may sound strange, since the 169.07 driver is newer, but try the current BETA drivers (169.04). Unless of course you have one of the new 8800GT(S)'s. 

See if it makes a difference. It did with me.

---

### Post by kubug on 2008-01-03
> **olavjunior said:**
> I've just installed the beta drivers (169.04) and it looks good so far :)
exited! 

But the nvidia-installation proses is nothing I would suggest to noobs. It's a pity ubuntu doesn't support such updates through the restricted manager.

Here is a quick how-to for installing the BETA drivers. 

Download them here:

For i386:
[http://us.download.nvidia.com/XFree86/Linux-x86/169.04/NVIDIA-Linux-x86-169.04-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/169.04/NVIDIA-Linux-x86-169.04-pkg1.run")

For 64 Bit:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/169.04/NVIDIA-Linux-x86_64-169.04-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/169.04/NVIDIA-Linux-x86_64-169.04-pkg2.run")[http://us.download.nvidia.com/XFree86/Linux-x86_64/169.04/NVIDIA-Linux-x86_64-169.04-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.04/NVIDIA-Linux-x86_64-169.04-pkg2.run)

Once you got them get all the dependencies:

```
sudo apt-get install build-essential
``` 

This should download the header files needed for the install.

Now, you should be able to close the X11 system and go on in text mode. Maybe you want to print this text from here on, since the browser will disappear when you enter the next command.

```
sudo /etc/init.d/gdm stop
```

Now get to where you downloaded the file to. Most likely on the desktop as mentioned earlier:

```
cd Desktop
```

Now run the file:

For i386:
```
sudo sh NVIDIA-Linux-x86-169.04-pkg1.run
```


For x64:
```
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
```

You can mostly likely just agree to everything it asks. The last question will be whether you'd want it to update the xorg.conf file automatically. I personally always say yes, but if you have spend hours trying to get JUST the right configuration, don't. In case you said yes and want to go back, it will have created a backup.

If everything went alright, you should now have the BETA drivers all up and running. 

Enter: 
```
sudo /etc/init.d/gdm start
```

... and should be right back in your Desktop, with the new drivers installed.

I did not discuss the removal of the old drivers, since that could be a bit more extensive, depending on how you installed them. It should theoretically be fine to install the BETA over your old ones, but don't call me on that one. ;-)

Hope this helped!

---

### Post by olavjunior on 2008-01-03
> **coreSOLO said:**
> nope sorry, I installed 169.07 and the issue persists. mem reaches close to 95% in a hour :(

I had to ultimately turn off compiz. Can a plugin be the cause here???

The problem is still present. But it takes much longer time now, so the leak is smaller. If the 169.07 is worse at this, I will def not install that one.. I've added a screen shot of what happens when I run compiz --replace when my system is sluggish.

---

### Post by kubug on 2008-01-05
My wifes computer runs ubuntu 7.10 w/ the nvidia 96.43.01 drivers on a 7600GT. I installed those drivers since they fixed a video playback and TV-out issue, but they seemed to also not have the memory leak. 3D and Compiz all work fine. 

My wifes computer has been running for about 2 weeks now without restart, and the memory hovers around 300MB (with a bunch of things running).

Just wanted to share. Maybe those drivers would be better with an older nvidia card?

---

### Post by Metaleks on 2008-01-06
I have the 64 bit version of Ubuntu.  If left at the login screen, and if I login about 10 hours after, half of my 2GB of ram will be taken up.  This has lead me to believe that the driver's memory leak happens before an Ubuntu session even begins.  But even if I login without waiting that long, it's basically a timed session, because after a few hours 1GB of RAM will be taken up.  I've never seen a memory leak as bad as this.

Can anyone else confirm the nVidia 96.43.01 drivers not having the memory leak?  Because I'm thinking I should install them.  I'll give the newest one's a try for now.

> **kubug said:**
> ```
sudo /etc/init.d/gdm stop
```
Also, I can't close the graphical session, I get some "device look-up failed" that keeps looping, not allowing me to input anything.  =(

---

### Post by kubug on 2008-01-06
> **Metaleks said:**
> 
Also, I can't close the graphical session, I get some "device look-up failed" that keeps looping, not allowing me to input anything.  =(

Wierd.... I am sorry, I am not sure why that's happening. 

What I do when I want to shut the GDM down (I once made a bad Metadata line in the xorg.conf, and had to work with a blank screen) is press ALT-F2 and enter "gksudo /etc/init.d/gdm stop". After entering the password, it shuts down immediately.

Dunno if that will help, since it's pretty much the same command as the other. :neutral:

---

### Post by NineseveN on 2008-01-09
Running 7.10 with eVGA Geforce 7600GS, default Ubuntu restricted drivers, Compiz enabled (+screensaver plugin) and I cannot duplicate this leak. Compiz releases memory exactly as it should for me.

I'll try on my laptop tomorrow just to see.

---

### Post by Keith Hedger on 2008-01-11
I also have the same memory leak but instead of manually resetting compiz if you edit the compiz startup script ie  sudo gedit $(which compiz) and scroll to the last line, after "$COMPIZ_OPTIONS" add  "--indirect-rendering" this saves doing a manual reset ad so far seems to be working ok for me

---

### Post by NineseveN on 2008-01-11
> **NineseveN said:**
> Running 7.10 with eVGA Geforce 7600GS, default Ubuntu restricted drivers, Compiz enabled (+screensaver plugin) and I cannot duplicate this leak. Compiz releases memory exactly as it should for me.

I'll try on my laptop tomorrow just to see.

Couldn't reproduce this on my laptop either...hmmm.

---

### Post by Xintruder on 2008-01-12
Hey guys, is there a temporary fix until nVidia uploads the new driver?
Thanks

---

### Post by Metaleks on 2008-01-24
A new driver is out.  169.09.  So far so good.

Can anyone confirm no memory leaks?  I just finished installing it.

---

### Post by cagljevic on 2008-01-27
I can reproduce the memory leak when running the compiz benchmark program.

while draging around different windows, the benchmark is running at a solid 60fps, but once I begin moving around / scrolling firefox windows the frames slowly begin droping and hovering around 20fps.  executing compiz --replace does not resolve it either, i have to restart x to get back to the way it was before i enabled the benchmark.

i normally turn off all the effects.  i just like accelerated window drawing, no tearing etc.  the added eye candy is not much of a concern for me.

169.09
nvidia 8600gt
gutsy 2.6.24-5
oss 1012
xorg 7.2

---

### Post by cuby on 2008-02-08
from [https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/151168](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/151168) 
The problem is very well explained by  Chris Rogers:
> [I]
 Chris Halse Rogers wrote on 2007-10-27: (permalink)

As far as I can tell, you will see this bug on any nVidia card with the nvidia-glx-new drivers, but only once you've exhausted the onboard texture memory. So I need to open a *lot* of windows on my 512Mb card before it starts leaking, but it still does. With 64mb of memory, you'll hit the limit much faster, but now instead of seeing black windows, the texture memory for that window will get added to compiz.real's memory space, and won't be released.

So, having enough more memory will greatly reduce the likelyhood that you trigger this bug, but cannot eliminate it entirely.[/I]

And Another Post:

 >  Chris Halse Rogers  wrote on 2007-11-01:  (permalink)

[I]Yes, see my comment above: <https://bugs.edge.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/151168/comments/72>

Previously, when the card ran out of video memory for window textures, you'd get all-black windows instead of the proper texture (the BWB). Using --indirect-rendering made it easier for the drivers to do this correctly (but you could still get black windows if you tried hard enough).

With the nvidia-glx-new drivers, they've done work to fix the BWB. Now, when you would normally get a black window, instead the memory for that window is leaked into the compiz.real process. And if you try *really* hard, you can still get black windows.

So, anything that used to reduce the incidence of black windows (more video memory, --indirect-rendering) will *reduce* (but not eliminate) the incidence of this bug.[/I]


---

### Post by olavjunior on 2008-02-15
Ok, thansk! Informative. But I didn't have this problem on Feisty. Maby it was an older driver. But I din't have the black window problem, or at least I had it eliminated. So then maby my xorg.conf are badly configurated, as maby the "addrgbglxvisual ="true"" or something like that will do the trick?? (I used to have these conf before..)

---

### Post by Discombobulated on 2008-02-17
This one was driving me mental for ages - now resolved with the 169.04 driver [COLOR="red"][([COLOR="Blue"]32-bit[/COLOR]]("http://www.nvidia.com/object/linux_display_ia32_169.04.html") / [[COLOR="Blue"]64bit[/COLOR])]("http://www.nvidia.com/object/linux_display_amd64_169.04.html"),[/COLOR] using these instructions:

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
sudo /etc/init.d/gdm start
```

7.10, AMD64

NVIDIA appear aware of the problem, have claimed it's fixed... ](*,)

[http://www.nvnews.net/vbulletin/showthread.php?t=100803](http://www.nvnews.net/vbulletin/showthread.php?t=100803)

---

### Post by kubug on 2008-02-26
Ok, here is a bit of an update. 

The problem is gone at home, with both my computer (8600GT) and my wifes computer (7600GT) with 169.09 drivers.

At work, I have a dual display on a 6150LE and the compiz leak is HUGE on the 169.09. Can someone with a dual display confirm this issue?? I am running them in Twinview (used to use Xinerama, but compiz doesn't work there).

It may be that the twinview part of their drivers still has that bug in it.

---

### Post by Kiri on 2008-04-04
I am still getting a leak sometimes from compiz running on hardy 8.04 on geforce go 7400 (64mb).

The memory usage is upto almost 600mb now (60% of my total ram).

Is there any workaround for this?
Or a way I can quickly release the memory and restart compiz?

---

### Post by ironcamel on 2008-04-07
See my earlier comment (#15) for a quick workaround.

---

### Post by Kiri on 2008-04-07
Thank you :)

---

### Post by adric22 on 2008-04-22
> **RFScheer said:**
> Yes my system has been suffering this problem since Gutsy release and I've been doing the ```
compiz --replace --indirect-rendering
``` at startup for the past month or more, hoping the problem would be solved.

Is there any news on this issue?  I just discovered it on my system.  I've been having to reboot once a day because my computer starts swapping like crazy.  System monitor wouldn't show it, but when I opened a terminal and ran TOP, I could see compiz.real eating about 550 MB of RAM.  So I did a search and found this thread.

---

### Post by kubug on 2008-04-22
Hi adric22,

what driver version do you use? I currently use the 169.12 on a TwinView setup (2 monitors). They seem to work ok with compiz. I don't have much of a leak anymore. Then again, I did upgrade to 4GB of memory. 

The thing now is that Thunderbird seems to gobble up my memory. Once I close thunderbird and reopen in it releases ~1.5GB of my memory. That is after I left my computer running for a couple days.

But no more problems with the nvidia memory leak for me (for now).

---

### Post by olavjunior on 2008-05-03
The problem isn't there anymore, or at least not as big as before. Top showed me that compiz real used 30% of my ram (2gb), and a compiz --replace pushed it down to 5%. But my system monitor shows no changes. I won't bother investigating why since it's not a problem any more

---

### Post by smartbei on 2008-05-09
I am still getting a memory leak, using driver 169.12 on a Geforce 6200 with 64mb onboard. It does appear to accumulate slower than under gutsy (right now at 100mb after a whole day - on gutsy it would be at 300mb after several hours).

---

### Post by HDave on 2008-06-05
I too am getting this problem on Hardy with an nVidia Geforce Go 7400.  Compiz takes about 3-4 hours to get to 400MB.

Doing a compiz --replace, resets everything.  

In the bug report, however, folks are report that the new driver (v173) is solving the problem.  We'll see....  In the meantime, I am thinking of writing a script that does a compiz --replace when compiz.real gets above 300MB!

---

