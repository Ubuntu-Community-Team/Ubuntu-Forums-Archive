---
title: "LightDM restarts on user login (But not guest)"
date: 2012-10-18
forum: Desktop Environments
---

### Post by Time Sheep on 2012-10-18
Hey
I am currrently running Ubuntu 12.04 LTS x64_86 on my laptop for use as a media center.
I installed the latest NVidia graphics drivers.
 
Here's what I did:
Installed Ubuntu
Installed updates
Reboot
Installed NVidia drivers (For my 9600M GT)
Reboot
Installed XBMC
Inserted HDMI cable
Disabled main monitor in NVIDIA X Settings and set the TV as new monitor
Ran "sudo restart lightdm" in terminal
Bam, got the picture on the TV now, great.
Restarted to clean up some mess I made
Attempted login, main monitor shows the X-server restarting and I end up at the login screen. Keeps happening no matter how many times I try.
 
What I tried:
Logged in as guest - works fine but cannot connect to internet or use the software I need. I also get access denied on "su".
Reboot - No difference at all
Multiple logins - Same problem
Unplugged HDMI cable and reboot - Picture shows on default monitor but problem persists.
 
 
Any suggestions out there? I'm starting to get a little lost. I will attempt resetting the X configuration, just need to find the disk first. If it works, this post will be on the internet for others to find.
 
UPDATE:
Restoring the xorg.conf did not help at all.

---

