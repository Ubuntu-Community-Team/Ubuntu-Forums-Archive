---
title: "[SOLVED] Upgrading from Gutsy to Hardy loses my Novatel U727 Mobile Wireless Broadban"
date: 2008-07-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by StewartM on 2008-07-30
Hello all,

I purchased a 1525N laptop this year from Dell which had Gutsy 7.10 installed on it. I also have a Zareason Limbo 2440 desktop computer which I purchased later with Hardy 8.04 installed on it (by the vendor). I could list the hardware specs on both, but given my problem I don't think it's necessary unless someone thinks it's important.

Anyway, yesterday while off work I decided I liked Hardy so much on my desktop that I went ahead and took the plunge on upgrading from Gutsy to Hardy on my laptop. I hit the "localedef" problem and the upgrade stuck. The problem is detailed here:

[http://ubuntuforums.org/showthread.php?t=861194](http://ubuntuforums.org/showthread.php?t=861194)

And I got around it eventually by this fix (quoting from a post by Bluztrvler on page 3 of that same thread):

[I]Thanks to herlements: This worked for me.

We may have the solution here (on the french forum).

Just reboot, but don't choose the upper choice proposed
by grub. Take another one, not in recovery mode.

Wait for the login screen, then ctrl+alt+F1
and log in.

Then make

sudo apt-get dist upgrade (but I'm not sure this is necessary)

then :

sudo dpkg --configure -a

and for me everything is fine. Still this is a big bug...



Seems that running dpkg --configure-a outside of X works. I still have issues with my desktop, but at least it boots.[/I]


So that apparently got me around that problem...

But then I lost sound and modem and wifi light, as I knew I would from having looked at the Dell wiki. So I went to the following page:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

After a few tries, I got the sources list updated, I got sound back, I got the WiFi light working, and I installed the new modem driver. (I don't know if the modem works, however, because I haven't been able to test it...see below).

Next I tried connecting on laptop using my Novatel U727 Wireless modem (which had previously worked on Gutsy). The way I had connected to it was to open a terminal window and issue the following commands:

sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4100

Then I checked by:

sudo dmesg|grep -i ttyusb

Then I would dial out using the KPP modem software (dialing 777). You can read the instructions here in their entirety (including the KPP setup)  by going to [www.sprint.com/downloads](www.sprint.com/downloads) and selecting linux to the pdf file. 

[http://www4.sprint.com/pcsbusiness/support/downloads/items.jsp](http://www4.sprint.com/pcsbusiness/support/downloads/items.jsp)

Anyway, what happens when I try inserting the U727 and opening the terminal and typing in the first command:

sudo modprobe -r usbserial

I get:

FATAL: Module usbserial is in use.

Wondering if there was something amiss in my upgrade process, I then downloaded and installed the KPP software on my Zareason Limbo 2440 desktop purchased with Hardy 8.04 natively installed. When I stuck the modem into my USB port and tried my "sudo modprobe -r usbserial" I get the same error message. 

This leads me to believe that this is not an upgrade screw-up on my end, but that something in Hardy is indeed incompatible with my U727 modem. Does anyone have any experience? I hate to be paying $60 a month for my modem and not be able to use it at all.

Thanks for any help,

StewartM

---

### Post by StewartM on 2008-07-30
As it turns out, the upgrade didn't break my Novatel u727 at all. This post is being typed on it. ;) 

How I had been checking success was going to web pages using Firefox, as that was the easiest way to do so, and had been getting a "Firefox is offline" message. When I took my laptop down to the local Sprint Store, the tech had me check email and Pidgin. They worked! It turns out that it's just *Firefox* 3.0 has a bug with wireless connections. One needs to go into the about:config in Firefox and set toolkit.networkmanager.disable from false to true. (The non-default mode).

It's bug #191889 in Firefox 3.0

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889)

I still get the "FATAL ERROR" message when I try to dismount the usbserial driver (sudo modprobe -r usbserial) but that apparently can be ignored and one can proceed with the subsequent steps (entering in the vendor and product IDs, and starting the KPPP dialer). I am beginning to wonder if I had to install the hsfmodem for this connection to work?

Two last issues: I have sound again, but it's faint even with the hardware and software settings upped to the max. I still note that under System|Sound that the Conexant HSF modem is still listed as one of the playback options, and am wondering if there is anything I can do to boost the sound volume.

For the latter reason, and the fact that my workaround is still "ugly" (in the error message trying to unload the usbserial driver), I won't mark this "solved" yet.

StewartM

---

### Post by StewartM on 2008-07-30
> **StewartM said:**
> 
Two last issues: I have sound again, but it's faint even with the hardware and software settings upped to the max. I still note that under System|Sound that the Conexant HSF modem is still listed as one of the playback options, and am wondering if there is anything I can do to boost the sound volume.

For the latter reason, and the fact that my workaround is still "ugly" (in the error message trying to unload the usbserial driver), I won't mark this "solved" yet.

StewartM

The sound is so faint that I can't hear music in the videos in Youtube  playing, so it's still definitely a problem (though I can hear my playlists in Rhythmbox. Any ideas would be appreciated.

StewartM

---

### Post by StewartM on 2008-07-31
> **StewartM said:**
> The sound is so faint that I can't hear music in the videos in Youtube  playing, so it's still definitely a problem (though I can hear my playlists in Rhythmbox. Any ideas would be appreciated.

StewartM

Duh! My linux guru friend told me that double-clicking on the sound icon reveals more volume options, and that brings the sound volume up to an acceptable level (though he also thinks it's a bit weak compared to what it should be, but he thinks that's a hardware problem with the 1525N).

And, as he also answered the only other question I had--whether or not my screen resolution of 1280 x 800 was the max of the hardware (it is) I'll mark this thread as solved.

StewartM

---

### Post by Flyingjester on 2008-07-31
well, i'm glad all got solved for you :) sorry i didn't see this earlier or i would have helped you out.

---

