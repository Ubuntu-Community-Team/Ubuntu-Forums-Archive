---
title: "[SOLVED] Is Openbox heavier than fluxbox"
date: 2008-07-05
forum: Desktop Environments
---

### Post by Inxsible on 2008-07-05
I have noticed that my default setup for Openbox  tends to take more memory than my Fluxbox install.

Openbox is over Arch and on startup, it takes about 46MB

Fluxbox is over Debian and on startup, it takes about 23MB

They both have sshd and conky running on startup. Here are the two ps_mem charts immediately on boot

Openbox:```
 sudo python ps_mem.py 
Password: 
 Private  +   Shared  =  RAM used    Program 

 88.0 KiB +  29.0 KiB = 117.0 KiB    crond
 92.0 KiB +  26.0 KiB = 118.0 KiB    init
 96.0 KiB +  35.5 KiB = 131.5 KiB    portmap
104.0 KiB +  73.0 KiB = 177.0 KiB    hald-addon-acpi
144.0 KiB +  67.0 KiB = 211.0 KiB    xinit
168.0 KiB +  46.0 KiB = 214.0 KiB    famd
228.0 KiB +  20.0 KiB = 248.0 KiB    udevd
136.0 KiB + 113.0 KiB = 249.0 KiB    hald-addon-input
200.0 KiB +  61.5 KiB = 261.5 KiB    dbus-launch
148.0 KiB + 117.0 KiB = 265.0 KiB    hald-addon-storage
164.0 KiB + 109.0 KiB = 273.0 KiB    hald-runner
276.0 KiB +  69.5 KiB = 345.5 KiB    openbox-session
304.0 KiB + 135.0 KiB = 439.0 KiB    agetty (5)
328.0 KiB + 146.0 KiB = 474.0 KiB    dbus-daemon (2)
440.0 KiB +  42.0 KiB = 482.0 KiB    syslog-ng
276.0 KiB + 211.5 KiB = 487.5 KiB    startx
444.0 KiB +  78.5 KiB = 522.5 KiB    login
560.0 KiB +  57.5 KiB = 617.5 KiB    sshd
  1.0 MiB + 144.0 KiB =   1.2 MiB    hald-addon-dell-backlight
848.0 KiB + 599.0 KiB =   1.4 MiB    bash (2)
  1.0 MiB + 537.0 KiB =   1.5 MiB    conky
  1.8 MiB + 227.5 KiB =   2.0 MiB    hald
  3.4 MiB + 301.5 KiB =   3.7 MiB    urxvt
  5.2 MiB +   1.5 MiB =   6.7 MiB    fbpanel
  6.8 MiB +   1.2 MiB =   8.0 MiB    openbox
 16.2 MiB + 561.0 KiB =  16.8 MiB    Xorg
---------------------------------
                         46.8 MiB
=================================

 Private  +   Shared  =  RAM used    Program 
```Fluxbox : ```
 python ps_mem.py
 Private  +   Shared  =  RAM used       Program

188.0 KiB + 184.0 KiB = 372.0 KiB       dhclient3
 88.0 KiB + 328.0 KiB = 416.0 KiB       klogd
316.0 KiB + 220.0 KiB = 536.0 KiB       ssh-agent
156.0 KiB + 448.0 KiB = 604.0 KiB       syslogd
124.0 KiB + 496.0 KiB = 620.0 KiB       anacron
332.0 KiB + 348.0 KiB = 680.0 KiB       udevd
152.0 KiB + 552.0 KiB = 704.0 KiB       init
352.0 KiB + 416.0 KiB = 768.0 KiB       getty (5)
144.0 KiB + 640.0 KiB = 784.0 KiB       xinit
456.0 KiB + 428.0 KiB = 884.0 KiB       dbus-daemon
136.0 KiB + 752.0 KiB = 888.0 KiB       hald-addon-acpi
216.0 KiB + 760.0 KiB = 976.0 KiB       cron
572.0 KiB + 432.0 KiB =   1.0 MiB       sshd
168.0 KiB + 940.0 KiB =   1.1 MiB       hald-addon-cpufreq
184.0 KiB + 940.0 KiB =   1.1 MiB       hald-runner
168.0 KiB + 956.0 KiB =   1.1 MiB       hald-addon-input
240.0 KiB + 896.0 KiB =   1.1 MiB       su
336.0 KiB + 836.0 KiB =   1.1 MiB       login
700.0 KiB + 508.0 KiB =   1.2 MiB       acpid
304.0 KiB + 972.0 KiB =   1.2 MiB       hald-addon-storage (2)
436.0 KiB +   1.0 MiB =   1.4 MiB       startx
488.0 KiB +   1.0 MiB =   1.5 MiB       avahi-daemon (2)
  1.4 MiB +   1.6 MiB =   3.0 MiB       mrxvt-full
  1.9 MiB +   1.1 MiB =   3.0 MiB       hald
  1.3 MiB +   2.0 MiB =   3.3 MiB       conky
  3.6 MiB +   1.4 MiB =   4.9 MiB       bash (3)
  3.3 MiB +   2.7 MiB =   6.0 MiB       fluxbox
  6.8 MiB +   1.0 MiB =   7.9 MiB       Xorg

 Private  +   Shared  =  RAM used       Program

Warning: Shared memory is slightly over-estimated by this system
for each program, so totals are not reported.
```Unfortunately, my Fluxbox install doesn't add up the memory for some reason, but conky tells me 27MB

