---
title: "HOWTO:  Ubuntu Gutsy 7.10 on Dell XPS M1330"
date: 2007-11-24
forum: Dell  Ubuntu Support
---

### Post by SnowflakeRV7 on 2007-11-24
Here's my success story after installing Ubuntu on my Dell XPS M1330 laptop.

I - The basic configuration:

XPS M1330
Processor - Core2Duo 2.2GHz
Memory - 2GB 667MHz
Hard Drive - 160GB 5400rpm
Graphics - nVidia 8400GS, 128M RAM
Screen - Slim 1280x800 LED Backlight
Wireless - Intel Wireless A/G
Extras: Fingerprint Reader, Dell Infrared Media Remote

The laptop by default has four primary partitions, in this order (sizes approximate, I forget the exact numbers):
1 - tiny partition - 100 MB?
2 - Dell Recovery Partition - 10 GB, 5 GB of which is in use.
3 - Main Vista Partition - 135 GB, 24 GB of which is in use.
4 - Another smaller partition, 2 GB or so.  Apparently it's a "Media Live" partition or something.

Within the fourth primary partition is a single extended partition, that fills the entire primary partition.

II - Setting up the computer:

During a startup, hit F2 and go into the BIOS setup.  By default the boot order is HD, USB, Network, CD or some such.  You want to move the CD to the top of the list, at least.  I put things in the following order:  CD, USB, HD, Network.

A note that i'll place here as it's a "general" comment":  When booting from the Ubuntu CD, I pushed the F4 key and selected the screen resolution 1280x800x32 each time.  I don't know if the Ubuntu CD would boot with the correct resolution or not, I didn't give it the chance to try (or to screw up :).

III - Resizing the partitions:

I read through all the notes here online about using Vista's own partition resizing tools to resize, but Vista would only offer to reduce the 3rd partition to 86 GB, so I didn't want to do that.  A few people used gparted to repartition without problems, so I elected to go that route.  I disabled the pagefiles, and let Vista do a defragmentation on the drives.  It took about 6 hours to defrag.

I booted into Ubuntu from the stock 7.10 CD (not the alternate).  I fired up gparted, and made the following changes:

1. Partition 1 was tiny, so I left it alone.
2. Reduce partition 2 from 10 GB to 6 GB.
3. Reduce partition 3 from 135 GB to 35 GB, and move it up next to partition 2.
4. Increase partition 4 from 2 GB to whatever was left (104 GB, I think), to fill the whole drive.
5. Moved the 2 GB extended partition to the start of partition 4.

I did it this way because it keeps all of the partitions in the *same order* that they were when the computer was built by Dell... Anything I do with Ubuntu now will show up on the computer *after* the other partitions, hopefully not screwing up or confusing the Vista install.

I told it to Apply the changes, and went to have a coffee.  It worked on each step in turn, resizing and moving stuff around.  Note:  When it went to resize the 135GB partition, it seemed to die.  You could still move windows around and move the mouse, but the gparted status window stopped updating for a few minutes.  I'm not sure what part of the process was taking the time, but it needed to finish that before it would continue.  I let it work, and in about 2.5 hours I had all of my partitions shuffled.

IV - Cleaning up the Vista Partitions

Next, I rebooted the computer, and dropped in the Dell Recovery DVD.  I didn't bother trying to boot into Vista first, based on reports of others online it seems the chances of a clean startup   were nil anyway.  I assumed it wouldn't work and that I would need to do a repair.  The Recovery CD started up, and I just followed the prompts until I was offered the option to Repair my installation... It's in the lower left corner of the window.  I chose that option.

Vista immediately detected that a repair was necessary, and when I said "ok" to the fix, it was finished almost as quickly as I hit the key.  Next, reboot.  Vista automatically detected that the drives had been played with, and performed a chkdsk on them.

V - Installing Ubuntu

On the next reboot, I popped in the main Ubuntu disk.  I booted into Ubuntu Live first, then clicked the "install" link on the desktop.

I proceeded through the install prompts, and when it got to the partitioning section, I chose "Guided, use largest available space".

Ubuntu installed hands-off, and automatically set up GRUB with the Vista partition, and the MediaLive partition, alongside the Ubuntu parts.

VI - Enjoying Ubuntu

After rebooting, I let Ubuntu download updates (about an hour and half over DSL).  Then I activated the restricted drivers for the nVidia card, rebooted to get the new nVidia xserver running, and then activated all of the fancy compiz features.

