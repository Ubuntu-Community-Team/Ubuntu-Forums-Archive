---
title: "How do I get these two Ubuntu machines to talk to each other?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by ardchoille on 2006-08-09
I have two Linux machines on the same subnet. How do I get MachineA to log into MachineB so that I can do some admin tasks on MachineB? Which apps do I need to install on which machines? Is there a tutorial on how to set this up?

---

### Post by RAOF on 2006-08-09
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by ardchoille on 2006-08-09
Ok, I think I followed that how-to and am getting this:

```

$ ssh user@192.168.0.2
ssh: connect to host 192.168.0.2 port 22: Connection timed ou

```

I also have Firestarter running on the box at 192.168.0.2, would that make a difference? If so, how do I get firestarter to allow the ssh connection?

Did I miss something in that how-to?

---

### Post by ardchoille on 2006-08-09
Ok, I set a new policy in Firestarter (on 192.168.0.2) to allow SSH on port 22 from 192.168.0.4. Then I went to that machine (192.168.0.4) and tried this command:

```

$ ssh user@192.168.0.2
ssh_exchange_identification: Connection closed by remote host

```

and that's what I got. 192.168.0.4 is the machine I am trying to connect from, and 192.168.0.2 is the machine I am trying to connect to. I have openssh-server installed and config'd on the target machine but I can't see what I am doing wrong. 

any ideas?

---

### Post by alamba on 2006-08-09
Have you started the ssh server? Try this:
1. cd /etc/init.d/
2. ./sshd restart

If it still doesn't connect try this and post the output here:
1. sudo apt-get install nmap
2. nmap localhost

A

---

### Post by ardchoille on 2006-08-09
I figured it out. I kept going over things in my head until it dawned on me that I always change /etc/hosts.allow and /etc/hosts.deny after a new install to enhance security. I had to add "ALL: 192.168.0.4" to /etc/hosts.allow for the target system to allow anything from that box.

All is working now and I am sitting at 192.168.0.4 ssh'd into 192.168.0.2 using irssi in the screen session on that box.

He he, it was my own security habits that were keeping me out :)

---

### Post by ardchoille on 2006-08-09
> **RAOF said:**
> [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Thank you very much for that link. It's quite educational :)

---

### Post by RAOF on 2006-08-09
The wiki is an **excellent** source of information.  Well worth a search :)

---

### Post by ardchoille on 2006-08-09
> **RAOF said:**
> The wiki is an **excellent** source of information.  Well worth a search :)

Good advice, but much of the time I have no idea what I need to search for.

---

### Post by ardchoille on 2006-08-09
Is it possible to sit at machineA, have machine B running x and log into x from machineA so I can run things like Firefox on machineB and see it from machineA?

EDIT: I found a solution at: [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

in case anyone else wants to do this :)

---

### Post by RAOF on 2006-08-09
> **ardchoille said:**
> Is it possible to sit at machineA, have machine B running x and log into x from machineA so I can run things like Firefox on machineB and see it from machineA?

EDIT: I found a solution at: [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

in case anyone else wants to do this :)

Or, you can use "ssh -X *user@remotehost*".  That forwards the X session over, so running "firefox" in the ssh session will start firefox on *remotehost*, and display it on the local X server.  Plus, it will look just like a local X app - you can copy/paste etc.

---

### Post by ardchoille on 2006-08-09
> **RAOF said:**
> Or, you can use "ssh -X *user@remotehost*".  That forwards the X session over, so running "firefox" in the ssh session will start firefox on *remotehost*, and display it on the local X server.  Plus, it will look just like a local X app - you can copy/paste etc.

Now that is truly awesome. I love Linux! 
:)

---

### Post by RAOF on 2006-08-09
That works best over a LAN.  VNC and the like are suited to remote access, where you're trying to access a box over the intertron.  The X protocol is not well suited for this; it requires quite a lot of bandwidth, so the windows update **slooooowly**.

---

### Post by ardchoille on 2006-08-09
If I am doing this from a LiveCD, should I launch ssh -X user@host from a terminal within the LiveCD's x session or should I CTRL+ALT+F1 and launch the command from there?

---

### Post by etank on 2006-08-09
If you are going to be using a gui then you need to be on a system running X. Run it from the X session.

---

### Post by ardchoille on 2006-08-09
Ok, I ran ssh -X user@host and I got the same type of prompt as when I use ssh user@host. I didn't see X or anything.

---

### Post by RAOF on 2006-08-09
You get the same sort of prompt, but any GUI application you run from that prompt will be displayed locally.  For example, try running "gedit".

It's not quite the same as VNC, sorry.  You don't get the whole desktop, just those applications you run.

---

### Post by ardchoille on 2006-08-09
> **RAOF said:**
> You get the same sort of prompt, but any GUI application you run from that prompt will be displayed locally.  For example, try running "gedit".

It's not quite the same as VNC, sorry.  You don't get the whole desktop, just those applications you run.

Ah, ok, well, that's good enough for me.

However, I am getting this:

```

$ gedit
X11 connection rejected because of wrong authentication.
The application 'gedit' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.

```
Looks like I need to tweak something on the remote box. What do I need to do now?

---

### Post by RAOF on 2006-08-09
Hm.  Odd.  I didn't have to do any further setup to get X forwarding happening.

You could try running the command "xhost +" before trying to run gedit.  Does that work?

---

### Post by ardchoille on 2006-08-09
> **RAOF said:**
> Hm.  Odd.  I didn't have to do any further setup to get X forwarding happening.

You could try running the command "xhost +" before trying to run gedit.  Does that work?

That command gives me this:

