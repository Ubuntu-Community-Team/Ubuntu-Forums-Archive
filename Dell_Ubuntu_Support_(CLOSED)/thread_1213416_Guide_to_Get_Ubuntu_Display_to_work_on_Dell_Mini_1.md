---
title: "Guide to Get Ubuntu Display to work on Dell Mini 10/12  (Not the 10v)"
date: 2009-07-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sammyboy405 on 2009-07-14
All,

Since there are so Many other Netbooks that use the GMA 500, Besides the Dell Mini 10. Ive moved the Guide over to [here]("http://ubuntuforums.org/showthread.php?t=1229345")
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

If you have a Dell Mini Specific question you might try asking here.  But for all GMA 500 / PSB please goto the [referring]("http://ubuntuforums.org/showthread.php?t=1229345") thread.  Makes it alot easier to keep things updated.

---

### Post by fj401971 on 2009-07-19
Confirmed that it worked with a Dell Mini 12.

---

### Post by sammyboy405 on 2009-07-19
Im working on some config settings for getting the 3d to work. But as it stands now the Random Freezes are Killing me. So I Said the Heck with it when I discovered the following Bug Fix in 9.04 Release Notes.

> Display freezes with Intel graphics cards

Users of various Intel video chipsets reported freezes under various conditions (e. g. a few minutes after suspend on the i945, see 339091). In many cases, switching off desktop effects in System &#8594; Preferences &#8594; Appearance was reported to help.

If it still happens without desktop effects, you can add Option "DRI" "off" to the Device section of /etc/X11/xorg.conf, as described above. This will disable 3D acceleration and desktop effects, but makes suspend work reliably again and also avoid many types of crashes.

These freezes happen particularly often on the i965 chips (359392). For that reason, desktop effects were disabled by default on this chipset in the final release. They will be re-enabled in a 9.04 Update once the problem has been fixed. 

and

> Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases (252094). Many of the issues have been resolved in Ubuntu 9.04, but some remain.

    *

      Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.
    *

      Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our testing has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf. Users wishing to maximize stability should stay with the standard default acceleration method, "EXA".

      /!\ In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert the UXA option.
    *

      If none of the above helps, some users reported success with using an older driver version. 

So Even though it dont reference the GMA500, im pretty sure just because its an Intel based chipset that this will fix my random freeze ups. I will Post later if it fixes the random freezes.

---

### Post by sammyboy405 on 2009-07-23
And after finially having time to read those those bugs..  basicly the GMA500 will never have a stable 3d.  I got 3d to Work. That was simple. But the constant video freezes where unacceptable. So Back to 2d I went. 

The Workaround for the freezes is to disable 3d.

So We shall wait for 9.10 and hope we get some good GMA500 Loving. I refuse to go back to Windows on my Netbook.

---

### Post by sammyboy405 on 2009-07-23
Ive added Information on how to check your Kernel version and how to upgrade it if its not the latest version.

All those who are more savvy in the ways of *INUX please correct me on anything if its wrong.  I dont like giving out bad info.

Also if there is an easier way than what I posted please comment if you would.  Maybe I Need to Learn something too.

---

### Post by windows-killer on 2009-07-29
> **sammyboy405 said:**
> I Know there are other posts out there similar to this. But it was so hard to track down each tid bit of information. So Im hoping with the Title of this thread and the contents in here will allow for others to easily find all the information needed rather than digging though several hundred threads.

--- Fixing Resolution on the Dell Mini 10(1010) and 12 With Ubuntu 9.04 --- 

You Need to have the 2.6.28.13-generic or 2.6.28.13-lpia Kernel else you will get DRM Errors after reboot. Please update to the latest Kernel before performing these procedures.

First lets check to make sure you have the right Kernel version before we proceed.
From the Terminal:
```

uname -a

```This will display your Kernel version. If it is 2.6.28.13 or Higher You are done. And continue down below. If it is not then do the following steps:
```
sudo apt-get update
sudo apt-get dist-upgrade
```Reboot
go back into a terminal
```

uname -a

```Make sure your Upgrade happened. If it did and you want to get rid of your old Kernel you can do:
```

sudo apt-get autoremove

```If not, no harm done, it wont hurt anything to leave it other than eat up about 100meg of space. Just continue on with the Guide.

---Continue on From here if you have the Correct Kernel Version---

From the Terminal:
Add this to your repository
```

sudo nano /etc/apt/sources.list.d/ubuntu-mobile.list

```add these 2 lines

```

deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main

```then ctrl+o (which saves it)
Then ctrl+x (To Exit)

Now you need to authenticate the keys
```

gpg --keyserver keyserver.ubuntu.com --search-keys ubuntu-mobile

```Press 1 and Enter
```

gpg -a --output /tmp/pub.asc --export C6598A30
sudo apt-key add /tmp/pub.asc && rm /tmp/pub.asc

```Now that your Ubuntu-Mobile Key is added do the Following.

```

sudo apt-get update
sudo apt-get install xserver-xorg-video-psb

```A Reboot May be required after the Installation.

I Hope this Helps everyone out. (this will also work for the Dell Mini 12)

** I Have Loaded Ubuntu / Kubuntu and Xubuntu and I have verified that this works on those flavors of Ubuntu. ***

Damn, provide a GUI for this please!

---

