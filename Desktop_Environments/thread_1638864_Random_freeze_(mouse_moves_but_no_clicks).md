---
title: "Random freeze (mouse moves but no clicks)"
date: 2010-12-06
forum: Desktop Environments
---

### Post by kirollos210993 on 2010-12-06
I am using Ubuntu 10.10,

I start the computer and then randomly, sometimes just when the desktop shows up and sometimes when i am browsing (Chrome or Firefox), the screen stops responding to any keyboard and mouse clicks. At the top gnome panel i have a 'system monitor' bar, which shows cpu usage, network speeds and disk load... all of them are frozen. I can still move my mouse but no response to any clicks. I normally hard reset. But if i keep going (2-6min) trying to click on windows, even the mouse cursor freezes. The numlock key light is also irresponsive to numlock key presses the whole time from the initial freeze.

These freezes occur with effects (compiz) on or off.

Freezes also always occur while the computer is on ubuntu's 'screen lock'. I come to move the mouse to enter the password, and nothing responds. I press the numlock key, no response from the light. I recently tried removing and reattaching the keyboard and mouse... no success. I have also tried doing what this post says: [http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/) : resulted in the numlock key light responding but still screen stayed black (because on lock screen it is black) and still couldn't see the mouse.

I installed all ubuntu versions from ubuntu 9.04 and in all of them i have experienced display problems. This problem i think i have experienced from 10.04, but probably from 9.04 as well.

I have done S.M.A.R.T. hdd checks and all (1000gb WD and another 500GB WD) passed.

I have an apache, ftp and webmin server on ubuntu and all can be accesed from another computer during the freeze. i.e. computer is connected to the network and CPU responds to proccesses. I have mostly resetted my computer using webmin, and i could still download stuff using apache and ftp.

I have had 2 graphics cards and both have the same problem. One of them is the Gigabyte 512MB NVDIA Geforce 9500GT and the new one (bought new 2 days ago) is an inno3d 1GB NVIDIA Geforce GT 240 (supposedly twice as better as the 9500gt).

I also have windows on this machine - that works fine. I have had freezes (on both grahics cards) but that was because i had settings too high on Test drive unlimited (That and flightgear are the only games i really play i.e. tested). No mouse or keyboard responded. Hard reset was only option.

I have reinstalled ubuntu many times, reformatted HDDs many times, reinstalled drivers, reinstalled NVDIA drivers from NVDIA's website, removed Cd & DVD drives to consume less power from a 460W P/S which came stock with a coolermaster case... no success.

My system is fairly new, bought it around the end of the first quarter of the year.

The specs are:
MB: Asus P5Q Pro (I think)
Graphics Card: currently = inno3d NVDIA Geforce 1GB GT 240. Old one = Gigabyte 512MB NVDIA Geforce 9500GT
RAM: 2 * DDR2-800 2GB Kingston
CPU: Intel E5200
Keyboard & Mouse: Microsoft wired keyboard 600
Screen: BENQ E2200-HD @ 1920*1080
P/S: Came with Coolermaster 690, 460W

I appreciate any help in advance. I am a beginner with little knowledge. I have read endlessly and haven't found a solution. I am also aware of similar posts, but they don't reflect on my problem's symptoms.

Thanks again

---

### Post by gogolink on 2010-12-06
Hi kirollos,

I'm not much of an expert myself, so I don't know if I can help.  But I was wondering whether perhaps your **swap** area is too small?  You'd probably want to have 3GiB or so of linux swap; you could check how much you have using gparted (Gnome Partition Editor; can be installed from software center).

Another tip (perhaps; you might know that): You should be able to open a terminal through a keyboard shortcut (I have Control+Mod4+T set to "Run Terminal"; can be set under System > Preferences > Keyboard Shortcuts), so that you can exit it even when your screen is frozen.

The terminal command "killall gnome-panel" will end and restart the panels; you could try if that does anything when your screen is frozen.  The command "top" will display active processes, and indicate if any one of them consumes too much of your CPU -- in which case you might want to end it.  And "sudo reboot" would restart your system...

Don't know whether this helps, but until a more experienced expert responds...

---

### Post by kirollos210993 on 2010-12-06
Hey gogolink,

Thanks for the reply and tips. My swap is actually 11.3gig (surprising -  i thought i made it 4 gig.) 

I didn't know about the terminal shortcut. But i will try and i don't think it will work because the computer doesn't respond to any clicks and the keyboard's numlock key won't respond to any presses of te numlock key. From all that i experienced, that is a sign of a lockup from the cpu. But as i mentioned in my inital post, i can access and send commands to the spu using webmin.

Building on the terminal idea, however, i will try to use 'ctrl + alt + {F1 or F2 or F3... F6}'. This gets me to the first, second, third... sixth virtual terminal.

