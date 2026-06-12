---
title: "Gutsy Gibbon on Dell Inspiron 1420 N"
date: 2007-10-18
forum: Dell  Ubuntu Support
---

### Post by ariodante on 2007-10-18
Has anyone tried installing Gutsy Gibbon using the Upgrade Manager over a factory installation of Feisty Fawn on the Dell Inspiron 1420 N?  If so, were there any problems?  One would hope that Gutsy was developed to be fully compatible with the 1420 N since Feisty came preloaded (albeit with some Dell modifications) ...

---

### Post by oilchangeguy on 2007-10-18
> **ariodante said:**
> Has anyone tried installing Gutsy Gibbon using the Upgrade Manager over a factory installation of Feisty Fawn on the Dell Inspiron 1420 N?  If so, were there any problems?  One would hope that Gutsy was developed to be fully compatible with the 1420 N since Feisty came preloaded (albeit with some Dell modifications) ...

if it ain't broke. don't fix it. also this needs to be moved to main support, dell support.

---

### Post by bruce89 on 2007-10-18
I just reinstalled my 6400n with Gutsy a month ago, couldn't be bothered with Dell's small number of modifications. The only thing that won't work is the modem (who uses them these days).

---

### Post by notwen on 2007-10-18
I'd wait on the new Gutsy images Dell will be introducing.  Links are provided here in this [thread]("http://ubuntuforums.org/showthread.php?t=578659").

---

### Post by b_woodbury on 2007-10-19
I just upgraded to Gutsy from Fiesty on my 1420N. Just about everything (except S-video) worked out of the box when I first got the computer a few months ago, so I was expecting a smooth upgrade. But it took a little longer than expected: about 20 hours to download and install the upgrade. As soon as the upgrade was complete, my computer rebooted and now all I get is a green screen. So . . . not a perfectly smooth upgrade for me.

---

### Post by b_woodbury on 2007-10-19
I restarted in safemode, edited my xorg.conf file by typing "sudo dpkg-reconfigure xserver-xorg" and selected all the default values. When I restarted my computer, my screen worked. Compiz fusion, however, does not work (not a big problem, but something I was excited to check out). Sound works, video works and network manager, which I had so much trouble with before that I used wifi-radar, now works fine.

---

### Post by inchaos on 2007-10-24
I've got a 1420n, today's the first day I've been running Gutsy...I'm kind of irritated.

I had finally gotten to the point where everything worked in Feisty exactly as I wanted it and then I was silly and upgraded...I guess that's what I get, right?  Haha.

