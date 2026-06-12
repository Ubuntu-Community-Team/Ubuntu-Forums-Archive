---
title: "network manager not showing in corner"
date: 2009-04-21
forum: General Help
---

### Post by Kapurnicus on 2009-04-21
Im pretty new to linux. Im using 9.04 I think and its the netbook remix. On a Dell mini9. today when I logged in I could see the background but nothing else came up. I can right click and create new launcher or folder so X is working fine, but is didnt get a taskbar or anything like that (classic Desktop). When I log in as a user using the netbook remix desktop Everything seems fine except the network manager isnt in the top right like it always is. The sound control and the battery options are there, but the network manager is mysteriously not. 

I didnt change anything inbetween it working and not working. I am an avid tinkerer and have changed things in the past. But I know how to go back in the recovery kernal and change back and text config files I changed. I changed nothing this time, was just off on bootup. If this sounds familiar help me out please.

---

### Post by iponeverything on 2009-04-21
try running nm-applet from the command line.

---

### Post by Kapurnicus on 2009-04-21
when i run nm-applet it says

"** (nm-applet:9550): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3"

also, it seems like the tabs on the desktop interface are about a thousand times less responsive than they were. I am running the update manager now to see if that fixes anything. I believe the network applet is running, its just not up in the corner where it belongs.

---

### Post by Kapurnicus on 2009-04-21
For some reason after an update and a reboot my network applet is back and things seem to be running full speed again. Hopefully it will stay this way.

---

### Post by Kapurnicus on 2009-04-21
However, after logging into my classic mode account ( not netbook remix desktop) It still just shows the background and nothing else. Maybe these two problems were unrelated. I dont want to have to delete all my gnome user preferences if there is another way to fix this. the curser is not an X it is the actual gnome arrow. there just is no taskbar at the top.

---

### Post by sir_nasty on 2009-04-21
I have the same laptop with the same issue.  Here's what I discovered....

If you put your mouse in the right position between the speaker and the battery monitor and click it will bring up the network properties, so it's still there just not showing the icon for some reason.  Also, Fn + 2 will turn off the wireless then turn it back on and that icon will pop back up.  As for how to fix it I have no idea but this is my temporary work around...  This happened after an update to me as well, I'm going to run the update manager again (LOTS of updates to do) and see if it comes back.

---

### Post by sir_nasty on 2009-04-21
just ran the update manager again, had another 100+ to do, now the icon is back with a new fancy look and working normally!  I just ran update manager until it had no more updates to do...

---

### Post by Kapurnicus on 2009-05-13
Finally gave up on fixing my classic mode desktop. Just delected everything relevant to the system in my home directory and let the system bascially rebuild my account. Obviously, this worked, since the problem was only with my user account, but there's no reason I should have had to do this. Somehow a config file I guess got borked and since I didnt changed any (by hand anyway) I'm going to assume it was the gui (or a change I told the gui to make) that killed it. It's unfortunate, but atleast its fixed.

---