```

$ xhost +
access control disabled, clients can connect from any hos

```

OK, I just realised something. I got the previous X error while another user was logged into that box and using X. I just ran gedit (that user is no longer logged in) and gedit ran fine, ugly.. but it ran fine. So, I am guessing what I need to do is run x on a different display than tty7 just in case other users are sitting at that box logged in. Got any advice for me about that? Something like "startx -1:" or something?

---

### Post by RAOF on 2006-08-09
> **ardchoille said:**
> That command gives me this:

```

$ xhost +
access control disabled, clients can connect from any hos

```

And if you then run "gedit", does it work?  That's what I wanted to test, whether it was Xorg access control that was preventing you from running gedit.

---

### Post by ardchoille on 2006-08-09
Well, I got that X error when a friend was logged in at the box. She is no longer logged in and I can now run gedit just fine.

I guess I need to be able to tell the remote box which display I want to use? Just in case people are currently sitting at that box.

Running apps from that box works great when no one is sitting at the box logged in, it's when someone is logged in that I have trouble running gui apps remotely.

---

### Post by RAOF on 2006-08-09
Hm.  Are you both logged in as the same user?  There's probably an Xauth cookie saying "this user's X session is on this ip address", or something.

---

### Post by ardchoille on 2006-08-09
No, her username is different than mine.. and I am the only admin on that box. I made sure the accounts were seperate when I set hers up.

No problem, really. I can always do "who" before I try to launch gui apps. I'm just ecstatic that this works so well :)

I Love Linux!!!

---

### Post by maniacmusician on 2006-08-09
this does work fairly well, but there are a couple of drawbacks.

1. you can pretty much only do one app at a time, right? because the terminal will be occupied until you close the app that you're using. unless you do CTRL + C, but i dunno, that might terminate the app too.

2. you can't copy files from the X session to your X session. for example if i do gksu while logged in to my other computer under ssh -x, it will open thunar, but i will not be able to copy a file from that thunar to a folder in this X session. but that cant be accomplished with VNC either, so this isnt exactly a complaint; but that kind of a feature would be truly amazing. 

also, this always confuses me; which one is the client and which the server. If i'm accessing another computer from here, is this the server? or the is the server the computer that I connect to?

thanks.

---

### Post by RAOF on 2006-08-10
1) You can open as many apps as you like.  Append a "&" on the end of the line, like so:
```
gedit &
```
and it will open it in the background of the terminal.  Your terminal will still work, and so will gedit.  Alternatively:
**Ctrl-z** will suspend whatever's running in a terminal.  This temporarily stops the running program.
**fg** will resume a program you've suspended.
**bg** will cause the program you've suspended to become backgrounded.  That is, it resumes running, but your terminal still accepts input.

2) Quite true; the programs you run like this run in (almost) all respects as if you had run them on the remote system.  So they only have access to the local filesystem of the remote box.

Finally, Client/Server.  X uses wierd terminlology.  The X **server** is the program that displays stuff on your local computer.  X **clients** are programs that ask X to draw stuff.  So, any GUI program is an **X client**.

When you're doing things over the network, the remote computer is the ssh server, and would it would be correct to call it the "server".  Any GUI programs you run on the "server", though are actually X **clients**, and they connect to your **local** X server.

Confusing, eh? :)

---

### Post by ardchoille on 2006-08-11
> **RAOF said:**
> 1) You can open as many apps as you like.  Append a "&" on the end of the line, like so:
```
gedit &
```
and it will open it in the background of the terminal.  Your terminal will still work, and so will gedit.  Alternatively:
**Ctrl-z** will suspend whatever's running in a terminal.  This temporarily stops the running program.
**fg** will resume a program you've suspended.
**bg** will cause the program you've suspended to become backgrounded.  That is, it resumes running, but your terminal still accepts input.

2) Quite true; the programs you run like this run in (almost) all respects as if you had run them on the remote system.  So they only have access to the local filesystem of the remote box.

Finally, Client/Server.  X uses wierd terminlology.  The X **server** is the program that displays stuff on your local computer.  X **clients** are programs that ask X to draw stuff.  So, any GUI program is an **X client**.

When you're doing things over the network, the remote computer is the ssh server, and would it would be correct to call it the "server".  Any GUI programs you run on the "server", though are actually X **clients**, and they connect to your **local** X server.

Confusing, eh? :)

Hmm.. that is a bit confusing.. but I am determined to learn about it :)

I just run a screen session on the ssh server, so I can open as many windows in screen as I need and switch between them from any other box i the house.

I am currently using irssi, mutt, bash, vim, elinks and a few other apps in a screen session that I connect to via ssh. I now have one machine that is the "master", which has all the apps I need, and 9 other machines (minimal installs) that connect to the master via ssh.. so all the files I work on are on the master machine and I can work on any file from any machine in the house.

Thank you all for your wonderful help.. I appreciate it :)

---

### Post by maniacmusician on 2006-08-13
hmm that is a pretty cool setup you've got there. I'm not trying to hijack this thread, but since you've got your problem solved, and mine is somewhat similar...

I'm trying to setup a way to easily transfer a large number of files. about 90 GBs worth. i have a wireless network all setup, and ssh kind of setup (I don't know if everything is in place. I had it better before but had to do a reinstall). I can't really use the scp command, and I don't have nautilus. I was thinking gFTP with ssh, but i've had no luck setting that up either. does anyone know of a way I can accomplish this? it doesn't have to be ssh, I just want my files back on this computer. 

Thanks.

edit: nevermind. I just used gFTP with ssh instead of open-ssh and it worked. odd, but at least it works. I wont complain.

---

