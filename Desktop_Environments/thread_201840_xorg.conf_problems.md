---
title: "xorg.conf problems"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Jontom on 2006-06-22
Hi I've recently installed kubuntu 6.06 on my work pc. Install all went well but when I tried to adjust the settings for my monitor I began to have serious trouble. My hardware is a Celeron 2.6 with a PC chips m/board (via chipset with s3 unichrome graphics) and a delta db770 monitor. It initially gave me a res of 1280 x 1024 @60hz which is very unpleasant on the eyes especially for this old monitor. So I went to system settings and tried to adjust the res to 1024x768 after getting root permission. This dropped me back out to the login screen. 

The monitor was initially detected as a generic monitor and the onboard graphics as vesa. After going back and getting  the monitor auto detected as a db770 and changing the settings to what I wanted, I was unable to login. Dropping to init 3 I tried startx and this gave me the error "fatal server error... caught signal 11". I then tried recovery mode and found I was able to startx (presumably this is as root?) so I created a new user and gave it sudo permissions by adding to the admin group, logged on as this user and X started normally. 

I have since been manually editing the xorg.conf to try and get settings I want and its sort of ok now but if I try and adjust the settings in kde I have to do the same thing i.e. make new user etc. So I'm thinking there is some sort of permission error happening but I dont know where, but it also seems related to the hardware as i installed on another pc and havent had issues.

Any Suggestions?

---

