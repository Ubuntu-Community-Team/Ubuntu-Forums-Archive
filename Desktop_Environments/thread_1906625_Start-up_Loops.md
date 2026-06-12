---
title: "Start-up Loops"
date: 2012-01-09
forum: Desktop Environments
---

### Post by vchapman on 2012-01-09
This machine has Ubuntu 10.04 and has been running for sometime without any problems.

All of a sudden in the last week as the software starts to load the the system loops.

It is (was) a single user machine. When powered up it went right to the desktop and was ready to be used.

Now just as the image for the desktop is beginning to be displayed, the machine loops to the login screen. If you click on the user name, the machine get to the point where it begins to display the desk top (it actually shows 2 icons for files that are on the desktop) and then reverts back to the login screen. So something is broken.

I have added a second user and if that name is selected at the login screen, the system loads the desktop normally.

Help with a fix will be appreciated. Thank you.

---

### Post by Basher101 on 2012-01-09
this is rather odd....did you make any updates recently that could have busted up your system? or any changes to Gnome/unity? which DE do you use by default? Do you have any kind of backup to roll back to?

*note: i have not much expirience with such problems, just going through logical deduction to help you here*

---

### Post by vchapman on 2012-01-09
> **Basher101 said:**
> this is rather odd....did you make any updates recently that could have busted up your system? or any changes to Gnome/unity? which DE do you use by default? Do you have any kind of backup to roll back to?

I did not knowingly make any updates to the system that would have busted it. Its not backed up.

I have added a second account and it seems to work fine.

---

### Post by vchapman on 2012-01-09
Here is more information.

If I force the login screen at start-up, the original user has the same problem if selected to login.
If I select the user that I added, the login proceeds as normal to the desktop. With the new user logged in, I can switch to the original user and that brings up the proper desktop for that person.

One other thing, when the original user is selected, the video goes very dim as the system tries to start the desktop.

---

### Post by Basher101 on 2012-01-09
could be graphics related. i do not know how to proceed from here, the only things that come to my mind would be either reinstalling the graphics drivers or make a whole reinstall of ubuntu.

the last one should be a last resort...

regards  
 
p.s. hopefully someone who can help you better will come soon.

---

### Post by vchapman on 2012-01-10
My problem seems to have disappeared! I haven't restored the automatic login yet but I will do that next.

---

### Post by jmate24 on 2012-01-11
could you post a copy of you logs and put them in a folder and compress them into a tar.gz file please:
/var/log/auth.log , /var/log/auth.log.1 , /var/log/boot.log , /var/log/bootstrap.log , /var/log/dmesg , /var/log/dmesg.0 , /var/log/dmesg.1.gz , /var/log/dmesg.2.gz , /var/log/jockey.log.1 , /var/log/kern.log , /var/log/kern.log.1 , and your display manager log whether it be Ubuntu = gdm.log and gdm.log.1 , lightdm.log , lightdm.log.1 and or your lxdm.log and lxdm.log.1 and finally your syslog, syslog.1, syslog.2.gz and syslog.3.gz.

thanks. if you don't know how to attach the file the attachment paperclip is next to the smiley face that has a small arrow pointing down it is between the A and the Undo Buttons on the top of the Message window.

thanks.

---

