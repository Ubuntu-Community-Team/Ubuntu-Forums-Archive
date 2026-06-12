---
title: "Ubuntu 7.10 on a Latitude D530"
date: 2008-02-28
forum: Dell  Ubuntu Support
---

### Post by SergeantPepper on 2008-02-28
I got a new job where they use a lot of open source software. They gave me a new Dell Latitude D530 to use and I thought I'd embrace the open source spirit and dive right in and install Linux on the machine. Setup went all right but I've had a few issues remaining.

When I first booted up I didn't have any sound. A Google search led me to this [site (http://users.piuha.net/martti/comp/d630/) ]("http://users.piuha.net/martti/comp/d630/") and after following the instructions and rebooting my sound was working perfectly.

That was the good news. The bad news is I have two main issues that are big productivity hits. The first is Ubuntu doesn't recognize my Wifi card. No Wireless option is listed my Network Manager and Ubuntu says I don't need any restricted drivers. I tried to follow the advice of installing wicd from this [thread (http://ubuntuforums.org/showthread.php?t=619746)]("http://ubuntuforums.org/showthread.php?t=619746") but it didn't help. They mentioned that there are different types of WiFi card and solutions vary depending on cards, but I don't even know where to begin and find out what card I have.

Second issue is that I use an external monitor for most of the day and I can't get Ubuntu to change resolution from the latptop's standard 1024x768 to the monitor's 1400x1050. Every time I try to change resolutions in System->Administration->Screens and Graphics the window either crashes or Ubuntu starts up in fugly 640x480 resolution. I think all this resolution meddling made Ubuntu think I am now running a generic VESA graphics card, at least according to the Graphics Card tab of Screens and Graphics.

Even with these problems Ubuntu has had its saving graces. Evolution is a great app and I prefer it over Outlook on Windows and Thunderbird. FYI, I've had GUI issues with Thunderbird when I install the Lightening extension. I works well on Windows. Go figure. Also, virtual desktops have been very helpful in organizing my desktop/brain, but Ubuntu's best feature is the Synaptic Package Manager. Auto updates and nearly every program you'll ever need, I am now spoiled by it. Anyway, if anyone has had similar experiences and can point me towards solutions to my problems that would be greatly appreciated. Thanks.

---

### Post by dennytharian on 2008-03-30
Did you get a solution for the laptop display resolution  issue ..

---

### Post by librarian on 2008-04-16
> **SergeantPepper said:**
> Ubuntu doesn't recognize my Wifi card. No Wireless option is listed my Network Manager and Ubuntu says I don't need any restricted drivers. I tried to follow the advice of installing wicd from this [thread (http://ubuntuforums.org/showthread.php?t=619746)]("http://ubuntuforums.org/showthread.php?t=619746") but it didn't help. They mentioned that there are different types of WiFi card and solutions vary depending on cards, but I don't even know where to begin and find out what card I have.


I'm setting up a Latitude D530 for a nonprofit office. I got the Broadcom 4328 wifi working by following the instructions at [thread (http://ubuntuforums.org/showthread.php?t=297092)]("http://ubuntuforums.org/showthread.php?t=297092").

You can get your wireless device name by browsing System > Preferences > Hardware Information OR using terminal with the command lspci and looking for something 802.11 something.

Thanks for the audio pointer!

---

