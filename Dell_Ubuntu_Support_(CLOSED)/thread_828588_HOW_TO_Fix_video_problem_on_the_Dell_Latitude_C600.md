---
title: "HOW TO: Fix video problem on the Dell Latitude C600/C500"
date: 2008-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SomeGayDude on 2008-06-13
After a lot of hair pulling, cussing and no help I figured out a fix for the Dell Latitude C600/C500 video problem.

This is a ATI Rage 128 Mobility graphics card.  The problem is not with the drivers, bit with X configuration.

1) Start with the clean install of ubuntu.  This will give you 800x600 screen resolution.

2) Download the _xorgconf24.txt_ to you desktop.  This is at the bottom of the message under _Attached Files_  *Note: As suggested by other users, I have included resolution depth of 16.  If the depth of 24 is undesirable, repeat all the steps but download _xorgconf16.txt_ instead.*

3) Start Terminal (Applications/Accessories/Terminal)

4) Enter the command _cd /etc/X11/_  (This is case sensitive as in capital X and has a space between the cd and /etc/X11  To paste in the Terminal use Shift+Ctrl+V)
```
cd /etc/X11/
```

5) Enter command _sudo gedit xorg.conf_```
sudo gedit xorg.conf
```

6) Enter your root/Admin password. (The text editor will open the problem file.)

7) Click the _Open_ button.

8) Open the downloaded xorgconf.txt file that was saved to the desktop.

9) Delete all the contents of xorg.conf (Problem file)

10) Copy all contents from xorgconf.txt (Working file)

11) Paste all contents to xorg.conf (New Working file)

12) Save xorg.conf

14) Reboot the laptop.

When the laptop restarts, it will be in the 1024x768 screen resolution.

I know their is a lot of instructions here.
If you have questions, easer steps, or find a mistake or misspelling please let me know.  This is a work in progress.

---

### Post by rose3694 on 2008-06-18
I wanted to say thank you this worked perfect on my Dell C600 with an ATI Mobility 128 card.

Thanks,
Rose3694

---

### Post by dumpy on 2008-06-29
so i tried this on my c600 (with ati graphics) and it did change my resolution, but now i have the "split screen" effect going on.  I'm thinking possibly a driver issue.

Anyone have any ideas?


Thanks!!

---

### Post by SomeGayDude on 2008-06-29
It should not be a driver issue.  Something is messed up with the xorg.conf file.  Could you please post the file and I will take a look.

---

### Post by moejoe on 2008-06-30
Thank you very much, your how-to finally fixed my problems on the C600 :)

---

### Post by SomeGayDude on 2008-06-30
I am glad that this worked for all of yous.

---

### Post by WinonaVaughan on 2008-07-01
I have a Dell Inspiron 5000e that I've been setting Kubuntu up on and it corrected the split 600 x 800 display that I previously had perfectly. The new 1024 x 768 resolution is obviously much better to work on as well. Thank-you too very much. Good work!

---

### Post by dhack21 on 2008-07-01
Definitely a helpful post. Worked great on my Inspiron 4000 as well.

---

### Post by ttmontoya on 2008-07-01
Thanks man this really worked:guitar:
You Rock!!!

---

### Post by PierreDeKat on 2008-07-12
Awesome! Worked for me, too.

Just a note to folks running Xfce or Xubuntu, you will have to enter

_sudo mousepad xorg.conf_

on step 5 instead of

_sudo gedit xorg.conf_

We don´t have the gedit text editor on Xfce/Xubuntu, so we need to use mousepad. But other than that, it works like a charm.

Thanks, SomeGayDude!

---

### Post by jonathan170982 on 2008-08-04
Thanks a million!! I am a newb to Ubuntu, and only installed it about a week ago, and its taken me since then to finally have the display working!!!!

Thanks alot!!
Jon

---

### Post by evogoalie on 2008-08-04
Newbie...
So please bear with me.

I followed the instructions, downloaded the file
Cut and pasted,  
The display is still is still in a split screen effect.
Any ideas ?

---

### Post by 937 on 2008-08-08
I tried this on my old Latitude C800 (with an M4 card) but it ended up with the old split screen stuff goin' on. Any ideas how to get it to work on a C800?
lspci reports an ATI rage mobility M4 AGP, also everything is sooo slooow, Oh what I wouldn't give for 1224x768.
800x600 works fine but it's just not right somehow...
Any ideas?
BTW- Very new to Ubuntu (4 days but like it so far) so any instructions  need to be in idiot proof format please.

