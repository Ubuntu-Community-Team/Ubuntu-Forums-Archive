---
title: "i need help checking failure of Breezy install to get to Internet"
date: 2006-04-25
forum: Desktop Environments
---

### Post by James King on 2006-04-25
Hello, this is my second post to any  ubuntu forum.  Replies to my first post regarding failure to get Gnome Mag via Synaptic Package Manager led me to conclude that maybe I can't get to the Internet because my apparently successful install of Breezy in a dual-boot configuration with XP on a Dell Latitude D610 may have a mistake caused by my inability to read the text-only install screens without a magnifier.

Since I can't get the repositories to get a magnifier, and since I can't see well enough to re-install anything but all the defaults without a magnifier, I need advice on how to test my current install of the Breezy CD without doing a lot of reading.  I have the LiveCD for Breezy as well as the InstallCD, both downloaded froom ubuntu.  I also have Live Knoppix amd System Recovery CD, both from the Christopher Negus book, Lenux Bible (which I can read with a Max Magnifier CCTV connected to ZoomText 8 via a WinTV USB card).  Following are the questions to which I think I need answers:

1. Is there a visually easy way to test my Internet connection from inside Gnome?  (The sudo apt-get update command from the Terminal windid not work.)
2. Is there a visually easy way to get the Gnome-Mag using one of my Live CDs (Breezy, Knoppix, System Recovery, etc.) to diagnose and fix my current Gnome install and gain access to the Internet with or without a magnifier from one of these Live CDs?
3. Is it visually easy to do an "expert" install of Breezy using either my InstallCD or my LiveCD for Breezy?
4. Do I need to turn off ZoneAlarm firewall, Norton Antivirus, and CounerSpy -- and/or turn on or off radio connection of Windows XP via WiFi thrugh a Spriint DSL modem and router via another Latitude D610 before booiting through GRUB to Gnome?
5. Do I need to turn off or on all that anti-malware stuff in XP and enable radio before re-installing either the ubuntu LiveCD or the InstallCD?
6. How can I get an install copy of Dapper Drake to see if it is easier than Breezy for me to see and use in my dual-boot system?  [I will still need XP until Linux has programs better than ZoomText 8/9 for Internet eye-and-voice reading, Dragon Naturally Spaeaking Professioinal 8 to control MS Office (or Open Officed?), and WinTV-USB-MaxMagnifierCCTV for book reading.]

Any answers to these questions, or to other questions you think are crucial to getting at least Gnomoe Mag and access to the repositories, would be greatly appreciated.  Thanks.

James King

---

### Post by Sef on 2006-04-25
> 3. Is it visually easy to do an "expert" install of Breezy using either my InstallCD or my LiveCD for Breezy?

It is a little tricky doing an expert install at first.  Visually it is not hard, but knowing what to do is not easy the first time.  

> 4. Do I need to turn off ZoneAlarm firewall, Norton Antivirus, and CounerSpy -- and/or turn on or off radio connection of Windows XP via WiFi thrugh a Spriint DSL modem and router via another Latitude D610 before booiting through GRUB to Gnome?

No.  They are turned off as long as Windows is not running.  Since you are using DSL, Ubuntu should automatically pick it up.  Your problem is most likely with the WiFi connection.  Could you tell us what is your brand and make of your WiFi.  

> 5. Do I need to turn off or on all that anti-malware stuff in XP and enable radio before re-installing either the ubuntu LiveCD or the InstallCD?

No.

> 6. How can I get an install copy of Dapper Drake to see if it is easier than Breezy for me to see and use in my dual-boot system?

[http://cdimage.ubuntulinux.org/daily/current/]("http://cdimage.ubuntulinux.org/daily/current/")

Note: Dapper is still Beta, i.e. in testing stage, so you may find some bugs in it for your system.

---

### Post by Rxke on 2006-04-25
there is another answer to your questions in the other topic you posted from Henrik of the accessibility team,  [http://ubuntuforums.org/showthread.php?p=957087#post957087](http://ubuntuforums.org/showthread.php?p=957087#post957087)

(Just in case you did not subscribe to the post anymore)

As a Dapper user, I can attest the high contrast themes are now easily accessible through the menu system ... preferences ... themes. The high contrast ones should pop up just about the default, human theme. :) 
...And the assitive technologies are installed by default under system... preferences... assistive technology; just click all the boxes except probably the last one and log out and in again or restart to get them working

---

