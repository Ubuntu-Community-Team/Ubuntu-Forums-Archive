---
title: "recordmydesktop and nvidia"
date: 2010-09-05
forum: Desktop Environments
---

### Post by Cavsfan on 2010-09-05
> **xtracool_protik said:**
> Hey Cavsfan,
 I don't have exact same hardware so I may be wrong (or shooting in dark) here but as per my knowledge the drivers u r using r open source drivers.
 If u have 32 bit Ubuntu installed I would say install [http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html) drivers from that link
 else if u r interested in bleeding edge open source drivers (sometime may go wrong as very much in development phase) look at [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

I wasn't apparently paying enough attention as the link I mentioned found driver 256.52 and when I 
looked at the real nVidia site you mentioned it had version 256.53 so now I have the absolute latest version installed. 
I had to find the 64 bit version though, but that was easy.
And this is amazing as I only ever used the 185 version that came with Ubuntu! At first it wouldn't install and I found 
that you have to stop the x server, etc. but, I found this link that worked perfectly 
[[COLOR=blue]_http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html_[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
I am still wondering how to get my "NVIDIA X server settings" back under System > Administration, but found 
if I enter "nvidia-settings" in a terminal it shows up fine.
:idea:
While I was entering this I got it back by adding a new option in System > Preferences > Main Menu. So, I am good to go!

I noticed you entered a command line for gtk-recordmydesktop, could you share that? I tried it with the 256.52  driver and still had some flickering.
So, I now know it is something I am doing wrong.

---

### Post by Cavsfan on 2010-09-10
Still getting flicker while recording my desktop with an ffmpeg command. I have the power, but am wondering 
if my monitor's max refresh rate could be causing the problem. It is 60hz and it shows to be 59.95hz at the present time.
It is an LCD and I am used to seeing 80hz on regular monitors.

**xtracool_protik**,  what ffmpeg command did you use to do that awesome video on post # 134 of this thread?

I used this tutorial to update ffpmeg [[COLOR=blue]_HOWTO: Install and use the latest FFmpeg and x264_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

Thanks!

---

### Post by xtracool_protik on 2010-10-06
Hey Cavsfan,
 Sorry for some reason I didn't get an update for posts anyway I've installed gtk-recordmydesktop from synaptic and used command as gtk-recordMyDesktop

---

### Post by Cavsfan on 2010-10-06
> **xtracool_protik said:**
> Hey Cavsfan,
 Sorry for some reason I didn't get an update for posts anyway I've installed gtk-recordmydesktop from synaptic and used command as gtk-recordMyDesktop

Thanks for getting back with me. Didn't you use any options with the command?
Because at the end of the video, I noticed you typed in killall or something.
I upgraded to Maverick now and haven't tried anything yet, but even a screenprint 
of the cube rotating produces some strangeness as it did on Lucid.

---

### Post by xtracool_protik on 2010-10-06
Yes I used killall recordmydesktop, thats cause for some reason I don't get gtk-recordmydesktop icon in my taskbar. And I guess if its issue with every screen casting application then probably frequency of ur monitor is not set properly, however before changing it I hope u know how to switch it back from ur BIOS (coz for wrong setting u'll have to revert from BIOS settings)

---

### Post by Cavsfan on 2010-10-06
> **xtracool_protik said:**
> Yes I used killall recordmydesktop, thats cause for some reason I don't get gtk-recordmydesktop icon in my taskbar. And I guess if its issue with every screen casting application then probably frequency of ur monitor is not set properly, however before changing it I hope u know how to switch it back from ur BIOS (coz for wrong setting u'll have to revert from BIOS settings)


Thanks! My only setting is 60hz at least that is all I have seen and I know that it the max.
It is a Hanns-G LCD 28" monitor 1920x1200 1080p monitor. I am amazed that it cannot go 
higher than 60hz as I am used to seeing 80hz on old CRT type monitors like my last one.
Oh well!

---

### Post by xtracool_protik on 2010-10-06
I have never seen Vertical sync. to be more than 60Hz but I've seen  only few monitors.
 I would suggest - if u can get ur hands on another machine (different hardware config) but same software setup, try it on that one, so that u can differentiate whether its hardware/driver issue or u r missing something related to software

---

### Post by Cavsfan on 2010-10-06
> **xtracool_protik said:**
> I have never seen Vertical sync. to be more than 60Hz but I've seen  only few monitors.
 I would suggest - if u can get ur hands on another machine (different hardware config) but same software setup, try it on that one, so that u can differentiate whether its hardware/driver issue or u r missing something related to software

It might just be a setting maybe there is a Vertical Sync setting that I have turned off.
I'll just play with it a bit. 
Thanks!

---

### Post by xtracool_protik on 2010-10-06
Sure, let us know how does it go :)

---

### Post by overdrank on 2010-10-06
I have moved your post to its own thread. Thanks :)

---

### Post by Cavsfan on 2010-10-07
> **overdrank said:**
> I have moved your post to its own thread. Thanks :)

Thank you!!! :)

---

