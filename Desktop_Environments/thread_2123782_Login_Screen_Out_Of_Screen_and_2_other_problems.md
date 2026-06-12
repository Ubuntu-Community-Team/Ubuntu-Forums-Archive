---
title: "Login Screen Out Of Screen and 2 other problems"
date: 2013-03-08
forum: Desktop Environments
---

### Post by RahulXxX on 2013-03-08
Hello Guys, I'm new to Linux world, infact I have installed Ubuntu 12.04 yesterday on my computer. I have Dual-COre processor, 2GB RAM, 500GB HardDisk, No graphics card and XP in parallel.
I'm facing So many problems in Ubuntu:

1) Login Screen is on left side and only half of it is visible.
2) I logged in with password which I had Set while installing Ubuntu but still it is showing me Guest-Hbicaz@ somthing
3) Sud command is not working. When i tried to install gedit using this command "sudo apt-get install gedit" . It is giving me these errors
    sudo: unable to change to sudoers gid: Operation not permitted
    sudo: setresuid() [0, 0, 0] -> [118, -1, -1]: Operation not permitted

Please Help Me. I'm new to Ubuntu.
I have searched to solve the Login screen problem but I cant solve because sudo command is not working

---

### Post by grahammechanical on 2013-03-09
First, Gedit is already installed. It is one of the default Ubuntu applications. You will find it in the Dash as Text Editor but if you search for gedit the Dash will find it.

Second, what do you want to do with Gedit? And why do you want to do it?

Third, at the login screen do you see your username above the password panel? Guest should be underneath the password panel and your username on top of it. Try clicking on your username and then enter the password. When you get to a desktop look in the Dash for Additional Drivers. Open the utility and activate another video driver. See if that fixes the problem with the login in screen.

You can also use the power/cog menu to log out as Guest and log back in as you - the user. Then sudo commands will work. How did you get into a Guess session? 

Regards.

---

### Post by RahulXxX on 2013-03-09
The last 2 problem had been solved yesterday evening but because of slow  internet I couldn't replied here. Sorry for that. Now I can access my  admin account and Sudo command is also working.
Now the only problem is Login screen's resolution. Thanks for replying :)
One solution for it maybe to edit xorg.conf but i couldn't find where is it? It is not in /etc/X11/

---