I will also give your commands a try. I will also give the '/etc/init.d/gdm restart' a try to restart my gnome display manager.

Thanks, anything helps.

---

### Post by kirollos210993 on 2010-12-07
hey everyone,

Computer just froze again. I accessed it using webmin and none of the commands worked.

Here's what happened:
I used the zoom function in compiz, and while i was zoomed into the program 'freemind', it froze; the cursor, however, moves, as i said before. I removed and reattached the keyboard and mouse and nothing happened except the mouse cursor froze completely.

The screen looks weird: the texts (words) radiating close from the center of the screen have vertical ( | not - ) flickering of one of the letters from each word. I am stuck in the previous zoom position and am unable to click on anything.

BTW, yesterday i completed a memtest86+ (something like that) from the ubuntu startup screen for about 8 hours and there were no errors

I have observed that the frequency of freezes have declined with this new graphics card (GT 240). It suggests that the problems are because the cards can't handle the complexity of compiz's effects? I don't know.

---

### Post by pedanticmofo on 2011-01-09
I've started experiencing similar problems with my 10.10 installation.  Twice so far in the last two days the system has frozen but:
1) I can still move the mouse around but mouse clicks don't work
2) hover highlight still works on the Chrome browser tabs and close tab Xs--I don't know about Gnome icons since I didn't think to check
3) the system monitor in the task bar continues to show system load
4) streaming music from Pandora continues to work

The keyboard seemed unresponsive but I didn't check the NumLock light and I only learned about the Alt+SysRq+K/+REISUB after the latest crash so I haven't tried that.  I held down the power button for a few seconds to force shutdown and then rebooted and everything seemed okay after each crash.

Unlike the other poster, I'm not using Compiz--i.e. I have Gnome's visual effects turned off--since it interferes with Flash, I also do not get any screen artifacts, and the mouse doesn't eventually freeze as well if the system is left alone for a few minutes.

During both crashes FBReader, Firefox, Chrome, and the OpenOffice Quickstarter were all that was running, but this is not an uncommon combination.

System configuration is as follows:
MB: Foxconn A74ML-K
Video: on board Radeon 2100
CPU: Sempron 140
RAM: 1GB of Crucial DDR2 800 with 128MB reserved for the on board video
HDD: 250GB Seagate Barracuda 7200.10 that SMART says is "Healthy"
Keyboard/Mouse: Logitech USB
PSU: SeaSonic 350W with Active PFC and the good caps.

I only have 2GB of swap space, but there was no noticeable disk activity when the system froze.

System changes in the last few days before the crashes happened included running the weekly update yesterday morning and installing [webcamstudio]("http://sourceforge.net/projects/webcamstudio/") for testing and then removing it, also yesterday.

Aside from running Memtest, which I am about to do, does anyone have any suggestions about what's wrong or what I can test to find out what's wrong?  Please keep in mind I don't have access to alternate hardware and can't afford to buy new hardware just for testing.

Thanks.

---

### Post by Sumit Raja on 2011-01-10
I have been having exactly the same problems on a Lenovo W510 with 10.10.

I have looked at syslog and usually logging has stopped about an hour before the hang. It seems like writes to disk have stopped.

I have kernel 2.6.36 because I read another post that said this might fix the problem, but no joy.

I did manage to shutdown 2.6.35 when this happened and it did give me this error numerous times. 
```
ata1 COMRESET failed errno = -16
```

A reboot always works. I have checked the seating of the hardrive and it seems stable and stays connected. I have run a BIOS disk test that was successful. smartcrl output is below.

Out of options on how to proceed on this, any one have anyway to diagnose further?

Thanks

Sumit

```
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   099   034    Pre-fail  Always       -       178663618
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       102
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       974175
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       99626061398127
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       102
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   084   000    Old_age   Always       -       73015754821
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   057   053   045    Old_age   Always       -       43 (Lifetime Min/Max 36/43)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       22
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       569
194 Temperature_Celsius     0x0022   043   047   000    Old_age   Always       -       43 (0 1 0 0)
195 Hardware_ECC_Recovered  0x001a   046   040   000    Old_age   Always       -       178663618
196 Reallocated_Event_Count 0x000f   100   100   030    Pre-fail  Always       -       106 (25193, 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       11
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       0

```

---

### Post by dotbart on 2011-01-12
I had the same issue here.
I seem to have solved it by switching my display drivers to the Nvidia proprietary driver.

Which is odd if you think about it: if the display driver froze, why would my mouse still move?
Anyway, still glad my screen doesn't freeze anymore

---