---

### Post by Fatal Toenail Infection on 2008-08-15
Just got done installing Ubuntu 8.04 onto this laptop hoping to breathe some life into it, but I ran into the split screen issue everyone else is talking about.  I tried this xorg.conf, but it didn't work for me.  So I did a little bit of my own research (I'm relatively new to linux) but I found the problem.  The problem is that the default depth in the xorg.conf is set to 24.  Change it to 16 and you will be golden!

---

### Post by evogoalie on 2008-08-21
Yup changing the default depth to 16 did the trick.

Thanks

---

### Post by KR4WM on 2008-09-12
> **Fatal Toenail Infection said:**
> The problem is that the default depth in the xorg.conf is set to 24.  Change it to 16 and you will be golden!

I'm a total noob to Linux. How do you accomplish this?

Thanks, -KR4WM

---

### Post by zappy00 on 2008-09-15
Thanks so much, SomeGayDude and Fatal Toenail Infection! you're Ubuntu stars! :KS

---

### Post by KR4WM on 2008-09-15
Disregard. I figured it out, but I still could not get Kubuntu to make use of my entire screen. There was a 1/2 inch on each side that stayed black. I gave up and went back to the "dark side" (Windoze). At least it works properly. Some day when I feel I have nothing better to do, and tire of mosquito hunting with my slingshot in the swamp next door, I'll give Linux another try. -KR4WM

---

### Post by oldexplorer on 2008-09-23
Thank you SO much!!! :) I really appreciate this. My laptop is now excellent. Great job...

---

### Post by UDanbert on 2008-10-02
I really hope I am not sounding stupid here. Another Newb to This wonderful new world. 
I have a lattitude C600 with the ATI Mobility 128 card. What I am having a problem with is a black border around the usable part of the screen. Like over an inch in 1024x768 and even bigger if I go lower on the res. 
is this fix to cure that problem? Or do I need to start a new thread to address my particular problem? 
Any simple instructions would be appreciated. I would like to have my full screen back. Yes, that is what it implies. before my latest upgrade to 7.10, I had full screen. 
Second, Should I be running 7.10 on this laptop? (If i should be asking this in another place, let me know, I will be happy to re-post that question)
Thank you all. 
UDanbert

---

### Post by UDanbert on 2008-10-03
This worked great to solve my problem. I did have to make the changes to 16 from 24. 
Thank you for your help.

---

### Post by mreester on 2008-10-04
Thanks so much for the advice, it worked perfectly. I had tried a few things in other threads with no luck, but this did the trick. 

However, if things go totally goofy (which they did for me with some of the other suggestions), folks might appreciate a fix for getting back to the default setting. 

Go to Terminal, and from the command line type:

sudo dpkg-reconfigure -phigh xserver-xorg

This will get you back to your default graphics setup. Thanks again!

---

### Post by tpak on 2008-10-07
Thanks to the various posters! My C600 required the OP's xorg.conf and the change to 16 for default depth to solve the split screen crazies. I think this fix will be required in Fedora Core 9 as well - I saw the same issues there and only mention it here in case someone finds this post. 

Now if I could just get the darn thing to boot without going into X at all I'd be happy. Off to read the upstart docs .... 

Thanks again.

---

### Post by mowgliee on 2008-10-25
i have tried this w/ both 16 and 24 and upon reboot 8.04 (fresh install) just goes into safe mode w/ a very small screen (no split screen effect though).

if i reinstall or use the dpkg cmnd, i get back to my low res split screen prob.

repeat the steps in the how, always goes back to screen and card cant be detected so dropping down to low graphics mode.

crazy considering i have the same laptop, same symptoms as everyone else so i should have the solution.  sigh.

---

### Post by mowgliee on 2008-10-25
ok problem solved!

i just used displayconfig-gtk to choose dell laptop display w/ desired res as my monitor and ati rage mobility 128.

then i just changed all the depth settings to 16 (24 failed).  and voila!  its all good.

my xorg.conf is very diff from the suggested one however.  but who cares, it works.  me happy!

i suggest you try the how to solution first though; i have no clue why i had to do it differently.

---