### Post by JustBrowsing on 2009-07-30
> **windows-killer said:**
> Damn, provide a GUI for this please!
:confused: Are you serious?! This guy lays it out step-by-step on how to get the Poulsbo driver working. Many thanks to the OP to get this thing working.

If you don't know how to use the nano program or run things from the terminal, you probably need to check out "Absolute Beginner's Forum".

I have the 3D driver installed right now, and I expect it to freeze at any moment. :o

---

### Post by sammyboy405 on 2009-07-30
> **JustBrowsing said:**
> I have the 3D driver installed right now, and I expect it to freeze at any moment. :o


Do this, Unless you Really want the 3D Features.

Keep the 3D Drivers..

Here is a Copy of my xorg.conf

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "DRI" "off"
        Option "MigrationHeuristic" "greedy"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection

```

I added the

```
Option "AccelMethod" "EXA"
Option "DRI" "off"
Option "MigrationHeuristic" "greedy"
```

And the freezes "So Far" have gone away and I still have the performance increase.

---

### Post by sammyboy405 on 2009-07-30
OK 14 did break it. But all is not lost as long as you have not removed 13.

On boot up in Grub select your 13 kernel.

Once booted up into 13
from a terminal
```

sudo apt-get --purge autoremove xserver-org-video-psb
sudo apt-get clean

```Reboot back into -14

Then you have a couple of options I will go over the easiest just because I think the Audience here maybe limited on *INUX Knowledge. I will post other ways later when I have time.

Booted into the version 14 kernel from a terminal

```

sudo apt-get install xserver-org-video-psb

```Reboot and you "Should" be good to go again.

Now Im not guaranteeing this just because im writing this off memory. I dont think there was anything else I did to get it to work with 14.

However I do have a set of Procedures im typing up tonight that will use some of the Newer driver that include 3d support. As mentioned earlier in this thread. However since 3d is so unstable Im including ways to fix the unstableness that seem to be working for me.

Im in the process of installing Windows 7 on my Mini 10 Right now but as soon as its done and I have my dual boot set back up I will get on these procedures.

But the above should work for ya as long as you still have -13 installed and listed in your grub boot list.

Also if there is any Linux folks out there.. Isnt there a way to just tell dkgp to reconfigure xserver-org-video-psb? I swore there was a command or ability to do that. If someone knows it post it. And someone give that a try rather than removing and reinstalling and all the reboots. I Think doing a re-configure on the current package would fix the -14 issues.

---

### Post by duskstriker on 2009-07-31
> But all is not lost as long as you have not removed 13.If you did remove 13, like I did, you can jump back pretty easily...

```
sudo apt-get install linux-image-2.6.28-13-generic
```To boot directly into 13 I tweaked menu.lst via...

```
sudo vi /boot/grub/menu.lst
```And then just moved "Ubuntu 9.04, kernel 2.6.28-13-generic" and "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery)" sections to the top of the list.

Also, I found that I lost wireless when I did this. You can recover it via...

```
sudo apt-get install linux-restricted-modules-`uname -r`
```Throw in a reboot and you should be good to go. I hope this is helpful.

---

### Post by PreviousN on 2009-07-31
> **sammyboy405 said:**
> Do this, Unless you Really want the 3D Features.

Keep the 3D Drivers..

Here is a Copy of my xorg.conf

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "DRI" "off"
        Option "MigrationHeuristic" "greedy"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection

```

I added the

```
Option "AccelMethod" "EXA"
Option "DRI" "off"
Option "MigrationHeuristic" "greedy"
```

And the freezes "So Far" have gone away and I still have the performance increase.

Thanks for posting your xorg.conf. I'm not getting freezes anymore. At least after running glxgears for ~5 hours and browsing the net for ~1 hour. You deserve a free beer!

---

### Post by sammyboy405 on 2009-07-31
> **PreviousN said:**
> Thanks for posting your xorg.conf. I'm not getting freezes anymore. At least after running glxgears for ~5 hours and browsing the net for ~1 hour. You deserve a free beer!

I Should Really Move this and Just generically base it on the GMA 500 Graphics and Not just to the Dell Mini's.  As there seem to be quite a few people with Other Branded Netbooks with the GMA 500.

---

### Post by nobodyisme on 2009-08-01
Maybe you could also post the instructions how to learn video players play HD video on GMA 500?

---

### Post by mikewhatever on 2009-08-01
Can someone post the output of glxgears running full screen with this setup.

---

### Post by RChickenMan on 2009-08-01
Hey guys, I wasted about ten hours of my life trying to get this to work, and I finally have a display at native resolution and acceptable 2d video performance!

Just in case anyone else is banging their head against the wall with the convoluted video error message that appears after startup...

After trying all combinations of kernel installations and whatnot (and a full reinstall of the OS!) I was finally able to fix all of my problems by running the following commands:

```
apt-get install psb-kernel-source psb-kernel-headers
```

I'm no linux expert, but I think this does something along the lines of rebuild the kernel with special headers to support the PSB Video Driver from Hell.  Either way, after rebooting, my display is behaving properly!

I'm still using the out-of-the-box xorg.conf (or whatever modifications were automatically made due to the package installations).  Is there anything I can do to further optimize 2d video performance (i.e. I would love to be able to actually view youtube videos in full screen again!)?

I hope my advice saves some headaches!

