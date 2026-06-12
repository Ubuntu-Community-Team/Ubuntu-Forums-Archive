---
title: "After odd Ubuntu behavior, comp no longer boots."
date: 2012-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by khopek on 2012-02-01
Suddenly, today I have had odd errors with Ubuntu..I could not print, my secondary harddrive was not being detected, the Disk Utility program wouldn't even show any options, sound stopped working, and the Sound utility wouldn't show any options.

On restart the computer would hang on the Dell startup screen, then on Grub, and every other screen until the OS started. And now the computer won't do a thing. It just stays frozen on the Dell startup screen.

Any ideas?

---

### Post by bluexrider on 2012-02-01
Bad memory, failed video card. If you have a live CD/DVD you can do a memtest. See if you can run any programs from the live CD/DVD or try booting a USB.

Sounds like some sort of hardware failure.

---

### Post by khopek on 2012-02-01
Ok it appears the video card was bad, I took it out and went back to integrated graphic; however, I get a blank screen right after an Ubuntu screen with 5 dots in the center appears for a couple seconds.

I went to recovery mode and ran startx. I get an error stating that no screens are found. How do I get Ubuntu to recognize my integrated graphics through recovery mode?

---

### Post by bluexrider on 2012-02-02
**Re: reset xorg.conf file**             
                                                                This can be  done by booting into recovery mode and selecting "fix x server" (or  whatever the actual wording is).  You can also do this from the command  line:

     
     ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 
which will automatically generate an xorg.conf file while backing up the current one.
                                                                                               __________________

The other thing I found out you can do is delete the xorg.conf file.  Then restarting the X session with startx. Doing this will create a  brand new xorg.conf file with the absence of not having one.

---

### Post by khopek on 2012-02-02
Thank you! Resetting the xorg.conf file worked. Everything seems perfect again!

---

### Post by bluexrider on 2012-02-03
Good thing, glad to get you going. Please mark this 
(SOLVED)

---

