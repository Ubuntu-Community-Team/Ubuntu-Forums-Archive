---
title: "High processor activity, problem on multiple machines (? screenlet related)"
date: 2009-05-31
forum: General Help
---

### Post by zcacogp on 2009-05-31
Chaps, 

I've posted this in "Absolute Beginner Talk", but thus far without any luck (although not for want of effort - thanks to all those who responded.) I also now have a few more details to provide. I hope the mods won't mind if I open another thread here. 

Problem looks like this: 

1. The CPU activity hovers around the > 50% mark. Fairly steady, generally between 50% and 60%. This is on two machines which have previously shown idle CPU activity of between 0% and 2%, steadily. 

2. If I have unsaved data in an application, and click "Log Out", I am asked whether I really want to log out on account of there being a program still running. 

3. If I click "Cancel" (ie. I don't want to log out), the CPU activity drops to around 1% (i.e. normal.) This happens at the point at which I click "Cancel" (not before). This leads me to wonder (nothing more than wonder, I am no expert) whether there is a rogue process which is started off but which is killed at the point of not logging off (sounds odd when you put it like that.) Running ```
top
``` doesn't show anything out of the ordinary. 

4. Sometimes I am also told there is an "Unknown" program also running, and do I want to close this as well? This doesn't happen all the time, and some threads on here have suggested this could be related to using Firefox. (I don't know whether this is relevant, I post it here for the sake of completeness.)

5. Changing the "Automatically remember running applications when logging out" setting in System > Preferences > Startup Applications makes no difference. 

6. The CPU trace is high but the machine feels fine to use - it doesn't feel sluggish or slow (even with the CPU throttled back.) 


This has happened to me on two machines: 

1. IBM X61s Laptop. Loaded Ubuntu 9.04 and all was well, until a couple of days later I noticed the high processor activity. (Thread here: 

[http://ubuntuforums.org/showthread.php?t=1171444](http://ubuntuforums.org/showthread.php?t=1171444) )

I hadn't noticed it before, which *implies* that it wasn't there before but is not conclusive. **BUT **I did notice it very soon after installing some screenlets (clock, calender and a system information panel.) I removed the screenlets, and just about everything else and it made no difference - symptoms all the same. I installed boot-manager to remove processes from bootup and ended up trashing the Ubuntu install, and re-installed it. The new install is fine - nice low processor activity traces, showing that the problem wasn't hardware related. 

2. Dual-core AMD 1400 home-built desktop. This had been running fine for a month or so, no problems. Until today, when I installed the same set of screenlets as on the lappie. I immediately noticed the CPU activity was high - with **exactly** the same symptoms as on the laptop. I have since removed the screenlets and the problem is persistant - no change. 

I am a beginner at this, but am more than happy to run diagnostic software or post the output of tests on the system. However I am kind of keen to find the answer to this. My playing-around with Ubuntu has been very happy to date, but this is vexing me. 

All suggestions welcome. (If anyone else has seen a similar problem then I'd be quite happy to hear from them as well.) 

Thanks, in advance, for any help. 


Oli.

---

### Post by lovinglinux on 2009-05-31
You shouldn't create another thread, specially considering that you previous one has lots of replies. As I said in the other thread, the sensors screenlets, including it's derivatives (ring sensors, circle sensors etc) are resource hogs by themselves. 

It seems that your problem is related to screenlets or Python. I had a similar problem on my machine, that was caused by Python 2.5, which was installed along Python 2.6 (which is the default in Jaunty), because some applications needed it. 

Check if you have Python 2.5 and 2.6 installed. Go to System >> Administration >> Synaptic Package Manager, click the search button, then type "python" and click the "Search" button.

If you have both, then select Python 2.5 and mark it for removal [color=#FF0000]BUT DON'T REMOVE IT[/color]. Just check which applications are dependent on it and paste here. If the list of dependencies includes a huge list of applications, including lot's of stuff related to gnome, then leave it alone.

If you also have Python **2.6** installed and the list of applications dependent on Python 2.5 is small and do not contain important packages, then you might want to remove it. In my case, only 3 applications (guake, mimms and ontv) were using Python 2.5 and I can live without them, so I removed Python 2.5 and my CPU usage dropped a lot.

BE CAREFUL WHEN REMOVING Python versions, since it could brake your system.

Also, check if you have any compiz settings that use images (like Wallpaper or Cube caps) pointing to missing files. I have noticed that when compiz cannot find the images it keeps using lots of CPU. This is probably not related to your problem, but it doesn't hurt to check.

---

### Post by zcacogp on 2009-05-31
Lovinglinux, 

Thanks for your answer. Fair point about the old thread, but I updated it and it didn't get any further replies. I started this one a) because I wondered if the old one had run it's course, and b) in this different area, wondering whether the problem wasn't a total beginner problem. Apologies if I have breached a forum code - I am happy to remove this thread and put all answers on the original one if you (or anyone else) would prefer it. 

The screenlets may be resource hogs, but I have had them running with the CPU activity low. They are currently on the re-built laptop, and that has low CPU use, suggesting that it is not the presence of the screenlets that is causing the problem. I also have removed the screenlets from this machine (the desktop machine) and yet the problem persists. (It is possible that there are 'bits' which are not removed, but I don't know how to find them.) 

I have looked for Python 2.5 in Synaptic, and marked it for removal (as you suggested), but can't see any list of other software which is dependant upon it. However if I do the same for Python 2.6 then it lists a VERY long list of other things that will be affected - from 'alacarte' to 'yelp', probably 35 or 40 applications. I guess the answer is therefore to remove 2.5 and see what happens. 

I can set the system to run no visual effects and it makes no difference, so I suspect that while the compiz missing files tip is a good one, it doesn't apply in this case. 

I'll post here again in a minute or so once I have removed Python 2.5. 


Oli.

---

### Post by zcacogp on 2009-05-31
OK, I have no visual effects and Python 2.5 has been removed. I rebooted the machine, and there is no change to the problem. 

Thinking about it, why would having Python 2.5 on the machine cause problems? I have a machine which worked fine, presumably with Python 2.5 on it, but then worked badly also with Python 2.5 on it. 

All help welcomed, thanks. 


Oli.

---

### Post by HermanAB on 2009-05-31
What is at the top when you run 'top'?

---

### Post by lovinglinux on 2009-05-31
> **zcacogp said:**
> OK, I have no visual effects and Python 2.5 has been removed. I rebooted the machine, and there is no change to the problem. 

Thinking about it, why would having Python 2.5 on the machine cause problems? I have a machine which worked fine, presumably with Python 2.5 on it, but then worked badly also with Python 2.5 on it. 

All help welcomed, thanks. 


Oli.

Python 2.5 works bad on Jaunty. I don't know why. I thought it could be it, because screenlets are Python scripts and the problem only appeared after installing screenlets and remained after closing them.

---

### Post by zcacogp on 2009-06-01
HermanAB, thanks. I'm not working on the affected machine at the moment, but from memory it is 'Xorg', running as user 'root'. 

lovinglinux, Hmmm, interesting. I am currently working on the X61s lappie that was affected but was rebuilt and currently is not affected, and this *doesn't *have Python 2.5 on it (I've just checked.) It does have the same set of screenlets on it as it had before, and as are (or were, before I removed them) on the desktop machine. 

Therefore, is Python 2.5 installed at the same time as the screenlets are installed? Apparently not - otherwise it would be present on this machine. Where did it come from then? 

I guess we could test the theory that Python 2.5 is causing the problem by installing it on this machine and watching the processor usage, but given that the only way I have found for recovering from this situation (to date) has been to rebuild the machine, I'd rather not go down that route if I can help it. :(

Thanks again for your help. 


Oli.

ETA: Another Q. If screenlets are Python scripts, what determines whether they use Python 2.5 or Python 2.6? And what's the difference?

---

### Post by lovinglinux on 2009-06-01
> **zcacogp said:**
> Therefore, is Python 2.5 installed at the same time as the screenlets are installed? Apparently not - otherwise it would be present on this machine. Where did it come from then?

It was installed on my machine when I installed ontv, mimms and guake, because all of them needs Python 2.5 to run. If you upgraded from 8.10, then it was already installed and probably wasn't removed.

 > **zcacogp said:**
> I guess we could test the theory that Python 2.5 is causing the problem by installing it on this machine and watching the processor usage, but given that the only way I have found for recovering from this situation (to date) has been to rebuild the machine, I'd rather not go down that route if I can help it. :(   

Don't bother. I removed Python 2.5 after reading a discussion about this problem on Deluge web site. So I'm not the only one who experienced improvements after removing it. It is probably the culprit on your machine too.

 > **zcacogp said:**
> If screenlets are Python scripts, what determines whether they use Python 2.5 or Python 2.6? And what's the difference?  

I really don't know. What I have noticed is that when I removed Python 2.5, the package manager checked the association of other applications with Python 2.6. So I guess if the application is not strictly dependent on a specific Python version, it can be re-associated with the newest version by the package manager.

I don't know if multiple versions of Python can run at the same time or if the applications  bind to the one already running if they can. Either way, since I had applications that strictly depended on Python 2.5, I'm sure this version was loaded and was causing high CPU usage.

---

### Post by zcacogp on 2009-06-01
> **lovinglinux said:**
> If you upgraded from 8.10, then it was already installed and probably wasn't removed.Now **that's** interesting. The laptop which was affected was built as a 9.04 machine from the outset - it wasn't an 8.10 which was upgraded. However, the desktop machine was an 8.10 machine which was upgraded, but it worked fine for about 3 weeks after the upgrade and the high processor usage only came about some time later. It had also run the suspect set of screenlets as well - the problems came about 'cos the screenlets moved around each time I started the machine up, and I was trying to make them always display in the same place. I didn't achieve it, but I did manage to trigger the higher-processor-activity problem. 

> **lovinglinux said:**
> 

Don't bother. I removed Python 2.5 after reading a discussion about this problem on Deluge web site. So I'm not the only one who experienced improvements after removing it. It is probably the culprit on your machine too.

In which case, how do I remove it? It's gone from the Synaptic interface (the box next to it is no longer shaded). What more do I need to do to remove it? Are there 'remnants' or 'fragments' which still need to be unpicked?    
> **lovinglinux said:**
> 
I really don't know. What I have noticed is that when I removed Python 2.5, the package manager checked the association of other applications with Python 2.6. So I guess if the application is not strictly dependent on a specific Python version, it can be re-associated with the newest version by the package manager.
When I removed Python 2.5, it didn't list any dependancies. When I started the same process for Python 2.6 it listed a huge long list. (I didn't complete the removal of 2.6, for obvious reasons! ;) ) > **lovinglinux said:**
> 
I don't know if multiple versions of Python can run at the same time or if the applications  bind to the one already running if they can. Either way, since I had applications that strictly depended on Python 2.5, I'm sure this version was loaded and was causing high CPU usage.Clearly you can have both Python 2.5 and Python 2.6 installed on the same machine at the same time. I guess the question is whether any applications will *only *work with 2.5, and how other applications bind to one or the other if they can work with either - do they bind at the point of application, or at the point of boot-up, or at some other point? And can they, once bound, re-bind to the other version at a later time? 

However, while these questions are interesting, I suspect they aren't helping solve my problem. If, as you suspect, Python 2.5 is the culprit then how do I fully get rid of it? (And if it is not, what is?!) 


Oli.

---

### Post by lovinglinux on 2009-06-01
> **zcacogp said:**
> In which case, how do I remove it? It's gone from the Synaptic interface (the box next to it is no longer shaded). What more do I need to do to remove it? Are there 'remnants' or 'fragments' which still need to be unpicked? 

No. It's already gone. No need to do anything else.

> **zcacogp said:**
> Clearly you can have both Python 2.5 and Python 2.6 installed on the same machine at the same time. I guess the question is whether any applications will *only *work with 2.5, and how other applications bind to one or the other if they can work with either - do they bind at the point of application, or at the point of boot-up, or at some other point? And can they, once bound, re-bind to the other version at a later time? 

I really don't know. I have created a thread a while ago, asking similar questions, but nobody answered it.

> **zcacogp said:**
> However, while these questions are interesting, I suspect they aren't helping solve my problem. If, as you suspect, Python 2.5 is the culprit then how do I fully get rid of it? (And if it is not, what is?!) 

If you already removed Python 2.5, then the problem lies somewhere else. Unfortunately, I'm out of ideas.

---

### Post by zcacogp on 2009-06-01
Lovinglinux, 

Hmmm. OK, thanks for your post. 

If seeing Python 2.5 removed from Synaptic means it really is gone then I guess we have ruled it out. Snag is, that then means the problem is unidentified ... 

Thanks for your input. Anyone else have any ideas? 


Oli.

---

### Post by zcacogp on 2009-06-01
Chaps, 

To answer HermanAB's comment a bit more precisely, the top lines of top are thus: 

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                      
 2943 root      20   0  453m 147m  23m R   15  8.4  26:25.04 Xorg                         
 3989 ogp       20   0  225m  94m  25m S    6  5.4   2:51.99 firefox                      
 3640 ogp       20   0  8308 5184 2188 S    5  0.3   0:44.34 gconfd-2                     
 3568 ogp       20   0 26516 7224 5676 S    3  0.4   0:51.96 x-session-manag              
 4461 ogp       20   0 18532 6792 5228 S    3  0.4   0:17.17 gnome-screensav              
 3632 ogp       20   0  3068 1268  652 S    2  0.1   1:04.58 dbus-daemon                  
 3675 ogp       20   0 32892  24m 8152 S    2  1.4   0:27.15 compiz.real                  
 3676 ogp       20   0 53116  20m  14m S    2  1.2   0:25.66 gnome-panel                  
 3771 ogp       20   0 23416 9.8m 7484 S    2  0.6   0:21.24 indicator-apple              
 3689 ogp       20   0 27888  13m 8076 S    1  0.8   0:19.00 python                       
 3777 ogp       20   0 26100  12m 9.8m S    1  0.7   0:07.85 fast-user-switc              
 3667 ogp       20   0 32312  11m 8084 S    1  0.7   0:25.57 gnome-settings-              
 3818 ogp       20   0 20492  10m 7972 S    1  0.6   0:00.77 gtk-window-deco              
19575 ogp       20   0  2448 1196  912 R    1  0.1   0:00.01 top                          
19684 ogp       20   0 22312 5432 4236 S    1  0.3   0:00.01 vino-server                  
    1 root      20   0  3084 1888  564 S    0  0.1   0:01.03 init                         
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                     
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0  
```   

Sorry - I suspect the formatting is going to be a bit skew-ed when this appears, but it may inform diagnosis. 

All help welcomed, thanks. 


Oli.

---

### Post by zcacogp on 2009-06-02
Not making much progress with this one. 

I have discovered how to login to "Failsafe Gnome", and when I do this then the CPU usage is still as before - namely high. I have also discovered that when I just log into a terminal and run ```
top
``` then the CPU usage is 0%. (I don't know whether this was a helpful diagnostic, but it may be worth mentioning.) 

I've found this guide here: 

[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

... which suggests that the Xorg process is using more CPU than it should be. It suggests that if I type this: 

```
glxinfo | grep render
``` and get this:   ```
direct rendering: Yes
  OpenGL renderer string: Software Rasterizer
```... then I will get high CPU usage - I don't, I get this: ```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
OpenGL renderer string: ATI Radeon HD 3300 Graphics
```... so I resume that is OK. 

It also suggests that I should look at the end of /var/log/Xorg.0.log to see if there are any error messages there. The last 10 or so lines of that file look like this: 
```

(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
```... and I can't see anything that suggests it is an error message (although I'm not 100% sure I would spot one if there was one.) 

It is also suggested that I should look at /var/log/gdm/* to see if there are any "Stuck in infinite look" messages. That file looks like this: 
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ogp-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  2 09:17:01 2009
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
```

Does that look odd to anyone? 

Another question, if I may. I am clearly struggling to get this resolved, and while there have been helpful suggestions on this thread (and its predecessor), I'm not getting anywhere. Can I raise this as a bug? Am I allowed to? If so, how? Do I register on bugs.launchpad.net? What's the difference between there and here? 

Thanks, as always, for any help. 


Oli.

---

### Post by zcacogp on 2009-06-02
OK, there is an interesting development. 

The high CPU usage is related to the **user account** I am using. If I log off and log on as someone else (I've just created a new account), the CPU usage is normal. 

I also have another account on this machine which pre-dates the appearance of the problem (my wife's account), and that doesn't exhibit the problems either. 

So there is something odd about my account. Logging in as me starts something which creates high CPU loads. 

If anyone else has any suggestions on this then please do chip in. 


Oli.

---

### Post by zcacogp on 2009-06-02
**[size="3"]Got it! [/size]**

Not sure if anyone else is reading this (give me a wave if you are!), but I have tracked down the problem. 

It is NOT to do with screenlets (which I was pretty sure it was.) 

It was to do with Remote Desktop. If I enable Remote Desktop (System > Preferences > Remote Desktop . "Allow other users to view your desktop"), the CPU activity jumps by about 50%. I can turn it on and off on screen and watch the CPU trace vary accordingly. 

I don't understand this, as I am SURE I had this setting 'On' previously without problems, so could it be something else interfering with the Remote Desktop system? 

This does give me some better evidence on which to investigate. 

All suggestions welcome, as always. 


Oli.

---

### Post by lovinglinux on 2009-06-02
> **zcacogp said:**
> **[size="3"]got it! [/size]**

not sure if anyone else is reading this (give me a wave if you are!), but i have tracked down the problem.

The wave smile is not working :)

Nice to know that you sorted it out.

---

### Post by zcacogp on 2009-06-02
LL, 

I'm glad too! 

It looks (from searching the forums) like this is just a "known fault". Advice is to turn off Remote Desktop and use something else - there are suggestions around. 

I don't currently use it, but was planning to get to grips with it sometime soon (I am still working up to using Ubuntu as fully as I used Windows previously), so while it isn't an immediate hassle it will be a pain in a week or so's time.

Ho hum. I keep telling myself that Ubuntu is the superior system for loads of reasons, but currently it has taken me upwards of 30 hours poking around to get where I am (working install on two machines, with a third machine not running at all since I put 9.04 on it as GRUB won't play.) I'm not sure how much longer I pursue it for, and when I simply start to use XP again. 

But that's probably a topic for another thread! Thanks again for your help. 


Oli.

---

### Post by lovinglinux on 2009-06-02
> **zcacogp said:**
> I don't currently use it, but was planning to get to grips with it sometime soon (I am still working up to using Ubuntu as fully as I used Windows previously), so while it isn't an immediate hassle it will be a pain in a week or so's time

If you intend to connect to a remote Ubuntu machine, then I would recommend using ssh. It's great and much more secure then remote Desktop. You can forward the X server from the remote machine using ssh and thus launch graphical interfaces that runs in the remote, but is displayed in the local machine. So basically you can access almost any tool in the remote without actually looking the other user screen. Besides, you can do a lot of stuff through ssh terminal.

More information:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[http://ubuntuforums.org/showthread.php?p=6926168#post6926168](http://ubuntuforums.org/showthread.php?p=6926168#post6926168)

> **zcacogp said:**
> Ho hum. I keep telling myself that Ubuntu is the superior system for loads of reasons, but currently it has taken me upwards of 30 hours poking around to get where I am (working install on two machines, with a third machine not running at all since I put 9.04 on it as GRUB won't play.) I'm not sure how much longer I pursue it for, and when I simply start to use XP again.

Ubuntu can offer some obstacles to get where you want, but once you get there you can pretty much forget about maintenance. Windows on the other hand can be easier to setup initially, but requires huge constant maintenance to make it work smoothly in the long run. I had to re-install Windows from scratch every 6 months or less, while my first Ubuntu installation was pretty much the same after 8 months. I only re-installed it because I wanted to try Jaunty 9.04 and ext4.

Another thing that should be considered is that you are installing the newest Ubuntu release. If you want more stability, you should consider sticking with LTS (long Term Support) releases, like Hardy Heron.

*UKeywords: 649167 2009 june ssh remote*

---

### Post by zcacogp on 2009-06-03
LL, 

Thanks again. For the answer and for the links. I've found them independently, but it's useful to know that I am along the right lines. I've managed to get a drive on another machine to mount OK using SSH, but it seemed to be a heck of a palaver - much tricker than on XP. 

I see what you mean about Ubuntu. Currently I am also enjoying it, but it does seem to have been a very steep learning curve to get to where I am now. And it's taken a lot of time. Perhaps I am looking to achieve a significant degree of expertise with it (as I have with XP), and therefore feel that I am further behind than I really am. I guess if I wanted to load Ubuntu and just use it then it would be easier. 

I will appreciate the benefits of long-term stability more as I use it more, I guess. That is surely when you really start to win. 

You're right about me not choosing an LTS version. I should have gone for HH. In fact, in retrospect, I'm not sure why I didn't. I think I'll stick with JJ (where I am now) until the next LTS version comes out, and stick with that for a couple of years. (Unless I get stupidly gung-ho between now and then!) 

Thanks again for your input. I have some questions about networking but will open a new thread for them - they don't belong on here. 


Oli.

---

