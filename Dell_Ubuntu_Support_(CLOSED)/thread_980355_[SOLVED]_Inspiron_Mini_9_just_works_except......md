---
title: "[SOLVED] Inspiron Mini 9 just works except....."
date: 2008-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by armandh on 2008-11-12
with 16G flash drive and 512 more mem upgrades arrived Tues. and no problem out of the box with Ubuntu pre loaded.

found the place to click for the std Ubuntu desktop that I am comfy with.

great to get the codex and flash pre loaded BUT.......

the desktop effects [off/medium/high] tab was missing from system>preferences>appearances and no effects

even with the compiz manager added no effects.

so I went to my trusty junk box and dug out an 8G HDD slapped it in a USB adapter on my old P-III 866 i pulled the ribbon from the HDD and loaded Ubuntu 8.04 on to the usb HDD. 

then switched the mini's bios to boot from any USB HDD first
presto working stock ubuntu and after the 173 updates and codex and flash and compiz manager wow it just works including desktop effects. [reboot with the drive unplugged and it is back to "normal"]

so the question is do they leave effects off due to battery life, or thermal consideration, or write cycles or any combination of the above??? It did not seem overly warm after all that.

anyone care to comment???

---

### Post by smiles76239 on 2008-11-12
I have a Dell mini 9 as well and I ran into the same problem. My mini has a 16 GB SSD and 1 GB of RAM and it runs with lightning speed but just as you said, the visual effects tab was missing. The mini 9 is the first computer I have ever used Ubuntu on,(or any Linux based OS)and I was pretty disappointed that I couldn't enable the visual effects, especially after watching many Youtube videos of Linux users showing off with compiz-fusion. Apparently, the reason that Dell disabled this awesome Ubuntu feature is because it interferes with the ultimately useless custom Dell interface, and even if you switch to regular desktop mode you still won't be able to use the visual effects.:-( Other than that, Ubuntu is working flawlessly and I'm glad I didn't get XP instead.

---

### Post by armandh on 2008-11-13
You will be happy to note that it is not the hardware. the effects work fine with non dell 8.04. so I guess I may partition and dual boot, or wipe the factory install and go to non dell regular 8.04 ubuntu, or find a 4 gig mem stick and put my regular non dell ubuntu on it. or just use it with the ext HDD when I want to see the effects. I THINK OPTION #2.

here is what I posted in testimonials

--------------------------------------------------------------------------------



a poster in the dell section replied that the advanced effects interfered with the dell desktop so they were left out.

while pre loading skipped all but 7 updates and all the codex/flash fun like all the mfg install it comes up short!

seen first above after booting from a USB HDD with REAL Ubuntu 8.04

so do I wait for the warranty to expire or do I feel lucky.

---

### Post by smiles76239 on 2008-11-13
After reading that you managed to get Ubuntu 8.04 (and the visual effects)working on your mini 9 by booting it off a 4 GB USB drive,I decided to give give it a try, I downloaded the ISO file of 8.04 LTS "Hardy Heron" from 

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

and I used UNetbootin to install it on my PNY 4 GB USB drive. 

Then I plugged the drive into my mini 9 and booted Hardy Heron from it, the visual effects worked flawlessly, but that was about it, my wifi didn't work and neither did the sound (which I tested using one of the preloaded .spx files).](*,) 

Also I recently purchased a Sandisk Extreme III 4 GB Class6 SDHC Card and it works perfectly with Dell's version of 8.04 but the live version only recognizes it if its installed before powering on the device and if if I pop it out and plug it back in , it isn't recognized.:confused: 

Not to mention since I don't have wifi I can't install Compiz-fusion.:mad:

I also booted Ubuntu 8.04 live on my Dell Studio 15 (which normally runs Vista) and I ran into the same problems (ie no wifi)

I'm just wondering if you had any of the same issues that I did and if you know how to fix them. THANKS IN ADVANCE!

---

### Post by armandh on 2008-11-14
> **smiles76239 said:**
> After reading that you managed to get Ubuntu 8.04 (and the visual effects)working on your mini 9 by booting it off a 4 GB USB drive,I decided to give give it a try, I downloaded the ISO file of 8.04 LTS "Hardy Heron" from 

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

and I used UNetbootin to install it on my PNY 4 GB USB drive. 

Then I plugged the drive into my mini 9 and booted Hardy Heron from it, the visual effects worked flawlessly, but that was about it, my wifi didn't work and neither did the sound (which I tested using one of the preloaded .spx files).](*,) 

Also I recently purchased a Sandisk Extreme III 4 GB Class6 SDHC Card and it works perfectly with Dell's version of 8.04 but the live version only recognizes it if its installed before powering on the device and if if I pop it out and plug it back in , it isn't recognized.:confused: 

Not to mention since I don't have wifi I can't install Compiz-fusion.:mad:

I also booted Ubuntu 8.04 live on my Dell Studio 15 (which normally runs Vista) and I ran into the same problems (ie no wifi)

I'm just wondering if you had any of the same issues that I did and if you know how to fix them. THANKS IN ADVANCE!

sound issue but wifi worked out of the box. 
I automatically enable other sources in the admin>software source
so I am waiting for the drivers to catch up for the sound B4 any perminent change to the on board drive.

I will do all my experimenting booting the usb drive.

now if I just knew enough to move the drivers I need to the usb hdd I would be confident I could move them back to a fresh install. however from the reboot issies you have It may be a kernel recompile and I am mostly point & click.

Thanks for the UNetbootin tip

---

### Post by Rallg on 2008-11-14
My XP model, using Ubuntu 8.10 on USB via unetbootin, then installed to a drive partition: WiFi worked the first time, sound still has not worked. As of a week ago, a search here for possible solutions did not produce anything that worked for sound, so I assume that I am missing a driver. In any case I can wait for a solution.

Keep in mind that if you turn off WiFi in XP before rebooting to Ubuntu, then the WiFi might remain off in Ubuntu.

---

### Post by starcannon on 2008-11-14
To enable desktop effects on the factory install on the mini9 i simply  installed fusion-icon from synaptic, now I have compiz goodness, no reloading the OS needed.
```
sudo apt-get install fusion-icon
``` You'll find fusion-icon in Applications>System Tools. If you want it to load at boot be sure to add it to System>Preferences>Sessions.
The only thing I don't like about my mini is the keyboard layout, who ever came up with it needs to go back to ergonomics 101.

The machine works perfectly out of the box though.

GL and have fun

---

### Post by silverh20 on 2008-11-14
lol i feel bad for you guys who went through all those crazy methods to get compiz to work. i did basically the same as the post before me did. 

i added compiz, compiz manager, and even avant window navigator (that mac osx like dock) all through synaptic package manager. after that all i had to do was like the previous person, add to my sessions section the necessary info so all that stuff starts each time i boot. runs flawlessly. i have video playback and flash and all that without any slow down all while compiz and avant are running and i only have the 512 mb ram model. i even tried that penguin tux racer game on one of my 4 desktops and got 15 fps avg while compiz, etc was running. and no my battery life hasnt seem to have been affected, i still average about 4 hours give or take a few min. 

there is one catch tho, not sure if this is compiz' fault or what because i didnt notice till after the install of it, but if i put the mini into suspend mode sometimes when i bring it out of it everything is frozen and i have to reboot. this happens rarely tho, not every time i enter suspend.

---

### Post by jazz1 on 2008-11-14
> **starcannon said:**
> To enable desktop effects on the factory install on the mini9 i simply  installed fusion-icon from synaptic, now I have compiz goodness, no reloading the OS needed.
```
sudo apt-get install fusion-icon
``` You'll find fusion-icon in Applications>System Tools. If you want it to load at boot be sure to add it to System>Preferences>Sessions.
The only thing I don't like about my mini is the keyboard layout, who ever came up with it needs to go back to ergonomics 101.

The machine works perfectly out of the box though.

GL and have fun

Does this have a performance downside versus the stock machine?

---

### Post by armandh on 2008-11-15
wow that works great
had fun trying 8.10 via the boot from external HDD

---

### Post by smiles76239 on 2008-11-15
THANKS EVERYBODY!

I got the visual effects to work on the preloaded OS using the Compiz Fusion Icon.:) (so no need to reboot!)