### Post by Sumit Raja on 2011-01-13
Nvidia drivers has not helped with me.:(

Beginning to think it is a faulty drive or a faulty SATA controller. The problem only seems to occur after a suspend resume cycle, never after a reboot.

---

### Post by tonyuprm on 2011-01-19
Hi all,

I'm having the same problem on my lenovo W510. I have installed Ubuntu several times. I have the latest NVIDIA drivers but still no luck. It freezes several times a day! Can this be a hardware problem?

Tony

---

### Post by m0lly on 2011-01-21
I added this to my /etc/apt/sources.list
```

deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu lucid main[FONT=monospace]
[/FONT]
```

Then I did:
```

sudo apt-get update
sudo apt-get upgrade

```
It might complain about certs you don't have from the xorg-edgers ppa site, I just ignored the warnings.

This fixed my problem.  Recommended for you?  Probably... but maybe not  -- this is bleeding edge dev of xorg.  There might be bugs.  You  probably want to disable that repo in your sources.list after you do the  apt-get upgrade ... proceed at your own risk!

---

### Post by CJ_Hudson on 2011-01-21
It's a long shot but maybe you could try updating your kernal?
Or even longer shot flash the system's BIOS?
Not sure how to do the first and never done the second in Ubuntu, only Windows.
Hope that helps some!

---

### Post by Sumit Raja on 2011-01-24
Having investigated this further this seems to be related to the NVidia & AHCI interupt conflicts.

Found a the following link [http://www.nvnews.net/vbulletin/showthread.php?t=126152&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=126152&page=2)

Am running with the Nouveau driver for a while and seeing if I get the same problem. I can reproduce it very easily by running eclipse for a while and tailing syslog. I see the ata errors in the log and then the system hangs.

---

### Post by Sumit Raja on 2011-01-27
Configured some Nvidia settings I have managed to run a stable system for about 24 hours now.

I did the following, if any one else wants to try it:

Edit (or create if missing)
```
/etc/modprobe.d/options.conf
```and paste the following lines in ( the EnableMSI being the important ones, the AGP option supposedly fixes my suspend problems which I haven't tested)

```

options nvidia-current NVreg_EnableMSI=1 NVreg_UsePageAttributeTable=0 NVreg_NvAGP=1
options snd-hda-intel enable_msi=1

```Then run
```
sudo update-initramfs -u
```and reboot.

So far no more ata timeouts or system freezes.

---

### Post by beeboo on 2011-02-15
Two-weeks in now, is your system still stable after these changes?

---

### Post by 3cardtrick on 2011-04-26
I'm also curious - has your system been stable since this? Or did you have to find another solution?

I seem to be having the exact same issues, but an "/etc/init.d/gdm restart" just as I login seems to keep the problems at bay.

Thanks,
3ct

---

### Post by cespinal on 2011-05-01
1+ here... installed ubuntu two days ago... having the same crashes in both unity 2D and 3D 

I'll just sit and wait... I believe this is more a bug than a miscofinguration issue. It's always like this with the new versions

Edit: will update the BIOS and see what happens.

---

### Post by cespinal on 2011-05-01
Bumpo.... 

I have gotten to the point where I am getting the crashes when doing something on a Browser... Firefox works better than Chromium but I still got a crash a couple of minutes ago trying to log in to an IRC

---

### Post by TBeholder on 2011-05-01
Had the same trouble from time to time, suspected ATI driver.
Then it gone away after some or other upgrade.
I played with **xorg.conf** a little, though. No idea what it was, maybe because "XFree86-Misc" was removed and "glx" is the only thing loaded in Section "Module".
Try this.

---

### Post by cespinal on 2011-05-03
Still waiting for that update :D.. I still have faith the system will become a lot more stable.

---

### Post by hubertofliege on 2012-03-28
I have this problem.  I'll check my driver, but could someone explain for me what the suspected culprit is?  I've had the same problems in 11.04 and 11.10 on an Asus B53J.

---

### Post by kirollos210993 on 2012-03-28
Hey everyone,

Just letting yous all know that now i don't seem to have this problem, or atleast too little to be classified as a problem.

I didn't change the graphics card, its still the same gt240, except ive got 11.10 now. I think it got better from 11.04, so maybe update, but i see that many still get it on 11.10, so idk.

and @[hubertofliege]("http://ubuntuforums.org/member.php?u=888791"), you get the problem on an Asus B53J, thats crazy, it looks like it has high specs. So i think it most certainly is an Ubuntu problem.

But yea sorry, can't really help, just updating everyone really.

Good luck to you, hopefully youll all be able to enjoy ubuntu like i am :)

):P

---

### Post by hubertofliege on 2012-04-11
Ulh.  Thats how I've fixed plenty of stuff in the past: waited for updates.  I was trying to avoid upgrading, though, because I don't like unity at all.  If anyone has any more suggestions, that'd be great.

Are there any other similar threads about this?

---