Basically, from here on out, the laptop is running just fine.  I added the DVD/MP3/FLASH/WMV stuff using the ubuntu repository, all seems to work fine.  Vista boots fine, and i've had no problems with the reduced drive size.  There's about 10G free in Vista, and I don't plan on installing anything else there now so that should do me just fine for the times I need it (I use MS at work, so i've got to have MS available at home from time to time).

VII - Final cleanup under Vista

I went back and turned on the pagefiles again, using the Vista default values (about 2G).

That's about it!  I hope this helps others who might want to install Ubuntu on this Dell model.

-Rob

---

### Post by SnowflakeRV7 on 2007-12-02
Update:  Since installation, i've been having a blast.  I haven't found anything that doesn't work yet, although it appears that I can't boot into the Media Direct partition using Grub, which means i'm pretty much locked our of media direct.  Makes me wish I had turfed that partition when installing, rather than going to the trouble to try and save it.  Oh well.

The SD card reader works flawlessly, both a Sandisk Ultra 2G and a Patriot Class 6 8G card were recognized, mounted, copied files to and from, and unmounted without problems.

World of Padman is an awesome game, btw.  Just had to throw that in... I found it in the latest issue of Linux Journal, and had to try it since I used to play Q3Arena and loved the Padman levels.  The only problem is that after about 10 minutes of play, it switches from fullscreen mode back to windowed mode, and essentially locks up.  I can hear the game playing in the background, and see some graphics in the window, but I can't control the game anymore or exit to restart.  The only way out is to ctrl-alt-backspace and re-log in to X.  Maybe a graphics problem, or maybe something is updating on the desktop and I dont' realize it.

Haven't tried suspend/hibernate yet, i'll try those sometime and post an update as well.

---

### Post by beamur on 2007-12-02
I also have an XPS M1330 with Vista and Ubuntu.  However, I am having issues with the wireless card (Broadcom BCM4328) and the WLAN (SPRINT).  Were you able to get those working?

---

### Post by SnowflakeRV7 on 2007-12-07
I purchased mine with the Intel Wireless card, and have had no problems with connectivity.  I didn't really need 802.11n capability, so I elected to forego it in favour of getting a known good wireless setup.  Basically, my configuration has the same hardware that the Ubuntu-preloaded 1420n has in the US.

I haven't tried the WLAN capability.  I didn't know until I bought the laptop that it had a SIM card (or whatever that is) slot... I only saw it when I swapped the battery the first time.  It wasn't capability that I needed, so it wasn't a factor in the buying decision.

Oh, and to update an earlier question, suspend/resume works perfectly.  Wireless too, it picks right up after opening the screen again.  Haven't tried hibernate yet, i'm still a little leery of something that needs to futz with my hard drive.

---

### Post by ninocass on 2007-12-13
have youhad anyissues with the soundin that when the volume isset to 50% or below there is no soundand youcan onlyhear stuff between 50% and 100%?

Thanks

Nino

---

### Post by SnowflakeRV7 on 2007-12-19
Hi Nino,

I haven't had any problems with the audio at all.  Note that I have the basic built-in audio, not the upgraded audio.  That might make a difference.

On mine, sound works from volume 0 to volume 100, out of the box.  The remote works to control volume and playback as well.

---

### Post by darktreb on 2007-12-20
Hi, I've been thinking of getting myself an XPS M1330 as well. The only thing I wanted to confirm was that the Ubuntu hard drive (way too many load cycles) issue could indeed be dealt with on the M1330. I sadly didn't discover it until it was essentially too late on my current computer. I'm not getting a laptop if I'm not going to run Ubuntu on it, but I'm not going to run Ubuntu on a laptop if it's going to mess up the hard drive. I don't see any reason why the hdparm stuff wouldn't work for the M1330, but just in case, I figured I'd ask.

Thanks in advance, and thanks for the handy guide which I will hopefully soon be using.

---

### Post by SnowflakeRV7 on 2007-12-20
Darktreb, can you include a link to some details?  I'm not keen on killing my hard drive either, but have heard nothing about any hard drive problems under Ubuntu... What are the symptoms, failure modes, etc?

---