In the synaptic package manager, I installed:
- compiz
- compizconfig-backend-gconf
- compizconfig-settings-manager 
- compiz-core
- compiz-dev
- compiz-fusion-plugins-extra
- compiz-fusion-plugins-main
- compiz-gnome
- compiz-plugins
- fusion-icon
- libcompfizconfig0
- libcompfizconfig0-dev
- libdecoration0
- libdecoration0-dev
- pdfcube
- python-compizconfig

BTW Can anyone tell me what the the Loose Binding option is for, (its located under Fusion-Icon> Compiz Options>  Loose Binding) and when I enable it my desktop effects and the display in general start to malfunction. :confused: It doesn't really matter, but I'm curious. Thanks in advance.

---

### Post by starcannon on 2008-11-16
> **jazz1 said:**
> Does this have a performance downside versus the stock machine?

Compiz of course will use more resources, and running the icon in the tray saps a little as well; that said, I have witnessed no visible slow down to any applications that I run.

I do hope that skype ends up in our mini9 repo's, I currently have it installed using the --force-architecture flag for dpkg.

---

### Post by planemanx15 on 2008-11-16
Just wondering... How do i get that really nice looking desktop page?  Im going to build a media center soon and large lcons like that would work fine.  

[IMG]http://i.dell.com/images/global/products/314x314/dhs_ubuntu_mini.jpg[/IMG]

Thats the best image i can find to show you guys

---

### Post by smiles76239 on 2008-11-16
As far as I know, the launcher with the large icons is unique to the version of 8.04 that comes with the mini 9. Here's a video link...

