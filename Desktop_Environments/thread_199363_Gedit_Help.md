---
title: "Gedit Help"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Trev0r269 on 2006-06-18
I'm in the process of installing lm-sensors (using the thread on these forums), and I'm trying to make the mkdev.sh file. When I use "sudo gedit /etc/init.d/mkdev.sh" I get this...

cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

The help command didnt offer me much of that.
I'm already logged in as the root in the console. I can open gedit using applications>accessories>text editor, but it appears not out of the command line. I'm a noob tryin to make the switch to linux, and if I can get my cpu fan to not run at 100% all the time, I'm going to do it. 

Thanks ahead of time for any help. If anyone would like to walk this n00b through the lm-sensors installation and config, I'd be very greatful.

---

### Post by aysiu on 2006-06-18
Try ```
sudo nano /etc/init.d/mkdev.sh
```

---

### Post by 5-HT on 2006-06-18
If you want to try and edit using gedit, what about either:[LIST=1]
[*]Logging in as a regular user and using 'sudo gedit ...'
[*]Stay logged in as root and drop the 'sudo' (though it is highly recommended to NOT log in to X as root for obvious reasons).[/LIST]Furthermore, you do not need to log in as root, you can use sudo: [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo").
You shouldn't be using sudo to escalate user privileges for root: It it meant (well... in a limited sense) to be used only for escalating limited-user privileges (root already has complete access to the system), or for running something as a different user.

If you want a root shell, simply enter ```
 sudo -s 
``` when logged in as your user.



I'm not sure, but am guessing the problem is happening because of a user conflict running gedit on X using sudo with root and as root.
Either of the two options above will hopefully prevent that conflict, but I would recommend option 1.

[quote=TrevOr269]I'm already logged in as the root in the console. I can open gedit using applications>accessories>text editor, but it appears not out of the command line [/quote] 
If you are logged in as root, again, you do not need to use sudo and it appears like gedit is functioning normally (just not when trying to call it using sudo as root with no user specification). As root, if you just enter 'gedit' at the command line does it open?

Sorry, I don't use lm-sensors myself so I couldn't be of much help there. However, I would suggest starting a new thread if you are having problems with lm-sensors as it would draw the appropriate attention (instead of being under a thread for gedit help).

Hope you get it working.

---

