---
title: "Dell Studio XPS 16 with intel core i7"
date: 2009-12-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by karthikophobia on 2009-12-30
I'll be getting my Dell Studio XPS 16 with intel core i7-720QM, 4GB DDR3 SDRAM and 1GB ATI RADEON 4670 in a week.

I've heard that there were some issues with Karmic and i7 turbo boost. Is it true? 
If yes, then is there any workaround?
Are there any other known issues?

Thanks

---

### Post by dyous87 on 2009-12-30
I am looking to get this as my next laptop too. I will be looking forward to seeing how it goes for you and if all the hardware including the i7 turbo boost works well.

Has anyone else had any experiences getting anything to work on this laptop?

---

### Post by karthikophobia on 2009-12-31
Will let you know as soon as get my hands on my XPS.

---

### Post by dyous87 on 2010-01-12
Just ordered mine today! I will have to wait till February 2 for it to ship out :(

---

### Post by CottonCandy on 2010-01-12
Hi karthikophobia & dyous87. :) I am hoping to be able to get a new laptop soon & while searching around last night I learned about the intel core i7. It sounds pretty awesome. I don't know yet what kind of laptop I want, but I'm pretty sure I'd like it to have i7 so I look forward to hearing how everything goes for you both & of course wish you both good luck. :D

---

### Post by fahadysf on 2010-01-21
I own a Dell XPS 1645 (Core i7 720QM) and can safely say after all my testing that Turbo Boost does not work as yet on Karmic Koala and older distributions. Here is the launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036")

This thing has been resolved upstream (kernel.org). The bug was listed here:

