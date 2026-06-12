---
title: "Help displaying X apps on remote computer"
date: 2006-01-06
forum: Desktop Environments
---

### Post by hypeiv on 2006-01-06
I have an Ubuntu Desktop (192.168.1.101) and just recently made an Ubuntu server (192.168.1.150) that has a very minimal install (no X). Even thought the server doesn't have its own X server I installed some x-apps (i.e. xemacs, kate, etc). I want to launch programs on the server via ssh and have the X display on my main desktop (I did this a few years ago with xwin in windows).

So on my main computer I go into a prompt and type in:

(524)~> xhost +
access control disabled, clients can connect from any host

Then on my server (tsch btw) I ran this but got an error:

Cheryl:~> setenv DISPLAY 192.168.1.101:0.0
Cheryl:~> echo $DISPLAY
192.168.1.101:0.0
Cheryl:~> xeyes
Error: Can't open display: 192.168.1.101:0.0

If anyone knows what I am forgetting to do please let me know. (Firewall I don't know about ??)

thanks

---

### Post by zappa86 on 2006-01-06
Did you physically go onto the server or did you ssh into it?

---

### Post by zappa86 on 2006-01-06
ohh by ssh! (sorry I missed that before). You should open up your ssh config file. Mine is located at: /etc/ssh/ssh_config on your desktop and do:
```
ForwardAgent yes
ForwardX11 yes
```

These values will be commented by default make sure the uncomment and put yes after them. After that it worked for me. BTW xhost is insecure, but if you have you own network then I guess its alright. the best way to do it is from the magic cookie xauth way.

---

### Post by hypeiv on 2006-01-07
[QUOTE=zappa86]ohh by ssh! (sorry I missed that before). You should open up your ssh config file. Mine is located at: /etc/ssh/ssh_config on your desktop and do:
```
ForwardAgent yes
ForwardX11 yes
```

These values will be commented by default make sure the uncomment and put yes after them. After that it worked for me. BTW xhost is insecure, but if you have you own network then I guess its alright. the best way to do it is from the magic cookie xauth way.[/QUOTE]

I set the $DISPLAY var to my desktop computer (.101) so I don't think it should matter if I run from ssh or from the server but yes I am running from SSH. I tried setting the values in my ssh_config and it didn't seem to fix my problem (I tried both with display set to :0.0 and to 192.168.1.101:0.0).

---

### Post by hypeiv on 2006-01-07
I got it working by putting this in my sshd_config on the server:

AllowTcpForwarding yes
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes

along with doing what you said to my client ssh.

What I was doing at first was trying to bypass the ssh tunnel and just set my display to the ip of the main computer. This is what we did on our windows machines in college and at my first job on our sun systems. Now I just have my display set to localhost:10.0 and let it flow through the ssh tunnel. Thanks for pointing me in the right direction.

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=hypeiv]I have an Ubuntu Desktop (192.168.1.101) and just recently made an Ubuntu server (192.168.1.150) that has a very minimal install (no X). Even thought the server doesn't have its own X server I installed some x-apps (i.e. xemacs, kate, etc). I want to launch programs on the server via ssh and have the X display on my main desktop (I did this a few years ago with xwin in windows).

So on my main computer I go into a prompt and type in:

(524)~> xhost +
access control disabled, clients can connect from any host

Then on my server (tsch btw) I ran this but got an error:

Cheryl:~> setenv DISPLAY 192.168.1.101:0.0
Cheryl:~> echo $DISPLAY
192.168.1.101:0.0
Cheryl:~> xeyes
Error: Can't open display: 192.168.1.101:0.0

If anyone knows what I am forgetting to do please let me know. (Firewall I don't know about ??)

thanks[/QUOTE]

You should just do
```

$ ssh -Y user@remote-host

```
The X forwarding will be done automatically for you, and the DISPLAY variable will be set.

---

### Post by zappa86 on 2006-01-07
I just started messing around with X apps on remote computers a few days ago. What I want to know how to do is if I start an app on one computer displayed on another computer, can I transfer it to even another computer without quitting it first.   I'm pretty sure there is a way to change the controlling terminal of a job (i dont know how) but X may be different and there may be another way. I think it would be sweet to start an X app on one computer, then when I go into another room, ssh into the computer and transfer control to the computer I just go on. Anyone know how? or even how to do it with just text apps? thanks.

---

### Post by hypeiv on 2006-01-07
i don't know how to do it with X but with text apps if you work inside 'screen' you can keep sessions open while you are logged out and resume them from anyplace.

sudo apt-get install screen

then type in: screen to load it and you will get a new prompt then load whatever console app you want to use and to deteach hit ctrl + A then ctrl + D (this drops you out of screen back to your command line)... now you can go into the other room and ssh to your computer and type in "screen -r" and it will bring that screen to your ssh terminal.

you can have more than one screen open check out the man page to see how to work with more than one screen I can't remember exactly how it works.

---

### Post by zappa86 on 2006-01-07
Thanks. thats awsome. i wish with text apps I could just suspend the job and go to another terminal (either tty1..6 a virtual one or ssh) and just pick up the job as active. but screen works, I just hope I remember it before I do it. With X apps it would be so sweet to be able to transfer control. I'm wondering if I should ask the x.org people?

---