### Post by darktreb on 2007-12-21
The Launchpad coverage is probably the best, though if you Google something overdramatic like "Ubuntu kills hard drive" you'll probably find some other good results.

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
[https://bugs.launchpad.net/ubuntu/+bug/104535](https://bugs.launchpad.net/ubuntu/+bug/104535)

Please let me know if you would like more information.

---

### Post by rhonaldmoses on 2007-12-30
Hi,

I've installed Ubuntu 7.10 on my DELL XPS M1330 2.2Ghz Laptop and everything works fine except one.

My memory card reader is not reading any memory cards, but the same card reader works without any problem under openSUSE and Windows.

How do I make it work in simple ways.

---

### Post by beschl on 2007-12-30
Hello,

In Austria it's only possible to order the Dell XPS M1330 with a Intel Wireless-N-Minicard. Does anyone know if this card works with Ubuntu??

[Dell Austria - XPS M1330]("http://www1.euro.dell.com/content/products/features.aspx/xpsnb_m1330?c=at&cs=atdhs1&l=de&s=dhs")

~Bernd

---

### Post by dandaman0061 on 2007-12-30
I just got a m1330 and mostly everything is setup the way I would like it to be.  Ubuntu, Vista, and MediaDirect all work thanks to this page: [http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html]("http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html") (if it's you rhonaldmoses thanks!)

Anyway, what I'm having problems with is the wifi/bluetooth on/off switch on the right and the respective lights coming on.  Wireless does work (using it now), and the bluetooth I'm sure will work with some digging, but I was wondering if there was a way to get the indicator lights and hardware to turn on/off based on the switch.  Thanks!

Danny G

---

### Post by SnowflakeRV7 on 2007-12-31
Interesting.  I lost my MediaDirect partition when I did my install... It's there, and shows up in Grub, but won't boot.  But I let Ubuntu install Grub in the MBR, so that's probably why.

I haven't tried to fix this, because I don't think MD is that important... Is it that useful?  I don't mind the extra boot time to get to Ubuntu, where i'm keeping my media anyway.  Would it be worthwhile to move to a separate data partition that Vista/Ubuntu/MD could read, and get MD working instead?  Does MD draw less power during operation, or anything like that?  Might be useful for long flights if that's the case.

---

### Post by SnowflakeRV7 on 2007-12-31
> **rhonaldmoses said:**
> My memory card reader is not reading any memory cards, but the same card reader works without any problem under openSUSE and Windows.
Are you sure it's not working?

I sometimes have to wait a few seconds before the memory card shows up on my desktop... But otherwise, it's worked every time i've tried it (well, except for the time I tried reading an 8G SDHC card that had died... I thought my reader was fried too until I confirmed that it was the card by trying to read it on three computers and using three different card readers).

If it's not reading, you'll have to look into the error messages that are probably being stored in one of the log files.  Check the /var/log directory and try doing a `tail -20 [filename]` to see the last 20 lines of a file.  If you do this right after you insert a card, you should be able to see any error messages as they come up.

-Rob

---

### Post by xxsaskexx on 2007-12-31
> **dandaman0061 said:**
> I just got a m1330 and mostly everything is setup the way I would like it to be.  Ubuntu, Vista, and MediaDirect all work thanks to this page: [http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html]("http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html") (if it's you rhonaldmoses thanks!)

Anyway, what I'm having problems with is the wifi/bluetooth on/off switch on the right and the respective lights coming on.  Wireless does work (using it now), and the bluetooth I'm sure will work with some digging, but I was wondering if there was a way to get the indicator lights and hardware to turn on/off based on the switch.  Thanks!

Danny G

I'm kind of in your same situation.  I was able to get wireless, and the blue light working with it, after doing the wi-fi installation steps at this site:[http://www.micahcarrick.com/11-04-2007/bcm4328-wep-gutsy-ubuntu.html](http://www.micahcarrick.com/11-04-2007/bcm4328-wep-gutsy-ubuntu.html)

My problem is that bluetooth does not work AT ALL for me, light included.  Dunno why.  I've been trying to get my Blackberry Curve phone to communicate with the comp, but it comes up with no device.  It may be just the phone, I don't have other devices to test with it unfortunately.  Everyone else seems to have it working without a hitch.

I've tried installing every bluetooth utility known, and still nothing.  Anyone else having similar problems?

---

### Post by RagingAardvark on 2008-01-03
This may sound daft, but do you actually have bluetooth hardware installed? Despite the Dell website seeming to indicate that it's standard, it's actually a separate option. 

Have a look to see if the card is installed.

KJ

---

### Post by SnowflakeRV7 on 2008-01-03
> **xxsaskexx said:**
> I'm kind of in your same situation.  I was able to get wireless, and the blue light working with it, after doing the wi-fi installation steps at this site:[http://www.micahcarrick.com/11-04-2007/bcm4328-wep-gutsy-ubuntu.html](http://www.micahcarrick.com/11-04-2007/bcm4328-wep-gutsy-ubuntu.html)
What wireless card do you have?  Mine worked out of the box, blue light on the keyboard and everything.  I've got the basic Intel a/b/g card, didn't need ndiswrapper.

> My problem is that bluetooth does not work AT ALL for me, light included.  Dunno why.  I've been trying to get my Blackberry Curve phone to communicate with the comp, but it comes up with no device.  It may be just the phone, I don't have other devices to test with it unfortunately.  Everyone else seems to have it working without a hitch.
Seconds on checking whether you've actually got Bluetooth.  It might explain why the light doesn't work if you don't actually have the hardware installed.  I haven't tried my bluetooth yet, but the light is there and it's on.

---

### Post by dandaman0061 on 2008-01-03
I gave up after a while on the Bluetooth last post, but I know I have the hardware (I used it in Vista).

One thing that occurred to me was in vista when I was digging around I purposefully disabled the Bluetooth (through vista not the switch) so I'll check if I re-enable it through Vista if it will work in Ubuntu.  My intel wireless worked right away, without ndiswrapper - but still no light on next to the power button.  And it still appears as if the switch to turn on/off wifi & bluetooth doesn't seem to have any effect.

So... I'll check the software Bluetooth thing tonight and post if I have progress.

---

### Post by dandaman0061 on 2008-01-03
AHH!  Well it looks like the Vista disabling of bluetooth was my problem.  After going back into Vista and reenabling the device, Ubuntu can find it and the light comes on!  So the Vista thing must turn off something in the hardware that Ubuntu can't turn back on... unless I missed something in my previous digging.

What's strange (not a big deal) now is that the hardware switch works to turn on/off the bluetooth and wifi... which it didn't do anything when bluetooth wasn't working (didn't even turn off wifi).  So yeah... still no wifi indicator light, bluetooth light works, bluetooth works, wifi works.

Danny G

---

### Post by xxsaskexx on 2008-01-04
> **SnowflakeRV7 said:**
> What wireless card do you have?  Mine worked out of the box, blue light on the keyboard and everything.  I've got the basic Intel a/b/g card, didn't need ndiswrapper.

Mine came with the Broadcomm 1505-N.  I heard the Intel card is the one that works out of the box.  


> Seconds on checking whether you've actually got Bluetooth.  It might explain why the light doesn't work if you don't actually have the hardware installed.  I haven't tried my bluetooth yet, but the light is there and it's on.

I'm pretty sure I got it installed, It's an option in the BIOS. Didn't install Gutsy/Vista as dual boot, so I can't test whether Vista would enable it.  Think I'll buy  a bluetooth adapter.  They're cheap anyway.  Thanks for the help!

---

### Post by Zeedok on 2008-01-05
Thought I'd add my two cents worth. My m1330 works absolutely perfectly, out of the box.
dual core

Specs:

2.4GHz dual core
4GB RAM
320GB hard drive
Intel mini-N wireless card, bluetooth etc

Everything I've tried works without modifications - the wifi button, card reader, wireless card everything!!

I haven't yet tried the webcam or fingerprint reader,  but so far I'm really impressed!!

---

### Post by amias on 2008-01-08
I'm interested in getting one of these m1330s , do both audio outputs work seperately ?  I would like to use them with mixxx as master and headphone out so ideally i would like them as separate jack or alsa outputs.

anyone tried this ?

Toodle-pip
Amias

---

### Post by spivak.d on 2008-01-13
Yup, both headphone jacks work fine (and are volume independent). Anyone have any luck playing DVDs with the 1330? It's the one feature I can't get to work with this laptop.

---

### Post by cendant on 2008-01-19
> **spivak.d said:**
> Yup, both headphone jacks work fine (and are volume independent). Anyone have any luck playing DVDs with the 1330? It's the one feature I can't get to work with this laptop.

That is probably you do not have codecs and CSS2 installed

```

## MEDIBUNTU REPOSITORY
deb http://packages.medibuntu.org/ gutsy free non-free
deb-src http://packages.medibuntu.org/ gutsy free non-free

wget http://packages.medibuntu.org/medibuntu-key.gpg
sudo apt-key add medibuntu-key.gpg
```

and have fun

```

## Multimedia Codecs
sudo aptitude install ubuntu-restricted-extras
sudo aptitude install w32codecs # 32-bit
sudo aptitude install w64codecs # 64-bit

## DVD playback
sudo aptitude install libdvdcss2
sudo aptitude install libdvdnav4
sudo aptitude install vlc
```

---

### Post by Omnios on 2008-01-19
Hi thiis is well writen
 
 I have a 1530 and love it. I havent installed Ubuntu yet as I am going to do a lot of research first. I have a 160G drive and have some idea's for it but have to figure out how this will work first. I have to find out how much space I need for vista for IE and possibly some games that will not run in wine. Also I am thinking of a n arangement as followed
 
Partitions:
1: Vista = ?
2: My documents partition shared and mounted as /home, also thinking of formating it as ext3 and using the window probra to mount and use it.
3: looking into swaping the 10G recovery to an external. I have a unused 40G drive lying around and thinking of slapping it into a external encloser if this is possible.
4: = Lin / partition. From experience this does not have to that huge. My old tower is using about 30G.
 
 The last part is that with home being in /home parition I will be able to set up wine fakedrives. What I really want to look into is if I can install a windows game in Vista/MyDos and use wine on the same file. This is mostly for games with broken updates such as Anarchy online. (so I will be able to bot into vista and update it as lin-update is broken and then boot into lin and play. 
 
 As for the media direct I was doing some reading in a XPS 1530 threak and somone hacked it to launch a progy, This mighth work for somthing like launching Mythtv.
 
 
 I  am also looking into using my old tower as a file server and a media center for the lappy using mythtv server and a mp3 streamer. Right now I can access mt lin tower and play music so far.

---

### Post by cendant on 2008-01-20
On freshly installed Ubuntu on xps 1330 the fan is always on.

I switched Bluetooth off, and it is still on. I enable CPU scaling and put the processor to 800 MHz and it is still on.

In Windows XP, the fan was never working (only during heavy times), in Windows Vista the fan was barely audible.

In Ubuntu 7.10 the air is constantly flowing out of the machine and I think it is the fan that is located to the left ot the touchpad that never stops

What is going on???

---

### Post by jerrylin on 2008-01-20
> **cendant said:**
> On freshly installed Ubuntu on xps 1330 the fan is always on.

I switched Bluetooth off, and it is still on. I enable CPU scaling and put the processor to 800 MHz and it is still on.

In Windows XP, the fan was never working (only during heavy times), in Windows Vista the fan was barely audible.

In Ubuntu 7.10 the air is constantly flowing out of the machine and I think it is the fan that is located to the left ot the touchpad that never stops

What is going on???

Check this page out. It has some information regarding your issue.

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)

It also has answers to alot of other questions.

---

### Post by cendant on 2008-01-20
any recommendations?

how is your fan behaving?

---

### Post by jerrylin on 2008-01-20
> **cendant said:**
> any recommendations?

how is your fan behaving?

Again, check out the page I linked. They have some solutions and information regarding why your fan may be constantly on.

Look under "pending".

---

### Post by MrShifty on 2008-02-01
Has anyone gotten the VGA and/or HDMI ports to work (on the model with Nvidia graphics card)? I fiddled with the "Screens and Graphics" GUI under System->administration with mixed results; I couldn't get get widescreen output (1920x1200 is what I was shooting for). Also, that GUI did a nice job of torching my xorg.conf beyond repair. Hooray for backups and nvidia-xconfig ;)

PS- I don't have anything HDMI ready, so I haven't tried that port at all. VGA works great under Vista. 

PS- The monitor I'm working with is a 24" Dell Ultrasharp.

PPS- Has anyone had luck with the media buttons (forward, reverse, stop, play/pause) with Amarok? Like most everyone else, they work great with Totem and Rhythmbox.

---

### Post by drsaamah on 2008-02-03
I've only tried the media buttons with banshee and totem.  They work great on those programs in my expreience.  Does anybody know how to completely turn OFF bluetooth?  I can adjust the Bluetooth manager settings so I have the computer hidden to devices around me, however I want it to be totally off for the sake of conserving battery life.

---

### Post by MrShifty on 2008-02-03
You can turn off the Bluetooth in the BIOS setup menu under the "Wireless" section.

---

### Post by herger on 2008-02-04
Hi all!
I am new with Ubuntu Gutsy and besides many problems in my Dell XPS 1330, I have these:
- Webcam doesn't work
- automount of cd and dvd (both blank and written) doesn't work.
Can You suggest anything?
Thanks and regards

Herger

---

### Post by MrShifty on 2008-02-04
The camera on the LED monitor works with V4L2:
[http://linux.bytesex.org/v4l2/](http://linux.bytesex.org/v4l2/)

So far the only application I've gotten it to work with is Ekiga.

I'm not sure about your CD drive issues, but posting the results of
```
$ less /etc/fstab 

```

would be a good start...

What other problems are you having?

---

### Post by Jamezracer on 2008-02-13
> **MrShifty said:**
> Has anyone gotten the VGA and/or HDMI ports to work (on the model with Nvidia graphics card)? I fiddled with the "Screens and Graphics" GUI under System->administration with mixed results; I couldn't get get widescreen output (1920x1200 is what I was shooting for). Also, that GUI did a nice job of torching my xorg.conf beyond repair. Hooray for backups and nvidia-xconfig ;)

PS- I don't have anything HDMI ready, so I haven't tried that port at all. VGA works great under Vista. 

PS- The monitor I'm working with is a 24" Dell Ultrasharp.

PPS- Has anyone had luck with the media buttons (forward, reverse, stop, play/pause) with Amarok? Like most everyone else, they work great with Totem and Rhythmbox.

so far no luck with either video ports. however, media buttons in amarok is an easy fix. open up the script manager in amarok and install one called gnomeMediaButtons (something like that). then you can set the shortcuts (they should be correct by default) in the gnome keyboard shortcuts manager. I just haven't been able to get tapping ff/rr to skip a track while holding down either one to seek within the track. thanks so much to whomever wrote that script, I was ecstatic when I found it.

---

### Post by darxoul on 2008-02-17
I have just installed Ubuntu (7.10) to my Dell XPS 1330 and the fan does not stop. I looked at the page [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330) and found that this issue is pending. But anyway, I couldn't understand what the guy is talking about. Is there anybody out there to translate those stuff into a human language?

I have intalled powertop but it doesn't start.
I also tried installing nvidia drivers for my graphics card, but I am not sure if I could do what I should have done.
My Gnome is not Ubuntu like (the colors are blue, not brown). The other things work as they did with the live cd, but the look is different which makes me think that somewhere something wrong has happened.
My shortcut buttons doesn't work. Should I do something to make them work?
Bluetooth doesn't seem to work but that might be because I disabled the device on the Windows side. I will try enabling it and restarting.

Urgent help needed.

Thanks in advance...

---

### Post by anaspeople on 2008-03-01
> **MrShifty said:**
> Has anyone gotten the VGA and/or HDMI ports to work (on the model with Nvidia graphics card)? I fiddled with the "Screens and Graphics" GUI under System->administration with mixed results; I couldn't get get widescreen output (1920x1200 is what I was shooting for). Also, that GUI did a nice job of torching my xorg.conf beyond repair. Hooray for backups and nvidia-xconfig ;)

PS- I don't have anything HDMI ready, so I haven't tried that port at all. VGA works great under Vista. 

PS- The monitor I'm working with is a 24" Dell Ultrasharp.



I just managed to swich screen only once, it wont work anymore. Does anybody know how to fix this? My graphics card is Nvidia Geforce 8400 GS

Thx.

---

### Post by MrShifty on 2008-03-01
what exactly did you do to switch screens? Did you use the button or some other method (changing resolution, primary/secondary screens, etc...)?

---

### Post by anaspeople on 2008-03-02
I just wanted to use Fn+F8 but it it wouldn't work.
Anyway I've just found out nvidia-settings can do all I need.
I'm really happy about it.

---

### Post by onit on 2008-03-02
> **SnowflakeRV7 said:**
> IV - Cleaning up the Vista Partitions

Next, I rebooted the computer, and dropped in the Dell Recovery DVD.  I didn't bother trying to boot into Vista first, based on reports of others online it seems the chances of a clean startup   were nil anyway.  I assumed it wouldn't work and that I would need to do a repair.  The Recovery CD started up, and I just followed the prompts until I was offered the option to Repair my installation... It's in the lower left corner of the window.  I chose that option.

Vista immediately detected that a repair was necessary, and when I said "ok" to the fix, it was finished almost as quickly as I hit the key.  Next, reboot.  Vista automatically detected that the drives had been played with, and performed a chkdsk on them.


I got as far as this stage, but the recovery disk (the one labeled "Operating System" that came with the laptop, right?) doesn't seem to have kicked in. There's just a screen telling me it'[s trying to fix problems, and scrolling back and forth, and not fixing problems.

Am I going paranoid or is this a deviation from smooth running and what can I do if it is?

---

### Post by arrakis31 on 2008-03-17
Question ?

Which version of ubuntu did you guys installed:

i386 or 64bits ???

I was wondering.
My xps 1330 will arrive in 2 days, I am excited

---

### Post by herger on 2008-03-17
Good choice!! ;) And good question...
I installed the 32-bit version and lost a lot of time in configuring it...
Probably in the future I will install a 64 bit, in order to use the multi-core architecture in compiling and executing programs and, above all, to have 4 Gb RAM (if You google around, You will see that it is almost impossibile to understand if the 32 bit OS will let You see ALL of the 4 Gb....)
Let me know what You decide.
Best regards

Herger

---

### Post by AMDATI on 2008-03-18
Hi guys, I'm gonna buy DELL XPS M1530, dose any of you know whether the updated sound cards work fine under ubuntu and Windows XP? (I really need these two Operation Systems :-) )

---

### Post by mattz on 2008-03-26
.

---

### Post by mlyons16 on 2008-03-29
> **SnowflakeRV7 said:**
> 

The laptop by default has four primary partitions, in this order (sizes approximate, I forget the exact numbers):
1 - tiny partition - 100 MB?
2 - Dell Recovery Partition - 10 GB, 5 GB of which is in use.
3 - Main Vista Partition - 135 GB, 24 GB of which is in use.
4 - Another smaller partition, 2 GB or so.  Apparently it's a "Media Live" partition or something.

Within the fourth primary partition is a single extended partition, that fills the entire primary partition.

III - Resizing the partitions:

I read through all the notes here online about using Vista's own partition resizing tools to resize, but Vista would only offer to reduce the 3rd partition to 86 GB, so I didn't want to do that.  A few people used gparted to repartition without problems, so I elected to go that route.  I disabled the pagefiles, and let Vista do a defragmentation on the drives.  It took about 6 hours to defrag.

I booted into Ubuntu from the stock 7.10 CD (not the alternate).  I fired up gparted, and made the following changes:

1. Partition 1 was tiny, so I left it alone.
2. Reduce partition 2 from 10 GB to 6 GB.
3. Reduce partition 3 from 135 GB to 35 GB, and move it up next to partition 2.
4. Increase partition 4 from 2 GB to whatever was left (104 GB, I think), to fill the whole drive.
5. Moved the 2 GB extended partition to the start of partition 4.

I did it this way because it keeps all of the partitions in the *same order* that they were when the computer was built by Dell... Anything I do with Ubuntu now will show up on the computer *after* the other partitions, hopefully not screwing up or confusing the Vista install.

I told it to Apply the changes, and went to have a coffee.  It worked on each step in turn, resizing and moving stuff around.  Note:  When it went to resize the 135GB partition, it seemed to die.  You could still move windows around and move the mouse, but the gparted status window stopped updating for a few minutes.  I'm not sure what part of the process was taking the time, but it needed to finish that before it would continue.  I let it work, and in about 2.5 hours I had all of my partitions shuffled.

IV - Cleaning up the Vista Partitions

Next, I rebooted the computer, and dropped in the Dell Recovery DVD.  I didn't bother trying to boot into Vista first, based on reports of others online it seems the chances of a clean startup   were nil anyway.  I assumed it wouldn't work and that I would need to do a repair.  The Recovery CD started up, and I just followed the prompts until I was offered the option to Repair my installation... It's in the lower left corner of the window.  I chose that option.

Vista immediately detected that a repair was necessary, and when I said "ok" to the fix, it was finished almost as quickly as I hit the key.  Next, reboot.  Vista automatically detected that the drives had been played with, and performed a chkdsk on them.

V - Installing Ubuntu

On the next reboot, I popped in the main Ubuntu disk.  I booted into Ubuntu Live first, then clicked the "install" link on the desktop.

I proceeded through the install prompts, and when it got to the partitioning section, I chose "Guided, use largest available space".

Ubuntu installed hands-off, and automatically set up GRUB with the Vista partition, and the MediaLive partition, alongside the Ubuntu parts.

VII - Final cleanup under Vista

I went back and turned on the pagefiles again, using the Vista default values (about 2G).

That's about it!  I hope this helps others who might want to install Ubuntu on this Dell model.

-Rob

Hi, I've sort of paraphrased the original quote here. I have that exact Dell model pretty much with that exact same default partition configuration too. I'm preparing to install Ubuntu on the laptop.

I've been following along quite easily with it.. doesn't seem to be too complicated, but I'm just trying to get some things sorted out.

A) First off, how do you turn off pagefiles? And how do you turn them back on after the installation is complete?

B) So, Use GParted? Okay... I don't have a lot of experience using that partition editor so how would you say, "Reduce the 10GB partition to 6 GB"?, and how do you move the partitions, such as "Reduce partition 3 from 135 GB to 35 GB, and move it up next to partition 2."?

