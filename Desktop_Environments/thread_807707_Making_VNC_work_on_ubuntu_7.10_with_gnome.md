---
title: "Making VNC work on ubuntu 7.10 with gnome"
date: 2008-05-26
forum: Desktop Environments
---

### Post by Jrdgames on 2008-05-26
Hello, I hope this doesn't sound rude or demanding but I have been trying to get VNC working without a user being logged in on the server for a couple days now with no luck (none good anyway).

I have tried following these guides:
[http://www.thelinuxvault.net/wiki/X11vnc](http://www.thelinuxvault.net/wiki/X11vnc)
[http://www.ubuntuforums.com/showpost.php?p=685779&postcount=1](http://www.ubuntuforums.com/showpost.php?p=685779&postcount=1)
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

I have Xvnc, tightvnc and the default vnc servers installed.

What I want is a vnc setup that is ready when Ubuntu boots and does not require a user to be logged in on the server, I want to be able to login remotely with vnc whether someone is logged in at the server or not and be on my own session.

According to the guides above it can be done but I haven't been able to do it.

I hope someone will be able to help me with this I really will appreciate it.

Oh and if this doesn't belong here I'm sorry I thought this the best place.

---

### Post by Jrdgames on 2008-05-27
I couldn't find a bump button or a rule that said not to bump topics so since my thread got to the fourth page I am bumping it.

---

### Post by IainPurdie on 2008-05-27
Hey fella,

To the best of my knowledge it's not possible. Certainly, it's not with 6.06 which I'm using. I gave up and set the system up to reboot directly into a desktop login which locked after a short period. Not great, I know, but the only "quick and easy" solution I had.

---

### Post by RottenBananas on 2008-05-27
Hey,
If you have ssh setup and working you should try forwarding X through ssh.

In your /etc/ssh/sshd_config file make sure you have this and its not commented.
```
X11Forwarding yes
```
Then you'll have to switch to a console (CTRL+ALT+F1) and type:
```
xinit -e ssh -XCT user@server gnome-session -- :1
```
Change user@server to yours.

You should see a console asking for a password (i think) and after you put that in your desktop should pop up. You can switch back to your original desktop by hitting CTRL+ALT+F7

Hope this helps

-Bananas

---

### Post by Jrdgames on 2008-05-27
Thanks IainPurdie and RottenBananas, good ideas.
> **IainPurdie said:**
> Hey fella,

To the best of my knowledge it's not possible. Certainly, it's not with 6.06 which I'm using. I gave up and set the system up to reboot directly into a desktop login which locked after a short period. Not great, I know, but the only "quick and easy" solution I had.
That sounds like it would work with the built in vnc but I don't want people to be able to see what I am doing at the server, that is why I want to use vnc with login.(multiple sessions)
> **RottenBananas said:**
> Hey,
If you have ssh setup and working you should try forwarding X through ssh.

In your /etc/ssh/sshd_config file make sure you have this and its not commented.
```
X11Forwarding yes
```
Then you'll have to switch to a console (CTRL+ALT+F1) and type:
```
xinit -e ssh -XCT user@server gnome-session -- :1
```
Change user@server to yours.

You should see a console asking for a password (i think) and after you put that in your desktop should pop up. You can switch back to your original desktop by hitting CTRL+ALT+F7

Hope this helps

-Bananas
I checked my file and Forwarding is enabled. First I tried running that command in a terminal and got:
```
X: user not authorized to run the X server, aborting.
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
```
Then I ran it again and got this:
```
X: user not authorized to run the X server, aborting.
xinit:  Server error.
```

then I changed to a console with ctrl+alt+f1 and typed the command and got this:
```
-bash: start_pipeline: pgrp pipe:Too many open files in system
-bash: /usr/bin/xinit: Too many open files in system
```
then I tried to change back to my desktop ctrl+alt+f7 and the screen turned all white with a hint of one of the applications I was running. And it is still white now it isn't responding to any connections either I think I am going to have to hard reboot it.

I was thinking of using the vnc with login via gdm because I want to be able to access the remote computer with a windows xp computer.

Any other ideas?

---

### Post by RottenBananas on 2008-05-28
Weird... thats the exact command i use and it works great for me.
it wont work in a terminal u need to hit ctrl-alt-f1...but no clue what those errors are, im kinda new to this stuff myself.

Whats ur vnc -via command look like?

---

### Post by Jrdgames on 2008-05-28
Both the server and client returned:
```
bash: vnc: command not found
```
from:
```
vnc -via
```

---

### Post by RottenBananas on 2008-05-28
on the server you need to type this in terminal
```
vncserver :1
```

it should prompt for a password i believe

after youve done this, on the client terminal type

```
vncviewer -via yourusername@your.server.name localhost :1
```

give that a shot

---

### Post by Jrdgames on 2008-05-28
That works great when a user is logged in at the remote machine but when noone is logged in it just comes up blank ([screenshot]("http://jrdltd.rack111.com/vncshot-notloggedinatconsole.png")), I think I remember someone somewhere saying that you could start an x session through ssh and then connect with vnc but I don't remember what the command would be maybe something lke gdm start or gnome start although I am not sure.

Thank you for jelping me with this. :)

---

### Post by RottenBananas on 2008-05-30
Hey no problem

Yeah for vnc someone needs to be logged in for it work.

If you wanna do remote without having a person logged in on the server ur gonna have to figure out a way to get ur X forwarding to work (The method i explained earlier)

Heres a link to the howto, the forwarding X section

[https://help.ubuntu.com/community/SSHHowto#head-3dfe4cbc16557b30eeb4d860b919ef926c9e67f1](https://help.ubuntu.com/community/SSHHowto#head-3dfe4cbc16557b30eeb4d860b919ef926c9e67f1)

As for the errors you were getting when you tried earlier(the too many files error) check out this website
[http://www.cs.wisc.edu/condor/condorg/linux_scalability.html](http://www.cs.wisc.edu/condor/condorg/linux_scalability.html)
Maybe increasing the file_max could get rid of that error. Not sure at all though so make sure you backup your files before messing with them

Good luck

---

### Post by Jrdgames on 2008-05-30
Thanks, I am forwarding X on the server and connecting with PuTTY and Xming on windows, It works good for single applications but it isn't really what I want.

I tried to install Freenx but couldn't get the special repositories to update and noone has an updated version or instructions on how to use the current version the official website just assumes you know how to do everything.

I am now trying to setup the free version of NoMachine but they also have incomplete docs. I hope I am able to get something to do what I want.

---

### Post by RottenBananas on 2008-05-30
Alright hope I helped,
Good luck :)

---

### Post by Jrdgames on 2008-05-31
Woot I have it working with the real NoMachine after installing everything what I had to do was edit /etc/ssh/sshd_config as was mentioned [here](http://ubuntuforums.org/showpost.php?p=1190037&postcount=2), I should have tried searching the ubuntu forums for nx first but I didn't know about it at the time.

Maybe I should edit the wiki since this is a free version and it works.

EDIT, I found an article here: [https://help.ubuntu.com/community/NomachineNX?highlight=%28nx%29](https://help.ubuntu.com/community/NomachineNX?highlight=%28nx%29) but it does not elaborate as much as it could.

---

### Post by IainPurdie on 2008-06-01
Just a quick "thanks in advance" to both of you. I'd started to bone up on this subject as well recently as I'm not 100% happy about the quick fix I mentioned at the start. As I'm already looking at SSH (helps when the office internet slows to a crawl - much less bandwidth heavy than VNC for command-line sessions) it makes sense to have a play with the X-forwarding.

---

### Post by Jrdgames on 2008-06-01
Try the NX free edition from NoMachine it works [http://www.nomachine.com/download-package.php?Prod_Id=5](http://www.nomachine.com/download-package.php?Prod_Id=5) that will forward the whole desktop on a separate session. If you only want to forward single applications and your client is a windows pc then you can use xming and PuTTY:
Guide - [http://www.novell.com/coolsolutions/tip/18137.html](http://www.novell.com/coolsolutions/tip/18137.html)
Xming - [http://www.straightrunning.com/XmingNotes/#head-121](http://www.straightrunning.com/XmingNotes/#head-121)
PuTTY - [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.htm l](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.htm l)

Although if you are on a ubuntu client then you can use the info in the wiki:
[https://help.ubuntu.com/community/SSHHowto#head-b5e51cf60cb289a0f9a3b95f7d580b3ea52a058a](https://help.ubuntu.com/community/SSHHowto#head-b5e51cf60cb289a0f9a3b95f7d580b3ea52a058a)

---

### Post by RottenBananas on 2008-06-01
Pretty nice thread we came up with here :)

---

