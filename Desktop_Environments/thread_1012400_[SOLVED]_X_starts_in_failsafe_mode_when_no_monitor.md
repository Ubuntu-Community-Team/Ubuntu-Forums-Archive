---
title: "[SOLVED] X starts in failsafe mode when no monitor is attached."
date: 2008-12-15
forum: Desktop Environments
---

### Post by Memfis on 2008-12-15
Hi,

I'm familiar with debian and have been running it as a server OS for many years. I took the leap and setup an Xubuntu 8.10 server.

The problem I have is that when no monitor is plugged in locally X starts in failsafe mode.

I want to run this as a headless box which I will vnc into.

What is the best way to prevent X starting in failsafe mode when no monitor is detected?

How can I prevent X or whatever from checking if a monitor is attached?

Lastly I'd like to thank mschemerii in the irc chatroom for attempting to help me, and breaking his own install of X at the same time. I hope he's OK as I've not heard back in several hours.

[edit] I'm not sure if this should be in desktop or install section. Please feel free to move thread if I've done it wrong.

---

### Post by Memfis on 2008-12-15
List of running X processes :

/usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf

xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

/usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

/bin/bash /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm

zenity --warning --text <big><b>Ubuntu is running in low-graphics mode</b></big>\n\nThe following error was encountered.  You may need\nto update your configuration to solve this.\n\n(EE) intel(0): No valid modes.?(EE) Screen(s) found, but none have a usable configuration.

---

### Post by Memfis on 2008-12-15
Sorry to keep replying to my own thread.

I've looked at the failsafe log and nothing jumps out.

Could I edit /etc/X11/xorg.conf.failsafe with some default values so that X starts ok?
Would doing this mean that when a monitor is plugged in the standard xorg.conf works, and when there's no monitor the failsafe settings take effect so that I can vnc to a working desktop?

---

### Post by louistan3 on 2008-12-15
I dont see why it would matter if the monitor is plugged in or not.

It shouldn't care if there is a monitor, maybe there's another problem? when you plug the monitor and boot, does it still go into failsafe?

someone who knows a bit better should reply. :S

---

### Post by Memfis on 2008-12-15
Booting with a monitor plugged in starts X/gdm/xfce normally.
After which vnc works fine.

---

### Post by louistan3 on 2008-12-15
ooh, have you tried booting without the monitor then plugging it in after the boot up and seeing if its failsafe or not? check it locally cause it might only be on failsafe mode when on vnc.

---

### Post by Memfis on 2008-12-15
If I boot without the monitor, then plug it in, xorg still runs in failsafe mode.
If I boot with the monitor plugged in, xorg starts normally and will continue when the monitor is unplugged until next reboot.

It's the boot time / xorg startup detection thats the problem.

Good night, back in 10 hours or so.

---

### Post by Memfis on 2008-12-16
Adding driver=vesa to the device section allows X to start :

Section "Device"
        Identifier      "Configured Video Device"
        Driver "vesa"
EndSection

We're getting there, now to figure out the VertRefresh & HorizSync for 1024x768*24 and where to put it in the xorg conf.

---

### Post by louistan3 on 2008-12-16
if i remember correctly, the new xorg system doesnt use the xorg.conf file anymore. 

Can anyone clarify this?

---

### Post by louistan3 on 2008-12-16
i just found this..

[https://help.ubuntu.com/community/XORGHardy]("https://help.ubuntu.com/community/XORGHardy")

its about the new xorg.. its for hardy though.

---

### Post by Memfis on 2008-12-17
[solved]

I'm sure that these settings aren't quite correct, but they seam to work for my vnc.

Section "Device"
        Identifier      "Configured Video Device"
Driver "vesa"
Option "NoDDCValue" "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
HorizSync  31.5-48.5
VertRefresh  50-70
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

---

### Post by Raptus_ on 2009-03-22
Hi,

Just wanted to say that I had the exact same problem til my Ubuntu file-server that also did not have any monitor attached. 

The solution over worked great! I just replaced the existing "device", "monitoring" ++ config's and that was that:D

thanks!

---

### Post by Hyper WD on 2009-06-21
I just wanted to add that I 've been trying to find a solution to this for the past 3 days for my Linux Mint box when I finally stumbled on this post purely by accident. Solved the problem completely. Kudos to Memfis for the solution. 
 
Works beautifully.
 
Thanks a lot!:D

---

### Post by pfunkman on 2009-07-10
> **Memfis said:**
> [solved]

I'm sure that these settings aren't quite correct, but they seam to work for my vnc.

Section "Device"
        Identifier      "Configured Video Device"
Driver "vesa"
Option "NoDDCValue" "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
HorizSync  31.5-48.5
VertRefresh  50-70
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Perfect, there are about a dozen threads on a few different sites about the same issue and i literally stumbled on this trying to fix it and it works.

:guitar:

---

### Post by mike16889 on 2009-08-10
thanx man, setting up an ubuntu fileserver/php test server/media center and haveing trouble with it booting headless, i want to just plug it into power and thats it, connected to network via wireless N card and this problem has rly held me up, will try your config and see if it works.

---

### Post by Endymion_hu on 2009-08-11
Hi,
I had the same problem but I have an intel graphics card and this solution didn't work.
For the intel driver the DDC option is different.
The working solution is:

[I]Section "Device"
        Identifier      "Configured Video Device"
Driver "intel"
Option **"DDC" "False"**
EndSection
[/I]

---

### Post by mike16889 on 2009-08-13
thanx man ur config did work, thanx alot.

---

### Post by zzeroo on 2009-08-20
*big thump* great work. Saves my day, too.

---

### Post by MIKE SILVA on 2009-09-07
Hi,

For me doesn't work.
Any help please. The system stops on the screen:

Ubuntu is running in low-graphics mode.
(EE) Intel(0): No valid modes
(EE) Screen(s) found but none have a usable configuration.

I don't have connected a monitor when system boot, only after a few minuts i connect i see this message.

My xorg.conf is:

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "DDC" "False"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
HorizSync 31.5-48.5
VertRefresh 50-70
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection



Any sugestion? If I write "vesa" for the driver, the system works, but the resolution is 640 x 480 and don't accept other.

Waiting for help, please!

---

### Post by MIKE SILVA on 2009-09-07
Forgot to add,

My computer is a Dell Intel 82845 G/GL.

With monitor is perfect, no problem. But I need to work withou monitor. Accessing by VNC.

---

### Post by TinkerJ on 2009-09-26
I too have:
```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

I need X to start without a monitor attached because the primary use is x11vnc.

But I think I need to use the intel driver because I have a secondary output running to projector for playing vids, and need video acceleration.

---

