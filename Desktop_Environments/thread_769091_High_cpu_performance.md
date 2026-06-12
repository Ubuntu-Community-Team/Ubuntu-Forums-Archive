---
title: "High cpu performance"
date: 2008-04-26
forum: Desktop Environments
---

### Post by Giannis_ on 2008-04-26
Hi! My problem is that the performance of my computer is very bad. It reacts very slow in all aplications, even in browsing files. I opened the system monitor and saw that the cpu usage after a restart was 20% - 30% with no program running. The pc is up to date and I use ubuntu 8.04. I hoped that the problem would not exist after I upgrated from 7.10 but it still does.
My cpu is a pentium 4 at 2.4 GHz with 768 Mb of ram. :confused:

---

### Post by inferiorwang on 2008-04-26
Have you changed your visual effects settings?

Go to System->Preferences->Appearance and click on Visual Effects.  Set it to none and see if that helps.  Once I changed that, my desktop got much quicker.  Translucent terminals will also suck up processing power.

---

### Post by inferiorwang on 2008-04-26
edit: oops...double post

---

### Post by Giannis_ on 2008-04-27
Thanks for the answer. I changed it but it didn't help.. I have only firefox and thunderbird open and the processor usage doesn't reach below 25%. :(

---

### Post by evozniak on 2008-04-27
After reboot is wrong says "no process running"
Linux estrucuture is complex, idle system heave many daemons in background, networking, sound, X11, daemon to acess your filesystem ext3 and many things to count.

Hint: try to full disable AIGLX from xorg.conf and post results

---

### Post by Kaparen on 2008-04-27
Open the console, write 'top' and check which process that is taking up cpu %.

---

### Post by nullmind on 2008-04-27
Hi, sorry you had so much up problems with the update :(

Check [this article]("http://devangelist.blogspot.com/2008/04/firefox-30-and-xorg-high-cpu-usage.html") I made (or see my signature) for info about how a Firefox 3.0 bug with Xorg causes a lot of CPU usage to occur.

1.) Did you install fresh or upgrade?
2.) What wireless driver are you using? If you need to know you can right click the wireless icon in the notification area (top-right by default) and select "Connection Information". It's listed as **Driver**.
3.) Are you playing music and using PulseAudio? If you want to try disabling PulseAudio, open Synaptic Package Manager (System->Admin.) and remove the **pulseaudio** package. Then press Alt+F2 and execute **gstreamer-properties** (remember you can press tab in the dialog to auto-complete text). Select a different **Plugin**, such as ALSA, for the **Default Output**. Restart any applications using sound, such as Rhythmbox.
4.) If you're using an **Intel Graphics** card (such as most notebooks that don't have an Ati/Radeon or nVidia/Geforce logo somewhere), using desktop effects and using 24-bit color depth. Attach your **/etc/X11/xorg.conf** configuration.

I think we're going to need a lot more info to figure out where the CPU usage is coming from.

When this happens, or in a session after it has been happening, open a terminal (Applications->Accessories->Terminal) and execute the following command and then attach **process.times** to this thread.

```

ps -e > ~/Desktop/process.times

```

---

### Post by willywongi on 2008-05-05
I'm experiencing some strange gaps while using a fresh install of Hardy: sometimes emesene and firefox stall for some 30secs, with a high cpu usage. After a while everything run smooth as it should be (centrino duo / 2gig ram). Something strange happens in Skype 2 for Linux: when I start it the window shows up but it freezes. After a while (with high cpu usage) it sort of "pops", playing all the sounds at once (ie.: startup sounds, missed messages/calls sounds, etc). So I thought the new audio system could be the culprit. Do you have any more info about it?

---

