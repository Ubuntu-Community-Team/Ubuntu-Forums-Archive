---
title: "Screen does not display in desktop"
date: 2007-04-28
forum: Desktop Environments
---

### Post by Green-e on 2007-04-28
I installed the server cd and installation worked fine, was able to see the command line. I then ran an apt-get update, then an apt-get install linux-generic and ubuntu-desktop. installation worked fine. When I rebooted the Ubuntu progress bar came up, loaded 100%. The screen flickered and then nothing. My pc made a sound though. So I rebooted a few times, still nothing. I then had the thought of entering my username and password. I think it booted up because I could hear like an intro sound (I'm assuming that it booted in, I have never used ubuntu desktop before).

So there seems to be a problem with my video card!?! I don't even know what it. it's an old compaq computer (2002-2003?!?), so it may need a new driver?

I modified the xorg.conf file to display at 640x480, just in case.

Any idea's or help would be much appreciated.

---

### Post by hellblade on 2007-04-28
Can you put your "/var/log/Xorg.0.log" and "/etc/X11/xorg.conf" files here?

---

### Post by Green-e on 2007-04-29
I'd have to set up samba, to connect to my windows machine. I viewed the Xorg.0.log file and noticed the following:

(EE) AIGLX: Screen 0  is not DRI capable.


/etc/X11/xorg.conf contains the following

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
Default Depth 24
SubSection "Display"
Depth 1
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "800x600" "640x480"
EndSubSection
EndSection

Hope this helps.

Will setup samba later and see if I can get those files.

Thanks for the help

---

### Post by Green-e on 2007-04-29
Here's the files
[URL="http://wngreenway.googlepages.com/xorg.conf"]
http://wngreenway.googlepages.com/xorg.conf[/URL]

[http://wngreenway.googlepages.com/Xorg.0.log]("http://wngreenway.googlepages.com/Xorg.0.log")

---

### Post by hellblade on 2007-04-30
The log leads to a 404.
> The page you have requested could not be found. (404)

***Edit: **I just noticed... the right link is [http://wngreenway.googlepages.com/Xorg.0.log]("http://wngreenway.googlepages.com/Xorg.0.log")*

---

### Post by hellblade on 2007-04-30
Could be the current generic VESA driver. What card do you have?
Maybe installing another driver for your card would fix the problem.

---

### Post by Green-e on 2007-04-30
Sorry, how do I check the video card?

Also can you point me to a web site that has all the bash command line tools and what they do.

Thanks

---

### Post by hellblade on 2007-05-01
Try ```
lspci | grep VGA
``` in a konsole/terminal window. This should tell you which card you have.

As for the bash, have a look here [http://tille.xalasys.com/training/bash/](http://tille.xalasys.com/training/bash/)
Some of the most common commands are cd, mkdir, ls, grep, cat, less, nano...
Try "man COMMAND" in a konsole to see the COMMAND's manual. Also if you want to take a quick look at their usage try the --help parameter (e.g. "nano --help")

---

### Post by Green-e on 2007-05-01
Thanks mate, did a bit of unix stuff back in college, it's slowly starting to come back to me, thanks for the tips.

This is the result of the lspci
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)

I'm guessing I'll need to update the driver for it???

---

### Post by Green-e on 2007-05-01
Found a couple of drivers on the intel site, now how the heck do I install them?

I've upacked one which is a source. I'm guessing I need to compile it ???

My understanding is that once compiled, I run it, which then updates the driver, so I do a reboot and apt-get install the ubuntu-desktop again.

The is another one which is an rpm. In the release notes it talks about xfree and some agpgart kernel module. Don't think I've got xfree installed, how do I check.

Here's the link to the [download]("http://downloadcenter.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")

Currently I'm accessing the server on my windows laptop via putty.

Thanks again for your help, feeling like an absolute nooooooob!!!

---

### Post by hellblade on 2007-05-02
No need to install the driver from intel's site. First try using the open source one provided with Ubuntu.
Edit your /etc/X11/xorg.conf and under the Device section, change Driver from vesa to i810.
You can now start/restart your X with ```
sudo /etc/init.d/gdm restart
``` (replace gdm with kdm if you use kde)

---

### Post by Green-e on 2007-05-03
It worked !!!!

Woooooo!!!

Thanks for all your help :)

---

### Post by hellblade on 2007-05-04
np. have fun with your box:)

---

