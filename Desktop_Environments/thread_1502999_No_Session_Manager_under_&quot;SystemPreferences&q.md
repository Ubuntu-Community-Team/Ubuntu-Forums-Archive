---
title: "No Session Manager under &quot;System/Preferences&quot;, no startup programs manager"
date: 2010-06-06
forum: Desktop Environments
---

### Post by kevdog161 on 2010-06-06
Hello - installed 10.04 yesterday, Had previously dabbled, trying to switch over to Ubuntu full time now.  Wanted to access the session manager, but when I scroll to System/Preferences, there is no entry for it, or for the startup programs manager.  Also, I'm getting the following error when attempting to open the "windows" entry:

Failed to execute child process "gnome-window-properties" (No such file or directory)


Did I somehow botch something in gnome which is now leading to the absence of the session manager as well as the inability to launch the "windows" manager?

---

### Post by germanix on 2010-06-06
I am not sure what you mean by "session manager"? Normally you will find the "startup-applications" icon under System>preferences. If it or anything else that you miss not there then go to System>preferences>main menu" and there go to "system" and check the boxes of everything you want to be included in the system menue or under the "admin" menu as you require.

---

### Post by hokiejp on 2011-08-26
In case anyone else stumbles on this, I had the same problem and it was because I had accidentally uninstalled the gnome-control-center package while trying to get rid of evolution.  It turns out you have to keep the evolution-data-server for the gnome configuration applets to work.

---

### Post by NLinTKO on 2011-08-27
I installed Ubuntu 11.04 on a new desktop computer and started exploring the world of Linux. So far am I impressed by what I see.
This morning however I stumbled upon the same issue as is mentioned in this thread. I am using the graphical interface, which brings me to the "Startup Applications". According to the Help text should there be two tabs: "Startup Applications Tab" and "Session Options Tab". However, this second tab does not appear. It is for me difficult to use the first tab as you have to give the correct command for an application to start. I don't know these commands. The second tab ("Session Options") would be very powerful as it can remember the applications I'm running. So I don't need to know the detailed commands.
Can somebody please tell me what to do (in simple terms) to make this Session tab visible?

---

