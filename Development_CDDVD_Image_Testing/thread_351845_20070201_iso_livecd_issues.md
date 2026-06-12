---
title: "20070201 iso livecd issues"
date: 2007-02-02
forum: Development CD/DVD Image Testing
---

### Post by Master Ar2ro on 2007-02-02
The following post deals with i386 ubuntu desktop ISO from 1st Feb 2007.
Since I don't have the possibility to test the installation, I decided to make a test of the LiveCD, here's what I found:

- Hardware beep close to the end of upstart loading screen - that's something I didn't expect, and was worried that something went wrong, if it's more like a feature then ignore that :P

- The crash report icon in tray, well a nice idea, but it seems to show up unneeded. Right after the livecd booted and the desktop showed up I got information that Add/Remove programs crashed, while I didn't even touch it, didn't run a single thing, and that application is probably not run automatically (at least I think so). Later, when I was closing Sudoku, after just a quick look at it, again a crash report showed up saying that Sudoku crashed, but I didn't notice anything like that. If it's gonna pop up all the time and state that most of the applications you use crash, then it's gonna get annoying and ignored... perhaps there are some crash reports left on the livecd fs?

- Sound has got a lot of noise in it - I'm not sure what's wrong, but the sound has a HUGE amount of white noise in it. I thought something was wrong, so I opened up the movie in the sample content on the desktop, and the noise was so loud that I could hardly hear what's said on the movie. Obviously changing volume didn't help. Changing between ALSA, OSS, and the third thing didn't make any difference either. I guess there might be something wrong with either detection or the driver. I'm using SB Audigy.

I'm gonna play a bit more with it later today.

---

### Post by spd106 on 2007-02-02
Thanks for the report. 

1) I don't get that beep on start-up, might be worth looking into.

2) The add/remove crash report is known and a fix has been uploaded [#80589]("https://launchpad.net/ubuntu/+source/gnome-app-install/+bug/80589"). I haven't seen sudoku crash though. Can you reproduce it? Have a look in the /var/crash directory.

3) I don't get any white noise, but then my sound card is ancient. Probably a driver issue as you say. Have you seen [http://www.ubuntuforums.org/showthread.php?t=343697](http://www.ubuntuforums.org/showthread.php?t=343697)?

---

### Post by Master Ar2ro on 2007-02-02
I just booted back to my edgy installation, I'll recheck sudoku in the morning tomorrow ;).

Ad1) As far as the hardware beep is concerned, it's there, every time I boot (it's one of the final steps while usplash is still up), and then it's again at shutdown (one of the first steps).

Ad3) I read through that thread just now, I don't know if my problem is related to that. Didn't really notice any channels missing, but with all that noise I might have simply missed that. What I found, are two differences in device manager in GNOME control panel, between the LiveCD and my current installation. First, a value in Alsa Sequencer Device
```
LiveCD:: info.capabilities strlist dbus.Array([dbus.String(u'alsa')], signature=dbus.Signature('s), variant_level=1)
Edgy installed:: info.capabilities list alsa
```
The other difference is in the subdevices that are detected under Edgy, but either not shown or not detected under feisty LiveCD. I've attached a comparison of the screenshots.

---

### Post by la3875 on 2007-02-03
I had no issues on my "legacy" machine using it "live". Next step to install on another drive. I love the control center. Graphic resolution was perfect. Lowercase "r" in Open Office drop-down lists was weird...

Great job everyone!!! What a difference a year makes!

---

### Post by Master Ar2ro on 2007-02-03
More testing done, more problems show up.

Ad 1) The beep at startup and shutdown is still present, at every boot and shutdown.

