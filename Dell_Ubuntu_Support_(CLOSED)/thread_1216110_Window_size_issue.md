---
title: "Window size issue"
date: 2009-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jwaclawsky on 2009-07-17
Does anyone have this same problem. If you do have a fix I would really appreciate any information. Thanks. My problem: 

I have a Dell Mini 9 running 8.04 and I am using this netbook to drive a Dell 24" monitor and occasionally a Sony 19" display. The Mini 9 works really well except whenever I start a new program the window the program is beginning to run in opens to fill the entire screen instead of a smaller window (from the last time it was opened). Is there some setting I can change so when I start a program the window size used is what it was when last closed? It appears the window size begins to open as the smaller (last opened/closed) window (you can see the window outline start) but then something grabs it and drives it to full screen. One other symptom of my problem is that sometimes when I am running a program such as VLC media player that when I close the window occasionally something goes to all the currently open windows on my desktop and and expands then to full screen. I have to resize everything back using the unmaximize window button at the top right of the window. This is getting annoying.

---

### Post by utnubuuser on 2009-07-17
Is gnome-session-restore enabled? > Alt+F2 >> gconf-editor >> apps >> gnome-session >> options >> auto_save_session

---

### Post by jwaclawsky on 2009-07-18
ok, I tried the auto_save_session and it had no effect. I turned it on then even rebooted (just to be sure) and then later I turned it off (and did the same - rebooted). It had no effect on or off.

Some additional information. This does not seem to be related to the external monitor. I tried the same thing with the Mini 9 screen and I have the same problem. Whenever I have a program running in less than full screen and then I shut it down (it is shut down in a window less than full screen) and then later when I restart the application it "tries" to open in its less than full screen previous state (you can see the outline of the old window starting) but then something in the processing sequence of opening windows and starting an application then grabs the window and drives it to full screen. Anyone else having this problem. Any help would be appreciated. Thanks!

---

### Post by jwaclawsky on 2009-07-20
Can anyone PLEASE help! I have been living with this problem since I first got the Mini 9 (I even contacted Dell when I finally found someone after 7 or 8 transfers, callbacks that "claimed" they knew Linux, but they were less than helpful and just confused, they just called me back intermittently and told me they were working on it and they finally stopped calling - very poor support). While this is not a huge problem and is quickly fixed by resizing windows, it is quite annoying after living with it for over 4 months. Again any assistance would be appreciated. Thanks!

---

### Post by ugm6hr on 2009-07-20
This is due to the application maximus.

It is designed to do this in order to make best use of the small screen.

If you want to get rid of it, just remove or disable it.

To remove:
```
sudo apt-get remove maximus
```

To disable:
Untick from Startup Applications

To configure:
[http://ubuntuforums.org/showpost.php?p=7349817&postcount=2](http://ubuntuforums.org/showpost.php?p=7349817&postcount=2)

---

### Post by jwaclawsky on 2009-07-20
ok, I removed maximus (BTW, you would think Dell would tell me that - I must have spoken to them 5 times) and removing maximus seems to have corrected  my original problem. But I now find my WiFi turned off and I can't get it restarted. I am not sure why removing maximus would cause that or even if it did cause the WiFi problem. I even reinstalled maximus and that didn't help. Does anyone have any suggestions to get me back on the air? Thanks.

---

### Post by jwaclawsky on 2009-07-20
...some additional information. My web cam no longer works either. Somehow uninstalling maximus deleted some needed file(s) is all I can figure out. Any help would be appreciated.  Thanks

....some additional information. I am now running 9.04 on my CD/DVD which I had the good fortune of making a bootable disk a few weeks ago. I wasn't intending to go to 9.04 but it works and WiFi now works (using it now). In summary:

Removing maximus some how disable my WiFI, my camera and my HP printer and god know what else (it is as if these device do not exits). I know it is the software because under 9.04 the WifI can be now be found. I am sure if I install skype I'll find the camera working and reinstall my HP driver and it will find my printer. I would appreciate anyone who could help me recover the lost functionality in 8.04.

How can removing "maximus" cause such secondary and totally unrelated problems?   ....sigh. ...Help anyone

---

### Post by ugm6hr on 2009-07-21
> **jwaclawsky said:**
> How can removing "maximus" cause such secondary and totally unrelated problems?   ....sigh. ...Help anyone

I don't know, it certainly should not do that.

In any case, why not stick with 9.04?

I find it an overall much better experience on the Mini than the original 8.04, and the developers are keeping netbooks in mind (due to the NBR being declared as supporting multiple Netbooks).

---

### Post by jwaclawsky on 2009-07-21
I tried the Dell recovery disk and WiFi still doesn't work. Something strange with Dell and this moronic maximus package. This is also just a crappy user program and recovery support and set-up from Dell. I wasn't ready to move all my apps and everything to 9.04 but that's what I am doing.  ...More later

---

### Post by jwaclawsky on 2009-07-21
I have one issue I need to deal with in 9.04. Now whenever I start a video the video screen opens and then promptly shuts down. I tried different file types including flash. Yet the videoes work ok within the browser - YouTube works fine for example. Can someone give me some guidance on how to go about trouble shooting this video situation (there must be error messages or an activity trace somewhere so I can figure out what is going on)?

---

### Post by ugm6hr on 2009-07-21
> **jwaclawsky said:**
> Now whenever I start a video the video screen opens and then promptly shuts down.

What kind of Video files?

Is it Totem that is causing the problem?

I would suggest looking at the Multimedia thread linked below for advice on getting codecs to play a variety of files etc.

EDIT: Link in my sig: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jwaclawsky on 2009-07-21
The problem seems to be with anything video. The files are .wmv, .mpg .asf and .avi (I tried different file types). The problem happens with both movie player and VLC media player. You actually hear a snippet of the file beginning to play with VLC and then the window disappears/closes. I tried it with a DVD movie and got the same result. There must be error messages somewhere???? I did notice a brief message about album art showing up but it disappeared too and shows up intermittently. ...my Skype video isn't working either, people can see me but I can't see them (it may be, and probably is, related but I am working one problem at a time)

...BTW, there was no thread linked in the previous reply post????

---

### Post by jwaclawsky on 2009-10-15
BTW, I have got everything working shorty after my previous post, once I figured out the video problem and understood how to change the configuration to point to X11 (on another thread). I am quite happy with 9.04 for the last 2 months I have been using it. Good stuff!!!

---

