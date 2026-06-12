---
title: "nVidia driver purgatory"
date: 2009-01-16
forum: General Help
---

### Post by earther on 2009-01-16
Last week my trusty Samsung monitor bit the dust.  Went to Fry's and got a 22" LG W2234S.  Came home plugged it in, tweaked xorg and all was well including Compiz . . . until this morning.  After an fsck at boot, I was in low graphics mode.  :(

I have been trying all day to straighten this out.  Every time I try to enable the nVidia driver to get Compiz working, it goes back to low graphics mode at reboot.  :( :(

Replaced xorg with the last working version but no joy.  Every time I run sudo dpkg-reconfigure -phigh xserver-xorg, it reverts to the nv drivers which gives me the right resolution 1680x1050 but no Compiz so the windows are UGLY and scrolling is a bit wacky etc.

I ran compiz-check:

```
~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8400 GS (rev a1)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install the proper driver for your graphics card.

Check if there's an alternate (proprietary) driver available? (Y/n) y
```


When I enable the alternate driver, I'm right back to low graphics mode at reboot.

Any clues as to what's going on?  I have a feeling I'll have to bite the bullet and upgrade to Hardy to get this working again.  *sigh*  Currently using a Hardy kernel on Gutsy and am thinking that might be the problem.

Any ideas??  Thanks.

---

### Post by balaknair on 2009-01-16
It could be that the nVidia kernel module you've got installed, the custom kernel and Xorg settings do not match.

What I'd suggest is completely removing the proprietary nVidia drivers, preferably with something like 'envy', and then reinstall the proprietary drivers(either via synaptic, the proprietary drivers manager or envy, or by getting the latest nVidia 180.22 drivers from the nVidia site and manually installing). The new drivers run like a dream on my box(Ubuntu 8.10, 8400-GS rev a1 just like your card).
In either case you might want to see if DKMS(dynamic kernel module support) is installed(just sudo apt-get dkms), since this can ease things related to kernel modules and updates quite a bit.

Why not just upgrade to 8.10 Intrepid, I find it to be a pretty great improvement over Gutsy(and Hardy as well).

---

### Post by earther on 2009-01-16
> **balaknair said:**
> It could be that the nVidia kernel module you've got installed, the custom kernel and Xorg settings do not match.
I'm suspecting something like that.

> The new drivers run like a dream on my box(Ubuntu 8.10, 8400-GS rev a1 just like your card).
That's encouraging.  I have been uninstalling and reinstalling all day but no joy.

> In either case you might want to see if DKMS(dynamic kernel module support) is installed(just sudo apt-get dkms), since this can ease things related to kernel modules and updates quite a bit.
Installing as I write.

> Why not just upgrade to 8.10 Intrepid, I find it to be a pretty great improvement over Gutsy(and Hardy as well).
Because there are [issues with dialup connection on Intrepid]("https://bugs.launchpad.net/ubuntu-doc/+bug/310331") - pon/poff etc. doesn't work properly.  Developers seem to have forgotten not everyone is connected to a big, fat pipe.[/QUOTE]

---

### Post by RJARRRPCGP on 2009-01-16
> **earther said:**
> 


When I enable the alternate driver, I'm right back to low graphics mode at reboot.


Install the kernel headers.

---

### Post by balaknair on 2009-01-17
The latest drivers can be downloaded from:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)



Chances are it's not uninstalling the older versions completely or isn't getting the correct precompiled modules from the repos.

To uninstall the old drivers safely:

ctrl-alt-F1 to get to text console--> Login with your user name and password

Stop the Xorg GUI
```
sudo /etc/init.d/gdm stop
```

Remove the Old drivers with envyng-
```
sudo apt-get install envyng-core
sudo envyng -t
```

Use the envyng text based utility to uninstall the driver.

Add the medibuntu repositories to your sources list
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Install the driver and necessary packages
```
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install nvidia-glx-180
```

After it's done, restart the GUI
```
sudo /etc/init.d/gdm start
```

Things should be working at this point.

---

### Post by earther on 2009-01-17
Thanks to all who have offered suggestions.

balaknair . . . it's my understanding that I can't use envyng with Gutsy.

I also don't know whether I can maintain a dialup connection in the  ctrl-alt-F1  text console.  Seems it failed lst time I tried.

Is there an alternate way to do this on Gutsy (with a Hardy kernel).

---

### Post by balaknair on 2009-01-17
Yes, that's right. With Gutsy you have to use 'envy legacy'(you can download the envy legacy .deb file from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Dial up connection: I honestly have no idea about using dial up from the console, though I think it can be done(with wvdialconf perhaps?). 

To be on the safe side, you can just download and install the packages build-essential and linux-headers while still logged in to the GUI, and envy as well. Use the nVidia driver installer package since this will compile a new kernel module to fit your kernel.

So change the order of steps to:
1) within the GUI
--- download envy and install it from the link given above.
--- download the appropriate driver from the nVidia website and save to your /home folder(don't install yet).
--- install the kernel headers ( *sudo apt-get install build-essential linux-headers-`uname -r`* )

2) Now exit the GUI and login to the console(Ctrl-Alt-F1)
--- sudo /etc/init.d/gdm stop
--- Use envy to uninstall the old drivers( sudo envy -t)
--- Install the NVIDIA 180.22 drivers (sudo sh ./NVIDIAxxx.run)
[I]TIP: instead of typing the full filename, just type in the command up to ./NV and then hit 'Tab', the file name will autocomplete.
[/I]
Use the default options for each step of the installer program,except for the last step-when it ask you if you wan it to automatically configure Xserver or xorg(something like that)- choose 'YES' for this option.