Could someone shed some light on this?

---

### Post by atomkarinca on 2008-07-05
I think to make a decent comparison you should try both of them on the same distro. In my experience a vanilla Openbox has always been lighter than a vanilla Fluxbox.

---

### Post by urukrama on 2008-07-05
Is the difference noticeable enough to worry about it?

---

### Post by Inxsible on 2008-07-05
> **urukrama said:**
> Is the difference noticeable enough to worry about it?Its a 256MB RAM system, so the additional 20 MB at boot is not a problem. But the moment I start Opera in Openbox or Iceweasel in Firefox, another 60-70 MB are consumed. It is during one of those browsing sessions when I have close to 15 odd tabs open when the additional 20 MB matter.

---

### Post by Inxsible on 2008-07-05
> **atomkarinca said:**
> I think to make a decent comparison you should try both of them on the same distro. In my experience a vanilla Openbox has always been lighter than a vanilla Fluxbox.Yes, I thought about the same thing, that the compare wasn't "accurate" since they were on different distros. But given that Arch is more minimal than a Debian install, I would have expected the opposite.


But then again, I did a business iso install of Debian - so that's pretty minimal as well.

---

### Post by atomkarinca on 2008-07-05
For the Openbox session, you can check /etc/xdg/openbox/autostart.sh and remove the things that you don't need.

---

### Post by urukrama on 2008-07-05
Your Openbox one also has a few additional things running that aren't there in the Fluxbox session (like fbpanel). That makes a difference too.

---

### Post by Inxsible on 2008-07-05
> **atomkarinca said:**
> For the Openbox session, you can check /etc/xdg/openbox/autostart.sh and remove the things that you don't need.I don't use the global autostart at all. Nothing there that I wanted, and my personal autostart only has fbpanel and conky and eval command to set my wallpaper. My fluxbox too has the fbsetbg to set my last wallpaper and conky. 

> **urukrama said:**
> Your Openbox one also has a few additional things running that aren't there in the Fluxbox session (like fbpanel). That makes a difference too.
Yes, but then fluxbox gives its own panel and I definitely need a taskbar so I was trying to compare a usable (for me) environment.

Even if we only compare the two WMs, in the instance that I listed, Openbox takes up 8 MB whereas Fluxbox takes 6MB