### Post by xavier_p on 2008-11-02
Thanks. Worked like a charm. I just edited the "xorgconf.txt" slightly though as I didn't want to change my keyboard or mouse settings.

---

### Post by yadster on 2008-11-18
This worked great thank you for the post

---

### Post by nos482 on 2008-11-21
thank you very much , this worked without a hitch.  
Ubuntu rocks:guitar:

---

### Post by palito1980 on 2008-11-24
Great job with this howto but I have a question.How to change refresh rate from 60 MHz to at least 75 MHz. It will be less tiring for eyes.

---

### Post by narobni on 2008-11-24
Ahhh.... at last! Did a clean install of Ubuntu 8.10 on my Dell latitude c600, it came up with only 800X600 resolution. Tried various other guides to change the resolution, but yours did it! Thank you very much for helping out :)

---

### Post by kurvenrauber on 2008-11-25
Thanks a lot for the understandable documentation.
I am absolute Beginner and want to use my old laptop (2001) for quick connections to the internet. Perfect now.:KS

---

### Post by orange_roughy on 2008-11-29
For anyone else who finds this awesome thread but cannot download the OP's attachment, here are the contents.

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

and the reason you can't download the attachemnt is because you're viewing this thread from something like ph.ubuntuforums.com/showthread.php?t=828588 or [http://backports.ubuntuforums.com/showthread.php?t=828588](http://backports.ubuntuforums.com/showthread.php?t=828588) instead of the correct domain: ubuntuforums.org.

Hope this helps someone. Took me a whole day to figure this out.

---

### Post by vascsab on 2008-11-29
Thank you very much! It's really working!

---

### Post by sarahwww on 2008-12-02
Let me add my thanks to the solutions presented here. I was going nuts, going through one old laptop after another (I am at a school), thinking my cd drives were bad. LOL! Now some of the little darlin's can use laptops with Ubuntu ( and they won't know what hit them!):guitar:

---

### Post by tiburk on 2008-12-05
This conf work fine in Ubuntu 8.04 and 8.10, but not work for Kubuntu 8.10.

Why reinstall my machine??? WHY????

---

### Post by SomeGayDude on 2008-12-05
> **tiburk said:**
> This conf work fine in Ubuntu 8.04 and 8.10, but not work for Kubuntu 8.10.

Why reinstall my machine??? WHY????

I believe Kubuntu still uses X and it should still work.  I never told you to reinstall anything.  Some installed software might modify the xorg.txt file and the instructions doesn't consider this.  I mention to fix this when ubuntu is newly installed so that any modifications can be done afterwards.  

If you still have issues then please create a new thread and someone will be able to help you.  I not comfortable with KDE so someone else would be more then happy to help.

---

### Post by ulrith on 2008-12-06
Thank you!!! It works! ):P

---

### Post by foofighterjim on 2008-12-14
Top man, thnaks for this.

---

### Post by mattmoose on 2008-12-21
I too have exactly the same problem.

xubuntu-desktop 8.10
Laptop: Dell Latitude "C600/C500" a.k.a. model PP01L
Video chipset: Ati Rage Mobility M3 AGP 2x (rev 02)

Thanks to the above help, I have full screen size now, but horizontal sync timing looks appallingly incorrect. The left hand side of the screen is good, but there are moving jagged vertical edges going down through the centre of the screen, then the right hand side looks ok again.