---

### Post by Squalo_ch on 2009-08-01
Brilliant. The fix did work on my mini10. Thanks RChickenMan and sammyboy405.

---

### Post by sammyboy405 on 2009-08-02
Guide has been Updated with new procedures. These have better performance. And more information about upgrading kernel versions.

---

### Post by mikewhatever on 2009-08-03
Well, will you post the output of glxgears command?

glxgears -geometry 1024x576

Let it run fro half a minute, then press Esq to quit.

---

### Post by SQuark on 2009-08-03
Around 124 FPS on my Mini 10.

---

### Post by s-tobe on 2009-08-03
Hi, This weekend I bought an ASUS 1101HA with GMA500 chipset. I installed Karmic Koala because of support for the brand new wireless and wired chipset and hoped that there would be support for the GMA500 as well.

Does the suggested solution for 9.04 support also cover Karmic with kernel 2.6.31 ?

thanks

---

### Post by mikewhatever on 2009-08-03
There doesn't seem to be a mobile repository for karmic, and a search through standard repositories doesn't turn up anything related to poulsbo or gma500, which means there is not driver for gma500 just yet.
You may also want to know that, since karmic is an alpha, it is not recommended for regular use.

---

### Post by duskstriker on 2009-08-03
I'm only getting about 20 fps.  =/

88 frames in 5.0 seconds = 17.512 FPS
85 frames in 5.0 seconds = 16.955 FPS
110 frames in 5.0 seconds = 21.820 FPS
100 frames in 5.0 seconds = 19.836 FPS
95 frames in 5.0 seconds = 18.833 FPS
104 frames in 5.0 seconds = 20.791 FPS
102 frames in 5.0 seconds = 20.275 FPS

