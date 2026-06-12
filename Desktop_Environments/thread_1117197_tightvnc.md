---
title: "tightvnc"
date: 2009-04-05
forum: Desktop Environments
---

### Post by num on 2009-04-05
hello,

how can i get tightvnc running remotely via Putty?

also when i connect via realvnc to tightvnc i get into root's account how can i get into my account that i setup?

---

### Post by num on 2009-04-07
anyone? please help?

---

### Post by geoffjay on 2009-04-07
once you've installed tightvncserver you should be able to create a new vnc session by doing:

$ vncpasswd
$ vncserver -g 1024x768

which will tell you what desktop to use, usually :1, then wherever you want to connect from you would do 

$ vncviewer server:1

change 'server' to the name of the computer you want to connect to

---

### Post by num on 2009-04-13
but how do i get the program running via command line?

---

### Post by geoffjay on 2009-04-13
What OS are you wanting to connect from? The vncserver command that I provided you with already is the one that you run in putty to start a VNC session on the remote computer which I'm assuming is Ubuntu and has the tightvncserver package installed. Once you've done that you can connect from Windows using a Tight/Real VNC client or from Linux using the vncviewer command that I provided you with already.

Keep in mind that you'll probably need to edit your ~/.vnc/xstartup file to use your window manager of choice.

Check out this link, it has more than enough information to get a basic VNC server going.
[http://bobpeers.com/linux/vnc.php](http://bobpeers.com/linux/vnc.php)

---

### Post by num on 2009-04-22
i am using windows xp pro but i want to start up tightvnc via putty from windows. how can i do this? its all command line. I tried $ vncserver but it won't work.

---

### Post by geoffjay on 2009-05-02
log in as whatever user you want to connect as using putty, then enter (for example)
$ vncserver :1 -geometry 1440x900 -depth 24

now in Windows start realvnc and enter server:1 (replace server with the name of the computer to connect to)

you of course read the manual and help right? 
$ man vncserver
$ vncserver -help

---