--- Restart the GUI with sudo /etc/init.d/gdm start
--- Reboot the system

Additional points:
Be aware that kernel updates can break the custom nVidia modules, so keep the driver installer handy(keep it in your /home folder for easy access). If you have to do a kernel update and lose the GUI, just reboot into recovery mode, log in to the text console with your username and password, and run the following command *sudo sh NVIDIA* -K*
Remember that the driver installer package downloaded from the nVidia website must still be available in your home folder(Don't delete it).

---

### Post by earther on 2009-01-18
Progress report . . . first I deleted all nVidia drivers per your excellent instructions.  Then opened the console and tried to install the 169.07 and 180.22 drivers from the nVidia site. Neither would compile correctly and I think that is the problem. I suspect the only thing that will fix this is a clean install. Here's the relevant part of the nvidia-installer.log:

> Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)

[EARTHER'S NOTE:  I didn't have an internet connection up but even when I did, it couldn't find a match.  So this time I just skipped it.]

-> No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.2) does not exactly match the current compiler (gcc 4.1).  The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel.

[EARTHER'S NOTE:  I couldn't find gcc4.2 in either the Gutsy or Hardy repos.  If you know of a way to get it please let me know.]
   
   If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation.  Otherwise, select "Yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation.  Abort now? (Answer: Yes)


[EARTHER'S NOTE:  Previously when I let it go ahead, it didn't work so why do it again.]

ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

Any other ideas or is this a dead end.

---

### Post by Leo Dragonheart on 2009-01-18
This is what helped me with my Nvida whoooos...



I've had the exact same problem with NVIDIA cards and the restricted driver. I searched for months to find an answer and I must tell you it was a painful runaround. The good news is I was able to fix it easily, simply by manually editing my xorg.conf file. In my case the problem was not with the NVIDIA driver at all. The problem was that my monitor was not correctly recognized by the X-server system. Once I identified my monitor specs in the xorg.conf file, everything worked perfectly. This is how I did it.

First you need to open your xorg.conf file in Gedit, like this:

Go to main menu, accessories, then terminal...

Code:

**sudo gedit /etc/X11/xorg.conf**

You'll have to enter your password to gain editing privileges.

Some say you should back up the file first, but I found gedit does this automaticaliy, and right now your original file isn't doing you much good anyway.

Next, you have to add a few lines to specific sections of your xorg.conf file. BUT DO NOT CHANGE ANYTHING ELSE!

In the Monitor section add the lines that appear in bold:
Code:

Section "Monitor"
    Identifier     "Configured Monitor"
   [B] HorizSync       31.0 - 65.0
    VertRefresh     51.0 - 90.0[/B]	
EndSection

Note that these are the specs that fit my particular monitor. They'll probably work for yours also - but if you want to you can replace the VertRefresh and HorizSync values with your monitor's actual data if you know what they are.

Next, in the Screen section add the lines that appear in bold, right before the EndSection line.