Really you're getting 124 FPS? On Jaunty? I'm uber jealous :(

---

### Post by mikewhatever on 2009-08-03
> **duskstriker said:**
> 

Really you're getting 124 FPS? On Jaunty? I'm uber jealous :(

Yes, you should apply the suggested fix.

glxgears -geometry 1024x576
551 frames in 5.0 seconds = 110.147 FPS
542 frames in 5.0 seconds = 108.276 FPS
618 frames in 5.0 seconds = 123.390 FPS
634 frames in 5.0 seconds = 126.569 FPS
636 frames in 5.0 seconds = 127.020 FPS
637 frames in 5.0 seconds = 127.279 FPS
717 frames in 5.0 seconds = 143.226 FPS
713 frames in 5.0 seconds = 142.445 FPS
708 frames in 5.0 seconds = 141.468 FPS
703 frames in 5.0 seconds = 140.531 FPS
708 frames in 5.0 seconds = 141.460 FPS

---

### Post by duskstriker on 2009-08-04
> **mikewhatever said:**
> Yes, you should apply the suggested fix.

glxgears -geometry 1024x576
551 frames in 5.0 seconds = 110.147 FPS
542 frames in 5.0 seconds = 108.276 FPS
...

Oh wow those numbers look great. Here's my configuration...

Kernel: 2.6.28-13-generic  (still running 13 because 14 broke everything)

Here's my /etc/X11/xorg.conf...

```
Section "Device"
    Identifier    "Configured Video Device"
    Option         "AccelMethod"             "EXA"
    Option         "DRI"                 "off"
    Option         "MigrationHeuristic"         "greedy"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerFlags"
    Option         "DontZap"             "False"
EndSection
```I performed these steps...

    ```
Make sure we have a clean updated install...
  sudo apt-get update
  sudo apt-get dist-upgrade

Clean up old kernel update files...
  sudo apt-get autoremove

Create a new apt-get sources list...
  sudo vi /etc/apt/sources.list.d/ubuntu-mobile.list
    
With these lines...
  deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
  deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

Authenticate the keys (security for the new apt-get sources)...
  gpg --keyserver keyserver.ubuntu.com --search-keys ubuntu-mobile

Press the number '1' and enter...
  gpg -a --output /tmp/pub.asc --export C6598A30
  sudo apt-key add /tmp/pub.asc && rm /tmp/pub.asc

Install the new video driver...
  sudo apt-get update
  sudo apt-get install xserver-xorg-video-psb
```I then tried to update my psb kernel source/headers via...

```
apt-get install psb-kernel-source psb-kernel-headers
```Reboot... no love. Although I do have the correct resolution, I'm only getting about 20fps. =/

---

### Post by gtaluvit on 2009-08-04
> **duskstriker said:**
> Oh wow those numbers look great. Here's my configuration...

Kernel: 2.6.28-13-generic  (still running 13 because 14 broke everything)

```
apt-get install psb-kernel-source psb-kernel-headers
```Reboot... no love. Although I do have the correct resolution, I'm only getting about 20fps. =/

You'll need to do a ```
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d
``` in order to get the 3D driver and higher framerates. Also, -14 does work, but you need to rebuild the module. When you boot into -14 X will fail to start up. Go to a command prompt and type ```
sudo dpkg-reconfigure psb-kernel-source
```

That will rebuild the kernel driver. Reboot and you're good to go.

---

### Post by duskstriker on 2009-08-05
> **gtaluvit said:**
> Reboot and you're good to go.

OMG Your my hero! :D

```
$ glxgears -geometry 1024x576
385 frames in 5.0 seconds = 76.989 FPS
517 frames in 5.0 seconds = 103.245 FPS
518 frames in 5.0 seconds = 103.533 FPS
511 frames in 5.0 seconds = 102.102 FPS
515 frames in 5.0 seconds = 102.853 FPS
507 frames in 5.0 seconds = 101.224 FPS
```

Now if only I could get Ubuntu's Visual Effects working. :P

Thanks again for all your help everyone!!

---

### Post by sammyboy405 on 2009-08-05
> **duskstriker said:**
> OMG Your my hero! :D

```
$ glxgears -geometry 1024x576
385 frames in 5.0 seconds = 76.989 FPS
517 frames in 5.0 seconds = 103.245 FPS
518 frames in 5.0 seconds = 103.533 FPS
511 frames in 5.0 seconds = 102.102 FPS
515 frames in 5.0 seconds = 102.853 FPS
507 frames in 5.0 seconds = 101.224 FPS
```

Now if only I could get Ubuntu's Visual Effects working. :P

Thanks again for all your help everyone!!

thought I Said in my Guide how to do that.

remove the "options" "DRI"  From your xorg.conf

But the flip side is your system will lock up with USB Devices.

So as long as you don mind random freezes remove that line and you can use Visual Effects.

---

### Post by optimistique1 on 2009-08-06
Hi All, I previously had the DELL MINI 12 with the deaded GMA 500 chipset and never managed to get the grahics to work.  However, I am considering getting the DELL MINI 10.
However, I notice there is a DELL MINI 10 and a DELL MINI 10v.
Does anyone know which version does not have the GMA 500 Chipset as I want to avoid all this heartache again...
Many thanks
Garry:)

PS:
Sorry, no poulsbo driver for 9.10
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-August/028670.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-August/028670.html)

---

### Post by sammyboy405 on 2009-08-06
> **optimistique1 said:**
> Hi All, I previously had the DELL MINI 12 with the deaded GMA 500 chipset and never managed to get the grahics to work.  However, I am considering getting the DELL MINI 10.
However, I notice there is a DELL MINI 10 and a DELL MINI 10v.
Does anyone know which version does not have the GMA 500 Chipset as I want to avoid all this heartache again...
Many thanks
Garry:)

PS:
Sorry, no poulsbo driver for 9.10
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-August/028670.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-August/028670.html)

Mini 10v Does NOT have the GMA500

---

### Post by bluepenny65 on 2009-08-08
Sammyboy,

I am using the new .15 image but using all your instructions and updates, 3D works great on my Mini 12 right now but I can only get about 60fps with glxgears....can the image  version be the reason for this? I want to get atleast 100+ fps

glxgears -geometry 1280x800
246 frames in 5.0 seconds = 49.053 FPS
292 frames in 5.0 seconds = 58.386 FPS
308 frames in 5.0 seconds = 61.438 FPS
284 frames in 5.0 seconds = 56.614 FPS
283 frames in 5.0 seconds = 56.506 FPS
303 frames in 5.0 seconds = 60.459 FPS
290 frames in 5.0 seconds = 57.940 FPS
290 frames in 5.0 seconds = 57.996 FPS
293 frames in 5.0 seconds = 58.412 FPS

---

### Post by sammyboy405 on 2009-08-08
> **bluepenny65 said:**
> Sammyboy,

I am using the new .15 image but using all your instructions and updates, 3D works great on my Mini 12 right now but I can only get about 60fps with glxgears....can the image  version be the reason for this? I want to get atleast 100+ fps

glxgears -geometry 1280x800
246 frames in 5.0 seconds = 49.053 FPS
292 frames in 5.0 seconds = 58.386 FPS
308 frames in 5.0 seconds = 61.438 FPS
284 frames in 5.0 seconds = 56.614 FPS
283 frames in 5.0 seconds = 56.506 FPS
303 frames in 5.0 seconds = 60.459 FPS
290 frames in 5.0 seconds = 57.940 FPS
290 frames in 5.0 seconds = 57.996 FPS
293 frames in 5.0 seconds = 58.412 FPS

You may not get as many FPS as a Mini 10 because your Resolution is Higher.  Mini 10 can only run at 1024x576  your running at 1280x800  So that may be the difference on why.

---

### Post by sammyboy405 on 2009-08-12
Ive been running a new config setup. Thought id share it. Havent had any lock ups yet. AND im getting 130 to 150fps with Compiz Working.

Here it goes. Im going off memory on what I did. You must already have done guide written above.

I Perfer nano to edit. ctrl+o to save and ctrl+x to exit

Open A Terminal:
```

sudo nano /boot/grub/menu.lst

```You should find a line that looks like this (your root UUID and kernel version will/may vary)
```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet splash
``` Change it to this (bold is to emphasize what needs changing)
```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=786mb

```This tells grub to force the kernel to recognize only 786mb of the installed 1GB, leaving 238mb free for the graphics adapter to use. The “nosplash” option prevents any sexy graphics being displayed during boot. I’m not sure if this is *essential* but it seemed like a good idea?

Now for Compiz.

```

sudo nano /usr/bin/compiz

```press ctrl+w and type whitelist and press enter.

```
WHITELIST=”nvidia intel ati radeon i810 fglrx”
``` Change it to this:
```
WHITELIST=”psb nvidia intel ati radeon i810 fglrx”
```Now your going to need to edit a line in your xorg.conf file. Doing this will allow for 3d effects.

```
sudo nano /etc/X11/xorg.conf
```Find the line

```
Option "DRI" "off"
and make it look like
 Option "DRI" "on"

```Now Reboot.

Once Rebooted

click System -> Preferences -> Appearance and click the Visual Effects tab. I chose “Normal” just to get things started…

Now Hope and Pray? LOL Have fun with it .. Also Check out X.Org Wiki - Home check out there FAQ there on some different options you can do inside your xorg.conf file with the 3d/2d settings.

Also Play with the Memory settings for the Kernel. I just choice a semi round number. I also installed compizconfig-settings-manager to fine tune the compiz setup you might or might not want to try it? Rotating desktop seems to work.

---

### Post by bluepenny65 on 2009-08-13
Okay.

---

### Post by excogitation on 2009-08-17
> **s-tobe said:**
> Hi, This weekend I bought an ASUS 1101HA with GMA500 chipset. I installed Karmic Koala because of support for the brand new wireless and wired chipset and hoped that there would be support for the GMA500 as well.

Does the suggested solution for 9.04 support also cover Karmic with kernel 2.6.31 ?

No it doesn't.

Is anybody working on getting this driver upstream?
If not - how about Karmic?

---

### Post by sammyboy405 on 2009-08-17
> **excogitation said:**
> No it doesn't.

Is anybody working on getting this driver upstream?
If not - how about Karmic?


Yes it Does with Some minor Changes

see this thread I have going on the issue. this should address the 9.10 issues and how to get it to work on 9.10

[http://ubuntuforums.org/showthread.php?t=1235843&page=2](http://ubuntuforums.org/showthread.php?t=1235843&page=2)

---

### Post by jonah1980 on 2009-08-18
hi guys, i tried this and it's screwed my system. i can't get into kde anymore and am stuck with a prompt, whatever it installed it seemed to remove something too and i don't remember what to put it back. can anyone please please help. i have a eee 1101ha, it worked ok before i tried this but resolution was stretched and i wanted 1366x768

---

### Post by pjman on 2009-08-18
@jonah1980 - Try running 

> sudo dpkg-reconfigure psb-kernel-source

This should get it working with the latest kernel upgrade. Also check out this thread - [http://ubuntuforums.org/showthread.php?t=1014534](http://ubuntuforums.org/showthread.php?t=1014534)

---

### Post by excogitation on 2009-08-18
> **sammyboy405 said:**
> Yes it Does with Some minor Changes

see this thread I have going on the issue. this should address the 9.10 issues and how to get it to work on 9.10

[http://ubuntuforums.org/showthread.php?t=1235843&page=2](http://ubuntuforums.org/showthread.php?t=1235843&page=2)

over at that thread they say it's not working with Karmic (yet).

---

### Post by optimistique1 on 2009-08-19
Hey I finally managed to get Ubuntu up and running on my Sony Vaio P thanks to you amazing guys with this command "kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=786mb ".

I just want to ask one question, after following the above I no longer get the splash screen at logon and log out.

Is there anyway to re-enable this?

Many thanks

Garry

---

### Post by sammyboy405 on 2009-08-19
> **optimistique1 said:**
> Hey I finally managed to get Ubuntu up and running on my Sony Vaio P thanks to you amazing guys with this command "kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=786mb ".

I just want to ask one question, after following the above I no longer get the splash screen at logon and log out.

Is there anyway to re-enable this?

Many thanks

Garry

Change nosplash  to splash

---

### Post by sammyboy405 on 2009-08-19
> **excogitation said:**
> over at that thread they say it's not working with Karmic (yet).

Using tidbits from each comment I was able to get it working fine on my Dell Mini 10 on 9.10

---

### Post by 12345p on 2009-08-19
Wonderful! 

Thank you for keeping this guide up to date & current.

I got this working on my Dell Mini 10! And what a big help indeed.

2 Notes:

sudo apt-get install psb-kernel-source (not sources)

and

the gpg part of the guide didn't work for me. But I was allowed to download the ubuntu-mobile stuff anyway. GLX-gears gets an average 110fps on my Z520..

Horray for my netbook on 9.04.netbook.remix

---

### Post by sammyboy405 on 2009-08-19
> **12345p said:**
> Wonderful! 

Thank you for keeping this guide up to date & current.

I got this working on my Dell Mini 10! And what a big help indeed.

2 Notes:

sudo apt-get install psb-kernel-source (not sources)

and

the gpg part of the guide didn't work for me. But I was allowed to download the ubuntu-mobile stuff anyway. GLX-gears gets an average 110fps on my Z520..

Horray for my netbook on 9.04.netbook.remix

i thought I fixed the typos on this thread but maybe not I will fix that now.. I have 3 fourms with this guide on it. so i might of gotten confused.

---

### Post by optimistique1 on 2009-08-20
Hi All,

I followed the below command which worked a treat:

kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=786mb.  This tells grub to force the kernel to recognize only 786mb of the installed 1GB, leaving 238mb free for the graphics adapter to use. 

However, my Sony Vaio P has got 2GB RAM so is it possible to amend the command (And if so what to?).  The reason I ask this is because when I look at my system info it only shows I have 1GB ram :confused:

---

### Post by pjman on 2009-08-20
> **optimistique1 said:**
> my Sony Vaio P has got 2GB RAM so is it possible to amend the command (And if so what to?).  The reason I ask this is because when I look at my system info it only shows I have 1GB ram :confused:

Change
> kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=786mb

to
```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=1792mb
```

I think this will leave ~256mb free for video. You can also change nosplash to splash to keep the splash screen. I wish I had 2gb on my mini 10 :-)

---

### Post by sammyboy405 on 2009-08-20
> **optimistique1 said:**
> Hi All,

I followed the below command which worked a treat:

kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=786mb.  This tells grub to force the kernel to recognize only 786mb of the installed 1GB, leaving 238mb free for the graphics adapter to use. 

However, my Sony Vaio P has got 2GB RAM so is it possible to amend the command (And if so what to?).  The reason I ask this is because when I look at my system info it only shows I have 1GB ram :confused:

```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=1792mb
```

That should fix ya.. 256 for Graphics and 1792 for System.

---

### Post by sammyboy405 on 2009-08-20
> **pjman said:**
> Change


to
```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=1792mb
```

I think this will leave ~256mb free for video. You can also change nosplash to splash to keep the splash screen. I wish I had 2gb on my mini 10 :-)

LOL Sorry Yea I Just now hit the submit button i got side tracked. At least we had the same answer. ;)

---

### Post by maddentim on 2009-08-27
> **sammyboy405 said:**
> Ive been running a new config setup. Thought id share it. Havent had any lock ups yet. AND im getting 130 to 150fps with Compiz Working.

Here it goes. Im going off memory on what I did. You must already have done guide written above.

I Perfer nano to edit. ctrl+o to save and ctrl+x to exit

Open A Terminal:
```

sudo nano /boot/grub/menu.lst

```You should find a line that looks like this (your root UUID and kernel version will/may vary)
```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet splash
``` Change it to this (bold is to emphasize what needs changing)
```
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=c34d1d57-59d3-4f6f-abc1-fd83aea4 ro quiet nosplash mem=786mb

```This tells grub to force the kernel to recognize only 786mb of the installed 1GB, leaving 238mb free for the graphics adapter to use. The “nosplash” option prevents any sexy graphics being displayed during boot. I’m not sure if this is *essential* but it seemed like a good idea?

Now for Compiz.

```

sudo nano /usr/bin/compiz

```press ctrl+w and type whitelist and press enter.

```
WHITELIST=”nvidia intel ati radeon i810 fglrx”
``` Change it to this:
```
WHITELIST=”psb nvidia intel ati radeon i810 fglrx”
```Now your going to need to edit a line in your xorg.conf file. Doing this will allow for 3d effects.

```
sudo nano /etc/X11/xorg.conf
```Find the line

```
Option "DRI" "off"
and make it look like
 Option "DRI" "on"

```Now Reboot.

Once Rebooted

click System -> Preferences -> Appearance and click the Visual Effects tab. I chose “Normal” just to get things started…

Now Hope and Pray? LOL Have fun with it .. Also Check out X.Org Wiki - Home check out there FAQ there on some different options you can do inside your xorg.conf file with the 3d/2d settings.

Also Play with the Memory settings for the Kernel. I just choice a semi round number. I also installed compizconfig-settings-manager to fine tune the compiz setup you might or might not want to try it? Rotating desktop seems to work.
@sammyboy405 - you are my hero.  desktop-effects up and running.  thanks for sharing!

---

### Post by excogitation on 2009-08-27
Thanks, guys.
Finally I have desktop effects working on the Vaio P with 2.6.28-15.

Now if flash videos (even non hd) just played fine on the P11Z ;-)


Well... you can't have everything, can you?

---

### Post by sammyboy405 on 2009-08-28
> **excogitation said:**
> Thanks, guys.
Finally I have desktop effects working on the Vaio P with 2.6.28-15.

Now if flash videos (even non hd) just played fine on the P11Z ;-)


Well... you can't have everything, can you?

Flash Videos seem to be a Limitation on The Atom Processor and not the GMA500..  Adobe needs to optimize there code a bit more. Ive noticed Youtube works somewhat ok.. Vimeo works ok.. Hulu Lags a bit.

---

### Post by gunnar123 on 2009-09-04
> **sammyboy405 said:**
> 

Now you need to authenticate the keys
```

gpg --keyserver keyserver.ubuntu.com --search-keys ubuntu-mobile

```Press 1 and Enter
[code]
gpg -a --output /tmp/pub.asc --export C6598A30
sudo apt-key add /tmp/pub.asc && rm /tmp/pub.asc


Somebody added another key to that keyserver that match "ubuntu-mobile"
so the intended entry is currently "2".
General recipe is to look for entry "Launchpad PPA for Ubuntu Mobile Team" and enter the index for that one.
So "Press 1 and Enter" should right now be "Press 2 and Enter".

Great tutorial !  I got this working on the Asus Eee 1101HA.
mem=786mb seems to improve a bit on things.
With glxgears -geometry 1024x576 I get appr 97-100 fps in High Perf mode (87 power saver)
Beware it's easy to cheat/get cheated and get higher fps by moving parts of the window off screen. So when posting your figures, make sure you have the gears window all visible/uncovered, fully on screen.

Worth mentioning, at least on the 1101HA the fps depends on the cpu clocking.
I use the eee-tray utility and typical result for plain glxgears (no -geometry argument) is:
Power Saver: appr 170fps (when display dims figure decrease, probably a further CPU underclock occurs?)
High Performance: appr 245fps
Super High Performance: (no change - entry not configured in eee-tray)
Insane Performance: (no change - entry not configured in eee-tray)

Compiz navigation with rotating cube makes me happy, a bit jerky on Power Saver
but then this Eee model is all a low power game.

When running nothing but the OS and System Monitor after a default install and the recipes applied I have 367 Mbyte RAM consumed of the currently 767 total allocated for this purpose.
Getting Firefox to operate in a lean way can be an interesting challenge for these machines, there is simply a huge tradeoff towards battery life vs CPU power.

A question may be to what extent sw is involved in various rendering in relation to
HW acceleration. Such stuff will likely unfold over time. Once it's shown a basic system works on these platforms (done here) the popularity/demand might increase for getting people taking a look at getting the most out of the graphics HW.

sammyboy405 is worthy of high praise for letting us share the cooked meals !

---

### Post by sammyboy405 on 2009-09-06
All,

Since there are so Many other Netbooks that use the GMA 500, Besides the Dell Mini 10. Ive moved the Guide over to [here]("http://ubuntuforums.org/showthread.php?t=1229345")
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

If you have a Dell Mini Specific question you might try asking here.  But for all GMA 500 / PSB please goto the [referring]("http://ubuntuforums.org/showthread.php?t=1229345") thread.  Makes it alot easier to keep things updated.

---

### Post by sammyboy405 on 2009-09-06
> **gunnar123 said:**
> Somebody added another key to that keyserver that match "ubuntu-mobile"
so the intended entry is currently "2".
General recipe is to look for entry "Launchpad PPA for Ubuntu Mobile Team" and enter the index for that one.
So "Press 1 and Enter" should right now be "Press 2 and Enter".


Fixed in new [Guide]("http://ubuntuforums.org/showthread.php?t=1229345")

> **gunnar123 said:**
> 
Great tutorial !  I got this working on the Asus Eee 1101HA.
mem=786mb seems to improve a bit on things.


If your Netbook has more RAM than 1GB make sure you adjust that number.

> **gunnar123 said:**
> 
With glxgears -geometry 1024x576 I get appr 97-100 fps in High Perf mode (87 power saver)
Beware it's easy to cheat/get cheated and get higher fps by moving parts of the window off screen. So when posting your figures, make sure you have the gears window all visible/uncovered, fully on screen.


This is very True. When I Test, I have no additional Windows open and I run it 2 ways.  GUI Terminal window, and a normal TTY. Obviously i get a little Higher FPS running in a TTY, But not much.
Worth mentioning, at least on the 1101HA the fps depends on the cpu clocking.

> **gunnar123 said:**
> 
sammyboy405 is worthy of high praise for letting us share the cooked meals !

It was my Pleasure.  I figure someone out there is way smarter than I am on this stuff and can take what I Did and Make it better for the GMA 500 user base.

---

### Post by isaidi on 2009-09-09
> **sammyboy405 said:**
> Flash Videos seem to be a Limitation on The Atom Processor and not the GMA500..  Adobe needs to optimize there code a bit more. Ive noticed Youtube works somewhat ok.. Vimeo works ok.. Hulu Lags a bit.

So does this mean Flash video's don't utilize the GMA500? and is simply running in 2D using the Atom processor ?

I am thinking of buying a GMA500 netbook, but questioning the lack of proper support. Specially laggy flash video support. 

Do the steps in this guide help speed up Flash video performance at all ? Is there a way to enable better support for flash video using hardware accelerators in the GMA500 chipset ? xorg options?

---

### Post by _sluimers_ on 2010-01-30
I'm missing openGL support. Does anyone have the same problem as I have?
I use the latest of lucazade's poulsbo drivers.

```
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

---

### Post by mrwoody on 2010-02-04
Hi. 

I own a Dell mini 10. 
Which one do you guys recommend: ubuntu or ubuntu remix? 

**Thanks**

---

### Post by _sluimers_ on 2010-02-04
I'd go for ubuntu, but that's personal taste.

---

### Post by mrwoody on 2010-02-04
> **_sluimers_ said:**
> I'd go for ubuntu, but that's personal taste.

Thanks for your advice. 
Do you know if multi-touch is supported on ubuntu? how about on remix?

---

### Post by _sluimers_ on 2010-02-04
no idea

---

### Post by mikewhatever on 2010-02-04
> **mrwoody said:**
> Thanks for your advice. 
Do you know if multi-touch is supported on ubuntu? how about on remix?

You can scroll up and down with two fingers on Dell mini 10, and that's about it. From what I read in reviews of Windows based models, multi-touch is a joke, and that's no surprise, on such a small touchpad.

---

### Post by mrwoody on 2010-02-04
thanks for your reply. 

> **mikewhatever said:**
> You can scroll up and down with two fingers on Dell mini 10, and that's about it. 


that is with ubuntu or ubunutu remix or both? 

> 
From what I read in reviews of Windows based models, multi-touch is a joke, and that's no surprise, on such a small touchpad.

I don't quite agree with this. I use multitouch all the time, to zoom, scroll up/down and go forward/backward (in a browser).
The only problem is that I hate windows, and I want to get rid of it.

---

### Post by mikewhatever on 2010-02-04
> **mrwoody said:**
> thanks for your reply. 
that is with ubuntu or ubunutu remix or both? 

Both. Ubuntu Remix is just an optimized interface with netbook-launcher and a applet or two. It's the same as Ubuntu proper under the hood. I'd say UNR is slightly less responsive interface wise.


> I don't quite agree with this. I use multitouch all the time, to zoom, scroll up/down and go forward/backward (in a browser).
The only problem is that I hate windows, and I want to get rid of it.

I should have said, 'doesn't work quite well' instead of 'it's a joke'. Scrolling up and down with two fingers is extremely useful indeed, but can you tell me how to apply back and forth in the browser. I don't think zooming in and out and rotating would have been very useful on mini 10, given the size of its touchpad, and that's pretty much what the reviews mentioned earlier pointed out.

---

### Post by mrwoody on 2010-02-05
> **mikewhatever said:**
> 
 but can you tell me how to apply back and forth in the browser. 

Use 3 fingers instead of 2. It is very useful. 

>  I don't think zooming in and out and rotating would have been very useful on mini 10, given the size of its touchpad, and that's pretty much what the reviews mentioned earlier pointed out.

I agree, zooming is not perfect. I usually use 2 different hands, which is not very convenient. What is worse is that it is not very responsive.

---

### Post by mikewhatever on 2010-02-05
No, mrwoody, that doesn't work. There is another neat trick, if you tap with two fingers to open a link in Firefox, it opens in a new tab and not the same one. Same thing applies to folders in the file browser.

---

### Post by pswoo on 2010-02-07
I've searched high and low on the internet and these forums, and it seems like some people have been able to get Ubuntu running on the Dell Mini 10, but I couldn't find any actual/usable instructions on how to do it.

Basically when I'm trying to install Karmic Koala, the screen cuts to black and becomes unresponsive. I've tried doing it in safe graphics mode and with the vga=771 option, but still can't make it to installation (can't even get to the first screen where you choose your language). The same thing happens for the Netbook Remix version.

If I choose 'try without installing', I can make it to the fancy splash page. Then the screen goes black and I get a 'waiting' cursor icon. Nothing happens after this (have let it run for a while).

As I'm manually shutting down, I get some message like "cannot read page..".

Running Ubuntu through Wubi seems to work well, but unfortunately neither the desktop version nor netbook remix was able to detect my wireless card. I guess I would be willing to settle with the Wubi option, if I could get this fixed.

---

### Post by Squalo_ch on 2010-02-07
Hello pswoo,

The first thing to do is to make sure that the installation USB key is good. Have you tried the installation key in any other machine?

---

### Post by mikewhatever on 2010-02-07
Pswoo, here is a link: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#karmic](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#karmic).

---

### Post by pswoo on 2010-02-07
I tried to install using USB on my main laptop, and it didn't work (though I burned a live cd using the same ISO, and it *did* work - but the mini doesn't have a cd drive).

