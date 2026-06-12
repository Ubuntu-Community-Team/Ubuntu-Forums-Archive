---
title: "compiz stopped working after xorg update"
date: 2011-10-19
forum: Desktop Environments
---

### Post by lswb on 2011-10-19
Runnung ubuntu Lucid 10.4 & gnome. After routine update via synaptic of xserver-xorg-core from 2:1.7.6-2ubuntu7 to 2:1.7.6-2ubuntu7.8 noticed that compiz and special effects stopped working after subsequent restart. Trying to reenable through System/Preference/Appearance/Visual Effects produced error message about missing drivers. I forced downgrade to earlier version and compiz/special effects were reenabled upon restart of X server. This is on a Thinkpad T60 with intel 945 graphics controller. Has anyone else experienced this?

I have not been active on the forums or launchpad (is that still active?) for quite a while until very recently and am unsure of how to file a bug report.

---

### Post by Precipitous on 2011-10-19
> **lswb said:**
> Runnung ubuntu Lucid 10.4 & gnome. After routine update via synaptic of xserver-xorg-core from 2:1.7.6-2ubuntu7 to 2:1.7.6-2ubuntu7.8 noticed that compiz and special effects stopped working after subsequent restart. Trying to reenable through System/Preference/Appearance/Visual Effects produced error message about missing drivers. I forced downgrade to earlier version and compiz/special effects were reenabled upon restart of X server. This is on a Thinkpad T60 with intel 945 graphics controller. Has anyone else experienced this?

I have not been active on the forums or launchpad (is that still active?) for quite a while until very recently and am unsure of how to file a bug report.
I am running UbuntuStudio Maverick and the same thing happened to me. When I tried to restart Compiz via the terminal I got the following message:

```
compiz (core) - Fatal: No valid GL extensions string found.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
```Currently my version of xserver-xorg-core listed in Synaptic is 2:1.9.0-0ubuntu7.5. 

I am thinking I should try to revert to an earlier version too, but I am not sure which one I should revert to, or the best way to go about doing it...  Anyone have any good advice?

---

### Post by keithweddell on 2011-10-19
Me too. Lucid on Dell Inspiron.

Keith

---

### Post by John Pye on 2011-10-19
Same as Keith I think.  I wondered if this was relevant.  Not tried it yet [http://ubuntuforums.org/showthread.php?t=1864221&referrerid=1192031](http://ubuntuforums.org/showthread.php?t=1864221&referrerid=1192031)
 
John

---

### Post by adxgrave on 2011-10-19
Me too. Lucid netbook remix on HP Mini 210. Upon starting xbmc, it complain about missing driver. Can't enable simple compiz and home screen is now missing. I'm staring at blank wallpaper. So how do you downgrade the xserver-core? or any others better way to go?

Edit: To downgrade

```

sudo aptitude install xserver-common=2:1.7.6-2ubuntu7
sudo aptitude install xserver-xorg-core=2:1.7.6-2ubuntu7

```

---

### Post by jwalker on 2011-10-19
me too, 10.04 here, how to roll back?

---

### Post by lesliek on 2011-10-19
I believe this has happened to me as well.

I'm using 10.04 and just did some updating as suggested by the update manager.

Now, neither my folderview screenlet nor sticky notes are working properly.

What to do?



LATER: Doing as suggested in reply #4 fixed the problems for me too.

---

### Post by jwalker on 2011-10-19
> **jwalker said:**
> me too, 10.04 here, how to roll back?

...and we're back!

the commands suggested in reply #4 should 'roll back' the update to xorg, I just did this and I'm back in business. 

Living with Linux!

---

### Post by lswb on 2011-10-19
Now, is anyone in this thread knowledgeable enough about bug reporting to make sure the developers are aware of the problem?

---

### Post by lesliek on 2011-10-19
Not me. I'm astounded I was even able to fix the problem!

---

### Post by adxgrave on 2011-10-19
lol. Me too. Tried fixing this from this morning. Next time i'll make sure to look closely what's being update. Phew!

---

### Post by sybille on 2011-10-19
Hi,

Could everyone who is experiencing the problem with the updated packages go to the  following Launchpad bug and click at the top of the page to confirm that  the bug is affecting you?
  
  [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)
  
  Thanks!

Also, for people who are working around the problem by downgrading the  problematic packages - xserver-common and xserver-xorg-core - please  realize that the updated packages were for a security update. So it is  important for you to follow the issue closely and to make sure to  upgrade as soon as there are new, fixed packages if you must continue to  use the old, insecure versions.

---

### Post by psygen on 2011-10-19
The same problem here... Dell Vostro V130 with Intel Graphics (VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)).