C) Why do you need to use the Dell Recovery DVD to repair the installation... I didn't even think that would be a necessary step.

D) And finally, and probably the easiest, when you install, you pick, "Guided - Use largest continuous free space?" Simple enough.

Thanks in advance.

---

### Post by thorcik on 2008-04-01
> **MrShifty said:**
> PPS- Has anyone had luck with the media buttons (forward, reverse, stop, play/pause) with Amarok? Like most everyone else, they work great with Totem and Rhythmbox.

sorry, I haven't noticed it earlier. anyway, go to settings -> global shortcuts and assign them however You want to. in my case it works smoothly.
oh, the same can be done with volume in kmix.

---

### Post by employeeno5 on 2008-04-03
My M1330 had everything work out of the box:

bluetooth
media Buttons
remote control
camera
function keys
nvidia card
suspend/hibernate
fan
sound (possibly some issues; i haven't explored them enough, but the basics are there)

everything EXCEPT THE WIRELESS...

oh it's killing me. I can't really enjoy my new light weight laptop until I can get wireless working. Every guide I've read everywhere seems to have work arounds for when you can't get drivers or firmware to work, but that's not even the problem. I can't get Linux to recognize that a card even exists. I've tried many "solutions" anyways but to no avail.

Linux can't even see that I have a wireless card installed. All the drivers in the world make no difference if it thinks the card doesn't even exist.
I know that it is installed and working only because when booting into Vista it works fine.

I got the Dell card not the intel mind you. It's number 1395. I did not know the intel worked better. 
My previous laptop had a Dell card 1390 and that worked out of the box, so I mistakenly assumed that this one would be likely to as well. 

If I can't get it going in the next week I'm going to get an Intel card installed. However, my laptop is on a great 3 year service plan so I don't think I can do it myself without voiding my warranty. I'm not looking forward to shipping my laptop off and waiting for many weeks in hopes it comes back still functioning correctly in every other regard as well as wirelessly.

The moral of the story is get the Intel card. 

Also, if anyone happens to know what I can do to get Linux to know that I even have a wireless card (never mind run it correctly) please let me know.

Uhg. I can't stand that I have to boot into Vista for wireless right now. I only kept Vista installed at all for some work related reasons, and had/have no intention of regularly using it.

It's a sexy machine but the machine loses all of it's sexy when you have Windows running. :)

