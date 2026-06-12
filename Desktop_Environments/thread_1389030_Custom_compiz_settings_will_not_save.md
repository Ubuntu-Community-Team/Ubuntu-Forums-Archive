---
title: "Custom compiz settings will not save"
date: 2010-01-23
forum: Desktop Environments
---

### Post by Starman~ on 2010-01-23
I am experiencing a similar problem as this thread but I do not use the fusion-icon.
[http://ubuntuforums.org/showthread.php?t=1319173]("http://ubuntuforums.org/showthread.php?t=1319173")

Compiz will not save custom settings when compiz-settings-manager is used. It will save setting thru "Simple-settings-manager". 
In addition, some settings will not take effect immediately. Example: The "viewport switcher" in "Desktop-wall". Color changes will not take effect unless I change the "preview scale".


> System:    Host Astroman Kernel 2.6.31-14-generic i686 (32 bit) Distro Linux Mint 8 Helena - Main Edition
CPU:       Single core AMD Athlon XP 2600+ (UP) cache 256 KB flags (sse) bmips 4009.1 clocked at 2000.00 MHz 
Graphics:  Card nVidia NV34 [GeForce FX 5200] X.Org 1.6.4 Res: 1280x1024@50.0hz 
           GLX Renderer GeForce FX 5200/AGP/SSE/3DNOW! GLX Version 2.1.2 NVIDIA 173.14.20 Direct Rendering Yes
Audio:     Card Creative Labs SB Live! EMU10k1 driver EMU10K1_Audigy at port a400 
           Sound: Advanced Linux Sound Architecture Version 1.0.20
Network:   Card-1 Marvell 88E8001 Gigabit Ethernet Controller driver skge v: 1.13 at port a000 
           Card-2 nVidia nForce2 Ethernet Controller driver forcedeth at port ec00 
Disks:     HDD Total Size: 160.1GB (19.6% used) 1: /dev/sda WDC WD1200JB-00E 120.0GB 
           2: /dev/sdb ST340014A 40.0GB 
Partition: ID:/ size: 11G used: 2.8G (28%) fs: ext3 ID:/home size: 23G used: 340M (2%) fs: ext3 
           ID:swap-1 size: 0.80GB used: 0.00GB (0%) fs: swap 
Info:      Processes 131 Uptime 21 min Memory 267.7/1002.5MB Client Shell inxi 1.2.6 


Re-installation of setting managers had no effect.
Suggestions for a linux neophyte?

---

### Post by Starman~ on 2010-01-24
Re-installation of all compiz packages failed to rectify the issue. There seem to be various forms of this issue around. Has anyone found a solution?

---

### Post by Starman~ on 2010-01-26
Still looking for assistance on this issue. There are various reports of similar problem around the net, but none address a solution. Some work arounds have been tried but no-joy for my problem. This is my 3rd fresh install of Mint and the first two were easier fixed by replacement. I'd very much like to solve this. I've been frustrated with releases of Ubuntu having various problems. Some research points towards an issue with "GConf Configuration Backend", but I'm guessing.

So, before I throw in the towel. Anyone want to give this a shot? I'm eager to learn from the experience.
I went back to square one, I have completely removed compiz and associated packages including mint-meta packages.

---

### Post by Starman~ on 2010-01-26
Looks like I'm not the only one with this problem 
[http://ubuntuforums.org/showthread.php?p=8727864#post8727864](http://ubuntuforums.org/showthread.php?p=8727864#post8727864)

Is there anyone willing to assist that has the know-how?

---

### Post by Starman~ on 2010-01-27
Okay, I'm begging. Anyone?

---

### Post by Starman~ on 2010-01-29
So much for community support. I'm overwhelmed.

After so much time wasted, I did one last fresh install of Karmic instead of Mint. I now recognize that there is a bug or several in the compiz package/plugins.
It worked better back when I was running Hardy. 

So where do you go to actually get help with a problem? All I'm doing here is talking to myself.

---

### Post by Rubicon421 on 2010-05-05
Same problem here. I have Ubuntu  10.04 32 bit installed on a P4 with a Radeon 9200 GPU. Initially the  extras were missing from Compiz. I got that part figured out and now  have all the features I was missing. 

The weird thing is that when I go to  System>Administration>Hardware Drivers it says that there are no  proprietary drivers in use (none listed as active or in the available  section below). In 9.10 on this same system it found the driver. Compiz  is working but acts a little funny now. It seems like my desktop will  randomly un-compost itself. One minute the desktop cube will work and  then a few minutes later it goes back to having desktop effects set to  none. Usually I have to restart to get it back to normal. When I restart Compiz is running but all the custom effects I had selected get reverted back to default. 

I also have Ubuntu Tweak installed. I installed several Compiz packs  through the Software Center but have not done anything extra in Synaptic  or the terminal. It's a clean install of 10.04.

I have noticed a few times when using the rotate cube feature (CTRL+ALT+mouse drag) that it will cause the desktop to uncompost. This may be an unrelated problem or another symptom of the same issue, not really sure.

---

### Post by soulspit on 2011-05-16
I have what is probably the same or related problem. I can save my settings successfully, but the problem is that individual settings - not all of them at once - keep resetting back to the default. This seems to only happen while the Settings Manager is open.

Basically what I have is a race against Compiz, where, for example, I set the shortcuts for navigating my workspaces, and then wobbly windows settings get reset to default, so I go set wobbly windows again, and find that the shortcuts for resizing windows have been reset, etc. It happens pretty inconsistently though. Eventually I can usually manage to get everything the way I want it, and I export the profile so that in the future I can go back to it if everything gets reset. But it's a huge pain...

Someone must have some ideas!

My system:
```
System:    Host tensile Kernel 2.6.38-8-generic x86_64 (64 bit) Distro Ubuntu 11.04 natty
CPU:       Quad core Intel Core i7 Q 720 (-HT-MCP-) cache 6144 KB flags (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips 12768.8         
           Clock Speeds: (1) 1600.00 MHz (2) 933.00 MHz (3) 933.00 MHz (4) 933.00 MHz (5) 933.00 MHz (6) 933.00 MHz (7) 933.00 MHz (8) 933.00 MHz                                                                                                                                       
Graphics:  Card: ATI Madison [Mobility Radeon HD 5000 Series] bus-ID: 02:00.0 X.Org 1.10.1 Res: 1920x1080@59.9hz                            
           GLX Renderer ATI Mobility Radeon HD 5000 GLX Version 4.1.10665 Compatibility Profile Context Direct Rendering Yes                
Audio:     Card-1 Intel 5 Series/3400 Series Chipset High Definition Audio driver HDA Intel bus-ID: 00:1b.0                                 
           Card-2 ATI Redwood HDMI Audio [Radeon HD 5600 Series] driver HDA Intel bus-ID: 02:00.1                                           
           Sound: Advanced Linux Sound Architecture Version 1.0.23                                                                          
Network:   Card-1 Intel Ultimate N WiFi Link 5300 driver iwlagn v: in-tree: bus-ID: 05:00.0                                                 
           Card-2 Broadcom NetLink BCM5784M Gigabit Ethernet PCIe driver tg3 v: 3.116 bus-ID: 0b:00.0                                       
Disks:     HDD Total Size: 500.1GB (37.0% used) 1: /dev/sda ST9500420AS 500.1GB 38C                                                         
Partition: ID:/ size: 390G used: 173G (47%) fs: ext4 ID:swap-1 size: 7.68GB used: 0.00GB (0%) fs: swap                                      
Sensors:   System Temperatures: cpu: 49.0C mobo: 26.8C                                                                                      
           Fan Speeds (in rpm): cpu: N/A                                                                                                    
Info:      Processes 201 Uptime 29 min Memory 1381.3/5970.4MB Runlevel 2 Client Shell inxi 1.4.98
```

---

### Post by wildmanne39 on 2011-05-16
> **soulspit said:**
> I have what is probably the same or related problem. I can save my settings successfully, but the problem is that individual settings - not all of them at once - keep resetting back to the default. This seems to only happen while the Settings Manager is open.

Basically what I have is a race against Compiz, where, for example, I set the shortcuts for navigating my workspaces, and then wobbly windows settings get reset to default, so I go set wobbly windows again, and find that the shortcuts for resizing windows have been reset, etc. It happens pretty inconsistently though. Eventually I can usually manage to get everything the way I want it, and I export the profile so that in the future I can go back to it if everything gets reset. But it's a huge pain...

Someone must have some ideas!

My system:
```
System:    Host tensile Kernel 2.6.38-8-generic x86_64 (64 bit) Distro Ubuntu 11.04 natty
CPU:       Quad core Intel Core i7 Q 720 (-HT-MCP-) cache 6144 KB flags (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips 12768.8         
           Clock Speeds: (1) 1600.00 MHz (2) 933.00 MHz (3) 933.00 MHz (4) 933.00 MHz (5) 933.00 MHz (6) 933.00 MHz (7) 933.00 MHz (8) 933.00 MHz                                                                                                                                       
Graphics:  Card: ATI Madison [Mobility Radeon HD 5000 Series] bus-ID: 02:00.0 X.Org 1.10.1 Res: 1920x1080@59.9hz                            
           GLX Renderer ATI Mobility Radeon HD 5000 GLX Version 4.1.10665 Compatibility Profile Context Direct Rendering Yes                
Audio:     Card-1 Intel 5 Series/3400 Series Chipset High Definition Audio driver HDA Intel bus-ID: 00:1b.0                                 
           Card-2 ATI Redwood HDMI Audio [Radeon HD 5600 Series] driver HDA Intel bus-ID: 02:00.1                                           
           Sound: Advanced Linux Sound Architecture Version 1.0.23                                                                          
Network:   Card-1 Intel Ultimate N WiFi Link 5300 driver iwlagn v: in-tree: bus-ID: 05:00.0                                                 
           Card-2 Broadcom NetLink BCM5784M Gigabit Ethernet PCIe driver tg3 v: 3.116 bus-ID: 0b:00.0                                       
Disks:     HDD Total Size: 500.1GB (37.0% used) 1: /dev/sda ST9500420AS 500.1GB 38C                                                         
Partition: ID:/ size: 390G used: 173G (47%) fs: ext4 ID:swap-1 size: 7.68GB used: 0.00GB (0%) fs: swap                                      
Sensors:   System Temperatures: cpu: 49.0C mobo: 26.8C                                                                                      
           Fan Speeds (in rpm): cpu: N/A                                                                                                    
Info:      Processes 201 Uptime 29 min Memory 1381.3/5970.4MB Runlevel 2 Client Shell inxi 1.4.98
```

Hi, you can not enable any effect in compiz when running unity, if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all. I hope this helps.:D

---

### Post by soulspit on 2011-05-16
> **wildmanne39 said:**
> Hi, you can not enable any effect in compiz when running unity, if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all. I hope this helps.:D

That sounds like it could have been a sure-fire winner, but I'm running KDE! Compiz effects certainly work, and I can enable them, it's just that the settings of individual plugins simply seem to randomly reset to default settings, one at a time in arbitrary order. They still work, but the shortcuts, settings, etc. change. It's quite bizarre. :(

---

### Post by Copper Bezel on 2011-05-16
Very strange. Are you using the flat-file backend or gconf? I'm assuming flat-file, if you're using KDE?

I'm still on 10.10, but I've never had this happen before, myself. I know Natty's Compiz is weird, but if the problem had to do with the changes to Compiz's interaction with gconf, it shouldn't make any difference while you're using flat file storage. Huh.

---

### Post by soulspit on 2011-05-16
I'm using the "KDE4 Configuration Backend". I'm going to give flat-file a go and see if it fixes things - I wasn't even aware of that option what's the difference? I see that "enable integration into the desktop environment" gets grayed out when I choose flat-file backend. It sounds very relevant, though, so hopefully this fixes the problem!

Yeah, compiz does all sorts of weird things in Natty Kubuntu. For example, no matter what I do, my Skype system tray icon (and any other non-KDE systray icon, like VLC) will not go into my system tray in the task bar, and instead insists on floating in the upper left corner of my screen, on top of everything. I should open another thread about that...

---

### Post by Copper Bezel on 2011-05-16
Yeah, give that a go, and we can deal with any other problems if they develop. I've never used the KDE backend, but I've never had any trouble with the flat file.

The system tray icons having a transcendental experience is the weirdest Natty issue I've heard yet and easily my favorite. I'm sorry that it's at your expense, but I thank you for the laugh. = ) (And yes, go ahead and start a topic; you can't be the only one, and someone will be Googling for a solution at some point.)

---

### Post by UltraParadigm on 2013-01-24
I checked out the profiles in compiz, and I noticed that I'm not using the default profile, I'm using one called "Unity".  There are two settings which keep returning to default when I reboot (most of the time).  So I went to the default profile and set them like they are set in the "unity" profile.    I'm thinking that when those settings return to default, now maybe they wont change since the default is the same.     I dunno, just trying it.  I'll report back.

Ubuntu 12.10

---

### Post by oldos2er on 2013-01-24
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

