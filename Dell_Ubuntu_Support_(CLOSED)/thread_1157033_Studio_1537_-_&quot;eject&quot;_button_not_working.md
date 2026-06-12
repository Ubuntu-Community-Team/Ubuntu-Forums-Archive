---
title: "Studio 1537 - &quot;eject&quot; button not working"
date: 2009-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nathan_U on 2009-05-12
Hello

I have encountered a problem on DELL Studio 1537 T4200 / ATI3450 / 250GB, the CDROM eject button is not working, no matter how long I will be pressing it. Everything was working fine on Kubuntu 8.10, problems start when I did an upgrade to 9.04 two weeks ago (yea, I didn't have time to post this issue earlier).

I tried to assign it manually by going to System Settings, then General tab, Input Actions and creating new global shortcut for command "eject CDROM" but it appears no button on keyboard is responding after being pressed (is this what this menu is for? heh). 

Any ideas, please?

---

### Post by twoaday on 2009-05-12
I had the same issue on a Dell Studio 1536 and found that there was a line that could be added to the sysctl.conf file I do believe. Also I tried a much simpler approach that worked wonders, which was to remove the power cord and the battery then hold in the power button for about 30 seconds, then reboot the buttons worked great from there on but I have to do it more often than I would like. The reason for this I found on the dell.linux support groups was that a static charge gets built up in the control panel (where the buttons reside) and keeps them from working properly. 

That code for the sysctl.conf goes like this:

sudo gedit /etc/sysctl.conf

then add this line to the bottom of the page:

#allow eject of cdrom using eject button 
dev.cdrom.lock=0


Hope this helps

---

### Post by Nathan_U on 2009-05-16
Indeed now the button is working, I tried both options so I can't be sure which one worked though :).

Thank you for help.

---

### Post by bmdavis on 2009-08-01
This is great, but when it ejects the media it does not unmount.  Any way to have it unmount after eject?  (if you right click and eject, the unmounting happens)

---