Anyway, at first I couldn't get the update to work, I kept coming up against errors with the package sources and I ended up needing to change some of the locations from beginning with "http://" to "ftp://".  I followed the steps found here:
[http://ubuntuforums.org/showthread.php?t=587051](http://ubuntuforums.org/showthread.php?t=587051)

Once the update had completed and installed, xorg started giving me trouble.  After the reboot, I got an error message saying that my monitor couldn't be detected properly and that Ubuntu was running in 'Low Graphics Mode.'  I was given the option to manually configure my monitor and graphics card, but for each subsequent reboot I was asked to reconfigure.  So I poked around on the forums for a while and came accross a topic recommending that I manually configure xserver, which I did, with the following:

```
sudo dpkg-reconfigure xserver-xorg
```

I accepted most of the defaults and the configuration issue was taken care of.

I don't have compiz/fusion running, and I'm told it's not really possible right now since I was cheap and got the Intel Integrated Graphics Controller, which, for some reason, has been blacklisted by Compiz.  I tried removing the blacklist code for my graphics card, to no avail.  I'll keep working on it.

My sound was being touchy, for some reason it was turned down halfway in alsamixer, until I figured that out nothing was loud enough.

There was also a fun time with a new screen dimming feature, much like what macs do after a short idle period, all it took was playing around with some defaults to get rid of it (on battery power it would randomly dim for no reason).  You could use the keyboard to turn the brightness back up but it was really annoying when I was in the middle of something and all the sudden my screen goes dark.

Other than that, nothing serious.  Some people have apparently had huge issues with monitor recognition and xorg, I guess I lucked out a little bit. 

Oh yeah, there's no functioning driver for the modem anymore, I'm not sure if that's a high priority but most people don't use dial-up anymore anyway...

---

### Post by frbe0101 on 2007-10-24
It did it, first problem was GUI and xserver failed to boot leaving me with nothing but a basic terminal, thought it was a FUBAR, it turn out to be a very small problem, fixed: [http://ubuntuforums.org/showthread.php?t=588033](http://ubuntuforums.org/showthread.php?t=588033)

Next problem is the network controller is unstable: changing wireless networks or ethernet lines locks up the network manager (in both ubuntu and kubuntu) and I tried the network reset command but it did nothing, only rebooting restarts the network controller. Anyone have a clue what going on?

---

### Post by inchaos on 2007-10-25
No, mine works fine.

Come to think of it, I have noticed a little bit of a lag when switching wireless networks but nothing I've had to reboot for.

Do you have a 1420n with Intel chipsets or a 1420 with AMD/Broadcom chipsets?

---

### Post by sleepykit on 2007-10-25
Upgraded here, and it's been "interesting".

Right now, the start up times are hellish with Gutsy (1.5 minutes) and for some reason the screen flickers right after the Ubuntu splash screen and before anything comes up. Despite having one of the better intel chip sets for video, compiz fusion is not working either. 

Not a smooth upgrade, and I wouldn't recommend trying it until Dell has a gutsy image out for users.

---

### Post by frbe0101 on 2007-10-25
> **inchaos said:**
> No, mine works fine.

Come to think of it, I have noticed a little bit of a lag when switching wireless networks but nothing I've had to reboot for.

Do you have a 1420n with Intel chipsets or a 1420 with AMD/Broadcom chipsets?

PRO/Wireless 3945ABG Network Connection, vendor: Intel Corporation.   
NetLink BCM5906M Fast Ethernet PCI Express, vendor: Broadcom Corporation.

I've posted a network inquire to the problem: [http://ubuntuforums.org/showthread.php?t=591586](http://ubuntuforums.org/showthread.php?t=591586)

---

### Post by inchaos on 2007-10-25
"Next problem is the network controller is unstable: changing wireless networks or ethernet lines locks up the network manager (in both ubuntu and kubuntu) and I tried the network reset command but it did nothing, only rebooting restarts the network controller. Anyone have a clue what going on?"


This is happening to me and it's driving me INSANE.

Someone tell me how to fix it!

---

### Post by inchaos on 2007-10-25
> **frbe0101 said:**
> PRO/Wireless 3945ABG Network Connection, vendor: Intel Corporation.   
NetLink BCM5906M Fast Ethernet PCI Express, vendor: Broadcom Corporation.
[http://ubuntuforums.org/showthread.php?t=591586](http://ubuntuforums.org/showthread.php?t=591586)

Wait...you have Intel *and* Broadcom?

Dell told me that couldn't happen. (My last computer had a Broadcom wireless card that I spent months trying to get to work, I wanted to make sure I would not have ANYTHING made by Broadcom in my new computer, lolz)

Or maybe they said I couldn't have AMD chipsets with an Intel wireless card...

---

### Post by dunaway on 2007-10-27
I installed 7.10 from update manager to 1420n with factory installed 7.04 on 10/25.  Problems:

1. no GUI, but finally got that working after reading some posts.
2. no sound; still no sound...anyone help?
3. network/internet has been on/off, but working right now.
4. no "Shutdown"/"Off" button, only "Standy", "Hibernate" etc...
5. when reboot, get command line; must type in "startx" to get to GUI

I should've waited; 7.04 was working fine.

---

### Post by sleepykit on 2007-10-27
> **dunaway said:**
> I installed 7.10 from update manager to 1420n with factory installed 7.04 on 10/25.  Problems:

1. no GUI, but finally got that working after reading some posts.
2. no sound; still no sound...anyone help?
3. network/internet has been on/off, but working right now.
4. no "Shutdown"/"Off" button, only "Standy", "Hibernate" etc...
5. when reboot, get command line; must type in "startx" to get to GUI

I should've waited; 7.04 was working fine.

For no sound, try installing gnome-alsamixer. I did that and found that the sound across the board was muted in a way I couldn't otherwise unmute. Finally did and it lives.

For the startx thing, make sure you have the correct driver in your xorg.conf. Should say "intel" and not "i810" although I don't know why yo this day. For me, as soon as it started booting straight into the gnome display manager, it also started giving the shutdown/restart options... Weird

---

### Post by frbe0101 on 2007-10-27
> **dunaway said:**
> I installed 7.10 from update manager to 1420n with factory installed 7.04 on 10/25.  Problems:

1. no GUI, but finally got that working after reading some posts.
2. no sound; still no sound...anyone help?
3. network/internet has been on/off, but working right now.
4. no "Shutdown"/"Off" button, only "Standy", "Hibernate" etc...
5. when reboot, get command line; must type in "startx" to get to GUI

I should've waited; 7.04 was working fine.

I experienced problems 1 and 3, but using KDE I get problems 2,3,4, haven't fix those so I used gnome.

---

### Post by frbe0101 on 2007-10-27
Great now the sound just died on me in both Gnome and KDE, how did you fix it?

---

### Post by nbubis on 2007-10-31
Could someone please post their xorg.conf file? 

since the upgrade i can't get opengl to work (X crashes), and trying to make a .conf file by running the dpkg command doesn't seem to even include a  "modules" section...

Thanks, Nathaniel.

---

### Post by Dellfan on 2007-10-31
I suspect he has a Intel wireless (the 3945) and a broadcom 10/100 wired ethernet NIC. Pretty well all Dell's use Broadcom ethernet chipsets.

---

### Post by natehall on 2007-10-31
> **ariodante said:**
> Has anyone tried installing Gutsy Gibbon using the Upgrade Manager over a factory installation of Feisty Fawn on the Dell Inspiron 1420 N?  If so, were there any problems?  One would hope that Gutsy was developed to be fully compatible with the 1420 N since Feisty came preloaded (albeit with some Dell modifications) ...

I did the upgrade and it fixed the screensaver freeze problem but the browser stopped working! I went in BIOS and rebooted fiesty fawn

---

### Post by dunaway on 2007-11-03
Update on status of upgrade from Feisty to Gutsy on Dell 1420n: after install of Gutsy, I had several issues, which were detailed in a previous post.  All issues have been resolved; more luck and persistance than skill.  Regardless, it's working.  I still have my fingers crossed that nothing decides to stop working.  Does anyone have a suggestion for a scanner to use with Ubuntu/Dell laptop?

---

### Post by ccfiel on 2007-11-03
dunaway

how did you resolve your issues? maybe you could share you experiences.

---

### Post by inchaos on 2007-11-04
I second this request.

---

### Post by dunaway on 2007-11-05
As requested, I will try and explain what I did to resolve the issues I had after upgrading from 7.04 to Gutsy.  First, the disclaimer...I'm a lawyer, not a computer expert, therefore, my attempt to explain my experience will likely not be technically accurate.  In addition,  I want to reiterate that my issues were likely resolved due more to persistance and luck than technical proficiency.  Having said that, here we go:  I upgraded via the upgrade manager.  Everything went fine until reboot after Gutsy was downloaded.  On reboot, all I got was the command line (no GUI).  I jumped on another computer and started searching for solutions; I found this one that seemed to help [.  Even after doing this, I still got the command line on startup, but could get a GUI after inputting "startx" at the command line.  After I actually got to the desktop, there were several probelms: 1. no internet/network; 2. no sound; 3. so "shutdown" or "restart" buttons and; 4. command line comes up on reboot/logout, so must type "startx" to get back to GUI.  1. no internet/network: I had recently set up wireless network at home via a NetGear RangeMax Next 802.11n.  Two computers friends actually set up the network and got my Dell 1420n laptop (pre-loaded w/ Fiesty) talking to each other.  I wasn't having any luck getting connected wirelessly, so I connected the laptop to the router directly via network cable and was able to get online.  After unplugging and reboot, I was able to find the router wirelessly, BUT Gutsy Network Manager still wasn't working correctly, but it was working enough so that I could get online; more on this in #4.  2. no sound: after upgrading there was no sound.  I was able to find some help here: [URL="http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Audio_Failure_On_Resume"]http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Audio_Failure_On_Resume]("http://ubuntuforums.org/showthread.php?t=588033")
and here [http://ubuntuforums.org/archive/index.php/t-575653.html]("http://ubuntuforums.org/archive/index.php/t-575653.html")
The sound did not start working immediately; I had to go into System/Preferences/Volume Control & Sound and "toy" with some things before I started getting sound.  Again, sorry for nothing technical,here, but I just kept messing with it until it worked.  3. no "Shutdown" or "Restart" buttons after upgrade: This was one of the last fixes, and thus somewhat fresher in my mind.  I installed the "Boot-up Manager" and after running it and reboot, I got normal boot (i.e.- brown/ubuntu background with username prompt then password prompt; no longer got command line prompt) and after login and GUI I had the "Restart" and "Shutdown" buttons.  Obviously, this also fixed #4 problem.  The weird thing is this: after this the Network Manager started working "differently" than it was working on Fiesty, and again, I had to "toy" with the Network Manager to get it to see my NetGear wireless router, but since I started getting normal login and reboot, the Network Manager/wireless works much bettere (i.e.- Gutsy finds the network automatically w/o trying to login to other "unsecure" wireless networks located nearby).  Thus, about 10 days after upgrading, I seem to have everything working as well or even better than they were working under Fiesty (factory install).  Again, more luck and persistance than anything, and I apologize for the non-technical explanation; I should have kept a "log" of what I tried (what worked and what didn't).  Of course, if you have any questions, I will be happy to try and fill in any additional details (if I can).  I apologize for the non-brevity of this post.

---

### Post by hiikeeba on 2007-11-07
I have upgraded an recycled desktop to Gutsy, and was wondering if I should try it on my 1420.   The answer is "Not yet."  I'm still new to Linux, and it sounds like the upgrade would be beyond my skills.  

Thanks to everyone for sharing their experiences.

Jeff

---

### Post by inchaos on 2007-11-08
In all honesty, it wasn't that bad.
I'm tempted to say it depends on weather you have a 1420 with Vista or self-installed Ubuntu or a 1420n that came preloaded with Ubuntu.

My upgrade worked.  X didn't break for me and I didn't really have to delve too far into the command line to fix things.  There are still three bugs for me.

1.  The Network Manager Applet hangs.  I frequently have to kill the process and reload it in terminal.

2. The screen dims and brightens randomly on battery power.  Not a big issue at all, just kind of strange.

3. I managed to get Compiz up and running, but when I have desktop effects enabled, I am completely unable to play any video.  The error comes back as 'insufficient resources', but my CPU and RAM are mostly free.  My video card is allotted 512 MB of RAM anyway, so there's no way it should be an issue.

These are all manageable issues, the computer boots, sound works, wireless works, all of my cards are detected and useable.

All in all, it was worth it.  And I'm not all that Linux-savvy either.

---

### Post by tpischke on 2007-11-09
Quick post with my Upgrade Manager experiences:

The Good:
 * Upgraded applications, etc

The Bad:
 * Had to reconfigure xorg.conf to get things working with intel drivers - no big deal
 * Compiz is a no-starter, unless you're willing to forgo video.  I'm not.
 * Wireless very unstable, fixed by switching to iwl3945 wireless driver.
 * Suspend and Hibernate don't seem as reliable as they were in feisty

Other than those things everything working fine, but I probably put in a good 10-20 hours of research and tweaking to resolve issues.  If you're happy with your feisty setup, DON'T UPGRADE.  Wait for Dell to get its act together and release an official 7.10 remastered version.

---

### Post by inchaos on 2007-11-10
Update:

Everything I've said so far has been using the internet update.

I recently reinstalled because I was messing with dual-booting and it went foul...not a huge deal.  

I found that when I reinstalled from the live CD, I didn't have as many issues.
There was no problem whatsoever with X breaking and so far my wireless seems stable.  

Still no Compiz, though. :(

---

### Post by Tux.Ice on 2007-11-10
ya thaats good man any ideas on hoary hedgehog

---

### Post by inchaos on 2007-11-10
Um, that's a little far away.

I'm just waiting for Dell to release a patched Live CD for us 1420n users.

---

### Post by ghindo on 2007-11-11
I'm a bit disappointed in Dell, to be honest.

I thought that everything in Ubuntu would be fully supported when I bought my 1420n.

It wasn't.  

I thought for *sure* that everything would be fixed in Gutsy.

If anything, things are worse now.

---

### Post by inchaos on 2007-11-11
I agree.

And everyone's saying they're not sure if Dell is going to support Gutsy anyway.

I heard a rumor that one could fix the stupid hanging Network Manager applet's problem by installing a different driver.

Does anyone know where we can find this other driver, what it's called, or how to go about installing it?

That's the one thing I haven't figured out how to do yet.  Otherwise, I might get a different graphics card for Compiz and games.

---

### Post by Kalli on 2007-11-12
> **ghindo said:**
> I'm a bit disappointed in Dell, to be honest.

I thought that everything in Ubuntu would be fully supported when I bought my 1420n.

It wasn't.  

I thought for *sure* that everything would be fixed in Gutsy.

If anything, things are worse now.


I also had the, apparently, naive idea that they would at least fix the biggest problems and fully test the computers they're selling, but it seems that there's no such thing as Linux that "just works"...

---

### Post by inchaos on 2007-11-12
Well, at least it's free.
:)

---

### Post by deserthowler on 2007-11-14
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

Several issues in Gutsy Gibbon aren't Dell's fault.  Dell does their part, but, until Gutsy works, there isn't much Dell can do.  They are being cautious.

I run 7.04 on my 1420n and will until 8.04 is released.  By then, 7.10 might be working.

I guess the message is "don't be on the bleeding edge if you don't like the sight of blood."

Earl

---

### Post by xskater on 2008-01-24
> **dunaway said:**
> I installed 7.10 from update manager to 1420n with factory installed 7.04 on 10/25.  Problems:

1. no GUI, but finally got that working after reading some posts.
2. no sound; still no sound...anyone help?
3. network/internet has been on/off, but working right now.
4. no "Shutdown"/"Off" button, only "Standy", "Hibernate" etc...
5. when reboot, get command line; must type in "startx" to get to GUI

I should've waited; 7.04 was working fine.

I'm having the problem with the network card randomly disconnecting and it wont let me reconnect to my wireless network unless i restart the computer... helppp its soo frustrating

---

### Post by Buffalo Soldier on 2008-01-24
> **xskater said:**
> I'm having the problem with the network card randomly disconnecting and it wont let me reconnect to my wireless network unless i restart the computer... helppp its soo frustrating

I was having the same problem. For me the solution was to change from using the ipw3945 driver to the iwl3945 driver. What I did was:
[list=1]
[*] Edit the */etc/modprobe.d/blacklist* file and add **blacklist ipw3945** to that file.

[*] Edit the */etc/modules* file and add **iwl3945** to that file.


[*] Edit the */etc/udev/rules.d/70-persistent-net.rules* file and comment out the line that's refering to your wifi card.
```
# PCI device 0x8086:0x4222 (ipw3945)
**[color=red]#[/color]** SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1b:77:c2:97:bb", NAME="eth1"
```

[*] Edit the */etc/modprobe.d/options* file and add **options iwl3945 disable_hw_scan=1** to that file.

[*] Restart computer.
[/list]

The only drawback is I cannot connect to my college AP (3com brand). Besides that, this iwl driver works flawlessly, even with WPA.

---

### Post by natehall on 2008-01-25
I have a 1420N that I've since done a fresh install with the Dell Gutsy DVD . It still occasionaly has network dropout so I tried your patch. Just In case I made a copy of your post and saved it. Good thing I did because it made my wireless go completely away! The blue light that the switch normally turns off stayed off regardless of the switch position. On the positive side it mimiced a [wierd problem]("http://ubuntuforums.org/showthread.php?t=651178") I had once where I had mutliple wired options and zero wireless options come up on my netowrk manager. 

 I went backwards through your procedure one at a time , restarting my computer each time I redid an edited line. Didn't work until I had redone it all.

---

### Post by fragos on 2008-01-25
My 1420n upgraded to Dell 7.10 works perfectly with wireless at home.  I have experienced some drop offs at my favorite coffee watering hole.  In that case the access point was linksys and the signal strenth is about 38%.  I've also noticed at that location that the linksys might not be seen but I can still manualy request a connect and get it.  My 1420n finds more access points than my friends laptops identify for them.  I'm not sure we can blame Dell or Ubuntu.

---

### Post by natehall on 2008-01-27
*he signal strenth is about 38%*

That's probably why I lose wireless every now and then. I use the computer alot far away from my source.

---

### Post by coulamac on 2008-02-23
How did you get Compiz-Fusion up and running on your 1420n?  I'm trying to do the same thing with my 1420n, which I upgraded to 7.10.  Thanks in advance for your insight!

~Andrew

---

### Post by LMP900 on 2008-02-23
> **coulamac said:**
> How did you get Compiz-Fusion up and running on your 1420n?  I'm trying to do the same thing with my 1420n, which I upgraded to 7.10.  Thanks in advance for your insight!

~Andrew

There is a [**workaround**]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") on Dell's Linux Wiki. It states that the workaround disables video playback, so I'm assuming you have to set the video output to "X Window System (No Xv)" under gstreamer-properties or the equivalent on other video players (e.g. VLC).

---

