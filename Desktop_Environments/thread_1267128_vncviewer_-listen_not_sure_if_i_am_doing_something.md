---
title: "vncviewer -listen ?not sure if i am doing something wrong"
date: 2009-09-15
forum: Desktop Environments
---

### Post by ubunRyan518824 on 2009-09-15
First of Hi and thanks for you help...

I am running Ubuntu 9.04 on my pc recently switched from XP. I have been using vnc single click so that customers could connect to me and I could control their desktop, but I was going from windows to windows before. Now that I am using linux Ubuntu I am not sure how to go about that. here are my conditions

On my computer
1) port 5500 is fowarding to my computer
2) i have ran apt-get install vncviewer (to install vncviewer)
3) i put vnc viewer in listen mode in terminal "vncviewer -listen"

on client computer
1) singelclick settings file has xxx.xxx.xxx.xxx:5500 (where xxx are is my internet ip)
2) lauch the single click file and it open as normal

On my computer
terminal windows gives me this:
rip@rippc:~$ vncviewer -listen 0
vncviewer -listen: Listening on port 5500
vncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.8

No windows opens that alows me to view their desktop. Am I doing something wrong or can this just not be done. I would really hate to have a VM or dual boot just to do remote support. Any help would be great!

Thanks 
RIP

---

