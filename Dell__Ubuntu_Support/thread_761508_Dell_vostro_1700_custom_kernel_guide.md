---
title: "Dell vostro 1700 custom kernel guide"
date: 2008-04-21
forum: Dell  Ubuntu Support
---

### Post by kimbuba on 2008-04-21
Hi to all,
i've written a mini-guide to make dell vostro 1700 working 100% with ubuntu 7.10

Here's the url 

[http://alerttail.sourceforge.net/dellvostro1700/](http://alerttail.sourceforge.net/dellvostro1700/)

among things that work: sound, mic, webcam, 3d, wifi-N...


It is based to a custom kernel configuration (based on vanilla 2.6.24).
Configuration include statically vostro 1700 hardware drivers; this way bootup is faster and memory footprint lower.

waiting for your feedbacks.

Hope it helps.
(it will be linked by [http://www.linux-laptop.net/](http://www.linux-laptop.net/) for reference)

---

### Post by jimisdead on 2008-04-27
I'm running 8.04 on a Vostro 1700 and the microphone doesn't work... everything else seems to work fine.

I see no point in compiling a vanilla kernel when the ubuntu one works well, so would you be able to tell me what needs to be changed to just get the microphone working - it would be most appreciated.

Thanks.

---

### Post by kimbuba on 2008-04-28
Hi jimisdead,
you are right, there's no need to compile a new kernel since all (now on 8.04) works quite well.
You would compile it if you expect to gain in performances.

For the Mic i suggest you to open gnome-sound-recorder and then play with
alsamixer (sudo alsamixer from console)

From there you should unmute channels, change input (analog to digital) and play with capture settings (F4 and F5 to swich different channels)

than try recording some sound with gnome-sound-recorder.

Kim

---

### Post by nue-- on 2008-05-24
I was able to get sound recording to work by just starting

sudo alsamixer

and changing the rightmost item ("Digital input source") from Analog 1 to Digital (arrow up).
This worked for my Vostro 1700, Hardy.

Thanks a lot!

---

### Post by nlarson on 2008-06-22
I just got 8.04 installed on my Vostro 1700.  One of my main issues is my wireless doesn't seem to want to connect.

I run sudo lshw -C network and get this...
```

  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:26:3a:95:92
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```
Why would it be disabled...but more importantly...how do I enable this interface?

Thanks for your help...

-- Nick

---