I am not trying to nitpick here. Just that I had heard that Openbox was even more minimalist (which it is since no panel - i don't know where else could one go even more minimalistic after Openbox and PekWM) and lighter - which unfortunately, for my installs its not.

Of course I don't know what would happen if I installed both on the same distro. I have a Debian + Xfce install and I am planning to chuck Xfce altogether and try some new WM like awesome or xmonad maybe. I might just try and install Openbox on it and compare if both fluxbox and openbox on debian give me different results.

---

### Post by Inxsible on 2008-07-05
BTW...urukrama, I have checked out your openbox blog and it is really good. Lots of good stuff !

---

### Post by p_quarles on 2008-07-06
Window managers cannot and should not take responsibility for any memory except what they themselves are using. So, the comparison here is really 6 MB vs. 8 MB. 

Also, the Xorg setup on each system is pretty dramatically different -- I'd guess there's a significant difference in the way the two are using memory. There are too many variables there for a direct comparison to give a definite sense of which WM uses less memory at startup.

---

### Post by urukrama on 2008-07-06
Which Openbox version are you using, btw? The latest version (3.4.7) runs lighter on this computer than the older versions did.

I remember testing the difference between fluxbox and Openbox about a year ago. Fluxbox came out lighter then, but the difference wasn't enormous (something like 6 vs 7 MB). That is small enough for me for all the goodness you get in Openbox.

---

### Post by Inxsible on 2008-07-06
> **urukrama said:**
> Which Openbox version are you using, btw? The latest version (3.4.7) runs lighter on this computer than the older versions did.

I remember testing the difference between fluxbox and Openbox about a year ago. Fluxbox came out lighter then, but the difference wasn't enormous (something like 6 vs 7 MB). That is small enough for me for all the goodness you get in Openbox.
Yes i am using the latest 3.4.7 from the Arch repositories.

I guess then it would still be the same as I am getting 6 vs 8 MB.

Can you tell me what's better in Openbox than fluxbox in your opinion? I am new to Openbox, so I would like to know.

---

### Post by basenvironment on 2008-07-06
I would worry about some of the other stuff you are running/using rather than the 2mb difference in *box. And if I wanted something lighter but with certain features I would go with icewm rather than either of those.

---

### Post by urukrama on 2008-07-06
> **Inxsible said:**
> Yes i am using the latest 3.4.7 from the Arch repositories.

I guess then it would still be the same as I am getting 6 vs 8 MB.

Can you tell me what's better in Openbox than fluxbox in your opinion? I am new to Openbox, so I would like to know.

Its themeing options are much more elaborate than Fluxbox', I find its window switching (alt-tab) much better, it tells you when a window is not responding and gives you the option to kill it, if you use GDM you can shutdown or reboot without administrative privileges, etc. The developers have paid a lot of attention to details and options that many users might never notice but that make Openbox stand out. I also find it manages windows better, but that could be very well a subjective judgement. Overall, Openbox just feels more polished to me than Fluxbox.

Give it some time, read through the documentation and don't be afraid to try things out.

---

### Post by Inxsible on 2008-07-07
Alright !!
I gotta take back what I said,

I restarted the machine and logged into Arch and ran ps_mem.py....I got Openbox using 2.7 MB. Its freaking awesome. Even fbpanel is taking up twice as much as Openbox. 

I guess, Openbox, Fluxbox and IceWM all range anywhere between 2-10 MB. So you cannot really judge them by comparing one instance.

Here's my new ps_mem.py for Openbox ```
bash-3.2# python ps_mem.py 
 Private  +   Shared  =  RAM used	Program 

 88.0 KiB +  27.0 KiB = 115.0 KiB	crond
 92.0 KiB +  25.0 KiB = 117.0 KiB	init
100.0 KiB +  34.5 KiB = 134.5 KiB	portmap
100.0 KiB +  71.0 KiB = 171.0 KiB	hald-addon-acpi
140.0 KiB +  72.0 KiB = 212.0 KiB	xinit
168.0 KiB +  46.0 KiB = 214.0 KiB	famd
136.0 KiB + 111.0 KiB = 247.0 KiB	hald-addon-input
228.0 KiB +  20.0 KiB = 248.0 KiB	udevd
156.0 KiB + 100.0 KiB = 256.0 KiB	su
148.0 KiB + 115.0 KiB = 263.0 KiB	hald-addon-storage
160.0 KiB + 107.0 KiB = 267.0 KiB	hald-runner
272.0 KiB +  63.5 KiB = 335.5 KiB	openbox-session
356.0 KiB +  28.0 KiB = 384.0 KiB	dbus-daemon
312.0 KiB + 130.0 KiB = 442.0 KiB	agetty (5)
280.0 KiB + 172.5 KiB = 452.5 KiB	startx
356.0 KiB + 115.0 KiB = 471.0 KiB	login
436.0 KiB +  41.0 KiB = 477.0 KiB	syslog-ng
552.0 KiB +  57.0 KiB = 609.0 KiB	sshd
  1.0 MiB + 142.0 KiB =   1.2 MiB	hald-addon-dell-backlight
  1.0 MiB + 539.5 KiB =   1.5 MiB	conky
  1.2 MiB + 635.5 KiB =   1.9 MiB	bash (3)
  1.8 MiB + 220.0 KiB =   2.0 MiB	hald
  1.5 MiB +   1.1 MiB =   2.7 MiB	openbox
  3.4 MiB + 296.5 KiB =   3.7 MiB	urxvt
  5.1 MiB +   1.5 MiB =   6.6 MiB	fbpanel
 16.1 MiB + 578.5 KiB =  16.6 MiB	Xorg
---------------------------------
                         41.5 MiB
=================================

 Private  +   Shared  =  RAM used	Program 
```

---