[http://bugzilla.kernel.org/show_bug.cgi?id=15064]("http://bugzilla.kernel.org/show_bug.cgi?id=15064")

Lets hope it makes its way into Ubuntu soon (as an update for Karmic preferrably, or at least in Lucid Lynx 10.04)

All that said... its still as fast as a Core 2 Duo 2.0 GHz (even at its non Turbo max of 1.6GHz). With Turbo it will definitely beat the crap out of the C2D 2GHz.

---

### Post by dyous87 on 2010-01-21
That's a shame to hear, I am eagerly awaiting my XPS 16 and I was hoping everything would work out of the box. Hopefully this fix makes its way into Ubuntu very soon.

How does everything else work if you don't mind me asking? Are there any issues with the GPU, hibernation, wireless, sound etc?

Thanks a lot,
David

---

### Post by karthikophobia on 2010-01-22
I got my xps 1645 few days back. The sound, doesn't work out of the box, I found this post
[http://www.garrettwp.net/wordpress/2009/11/11/ubuntu-9-10-and-dell-xps-16-i7-install/](http://www.garrettwp.net/wordpress/2009/11/11/ubuntu-9-10-and-dell-xps-16-i7-install/)

camera started working after updating but couldn't get bluetooth to work yet. Plz help

---

### Post by CottonCandy on 2010-01-26
> **fahadysf said:**
> I own a Dell XPS 1645 (Core i7 720QM) and can safely say after all my testing that Turbo Boost does not work as yet on Karmic Koala and older distributions. Here is the launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036)

This thing has been resolved upstream (kernel.org). The bug was listed here:

[http://bugzilla.kernel.org/show_bug.cgi?id=15064](http://bugzilla.kernel.org/show_bug.cgi?id=15064)

Lets hope it makes its way into Ubuntu soon (as an update for Karmic preferrably, or at least in Lucid Lynx 10.04)

All that said... its still as fast as a Core 2 Duo 2.0 GHz (even at its non Turbo max of 1.6GHz). With Turbo it will definitely beat the crap out of the C2D 2GHz.
What about hyper threading? Isn't that supposed to help make the i7 able to run faster or at least run more things at the same time compared to a duo? or does that not work also?

---

### Post by v.anand on 2010-01-28
I too own this laptop. Tried installing 9.10, didn't detect wlan card and also my internet connection. Will any fix for this model in particular be made anytime soon?

---

### Post by karthikophobia on 2010-01-28
Did you check preferences > Hardware drivers. If yours is Broadcom STA, this should solve the problem.
I you have already tried it, then, forgive me for mentioning it.


Also is your bluetooth working?

---

### Post by dyous87 on 2010-01-28
Just received my laptop today and I cannot get wireless working! I know I have and Intel WiFi Link 5300 in here. :(

---

### Post by dyous87 on 2010-01-28
I feel dumb. Wireless is working fine. I found out that the button that disables bluetooth is the same button that disables wireless. 

Now I will try to get sounds working.

---

### Post by dyous87 on 2010-01-28
I can conform that sound is now working using the method posted by karthokophobia:

 [http://www.garrettwp.net/wordpress/2...16-i7-install/]("http://www.garrettwp.net/wordpress/2009/11/11/ubuntu-9-10-and-dell-xps-16-i7-install/")

Also the webcam seems to work out of the box.

I was able to get the ATI FGLRX drivers working in System>Administration>Hardware Drivers.

System Monitor also detects all 4 cores (8 threads) of the Core i7 processor. So far I am very happy :)

---

### Post by v.anand on 2010-01-29
I installed ubuntu on windows using Wubi. This time, wlan card got detected in hardware diagnostics, however installed updates, system restarted after which it doesn't go beyond the initial logo. Doesn't even show log in screen. What should I do now?

---

### Post by CottonCandy on 2010-01-30
Glad to hear you got everything working dyous87. :)  

I believe I read somewhere that the xps 16 can get really hot, especially near where your wrists would be when typing or using the trackpad. So you may want to watch out for that issue.

---

### Post by karthikophobia on 2010-02-01
I think Dell has resolved the issue. It hardly gets hot. 


Sry to be so persistent but can anyone help me in making bluetooth work.

Thnq

---

### Post by CottonCandy on 2010-02-01
I don't know if this will help but I did a bit of searching & found [this thread]("http://forum.notebookreview.com/showthread.php?t=452031") which suggests [this]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R251268&SystemID=StudioXPS1645&servicetag=GMF3KL1&os=WV64&osl=en&deviceid=21455&devlib=0&typecnt=0&vercnt=3&catid=-1&impid=-1&formatcnt=1&libid=20&typeid=-1&dateid=-1&formatid=-1&fileid=367315") or other drivers may fix bluetooth.

---

### Post by friv_livs on 2010-02-04
Have any of you timed how long it takes to tarball by gzip a known amount of gb's?

If so, what approximate time and how many gb's?

Thanks in advance,

friv_livs

---

### Post by v.anand on 2010-02-09
Grub 19 doesn't load, however 14 still does. Sound doesn't work though. Tried the method mentioned by Garrett Power, at the terminal I get a message stating permission denied. Please help me to solve this issue.

---

### Post by karthikophobia on 2010-02-10
U need to open the file as root user

---

### Post by karthikophobia on 2010-02-13
> **CottonCandy said:**
> I don't know if this will help but I did a bit of searching & found [this thread]("http://forum.notebookreview.com/showthread.php?t=452031") which suggests [this]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R251268&SystemID=StudioXPS1645&servicetag=GMF3KL1&os=WV64&osl=en&deviceid=21455&devlib=0&typecnt=0&vercnt=3&catid=-1&impid=-1&formatcnt=1&libid=20&typeid=-1&dateid=-1&formatid=-1&fileid=367315") or other drivers may fix bluetooth.

Isn't the thread about windows?

---

### Post by bhargav@in.com on 2010-02-18
I installed Ubuntu 9.10 on my Dell XPS 9.10 with core i7 . As expected the sound problem was there , which i corrected using the help in this thread . Another problem i still face is that my Wireless Lan is not working .

It is pretty weird because  i shutdown windows ( Windows 7 Professional ) with my WiFi on , then upon restart I can use wifi in ubuntu . But (in ubuntu) when i switch off wifi manually and try to switch it on again , wifi doesnt work and the LED also doesnt glow .

---

### Post by sagen on 2010-02-24
I'm considering this laptop, how's the graphics working out? The only thing holding me back is ATI's history, but there's always hope for improvement.

Bugfree 3D with fglrx? Does HD video rendering work?

Thanks

---

### Post by dyous87 on 2010-02-24
> **sagen said:**
> I'm considering this laptop, how's the graphics working out? The only thing holding me back is ATI's history, but there's always hope for improvement.

Bugfree 3D with fglrx? Does HD video rendering work?

Thanks

I was afraid of the same thing but the ATI drivers work out of the box with this model with any issue. I have compiz working on full settings and when running "glxgears" here is some of my output:

```
2506 frames in 5.0 seconds
2606 frames in 5.0 seconds
2416 frames in 5.0 seconds
2532 frames in 5.0 seconds
2464 frames in 5.0 seconds
2412 frames in 5.0 seconds
2617 frames in 5.0 seconds
2460 frames in 5.0 seconds
2453 frames in 5.0 seconds
2527 frames in 5.0 seconds

```

It is a great machine and I couldn't be happier. It is definitely the best laptop I have ever had. I would definitely recommend that you go for it.

---

### Post by karthikophobia on 2010-02-25
It is the best laptop in its price range and no issues with graphics.

---

### Post by wankel786 on 2010-02-25
Slightly off topic but I could really use some input. I have the xps 1640, and my touchpad is really unusable. If I have two fingers down on the pad, the cursor goes beserk. Does anyone have this issue and have they been able to fix it at all? Anyone mind sharing their touchpad settings? Thanks!

---

### Post by keep you kimi on 2010-02-27
sorry to say but HD movies are awfully choppy, no matter what player i'm using (totem, vlc, mplayer). 
they were playing ok for a day, then smething happened...
can you tell me, should i set my cpu to performance to watch 1080p movies? i have it in ondemand and there is no way to watch anything...

help.

---

### Post by grummbaleena on 2010-03-01
Yesterday I stumbled upon this thread while trying to get my sound to work and followed the instructions at [http://www.garrettwp.net/wordpress/2009/11/11/ubuntu-9-10-and-dell-xps-16-i7-install/](http://www.garrettwp.net/wordpress/2009/11/11/ubuntu-9-10-and-dell-xps-16-i7-install/)

After this sound was working fine. Then today I booted into Ubuntu and now the only sound I can hear is the alert once the login screen loads. Has anyone had any problems similar to this? Any troubleshooting help would be greatly appreciated. Thanks.

---

### Post by grummbaleena on 2010-03-14
Okay so I seemed to have sound working now. I later realised that after I initially had sound working I had booted into windows and updated the BIOS. This seems to have killed sound completely within Ubuntu.

The other day I decided to open up the Sound Preferences and noticed that under the Output tab the R700 Audio Device [Radeon 4000 Series] Device was selected. I'm guessing this is for the HDMI output. After changing that selection to the first option, Internal Audio Analog Stereo, sound has been working fine. I've attached a screenshot of my current sound settings in case it helps anyone.

---

### Post by imopen on 2010-03-21
Sorry for the maybe retoric question... but at the end I didn't understand... The i7 720qm works fine with the latest kernels? I mean, does turbo boost work as expected? The  processors over clock when they need more power? 

I'm looking for the same laptop... And I would like to buy with no surprises :)

Thanks in advance ;)

---

### Post by keep you kimi on 2010-03-23
i dont think so. mine works at 1.6ghz max.
its is fast enough for me at 931 mhz though, so i'm patient. the kernel supplied with 10.04 will not solve it i read somewhere here..

---

### Post by biko.bukows on 2010-04-08
Sorry if it's not the right place to ask, but I considering buying XPS with i7.
In the past i had problems with Hibernate and wake-up the system.
Does this problem is a issue in this computer with Ubuntu karmic?

Thanks

---

### Post by cocamoxb on 2010-04-11
My general Dell Studio XPS (1645) report so far with ~1 week working for IT business. This means no graphics, sound, or high-end multimedia editing. OpenOffice, Firefox, Pidgin, and terminal (lots and lots of multi-window).

General System Hardware:
Dell Studio XPS 16
Intel I7-720QM, 1.6, 6MB
 4GB, 1333MHZ, DDR3, 2X2G
                                            ATI Mobility RADEON HD 4670-1GB
Wireless Intell 5300
HDD 500GB 7.2k RPM
130W PSU

System Software:
Ubuntu 9.10 Karmic x86_64 64-bit (fresh install to wipe Windows7)
ext3 file system
dual partition with "/home" encrypted on its own and "/" as its own
ATI 10.3 Proprietary Drivers (ati-driver-installer-10-3-x86.x86_64.run)
Compiz, Skydome, etc (normal eye candy)


Things that I've noticed:

Wireless:
Nothing worked "out of the box". I had to hit the soft-button on the top of the keyboard to brightly "illuminate" the button. Second, I have to open a terminal and type "iwconfig wlan0 up" Then I have to right-click the network-manager tray icon and "enable wireless". Then the SSIDs show up and my pre-configured associations will connect. 
***If any one has an idea on how to get network-manager to work with the soft-button without having to go into the terminal, please let me know.

Outside wireless, I built the entire laptop from the .iso on a CD on a 3-hour flight with no internet access. After the flight, there were no video issues with the ATI driver\card. Compiz works well. Urban Terror works well. Yes, its old but fun.

Over all I'm fairly pleased with the performance. I have not had any heat or fan issues beyond the normal expected operation.

04/22/2010 UPDATE:: Network Manager seems to have really had issues with wireless and wired for the first couple days. Seems like since I connected to a SSID and a wired network once each everything works now. I've been running ATI 10.3 drivers and they run very well. I haven't been able to get the i7 to work with turbo but that is a kernal thing that seems to be resolved in 10.x coming out at the end of April.

Over all, things seem to be working pretty well.

---

### Post by nypdz on 2010-05-04
i have certain issues still to be solved
-the sound quality as compared to windows seems to crack at volumes.
-the audio jacks do not work at all. ( external speakers, headphones )

please help.

---

### Post by yomyom on 2010-05-04
> **nypdz said:**
> i have certain issues still to be solved
-the sound quality as compared to windows seems to crack at volumes.
-the audio jacks do not work at all. ( external speakers, headphones )

please help.

Hi nypdz,

Here is how I managed to get my audio jack working (see related bug report at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/553002](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/553002))

1. Go to System/Preferences/Sound/Output and check that "Analog speaker" is selected as connector
2. Create a file "dellstudio.conf" in /etc/modprobe.d/
3. Add the following line: options snd-hda-intel model=dell-m6
4. Save and close
5. Reboot

I hope this helps

---

### Post by karthikophobia on 2010-05-04
This should sortout the porblem with your headphone/external speaker issue
[http://ubuntuforums.org/showthread.php?t=1471260](http://ubuntuforums.org/showthread.php?t=1471260)

---

### Post by nderic77 on 2010-05-04
> **yomyom said:**
> Hi nypdz,

Here is how I managed to get my audio jack working (see related bug report at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/553002](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/553002))

1. Go to System/Preferences/Sound/Output and check that "Analog speaker" is selected as connector
2. Create a file "dellstudio.conf" in /etc/modprobe.d/
3. Add the following line: options snd-hda-intel model=dell-m6
4. Save and close
5. Reboot

I hope this helps

TOUCHDOWN!!!

This worked like a champ on Lucid 64bit for my Dell Studio 15. (which, by the way, with 8 gigs of RAM and core i7 was a steal at $1199 incl shipping + tax from costco.com)

My laptop now does everything I have wanted it to do. my XP VM works completely on Virtualbox; I am a very happy camper!

---

### Post by Shakz on 2010-05-06
> **dyous87 said:**
> Just ordered mine today! I will have to wait till February 2 for it to ship out :(
Nah they always ship earlier man...did with my wifes and did with mine.


EDIT: man this is an old post :-/

---

### Post by nderic77 on 2010-05-07
> **Shakz said:**
> Nah they always ship earlier man...did with my wifes and did with mine.


EDIT: man this is an old post :-/

FWIW, you are correct... mine arrived in <2 weeks, even though Costco had predicted that it would not even *ship* for 20-25 business days.

---

### Post by capo1949 on 2010-05-23
hi all
can you please comment on a review I read that says screen very difficult to read outdoors in bright sunshine and no so clever in well lit office
Graham
[http://www.notebookreview.com/default.asp?newsID=4764](http://www.notebookreview.com/default.asp?newsID=4764)

---

### Post by simpleroute on 2010-06-24
I've had a couple minor issues with my i7 XPS 16 (1645) that I haven't seen anyone comment on and was curious if I stand alone:

[LIST]
[*]Sometimes external USB mice will stop registering clicks (mouse will move but clicking on the mouse does nothing - tried several mice).  I have to click the touchpad and it will start working again.
[*]My fan seems to run quite a bit even when downclocked and doing light work.  Anyone else having fan issues?
[/LIST]

As for other issues I encountered that others have posted about - the sound fixes previously mentioned and multitouch scroll fixes both worked for me (modified alsa-base.conf and created a script for login respectively).

---

### Post by artemisgallow on 2010-06-25
> **simpleroute said:**
> I've had a couple minor issues with my i7 XPS 16 (1645) that I haven't seen anyone comment on and was curious if I stand alone:

[LIST]
[*]Sometimes external USB mice will stop registering clicks (mouse will move but clicking on the mouse does nothing - tried several mice).  I have to click the touchpad and it will start working again.
[*]My fan seems to run quite a bit even when downclocked and doing light work.  Anyone else having fan issues?
[/LIST]


I'm running 10.04 on the 1645 as well. I only briefly had an external mouse on, but it worked fine for the ~5 minutes I had it on.

I do have the problem you'vve got with the fan. It seems to run every couple minutes, when I've only got a browser up. Watching the temp ( which I'm not even sure if it's setup correctly) I get a steady creep from ~50 to 60+ then the fan kicks in, it goes back down to 50, and then repeats the process.

Has anyone had any major heating problems with their studio xps? Mine gets a bit warm at idle, and rather hot if I'm playing a game. I still can't understand why Dell thought that back vent design was a good idea. I still have about a week to send it back if it's getting too hot, I just really love the machine other than that. *frets*

---

### Post by simpleroute on 2010-06-27
> **artemisgallow said:**
> Has anyone had any major heating problems with their studio xps?

Mine gets pretty warm as well.  I'll get high fan usage when doing very low intensity stuff as I said, but I also get a good amount of heat when the fan is on high.  I had read the 1645s had heat issues compared with later models (didn't really read any real resolution).  Kind of wish I had kept the Windows install around longer to see if it's a problem with Ubuntu or if it had the heat issues out of the box.

Definitely love the laptop though.  Swapped out the hd for a solid state and the thing is amazingly fast.

---

### Post by capo1949 on 2010-06-27
Hi

I have found that my 1558 works fine outdoors. Yes I also suffer with the area around the  touch pad becoming very warm and the fan switching in and out although the noise is not at all intrusive, as I am quite deaf, lol.

What solid state HD did you fit and how difficult was it?

---

### Post by simpleroute on 2010-06-27
> **capo1949 said:**
> What solid state HD did you fit and how difficult was it?


The 1645 (along with most recent laptops) uses a 2.5" sata drive.  As long as the drive you replace your original one is the same size (2.5") and the same interface/connector (sata) then it doesn't make a difference if it's solid state or a normal drive.

I ended up using an OCZ Vertex 60 GB drive in mine (I just use it for web dev, light coding or surfing so I don't need much space).  The OCZ Vertex stuff (Vertex 2 is out now) has been pretty close to Intel on SSD speeds while being a lot cheaper.  

The process to replace the drive is pretty similar on most models (need to locate the old drive, remove it, swap the mount and any adapter off the old drive onto the new drive then put it back in).  The [manual for the 1640]("http://support.euro.dell.com/support/edocs/systems/sxl16/en/sm/hdd.htm#wp1109848") gives an idea how to do it.

Total time to swap the drive out was about 5 minutes (pretty easy if you have the right drive).  I had to install an OS after of course...

---

### Post by samcoinc on 2010-07-14
32 bit lucid

I have a 1645 studio xps.  Everything seems to run pretty good.  Issues I have seen.

- The wireless soft button will turn the wireless off - but not back on.  (must be a trick)

- I am dual booting lucid and windows 7.  windows 7 boots 100% of the time when picked from grub.  Lucid boots 50% of the time.  Right after picking ubuntu from grub (or letting it time out) the blue tooth light will go off and on - then the hard drive will flash - then nothing but a blinking cursor.

- the offical ati packages for the video card work great for a coulple of weeks - then blank screen boot right before the login screen should display.  Hard lock (cannot get to terminal or nothing) will boot into safe mode or whatever - Uninstall the ati drivers and use the open source ones - starts working again.  This has happened twice with 2 different versions of the ati driver.

sam

---

### Post by deman88 on 2010-08-08
Dell Studio XPS 16, no sound in 10.04, adding to alsa-base.conf like in 9.10 doesn't work, any ideas?

---

### Post by samcoinc on 2010-08-13
here is a new one.  (still the dell 1640 studio xps)  I wiped it and installed lucid 64bit.  Now - the wireless card will come up or the blue tooth - not both at the same time.  I cannot see a pattern.  Sometime the wireless sometimes the bluetooth.  (fresh install - updated)

sam

---

### Post by Romu on 2010-08-14
Hi everyone.

When I bought the XPS Studio, before installing 10.04 as exclusive OS, I forgot to backup the screen ICC profile.

So, I would greatly appreciate if someone can send me the ICC profile. My XPS is a 1645 with a "Full HD WLED 1080p Truelife 15.6" screen.

Thanks.

---

### Post by etheralabyss on 2010-08-29
Hi guys, first post and fellow XPS 1645 user here.
I had some problems with my XPS, namely the audio jack and wireless, and I (think) have a solution.

I've installed GNOME Alsamixer for adjusting volume; the audio jacks worked after that.

For wireless, I'm using Wicd; now the wifi LED works (Blinks when connecting).

Now, the only problem I have is ATI's driver. Can someone help me? fglrxinfo shows "Segmentation fault".

---

### Post by TheWhiteDemon on 2010-08-29
I have an XPS 16 with Core i7 and a 128GB Samsung SSD. I refused to stick with Lucid for 2 reasons:

1.   HORRIBLE HEAT ISSUES. I mean seriously running VERY HOT.
2.   Lack of any TRIM support in the normal Lucid kernel without a lot of extra work.

I had the other issues listed in this thread as well but was able to reconcile them fairly easily.  Unfortunately, Maverick was even worse when it came to heat issues (But that's to be expected as an alpha. I just hope things get much better over the next couple of months).

Ubuntu is still one of my favorite distros, but I would have to recommend to anyone thinking of buying an XPS to not go with Ubuntu.  Unfortunately, Fedora, OpenSuse, PCLinuxOS, and many others have the same Heat issues.

Try it out for yourself of course, but in my experience I have only found two Linux distros that I can run on my XPS without the heat issues - Sabayon, and Mandriva.  Mandriva is the only distro I can recommend for the XPS since everything works out of the box including TRIM.

---

### Post by lasombra on 2010-11-25
I got my Dell Studio XPS 16 last week and I'v installed Maverick. But I have several problems:
[LIST]
[*]I cannot enable desktop effects (nor with nouveau nor with proprietary driver)
[*]Bluetooth module is recognized and the bluetooth icon is shown. Clicking on the icon, changing the status of the adapter (enable/disable) does at least change the text, but not sure if the status really changes. Cause, always when I open the properties, there is a big button stating "Bluetooth is off". Clicking this button does not do anything. So how can I use bluetooth
[/LIST]

Then I have another question: Do you have any tipps to improve battery life for the XPS?

---

### Post by karthikophobia on 2010-11-25
> **TheWhiteDemon said:**
> I have an XPS 16 with Core i7 and a 128GB Samsung SSD. I refused to stick with Lucid for 2 reasons:

1.   HORRIBLE HEAT ISSUES. I mean seriously running VERY HOT.
2.   Lack of any TRIM support in the normal Lucid kernel without a lot of extra work.

Maverick is much better. It runs much cooler. Don't know abt TRIM support though.

---

### Post by gibbylinks on 2010-11-25
If you are running 2.6.33 kernel or above you will have trim support, you just need to add the "discard" option to your fstab to enable it.

Also if your read the threads you will find that if you format you drive with Maverick it should format correctly (align it)

I suggest you search the forums, there are lots of threads about running an SSD.

[http://ubuntuforums.org/showthread.php?t=1463870&highlight=ssd+lucid](http://ubuntuforums.org/showthread.php?t=1463870&highlight=ssd+lucid) this thread refers to Lucid but there are some good tips. :p

---

### Post by wankel786 on 2011-02-03
> **lasombra said:**
> 
[*]Bluetooth module is recognized and the bluetooth icon is shown. Clicking on the icon, changing the status of the adapter (enable/disable) does at least change the text, but not sure if the status really changes. Cause, always when I open the properties, there is a big button stating "Bluetooth is off". Clicking this button does not do anything. So how can I use bluetooth



Also have this same issue, anyone found a solution?

---

### Post by Lorthirk on 2011-05-06
Hello. On Ubuntu 11.04, I set options snd-hda-intel model=dell-m6 on /etc/modprobe.d/alsa-base.conf but then it seems that the microphone stopped working. Any suggestion?

---

### Post by Novacaptain on 2011-05-06
go to System settings (click on the "off" icon in upper right corner and select it from the pull-down menu) 

sound,

on the "input" tab,

select analog microphone and make sure it is not muted.

That's what I had to do to get sound working in skype.

---

### Post by Lorthirk on 2011-05-06
Unfortunately I already double checked everything :\

I assume that the microphone is working with dell-m6 on alsa-base.conf?

---

### Post by Novacaptain on 2011-05-06
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Maybe its time to get to the bottom of things. I for one have no idea what that command does.

---

### Post by Lorthirk on 2011-10-14
Sorry to bring up the thread again, but with Oneiric it seems that there are issues once again. Even taking these steps microphone won't work for me. Can anyone confirm?

---

### Post by pheonixcoder on 2011-10-17
Hey, i have a dell XPS 1647. I faced the same issue with headphones jack with 11.10. For me setting options snd-hda-intel model=dell-eq worked. Please keep in mind that after restart of alsa, i had to close already opened file to get the sound on headphones.

---

### Post by Lorthirk on 2011-10-17
options snd-hda-intel model=dell-m6-dmic worked for XPS 1645. Thanks.

---

### Post by pheonixcoder on 2011-10-18
Thats a great news !
I would suggest you to add this in the list on this forum [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by Lorthirk on 2011-10-18
> **pheonixcoder said:**
> Thats a great news !
I would suggest you to add this in the list on this forum [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Did it ;)

---

