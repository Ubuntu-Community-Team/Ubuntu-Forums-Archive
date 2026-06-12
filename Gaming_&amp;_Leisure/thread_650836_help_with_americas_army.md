---
title: "help with americas army"
date: 2007-12-26
forum: Gaming &amp; Leisure
---

### Post by kendalw3 on 2007-12-26
hello all... i just installed americas army but i am having troubble getting it to run.... i get this in terminal.... any help would be great!!!

kendal@kendal-laptop:/usr/local/games/armyops$ ./armyops
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History: 

Exiting due to error


i have no idea what to do :(

---

### Post by valkarin on 2007-12-27
First off, what video card are you running?  Second, do you have the proper drivers installed for your card to have 3d acceleration?  The DRI line makes me think that this might be the problem.  If it is not, it could be your monitors refresh rate.  If that is the problem you will have to edit your xorg.conf file.  Be sure to back up that file before you do anything to it.  Just make a copy and add .backup to the end of it.  

Also, you failed to mention what release you are running.  7.10 or an older one?  Be sure to include what release and what hardware you are running when you ask for help.  It is needed info before anyone can help you.

---

### Post by kendalw3 on 2007-12-27
I am running ubuntu 7.10 64 bit and i have a ati radeon x1200 video card.  I'm still rather new to linux and i am not sure how to modify things like monitor refresh rate and the like.... i belive my video card is set up correctly but again i'm not sure how to verify that too.... compiz fusion works and took me a bit of time fiddling around to make it work if that is of any help.... thank you again for you help

by the way i downloaded aa 2.5

thanks again

---

### Post by Tong Bang on 2007-12-27
dont mean to bump this but i played the game and its fun

---

### Post by kendalw3 on 2007-12-28
i am looking forward to playing.... i just hope i can get the help i need

thanks

---

### Post by kendalw3 on 2008-01-02
bump

---

### Post by intel on 2008-01-02
if this is a problem with ATI X1200 please take a look at the following site

[https://groups.google.com/group/x1250](https://groups.google.com/group/x1250)

post any driver installation s/w problems there

---

### Post by cmcfarland21 on 2008-01-05
I am getting the same error.  I have Ubuntu 7.10.  I have no problem running Enemy Territory so I don't think its my video card.  

charles@charles-desktop:~$ armyops
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History: 

Exiting due to error

---

### Post by kendalw3 on 2008-01-07
I believe my driver is working fine... it seems to work with everything else... except americas army.  I have  a dual boot with vista and unfortuneately it works just fine on vista.... i would much rather it work on linux... but either which way if anybody knows how to get it working on linux that would be great

---