I did rollback to version and is working.

---

### Post by WhatAbout on 2011-10-19
Honestly im getting enough of these "updates" that ruin your OS. From the time i changed from win to ubuntu i have constantly been surprised by how unstable the OS really is. This is the last time i update ANYTHING the automatic updater pops up with! Actually im going to turn it off. Last time i was stupid enough to press update, AS ANYONE WOULD DO ON A WIN OR MAC PC, without researching hours for what they did, grub would not boot ubuntu up.

And now this? I used one full day to go through any setting and package compiz has installed, only to find out that the noob developers send malfunctioning packages to me automatically??

Welcome to ubuntu, always in BETA.. ahem sorry... ALPHA version!!

---

### Post by jwalker on 2011-10-19
> **WhatAbout said:**
> Honestly im getting enough of these "updates" that ruin your OS. From the time i changed from win to ubuntu i have constantly been surprised by how unstable the OS really is. This is the last time i update ANYTHING the automatic updater pops up with! Actually im going to turn it off. Last time i was stupid enough to press update, AS ANYONE WOULD DO ON A WIN OR MAC PC, without researching hours for what they did, grub would not boot ubuntu up.

And now this? I used one full day to go through any setting and package compiz has installed, only to find out that the noob developers send malfunctioning packages to me automatically??

Welcome to ubuntu, always in BETA.. ahem sorry... ALPHA version!!

word. 

persevere i've been here since '06 and it drives you nuts but you will learn and it gets to a point where you learn so much you fix things quickly. and on the way you get pretty empowered

---

### Post by sf_basilix on 2011-10-19
ugh. Same thing happened to me. Compiz broke.

I agree with the previous poster. I chose 10.04 LTS because it's supposed to be LONG TERM SUPPORT with only security fixes. If security fixes break things, then that's not supporting things. They need to fix things that break just as fast as securing the holes!! I also think there should be warnings if things break, before applying them.

I'm not an apple fan and I can't stand windows unstability, but mac os x is looking better each day.

---

### Post by gpalarea on 2011-10-19
Same thing here, and the suggested rollback did the trick.  Thanks!

Edit: a fix has been realeased!

---

### Post by Precipitous on 2011-10-19
> **adxgrave said:**
> Me too. Lucid netbook remix on HP Mini 210. Upon starting xbmc, it complain about missing driver. Can't enable simple compiz and home screen is now missing. I'm staring at blank wallpaper. So how do you downgrade the xserver-core? or any others better way to go?

Edit: To downgrade

```

sudo aptitude install xserver-common=2:1.7.6-2ubuntu7
sudo aptitude install xserver-xorg-core=2:1.7.6-2ubuntu7

```
I am running Ubuntu 10.10. When I attempt this downgrade I get the message that version 2:1.7.6-2ubuntu7 is not available...  Does anyone know what version of xserver-common and xserver-xorg-core Maverick users should downgrade to? Has anyone else running 10.10 experienced this issue?

---

### Post by sybille on 2011-10-19
> **Precipitous said:**
> I am running Ubuntu 10.10. When I attempt this downgrade I get the message that version 2:1.7.6-2ubuntu7 is not available...  Does anyone know what version of xserver-common and xserver-xorg-core Maverick users should downgrade to? Has anyone else running 10.10 experienced this issue?

