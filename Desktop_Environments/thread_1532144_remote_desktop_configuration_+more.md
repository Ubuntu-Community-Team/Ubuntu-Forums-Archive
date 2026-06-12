---
title: "remote desktop configuration +more"
date: 2010-07-16
forum: Desktop Environments
---

### Post by kysato on 2010-07-16
remote desktop requires authentication on server side when trying to login remotely via VNC. I have the option set to not require confirmation of each access to the machine, I set a password that the user must enter from the client side.

just testing this locally over my LAN, VNC connects and asks for a password(the user field is blank; might be nice to have to enter a valid username and password so I don't have to share a general password). after entering the password on the client, a window pops up on the server 'An application wants access to the keyring Default but it is locked' and requires me to enter a password, which once I do then the VNC gets control and all is good... but obviously if I am trying to remote further than down the hall this won't work.

Ideally I would like to remote into ubuntu desktop with account credentials from the server and require no physical person at the server to allow access. I currently have an XP pro box setup this way with remote desktop and works flawlessly. I want to keep it true to the same functionality where when I log in remotely it joins a session with applications already running, such as a web browser and mail client, with those applications left running when I logout of the remote session. its not all that important if it locks the server side locally as there will eventually be no physical access to the machine once its been setup.

as you may have noticed I am fairly new to linux, but very willing to learn. my primary reason to move to the linux platform is that I am hoping it will provide better performance than windows XP/windows 7 when I upgrade the box to an atom based mainboard. any other thoughts or recommendations on my planned setup would be greatly appreciated as well.

just to be clear, the 'server' is ubuntu desktop and client side is generally windows XP, windows 7, windows server (I work almost exclusively on windows boxes)

---

### Post by Drenriza on 2010-07-16
If you have a linux setup why not ssh to the machine?

ssh [option] [user]@[ip]

[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)
[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

I use ssh daily to administrate servers.

---

### Post by kysato on 2010-07-16
> **Drenriza said:**
> If you have a linux setup why not ssh to the machine?

ssh [option] [user]@[ip]

[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)
[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

I use ssh daily to administrate servers.

I suppose I could use SSH, but that will not give me the desktop view will it? which is what I am aiming to do.... to access firefox, email, and vuze gui from my windows machine at work or any other location I happen to be at (which %98 are windows based systems)

actually now that I mention that I am usually remoting from windows based systems, is there any way to usethe microsoft remote desktop client (mstsc.exe) to connect to the ubuntu desktop rather than VNC. it would be that much more seamless, else I have to tote vncviewer around with me or download it before remoting in.

thanks,
Kys

---