---

### Post by amias on 2008-04-04
have you tried using the windows drivers with ndiswrapper ?

---

### Post by employeeno5 on 2008-04-04
Yes, I'm going to clean it up though it give it another couple gos if need be.

---

### Post by QwUo173Hy on 2008-04-08
I'm hoping to order one of these in a few days. Can someone tell me if "Rotate Display" works? On Hardy Beta, that's Application->Other->Screens&Graphics
Then 'Rotate'

Thanks!

---

### Post by Exa on 2008-04-12
> **xxsaskexx said:**
> Mine came with the Broadcomm 1505-N.  I heard the Intel card is the one that works out of the box.  




I'm pretty sure I got it installed, It's an option in the BIOS. Didn't install Gutsy/Vista as dual boot, so I can't test whether Vista would enable it.  Think I'll buy  a bluetooth adapter.  They're cheap anyway.  Thanks for the help!

I had this issue as well. I had completely uninstalled Vista and Ubuntu didn't recognise the Bluetooth adaptor. The solution is very painful...to say the least.

You have to reinstall Vista; yes, that does mean you have to wipe your Ubuntu partition. Then install the Bluetooth driver from [_here_]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R127314&SystemID=XPS_M1210&os=WW1&osl=en&deviceid=12084&devlib=0&typecnt=1&vercnt=1&formatcnt=1&libid=5&fileid=169465"). [**IMPORTANT: Download this driver. DO NOT install the one included on the Dell Drivers CD.** *Turn Bluetooth on **within** Windows Vista*. You'll notice the blue light next to the power button comes on.