This particular issue is only affecting users of Lucid, as you can see from the Ubuntu security notice for the new packages:
[http://www.ubuntu.com/usn/usn-1232-2/](http://www.ubuntu.com/usn/usn-1232-2/)

If you're having trouble with Maverick, I think it's a different problem, unfortunately.

---

### Post by halloween2311 on 2011-10-19
I noticed that Launchpad had this listed as fixed so I ran update manager and sure enough a new xorg package was available.  After a download and reboot I was able to reset the desktop settings under appearance - of course all of my compiz settings were gone but fortunately I had a back up profile that had most of my settings and tweaks so I was able to get quickly underway.

Note I believe this fixes the display issue but does *not* fix the security issue the original patch addressed.  (someone correct me if I'mwrong on that one.)

---

### Post by gpalarea on 2011-10-19
A fix has been released, no need for rollback any more.  That was quick!

---

### Post by Precipitous on 2011-10-19
> **sybille said:**
> This particular issue is only affecting users of Lucid, as you can see from the Ubuntu security notice for the new packages:
[http://www.ubuntu.com/usn/usn-1232-2/](http://www.ubuntu.com/usn/usn-1232-2/)

If you're having trouble with Maverick, I think it's a different problem, unfortunately.
Do you have any ideas as to where to go from here? My symptoms are: AWN reports that I need to turn on a desktop effects  compositor to run any themes. If I attempt to turn on desktop effects, Ubuntu reports that no suitable driver can be found. If I restart Compiz via the terminal I get the following:

```
compiz (core) - Fatal: No valid GL extensions string found. compiz (core) - Error: Failed to manage screen: 0 compiz (core) - Fatal: No manageable screens found on display :0.0  Launching fallback window manager
```In an attempt to resolve the issue I have done the following:

Re-installed the latest Nvidia driver.
Ran the Nvidia utility to re-configure x
Re-installed Compiz
Re-installed xserver-common and xserver-xorg-core

So far nothing has helped...

---

### Post by snakeplizzken on 2011-10-20
"Do you have any ideas as to where to go from here? My symptoms are: AWN  reports that I need to turn on a desktop effects  compositor to run any  themes. If I attempt to turn on desktop effects, Ubuntu reports that no  suitable driver can be found. If I restart Compiz via the terminal I get  the following:"

I got a similar problem on my desktop machine after this update.
Every time I try to enable desktop effects the screen gets scrambled when it is looking for drivers.

How do you resolve a problem like this?
[]("http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg558440.html")

---

### Post by dansang on 2011-10-20
[snakeplizzken]("http://ubuntuforums.org/member.php?u=1405845") a new update has been released! Update using update manager..it should sort it!!

Percipitous try installing compizconfig settings manager from synaptics package manager! then go to systems>preferences>compizConfig settings manager.  Make any adjustments from there.

I had the same problem launching compiz from the terminal! this work around got my compiz settings back!

---

### Post by snakeplizzken on 2011-10-20
No. The new update did not fix the problem. That was my concern.
It worked on one machine but not on the other for some reason.

I don't know what to do as I am not getting any relevant error messages.

Something must have happened with the drivers or maybe it is something with Compiz.

---

### Post by snakeplizzken on 2011-10-20
I think I solved the problem.

Earlier the command "glxinfo | grep render" gave the output: 
direct rendering: No

I ran two commands:
1. sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
2. sudo dpkg-reconfigure xserver-xorg

The second one didn't give any output so I guess it did not do anything.

But now "glxinfo | grep render" prints:
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) G41 GEM 20091221 2009Q4 x86/MMX/SSE2

And I was able to enable desktop effects :D.
Back in business...

---

### Post by Precipitous on 2011-10-20
> **dansang said:**
> 

Percipitous try installing compizconfig settings manager from synaptics package manager! then go to systems>preferences>compizConfig settings manager.  Make any adjustments from there.

I had the same problem launching compiz from the terminal! this work around got my compiz settings back!
Unfortunately this did not work...  There was an automatic update to xserver-common and xserver-xog-core today to version 2:1.9.0-0ubuntu7.6. That did not resolve anything either...

Anybody have any other ideas?

---

### Post by Nick Payne on 2011-10-21
Latest update has not fixed the problem. I have just installed the third update to xserver-common and xserver-xorg-core in three days, and desktop effects still can't be enabled. When I try (through Perferences / Appearance / Visual Effects) I just get a error dialog saying "Desktop effects could not be enabled". xserver-common and xserver-xorg-core are version 2:1.7.6-2ubuntu7.10.

Was working fine until the first of these three updates a couple of days back...

---

### Post by bohemian9485 on 2011-10-21
My Compiz crashed too after an update two days ago, but after this morning's update I was able to get back those Compiz effects

sysadmin@SIQ-CFMS-007:~$ cat /var/log/dpkg.log|grep -i "status installed xserver"
# this update crashed Compiz
2011-10-19 16:47:33 status installed xserver-common 2:1.7.6-2ubuntu7.8
2011-10-19 16:48:50 status installed xserver-xorg-core 2:1.7.6-2ubuntu7.8
2011-10-19 16:48:50 status installed xserver-xorg-video-geode 2.11.11-1~lucid1
# this update did not solve the problem
2011-10-20 09:18:51 status installed xserver-common 2:1.7.6-2ubuntu7.9
2011-10-20 09:18:51 status installed xserver-xorg-core 2:1.7.6-2ubuntu7.9
# this update seems to correct the problem and Compiz was able to work again
2011-10-21 11:37:54 status installed xserver-common 2:1.7.6-2ubuntu7.10
2011-10-21 11:37:54 status installed xserver-xorg-core 2:1.7.6-2ubuntu7.10

---

### Post by psygen on 2011-10-25
Bug is fixed. Here, now, work without problem.


> **snakeplizzken said:**
> I think I solved the problem.

Earlier the command "glxinfo | grep render" gave the output: 
direct rendering: No

I ran two commands:
1. sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
2. sudo dpkg-reconfigure xserver-xorg

The second one didn't give any output so I guess it did not do anything.

But now "glxinfo | grep render" prints:
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) G41 GEM 20091221 2009Q4 x86/MMX/SSE2

And I was able to enable desktop effects :D.
Back in business...

---

### Post by Precipitous on 2011-10-25
> **snakeplizzken said:**
> I think I solved the problem.

Earlier the command "glxinfo | grep render" gave the output: 
direct rendering: No

I ran two commands:
1. sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
2. sudo dpkg-reconfigure xserver-xorg

The second one didn't give any output so I guess it did not do anything.

But now "glxinfo | grep render" prints:
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) G41 GEM 20091221 2009Q4 x86/MMX/SSE2

