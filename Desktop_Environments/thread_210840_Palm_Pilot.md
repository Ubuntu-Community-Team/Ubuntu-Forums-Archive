---
title: "Palm Pilot"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Charles Hand on 2006-07-07
I'm trying to get some functionality similar to Palm Desktop under ubuntu and gnome. So far I know of two options: gnome-pilot and jpilot.

gnome-pilot: I can get the "Pilot Applet" on the panel, and I can hotsync over the network with my Palm TX. Yay! But when I try to run gpilot-applet, which I'm guessing is the Palm Desktop-like program, it won't start. No messages, nothing. All over the Internet I'm finding 404's where gnome-pilot sites used to be. The installation comes with no documentation to speak of.

jpilot: I can get the desktop application to run, but when I follow the FAQ's about netowrk hotsync, it tells me to put a dot "." in the configuration for "Serial Port". Then it tells me to run jpilot-sync. When I run jpilot-sync it says:
****************************************
 Syncing on device .
 Press the HotSync button now
****************************************
pi_bind error: . Is a directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

-Charlie

---

### Post by SteinbergerNate on 2006-07-07
Ok, well I discovered that the applet is actually broken. Don't run the applet. What you DO want to have running is the daemon. After going into Evolution and making sure you have your serial port and everything set up right (it should be something like /dev/ttyS0). Then exit out of Evolution. Go to a terminal window and type: 
```
killall gpilotd
```
to make sure that there is no instance of gpilotd running before you try to do this. Then, we will restart gpilotd by simply typing 
```
gpilotd
``` 
and then it should show you that it's watching on whatever port you told it to watch. When you press the hotsync button, it should show you that it's doing it's thing. This should sync to Evolution much like you would sync to Outlook.

Jpilot is much more like the Palm Desktop. If you can get gpilotd to work fine then you should just have to use the port settings that worked in there in Jpilot.

This is what worked for me. I hope it works for you but if not just come back and I'm sure someone will have a solution.

---