[http://www.youtube.com/watch?v=xb1iMYODSjM](http://www.youtube.com/watch?v=xb1iMYODSjM)

---

### Post by planemanx15 on 2008-11-17
Looks like i'll just strech the desktop icons out... KISS "keep it simple stupid"

---

### Post by armandh on 2008-11-17
does not take much for a media center I'm using an old 933 P-III with 512 meg mem and a newer 128 meg video card that has DVI out put. after a trip to medibuntu.org it plays about everything but I have a set top blue ray. As soon as I pluged it [the computer] in to the flat screen [DVI/HDMI adaptor plug]  I had a huge choice of resolutions. the set also has format selections but I use the unscaled option and it just fills the screen.

---

### Post by notwen on 2008-11-17
> **armandh said:**
> sound issue but wifi worked out of the box. 


> **Rallg said:**
> My XP model, using Ubuntu 8.10 on USB via unetbootin, then installed to a drive partition: WiFi worked the first time, sound still has not worked. As of a week ago, a search here for possible solutions did not produce anything that worked for sound, so I assume that I am missing a driver.

Try this to get sound working. I needed to do this on my Mini that came pre-installed w/ XP after installing Ubuntu.  Open up a terminal and enter the following command:
```
sudo nano /etc/modprobe.d/alsa-base
```

add this to the end of the file

```
options snd-hda-intel model=dell
```

Save the file, reboot and adjust volume accordingly viz the sound icon on gnome-panel.  Let me know if you run into any issues.  =]

---

### Post by smiles76239 on 2008-12-04
Thank You so much, My sound works perfectly!!!

---

### Post by soaham on 2009-02-25
Hi, just got the Mini with Ubuntu 8.04.. but i do not see the visual Effect tabs.  I followed through with the instructions here, i.e installed Fusion-Icon and also the Compiz manager, still i do not get the  Visual Effects tab under "System --> Preferences --> Apperence"

I get the "Fusion-icon", I have the "Advanced Desktop Effects Settings" under system--> preferences, but as soon as i choose "compiz" from the Window Manager in Fusion Icon, my windows losee the top bar, i am not able to close things, none of the effects work.

I have to switch back to Metacity in order to get the windows working properly.. 

I have been trying for a week now, it sounds simple when every one says it.. but for a noob like me, it is just not working.

any help would be greatly appreciated. 




~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
 Driver in use:         Unknown
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by armandh on 2009-02-25
in the end I dumped the dell 8.04 in favor of out of the box 8.10
+ the one line edit for sound, medibuntu.org for playing dvds and flash down load for ubuntu

compiz manager gave me all the options I wanted and I added maximus and set the KB shortcut for full screen.

all this dual boot with XP-SP2 and quickbooks
I did not bother with some of the drivers for xp as I only use it for QB

I added a 4Gb flash card for removable storage.

---

### Post by smiles76239 on 2009-02-25
I did the exact same thing as armandh. (I even added a 4GB SDHC Card). Dell's version of 8.04 is glitchy and a there are serious problems with the update manager. I put Ubuntu 8.10 on my Mini 9 and it runs exceptionally well. 

The only thing you'll have to do is just add in one line of code to fix the sound. (There is a description of how to do this a few posts above this one.) Other than that, everything worked right away (Wifi, peripherals, etc...)(Also, since you said you were a noob, I think I should mention that Cheese, the Webcam App, will need to be installed in order to get the Webcam up and running. If you have trouble w/ getting it to work just let me know.) :p

---

### Post by sirebral on 2009-02-26
That is so funny.  I was going to put Xubuntu on my mini 9 so fast, but when i played around with the default install I actually liked it.

I found the pre installed OS to be really stable.  Of course when I received mine they had fixed their repository so I could actually update.  And I have never used the software that forces a package into LPIA.  I think Dell heard people moan and fixed it.

I have actually had only one problem with this.  When I run Pidgin and Skype the audio conflicts until I kill pulseaudio.

---

### Post by armandh on 2009-02-26
my 9 was ordered sans camera.
mostly used for meetings 
the local Linux user groups 
or quickbooks ability to provide answers at a different meeting where I am treasurer

I love the extreme portability without limitations to ability.

I found the Dell OS a smaller foot print but short featurers too.
I did not mind two big OS footprints as I was keeping very little data. 
just what I needed for the meetings.

---

### Post by hollowtd on 2009-04-06
So When I run Compiz and emerald, i can get the cube to work but I can't select Applications or Places or System folder without it running really slow It won't open up and let me "scroll" down for example. I can tell that it wants to though. Does anyone have any ideas how to make it run smoothly? I know it can. (I have a file on the desktop. It flashes on and off, like metacity and compiz are fighting?) Any fixes for gliches, as I really want this to work and have tried all I know. Things just run slow or not at all but it does "work" sort of. Please

---

### Post by armandh on 2009-04-07
I am running OOTB 8.10 and with the package manager I added only 'compiz config settings manager' which seems to do a good job of resolving compiz feature conflicts.

cube works great and no slow down from other desktop bling.

---