This is exactly the fault I had on Ubuntu 8.04 / 8.10 install attempts, hence my trying xubuntu... :(

Help, any ideas?!?

Regards
Matt

---

### Post by SAsghar on 2008-12-23
Hi, sorry to bring up an old issue
Just installed the version 8.10 and graphics arent working out on my Dell Lat C600
I have copied the file (replaced by xorg.conf) the resolution is good but have a split screen
Would appreciate it if you could advise on how to remove the split

---

### Post by pfry on 2008-12-23
Gay Dude,

You're the man....worked perfectly.

Thanks,

paul

---

### Post by solotim on 2008-12-30
Thanks too.
Your file did work.
I just wonder why dpkg-reconfigure xserver-xorg can't make sense now, since in xubuntu 7.04 or before this command can actually change the resolution.

---

### Post by woodslot on 2009-01-02
Thanks. 

I'm a newbie and I've been playing with my installs (8.10 and 8.04 and Debian) trying to fix this same problem on my old ThinkPad A22m (2628STU) with the ATI Rage Mobility video. 

I knew there had to be a fix since I could run Knoppix with full screen resolution so I've been surfing for a solution over the past several days.

I finally got away from the multiple split screen issues by running the Live CD in video safe mode (F4 from the initial boot screen). That gave me the 800x600 resolution with a black boarder all around. I installed from within the Live CD mode and the install was complete with a stable but low res display. 

I replaced my xorg.conf Device, Monitor and Screen defs with those from xorfgconf.txt and that worked great. After reboot the whole display was being used at 1024 res. My panel display can run at 1400x1050 so I tweaked the xorg.conf file to add modes 1400x1050 and 1280x1024 (I also set default depth to 16)

	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1024x768"
	EndSubSection

This initially had no effect. Xorg.0.log  (System-> Administration->System log) showed that with the 1280 and 1400 resolutions the HSYNCH was out of range. The Log also ID'd the panel ID as IBM ITSX93 and Googling that I found the IBM specs and found the HSYNCH can be as high as 70 MHz. With a change to the Monitor section to read as follows:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

and with a reboot I now have full screen resolution at 1400x1050. 

Thanks again. Your HOW TO had the detail needed.

---

### Post by CadaverBSE on 2009-01-04
Thanks for this fix, but I too had some slight differences. I combined SGD's post with another regarding refresh rates and got my Latitude 600 up and running. 60Hz 1024x768 works, I have not tried higher rates.

Version: Ubuntu 8.04 EMC2 

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31.5-90
	VertRefresh	59-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	16
```

Jay

---

### Post by mike@romram.se on 2009-01-05
To learn more, read about this here: [https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

You will find that most probably it is only the HorizSync value that you will have to add.

---

### Post by Rock1 on 2009-01-19
This is my first experience with Ubuntu.  I set is up on a C600 and installed the fix without any problem, thanks very much.

---

### Post by gnoob on 2009-01-20
Thanks a bunch, I have been looking for this for a while. This worked on my old dell inspiron 4000 running 8.04. I had to go into screen resolution once I restarted to set it to the higher resolution, but besides that it worked like a charm.

---

### Post by tim123456 on 2009-01-25
> **SomeGayDude said:**
> I am glad that this worked for all of yous.
I have the same split screen problem, but I can't locate the file or fix you posted in response to this message.

Could you direct me to the fix?

Thanks!

---

### Post by Ms. Phitt on 2009-02-03
> **tim123456 said:**
> I have the same split screen problem, but I can't locate the file or fix you posted in response to this message.

Could you direct me to the fix?

Thanks!

It's in the first post on the first page of this thread.  Here's the link in case you were referred to the wrong place:

[http://ubuntuforums.org/showthread.php?p=5182387#post5182387]("http://ubuntuforums.org/showthread.php?p=5182387#post5182387")

---

### Post by cee-jay on 2009-02-08
(SomeGay) Dude!  Perfect fix--now I can continue to use the heck out of my dear ol' trusty c600!
=D>

Also, it's crazy how all of the "thanks dudes" are from us lowly 'First Cup-ers."  heh heh

---

### Post by Tacofitz on 2009-02-17
another happy customer thank you!

---

### Post by bugtussle on 2009-02-19
> **PierreDeKat said:**
> Awesome! Worked for me, too.

Just a note to folks running Xfce or Xubuntu, you will have to enter

_sudo mousepad xorg.conf_

on step 5 instead of

_sudo gedit xorg.conf_

We don´t have the gedit text editor on Xfce/Xubuntu, so we need to use mousepad. But other than that, it works like a charm.

Thanks, SomeGayDude!

Very Sweet, My Inspiron 4000 looks perfect now. I thank both of you very much!!:D

---

### Post by rjones5296 on 2009-02-20
WOW thanks This worked fine on my Dell Inspiron 4000.
Did the patch rebooted then I had 1024x786 screen resolution.
Thanks again this is sooooo coool.

bob

---

### Post by jigmasta on 2009-02-26
great fix, additionally changing resolution depth to 16 finally made my day. Maybe it should be considered to change this by default in the downloadable file (or point out to this problem in the first place).

---

### Post by Bozzer on 2009-02-28
I followed the instructions exactly on my Dell C600, now it only runs in low-graphics mode with the messages, "(EE) Failed to load module "ati" (module does not exist, 0)" and, "(EE) No drivers available." A C600 is a C600, shurely? Any ideas? (I tried changing the depth from 24 to 16 - same result!)

---

### Post by SomeGayDude on 2009-03-02
I have never heard of this error message.  I have no idea how to fix this.  Sorry for the late reply.  I drive trucks and dont get much of a chance to get on the internet.  My Latitude donst have an A.  Just has Latitude C500/C600.  It might not use the ATI Rage 128 Mobility graphics card.

---

### Post by deputyjones on 2009-03-03
Worked perfectly on my C600 in Crunchbang Linux, thanks!

---

### Post by JQuinonez on 2009-03-08
Thanks man

you are the best

---

### Post by markuk25 on 2009-03-09
Thank you very much.  I have been looking for a fix for ages.  Worked first time.

---

### Post by Hondo88 on 2009-03-10
Thanks. Like others, I had being trying many other things. Found this, worked perfectly.

---

### Post by FSAZ on 2009-03-17
Excelente. Muchas gracias.

---

### Post by duststorm on 2009-04-01
Based on some other info I found here and there over the web, I managed to create a config that supports a 1400x1050 resolution on my Latitude C600 without glitches.  So this is for those with a Latitude that has a 1400x1050 screen.

xorg.conf
> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection




Just wanted to share this since I didn't find a "plug and play" xorg config file that gives you 1400x1050.
Also, I'm using 8.10 Intrepid (Xubuntu) but I believe it should work fine for both older and newer releases, and also with Ubuntu and Kubuntu.

Enjoy :)

---

### Post by scratchy12 on 2009-04-22
> **Fatal Toenail Infection said:**
> Just got done installing Ubuntu 8.04 onto this laptop hoping to breathe some life into it, but I ran into the split screen issue everyone else is talking about.  I tried this xorg.conf, but it didn't work for me.  So I did a little bit of my own research (I'm relatively new to linux) but I found the problem.  The problem is that the default depth in the xorg.conf is set to 24.  Change it to 16 and you will be golden!
I agree with everyone else,  Some Gay Dude rocks.  With his help I figured out the resolution.  Fatal Toenail Inf. rocks too because changing 24 to 16 got rid of that annoying split screen.  Thank you!

Anyone have ideas on how to get my S Video out to work?

---

### Post by Sidney232 on 2009-05-16
Wow! Great fix! My C600 is now usable. I only copied the three sections of the new xorg.conf for the screen fix (depth=24 version) and it all worked perfectly.

---

### Post by Digital Magi on 2009-06-21
Thank you so much! You helped me bring my old laptop back to useful life. This worked, just like you specified.:)

---

### Post by Vulkano on 2009-07-03
Thanks for the help! Just had to change one thing though. Instead of using the driver "ati" I defaulted back to "vesa". When using the "ati" driver I had the split screen "effect" with Depth 24. However, with the "vesa" driver I can use a Depth 24 option with no problems.

Still wonder if how can I make it go higher... On the other OS installed in this same faithful ol' box, I can go up to 1400x1200 (although I can barely see anything on a 14" screen using that res!). However, when trying to get such a res in Ubuntu, I get a message like "going to low resolution" or something like that when starting X.

For now, I can use the machine in a comfortable res, so perhaps I might try to tackle the task in the future.

I followed duststorm's lead and modified the HorizSync according to his numbers (higher than what I had), and was able to increase screen resolution to 1280x1024. Although I did include the "1400x1050" option in the xorg.conf, when restarting X screen resolution defaulted to 1280x1024. In the Screen Resolution GUI application the 1400x1050 option was not available. Perhaps it has something to do with me using the "VESA" instead of the "ati" driver.

For others I advise trying either a broader range for the HorizSync and the VertRefresh frequencies or change between the VESA and the ati drivers. Within one of these changes might be the clue.

Now that I fixed my res problem, I'm taking a plunge to make my wifi PCMCIA card work.

Now that my screen res problem has been fixed

---

### Post by Mulenmar on 2009-07-06
Well, it took the better part of an hour hunting through Dell's website :mad:, but I finally tracked down the exact specifications of the Dell Latitude C600, including the supported resolutions for the display. Nothing on the timings, just the external refresh frequency. :mad:

Apparantly 1400x1050 IS the maximum possible with the LCD screen, but the ATI Radeon M3 can drive an external monitor at up to 1600x1200 at 32-bit color.:-o

Here's the link -- and I actually tested it this time, so it works. :KS

[http://support.dell.com/support/edocs/systems/latc600/en/ug/specs.htm]("http://support.dell.com/support/edocs/systems/latc600/en/ug/specs.htm")

---

### Post by HemiGTX on 2009-08-12
sorry to drudge an old thread up but what i done for this problem on 8.04 was "sudo displayconfig-gtk"

there you can make the changes needed, i have an external monitor running at 1200x800 and the lappy monitor can run at 1024x768 on an ati Radeon Mobility M6 LY

---

### Post by kyfiredawg on 2009-08-12
Being new to Ubuntu and installing it on an old Dell Latitude C600 with ATI Mobility M3, I had this problem. After searching and searching I found this post. I followed the instructions and it worked like a charm!  Thank you for posting it.

---

### Post by RSBaarda on 2009-11-19
New to Ubuntu so thanks for the info in this post. It took a bit more work to get the higher res in 9.10 but is now working fine. I was ready to toss this laptop but now it gives me a good spare. THANKS:D

---

### Post by mihela816 on 2009-12-15
Thanks, you ended my frustration with my Dell Inspiron 4000.

---

### Post by Wins2LinX on 2010-01-30
You made life possible for me with Ubuntu and Dell c600 lappy.

Hats off for your support.

Thanks,
Thanks
& Thanks...

---

### Post by thecourt on 2010-02-24
I am stuck on step 5. I am new to Ubuntu. Please help...

---

### Post by SomeGayDude on 2010-02-28
Are you getting an error message?  My laptop died so and I don't know if 9.10 will even run on the machine.

---

### Post by doubtful wisdom on 2010-04-11
Finally have decent video on C600.  Thank you!  Since I am using Xubuntu it was necessary to use mousepad, since gedit is not installed by default.

---

### Post by davidzeb on 2010-05-14
> **SomeGayDude said:**
> Are you getting an error message? My laptop died so and I don't know if 9.10 will even run on the machine.
 
 
9.10 does work on the c500/600.  If you are having the split screen issue, hit fn F7 (the Font Key)

---

### Post by jbiwer on 2010-06-19
Excellent!   Thanks!:popcorn:

---

### Post by ilcarlos on 2010-07-27
Thanks for your help. Work for my 10.04 C600:KS

---

### Post by orange_roughy on 2010-08-16
How to do this in 10.04? There is no xorg.conf file since 9.10 at least. please help...

---

### Post by dembru on 2010-09-04
simply copy the file in the directory and rename it as xorg.conf
it worked for me with 10.04

---

### Post by strykerboy314 on 2010-10-13
this still isnt working for my laptop the c600 its still doing the same thing

---

### Post by RWDPLZ on 2011-02-20
THANK YOU! Worked perfectly on my A22p with 10.04

---

### Post by kcaravelli on 2011-04-06
Thank you.  Worked great on my C600 after second try.  Don't know why first one didn't work.  Great job!

---

### Post by BeADroid on 2011-12-10
dude Thanks so much, this fixed my isntall of 11.10. You ROCK

---

### Post by CoryV on 2011-12-27
SGDude, my hero - thanks for your research! :KS

The 16-bit color depth version worked for me on a C600 @ Linux Mint 11/LXDE w/ ATi Rage Mobility M3 AGP 2x rev 02.
However, I had to replace 
  ```
Driver  "ati"
```with
  ```
Driver  "vesa"
```to stop the slight horizontal flicker.

To test before reboot [read this post]("http://ubuntuforums.org/showpost.php?p=679706&postcount=23")!

Details/note to self: read well and do try the "too simple to be true" and even the not so obvious.
In my case, both "ati" and "r128" -which seem more modern and fitting- still resulted in a faint flicker, and several hours of trying vertical refresh rates and ModeLines got me nowhere.

---

### Post by talp on 2012-01-02
thanks for your help

---

### Post by CHPbuntu on 2012-01-15
Worked great on my Inspiron 5000e with Xubuntu 10.04! Great instructions, thanks for your work. To echo what others have said, you rock. :guitar: I am excited to use Xubuntu!

---

### Post by SonycTemple on 2012-01-28
Thank's [SomeGayDude]("http://ubuntuforums.org/member.php?u=30663") for xorg.conf!!

---

### Post by kipjones on 2012-02-12
Thank you!

---

