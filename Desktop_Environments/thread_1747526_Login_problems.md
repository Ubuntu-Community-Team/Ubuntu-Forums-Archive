---
title: "Login problems"
date: 2011-05-02
forum: Desktop Environments
---

### Post by clemm on 2011-05-02
After my last upgrade from 10.? to 10? my users' (kids) were unable to login. I tried to fix it and could not find anything wrong.

Now I have upgraded to 11.? and the problem persists. The users could still login by selecting an older version at the prompt during boot up.

I deleted there account and reinstall the user and still they could not login. I added a completely new test user and could not log that one in either.
The system excepts the password, waits a several seconds, then the mouse curser changes to the spinning circle. The hard drive lights flash for many seconds then eventually the hard drive stops flashing. I have let it sit a long time and it never continues.
Tonight I came home tried to login and it is doing the same thing to me tonight. I ran fix packages, fix grub and everything else I could think of and could not log in.
Finally I logged in to the oldest version on there and it let me in.?
The screens are all the same  but the desk top is entirely different? I have never seen one like this. I think its like the new version of fire fox, with every thing moved around. Icons down the side. Menu's hidden at the top??? I can probably get used to that but I need to able to login, and my user's to login? 
Thanks
:confused:

---

### Post by Krytarik on 2011-05-02
First, you are seeing the new Unity interface, actually that's a good sign!

Because many users apparently don't do so right after the first login, and it means that your video driver is working properly, with 3D-acceleration.

Please see the links in my signature to get started with Unity.

Now to your actual issue, your are talking about the kernel options in the boot menu, right?

After a provoked failed login reboot with the kernel that works and log in as the same user, then post the contents of the log files "/var/log/Xorg.0.log.old" and "~/.xsession-errors.old", the latter is in the user's home directory. Please use the #-button in the editor to enclose them into code-tags.

---

### Post by clemm on 2011-05-05
I can not find those files. with this new format I cant find anything except the stuff I dont want to find.
I dont like this new version.

---

### Post by clemm on 2011-05-05
I finally found the first file. xorg0.log.old.
Im not a programmer. Do I use the text editor, and do I have to put a pound symbol at the begging and end of each line, or just the beginning and end?
This file is huge, am I really supposed to copy it here?
Thanks

---

### Post by clemm on 2011-05-06
This new version is intolerable. 
Back to windows until I find a version that works, if linux ever makes one.

---

### Post by Krytarik on 2011-05-06
> **clemm said:**
> This new version is intolerable. 
Back to windows until I find a version that works, if linux ever makes one.
Are you always giving up that fast!?

I'm still at rockin' Lucid 10.04 here.

You can choose "Ubuntu Classic" as the "Session" option at the login screen after clicking at your username.

---

