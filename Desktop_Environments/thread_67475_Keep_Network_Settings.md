---
title: "Keep Network Settings?"
date: 2005-09-20
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2005-09-20
Okay, so I'm having a little trouble with Kubuntu. I can get the internet, but only after a series of commands I have to type in after boot. 

This is what I type in on each startup:

sudo -s 
modprobe ndiswrapper 
iwconfig wlan0 key 
iwconfig wlan0 enc 
iwconfig wlan0 essid 
/sbin/dhclient wlan0 
 

Is there any way to automate these terminal commands to execute on bootup so I dont have to retype this everytime? Other than minor setback I love Kubuntu (my first experience with Linux  )

---