Code:
[B]
    SubSection     "Display"
        [Depth       24
        Modes      "1280x1024_60"
    EndSubSection[/B]

This set my monitor to my desired resolution which is 1280X1024. You can substitute the resolution data to suit your needs. Reboot your computer and you should have a high resolution display. Next, you should run the NVIDIA settings program to fine tune your system.

If this doesn't work, then you can boot in recovery mode and select the fix x-server option. This will give you a high resolution display but no special effects, etc.

I hope this helps.

---

### Post by balaknair on 2009-01-18
GCC 4.2- is available 
in the gutsy repos- version 4.2.1
[http://packages.ubuntu.com/gutsy/gcc-4.2](http://packages.ubuntu.com/gutsy/gcc-4.2)

in the hardy repos- version 4.2.3
[http://packages.ubuntu.com/hardy/gcc-4.2](http://packages.ubuntu.com/hardy/gcc-4.2)

I'm not sure just how installing GCC 4.2 will work out for you though, since some dependencies might not be installable without breaking something you already have on your modded gutsy(the default version on Gutsy is 4.1.2, and on Hardy 4.2.3, but apparently 4.2.1 is available on Gutsy). It might install without problems, but it's not 100% certain.

What I'd suggest--> Back up all important data on your computer, then try 
sudo apt-get install gcc-4.2 
This will get you GCC 4.2.1 if you're using the Gutsy repos.

**OR**

Get the gcc-4.2.3 deb package from [http://packages.ubuntu.com/hardy/amd64/gcc-4.2/download](http://packages.ubuntu.com/hardy/amd64/gcc-4.2/download) (if you use 64 bit Ubuntu) or [http://packages.ubuntu.com/hardy/i386/gcc-4.2/download](http://packages.ubuntu.com/hardy/i386/gcc-4.2/download) (if you use 32 bit Ubuntu)
What I'm unsure of is whether all the dependencies will also be satisfied.

Worth a shot, though. If dependencies are not satisfiable, the installer will simply abort, so it's probably not too risky.

---

### Post by earther on 2009-01-18
Thanks for the additional suggestions but hopefully no need to follow up on them.

It's a miracle . . . I'M UP AND RUNNING!!! Out of low graphics mode, nVidia driver enabled and Compiz is working.  So happy to have the cube and window management back.

Here's what I did.  After removing all previous nVidia drivers etc., just I let Envy do the install via console - I understand that's a bit of a deal with the devil but it worked.  It doesn't want to keep 1680x1050 resolution setting but I just added it to the xorg.conf.  Keeping fingers crossed at the next reboot.

Really appreciate all the suggestions and hand holding.  Will let you know if it's still working in the morning.  :)  I'm sooooo happy!!!

---

### Post by balaknair on 2009-01-18
Great. :D

Wishing you luck.
Have fun.

---

### Post by earther on 2009-01-18
Everything is still working this morning including the appropriate resolution.  YEA!!  Thanks for your help, balaknair.  Couldn't have fixed things without it.

---

### Post by balaknair on 2009-01-18
Glad to help. :D

Could you please mark this thread as solved then?
(At the top of the thread, on the right side-> Thread Tools> Mark Thread as solved)

It'd help others who might have similar trouble find it easily.

Thanks.

---

### Post by earther on 2009-01-18
> **balaknair said:**
> Could you please mark this thread as solved then?
(At the top of the thread, on the right side-> Thread Tools> Mark Thread as solved)
I would if I could.  [IMG]http://www.eartherdesigns.com/ss/nosolved.gif[/IMG]

I'm also not seeing the thank you button.  Maybe I need to check my user preferences.

---

### Post by balaknair on 2009-01-18
Hmm that's OK then. :D

I guess there's something the matter with the Ubuntuforums site, these past few days it's been really weird, servers were down a lot, kept getting disconnected/logged out, I'd be typing a long post with a fair amount of formatting, click 'submit reply' and I'd get a 404 error, and have to type it all in again. And I saw the 'Thanks' button is nowhere to be found when I tried to thank someone the other day. Now it seems the 'Mark as Solved' option is gone as well.

Server/site maintenance going on? Major redesign?
I'm not sure, but I do hope things get fixed soon.

---

### Post by frisket on 2009-10-26
> **earther said:**
> Every time I try to enable the nVidia driver to get Compiz working, it goes back to low graphics mode at reboot.

I want exactly the reverse, and I can't find any pages about it at all. I tried to upgrade from 8.04 to 8.10 on a system with a Geforce4; the docs said as it wasn't supportable  the binary drivers, the old nv driver would be used.

It lied: 8.10 went right ahead and installed a new driver, so the system hangs hard when it gets to the login screen.

I want to back out and revert to the nv driver. It's only 1024x768 but I don't use or want 3D graphics or TV-out, and the nv driver installed with 8.04 was working fine.

How do I revert this setup with 8.10 (and eventually 9.04)?

---

