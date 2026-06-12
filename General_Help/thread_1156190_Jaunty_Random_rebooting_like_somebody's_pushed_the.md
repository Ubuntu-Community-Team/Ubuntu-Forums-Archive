---
title: "Jaunty Random rebooting like somebody's pushed the reset button"
date: 2009-05-11
forum: General Help
---

### Post by dj-toonz on 2009-05-11
Hi All, I'm having problems with Jaunty every now & then. sometimes it goes through the login stage then before it gets to the login window where you have to enter your username & password. it reboots & goes through all the stages again. then again before you enter your login details. it will bloody reboot again. then it's fine I can log in to the system. then I don't know when it will happen. it's so random. it just either reboots back to the login window or fully reboots the system :-( did it when when I opened openoffice, but now it doesn't do it when I open openoffice. Now when I open up streamtuner & click on search it reboots the system (so removed streamtuner) I left the system on last night to download a file, woke up this morning to find the system back on the login window. (it seems like somebody had held the power system button down) but nobody was in the house, only me & I was in bed :-(. is there a command to use to find out what caused the system to random reboot itself or find out what's causing the system reboots? cheers

---

### Post by rudy.b on 2009-05-11
If you haven't already, you may want to check out the system log to see what it says.

System > Administration > Log File Viewer > messages

If you've never looked at your log file before, you may feel overwhelmed with reams of data.  So you'll want to identify key items, in this case the shutdown/startup entries.  Here's an excerpt from my log:

```

May 11 04:39:38 home exiting on signal 15

```

This says that I shutdown my system at 4:39am on May 11.  Check your log to see if you can find any error messages prior to shutdown which might lead to the cause of the problem.

---

### Post by dj-toonz on 2009-05-11
thx for that, i've taken a look at the system logs & it seems like it's rebooting every hour when I check it 
May 11 03:14:59 lee-desktop kernel: [13620.297437] Clocksource tsc unstable (delta = 46870250434 ns then next line is to do with terminating then reboot 

I've got loads of that in the system log so how do i dechipher it ?

---

### Post by dj-toonz on 2009-05-11
I've just read up on the problem & it seems for some reason ubuntu is changing the clock speed or something like that & the desktop is having problems when it does it & causing the random reboots. so does anybody have any idea or a clue how to stop it? cheers as that is always the last line I can see in the system logs before the next line is shut-down

---

