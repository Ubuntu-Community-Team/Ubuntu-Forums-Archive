---
title: "Brightness control command which requires root permission in a script"
date: 2013-03-26
forum: Desktop Environments
---

### Post by Evan I S on 2013-03-26
Hi all,

I would like to ask for help regarding automatically run command as root.  I need to run below command line in a terminal to set brightness for the sake of my sensitive eyes.

setpci -s 00:02.0 F4.B=15

I tried to make it as a script but not working.  This is first time though.
#! /bin/sh
sudo -s "*my password*" <- to login as root
setpci -s 00:02.0 F4.B=15 <- since I gained root, run the command right away.
exit 0 <- let system know script is finished

However, setpci command required root permission.  What I am doing now so is that as soon as xwindow loads open a terminal window then login as root and then type the setpci command.  I am seeking a way to make these steps automate itself after finishing boot up.  I have been exploring google since lunch time because of it(roughly 10hours).  However, I could not find a solution for it yet.](*,)  I am novice in a boot camp of LINUX.  It would be great that give me explicit instructions as much you can. :-D  I much appreciate it!

Best wishes,
Evan S

---

### Post by Cheesemill on 2013-03-26
You can add an entry to your sudoers file so that the setpci command can be run without prompting for a password.

First run the following commands to open the sudoers file for editing...
```
sudo -i
EDITOR=nano visudo
```
Now add the following line **to the bottom** of the file replacing username with your actual username. 
```
username ALL=(ALL) NOPASSWD: /usr/bin/setpci
```

Hit CTRL+x and save the file and then exit your root shell.

You should now be able to run 'sudo [COLOR=#000000]setpci -s 00:02.0 F4.B=15' without being prompted for a password, so just add the command to your startup applications using the 'Startup Applications' application.[/COLOR]

---