The page I was linked to seems to contain instructions for getting the drivers, given that you've already installed Ubuntu and can run those commands from a terminal, access the net and download the package. I can't do that, since I can't even make it through installation - and Ubuntu isn't recognizing my wireless card anyway, although I guess I could plug in to the wall..

---

### Post by Squalo_ch on 2010-02-07
Hi pswoo,

Since your USB stick does not work on your main laptop, it seem that the problem is there.
I don't know how you created your ubuntu USB key, but I recommend you to give it a try using Unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hope that solves your problem.

---

### Post by pswoo on 2010-02-07
Unfortunately it did not work. Not sure why, but every attempt I've made to boot from a USB has failed (on both the laptop and the netbook).

Here's a summary. I've run disk checks on the USB stick, memory checks on the laptops and they're both fine. I've set up the USB stick using both unetbootin and usb-creator-gtk, and had success with neither. Screen goes blank right after the Ubuntu splash screen (but before the installation process). I've tried this with multiple distributions (Ubutnu 9.10, Netbook Remix, Xubuntu). As I said, on my main laptop (Dell XPS1530) it worked after I conceded to burn a DVD with the image. It's also able to run via Wubi.

Maybe if I get a hold of a portable CD/DVD drive I can get it to run, since that worked on my XPS1530.

Alternatively, I'd be willing to run Wubi - if only I could get it to recognize my wireless card (I guess broadcom chips have been known to be problematic?).

If you have any ideas, I'll try again. I appreciate your help.

Edit: It seems that I can book from my camera's sdhc card! Still not  sure what was going on.. but I'm very happy. Thanks.

---

### Post by findMeAUserNameFittingBjr on 2012-02-07
Hey all!

Yesterday I finally switched to ubuntu on my dell mini 12 (inspiron 1210) :KS. I went to [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell_Mini_12_.28Inspiron_1210.29](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell_Mini_12_.28Inspiron_1210.29) -->
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/) 

in order to find a suitable display driver. So I installed the EMGD 1.8 witch should be working on Oneiric (11.10).

The result is: ubuntu stops while booting by just showing the boot screen. And no further action - the only thing working is ctrl alt del and the "safe mode". Please help me, I'm stuck.

Thank you for your help!

Bjoern.

---