Ad 2) Sudoku crashed again. I used the crash report bubble and sent the crash report, steps to reproduce:
 - right after boot run sudoku
 - press fill two times without selecting any field
 - select two random fields two times (so that the window with number selection pop up)
 - close sudoku
 - you got a crash report (I copied it over this time, so I can upload it all if you want, here's just the traceback: )
```
Traceback:
 Traceback (most recent call last):
   File "/usr/lib/python2.5/site-packages/gnome_sudoku/gnome_sudoku.py", line 652, in auto_fill_current_square_cb
     self.gsd.auto_fill_current_entry()
   File "/usr/lib/python2.5/site-packages/gnome_sudoku/gsudoku.py", line 1177, in auto_fill_current_entry
     filled = self.grid.auto_fill_for_xy(e.x,e.y)
 AttributeError: 'NoneType' object has no attribute 'x'
```

Ad 3) The noise is still there, no changes, it's messed up at every boot

NEW 4) This time Feisty failed to correctly set up my screen resolution (two times I booted it correctly set 1280x1024, this time all I had was 640x480). No idea why, but I copied over the logs and config files, so I'll search for any error messages. I don't believe that it might be the reason, but the last two times I booted Feisty LiveCD was when I restarted from Edgy, this time I restarted from Windows XP... I don't believe that this might be the cause, but I'll try to boot after restarting linux again later today.
//EDIT: Restarting from Edgy and booting the LiveCD the resolution was ok again. Perhaps it really is a windows issue...

NEW 5) The usplash screen on shutdown disappeared too soon, not showing the message about removing CD and pressing enter, just blank console screen left and CD tray open... though pressing enter worked, so I guess the graphical mode got killed for some reason. Can't give any logs for that though ;)

I'll report when I find out something more...

---

### Post by jerrylamos on 2007-02-03
I'm trying to use rsynch, but the commands as given in Wiki don't work.  This  report is from Herd 3 Thursday 0201 download.

Hardware.  All three run fine with Dapper, Edgy, and Windows.

1. IBM Netvista 8303 SB2 Pentium 4 2GHZ 1024MB Windows XP

2. IBM Thinkpad R31 1GHZ built in graphics 512MB Dual Boot XP, Dapper

3. Scratch built 1 GHZ Celeron 512MB with PCI graphics card and PCI ethernet
   quad boot Dapper, Edgy (Xmas), Xubuntu Edgy (not much use with no Places, Network),    
   and a Windows 98 (for printer head clean & cartridge change, Ubuntu can't do.  98 is 
   somewhat sick from Feisty Herd 2 partition damage) and a partition available for instal
   of Feisty herd x.

During startup Add/Remove crashes on all three.  I click restart.  No message back.

On 1, a while after the beep, the LCD monitor reports no signal and goes black into power save mode.  

On 1, With "safe graphics mode" after the beep Feisty CD Live came up 1268x1024 (17"LCD) looks fine.  Feisty CDLive comes up 1024x768 on the other two.

On 1, top line icon shows "Wired network connection".  Logs onto internet fine.

On 2. one top line icon reports "Wired network connection" and another icon reports "Network Connection: eth0".  Log onto internet fine.

On 3. persistent mode works fine.  I almost forget it's not running from hard drive.  I can install packages (AOL instant messenger with open source GPL) etc. 

On 3. Network Manager reports "no network connection".
I do sudo dhclient, then I can access internet O.K.  Network Manager still reports "no network connection" even though it is running fine.

Usability:  Dapper splash screen is very readable.  Edgy and Feisty splash, I wonder why nothing's happening, and notice a couple dark blue lines on black.  I get really close and squint, and it says "press enter to continue".  Edgy Xmas edition has just as tiny print but its more in the middle of the screen and much much brighter.

Usability: Feisty System, Control Center much slower to use.  Information is all spread out all over the screen, and with the big hieroglyphics the options don't fit the screen, even at 1280x1024.  Is there a "list mode" available?

So far, for general linux work and internet, Dapper is easier to use and my clear preference.

---

### Post by pochu on 2007-02-04
Please, report the bugs in [Launchpad]("https://bugs.launchpad.net/ubuntu/+filebug"), so they can be fixed.

Best regards
Pochu

---