And I was able to enable desktop effects :D.
Back in business...
I did this and ran into disaster...  

I am running the latest Nvidia driver from their website. After running the commands listed above, I could still not apply any desktop effects until I switched over to the Nvidia Current driver installed from Synaptic. When I booted my computer using this driver, I got desktop effects back (I could tell because AWN had a theme with a transparent background applied). Unfortunately, the computer locked up before everything finished loading (this is why I switched to the latest Nvidia driver from their website in the first place).  

I re-installed that driver and rebooted. Now I get to a desktop with nothing but wallpaper. No AWN, no Conky, nothing. The only way I was able to get a browser open to post this was by booting to a Recovery Mode Prompt...  I am completely dead in the water. 

Does anyone have any idea as to where to go from here?

---

### Post by Precipitous on 2011-10-26
> **Precipitous said:**
> I did this and ran into disaster...  

I am running the latest Nvidia driver from their website. After running the commands listed above, I could still not apply any desktop effects until I switched over to the Nvidia Current driver installed from Synaptic. When I booted my computer using this driver, I got desktop effects back (I could tell because AWN had a theme with a transparent background applied). Unfortunately, the computer locked up before everything finished loading (this is why I switched to the latest Nvidia driver from their website in the first place).  

I re-installed that driver and rebooted. Now I get to a desktop with nothing but wallpaper. No AWN, no Conky, nothing. The only way I was able to get a browser open to post this was by booting to a Recovery Mode Prompt...  I am completely dead in the water. 

Does anyone have any idea as to where to go from here?

OK - I was able to get everything working by upgrading to Natty...  Big sigh of relief!

---

### Post by matmiller on 2011-10-27
Hi there!

I had similar problem and instructions from **snakeplizzken** worked for me.

Before running them the ```
glxinfo | grep render
``` gave me:
[FONT="Courier New"]direct rendering: Yes
OpenGL renderer string: Mesa X11[/FONT]

after:
[FONT="Courier New"]direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GME GEM 20091221 2009Q4 x86/MMX/SSE2[/FONT]

Thanks a lot snakeplizzken!!! :)

---