Now, you can reinstall Ubuntu and wipe the Vista partition or keep it if you want to.

Or you could just buy a dongle :), which you've probably already done. I don't why I even bothered...got time to burn :confused:.

---

### Post by agibby5 on 2008-05-09
Firstly, this is a good post.  I'm following the instructions as I'm typing this... 

> **Exa said:**
> I had this issue as well. I had completely uninstalled Vista and Ubuntu didn't recognise the Bluetooth adaptor. The solution is very painful...to say the least.

You have to reinstall Vista; yes, that does mean you have to wipe your Ubuntu partition. Then install the Bluetooth driver from [_here_]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R127314&SystemID=XPS_M1210&os=WW1&osl=en&deviceid=12084&devlib=0&typecnt=1&vercnt=1&formatcnt=1&libid=5&fileid=169465"). [**IMPORTANT: Download this driver. DO NOT install the one included on the Dell Drivers CD.** *Turn Bluetooth on **within** Windows Vista*. You'll notice the blue light next to the power button comes on.

Now, you can reinstall Ubuntu and wipe the Vista partition or keep it if you want to.

Or you could just buy a dongle :), which you've probably already done. I don't why I even bothered...got time to burn :confused:.


For some reason, I have no idea what you're saying here...

---

### Post by agibby5 on 2008-05-09
I followed these directions... however, when I try to boot into the Media Direct OS, it says "MD parition not found" or something like that.  My MD partition is still there.  How can I get this to work?

---

