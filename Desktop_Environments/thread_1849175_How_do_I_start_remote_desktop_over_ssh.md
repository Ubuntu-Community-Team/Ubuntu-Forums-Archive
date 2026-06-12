---
title: "How do I start remote desktop over ssh?"
date: 2011-09-24
forum: Desktop Environments
---

### Post by Higgs1 on 2011-09-24
I want to make it so that I can do ctrl+alt+f8 to get to a screen that looks as if it was the screen on any other computer (another computer or the same computer) but not an existing screen on that computer (no desktop sharing like teamviewer).
I've tried ssh -X and then gnome-session, but it comes up with a "cannot open display" error. I also tried it with exporting various DISPLAY variables, including localhost:1, client:1, and :1 but I'm thinking that maybe this approach won't work.
How do I create another graphical virtual terminal (just like the ctrl+alt+f7) that is served by another computer?

---

### Post by Higgs1 on 2011-09-24
bump

---

### Post by haqking on 2011-09-24
> **Higgs1 said:**
> bump

Does your machine to which you are ssh -X to support X forwarding ?

---

### Post by Lars Noodén on 2011-09-24
You can tunnel VNC over SSH if you want.

---

### Post by sanderd17 on 2011-09-24
You can only run one xorg server per graphical card if I'm right (didn't look too deep into it). 

So you will need something like vnc. With xorg allone you can't do it.

This is why multiseat computers need to have all those graphical cards, while they still only need one CPU, one motherboard and one bunch of RAM.

---

### Post by haqking on 2011-09-24
> **sanderd17 said:**
> You can only run one xorg server per graphical card if I'm right (didn't look too deep into it). 

So you will need something like vnc. With xorg allone you can't do it.

This is why multiseat computers need to have all those graphical cards, while they still only need one CPU, one motherboard and one bunch of RAM.

You dont need  mutltiple graphics cards to carry out a remote X session ?

X is loopbacked so requests are sent remotely then the local X server carries it out.

---

### Post by sanderd17 on 2011-09-24
Something is bothering me.

How is the window manager selected?

You can just start an x app from an ssh terminal without choosing the window manager.

So I guess the window manager and the xorg client that were already running on the client computer are used.

Is this right?

That would mean you can't start a second WM simultaniously.

As I said, I don't know too much about it.

---

### Post by haqking on 2011-09-24
> **sanderd17 said:**
> Something is bothering me.

How is the window manager selected?

You can just start an x app from an ssh terminal without choosing the window manager.

So I guess the window manager and the xorg client that were already running on the client computer are used.

Is this right?

That would mean you can't start a second WM simultaniously.

As I said, I don't know too much about it.


X always runs in a local loopback network mode even when not across a remote X session. When you initiate a remote X session the commands are sent out but addressed locally.  The work of running the application is handled remotely but display and graphics involved are carried out locally.  But of course a lot or remote machine to which you would ssh -X to for example wont have a GUI or DE, and so graphical tools dont exist, so say you wanted to ssh -X a gedit session, gedit needs to exist for the remote server to handle it, however the display of it runs locally.

Try it, ssh -X to a remote machine, real or a VM.

---

### Post by Higgs1 on 2011-09-24
> **haqking said:**
> Does your machine to which you are ssh -X to support X forwarding ?

Thanks for the reply,
I can launch xclock, xeyes, gedit, gnome-terminal, and transmission so I'm assuming the remote machine supports X forwarding.

The remote machine is running Linux Mint (Ubuntu version) and isn't far from a fresh install. I'm currently running something that started as Ubuntu.

---

### Post by haqking on 2011-09-24
> **Higgs1 said:**
> Thanks for the reply,
I can launch xclock, xeyes, gedit, gnome-terminal, and transmission so I'm assuming the remote machine supports X forwarding.

The remote machine is running Linux Mint (Ubuntu version) and isn't far from a fresh install. I'm currently running something that started as Ubuntu.

OK so X is working across ssh, you dont want to share a desktop view using VNC or Teamviewer etc.

So i dont get what you want ?

You can either run X apps across the network using ssh -X or vnc to the current desktop session.

I am not understanding you ?

---

### Post by Higgs1 on 2011-09-24
From my experience vnc and teamviewer share the currently running desktop thats running on the computer. I want a new desktop, just like running any other x application (I'm saying that the whole desktop thing is just a normal application, if this is wrong correct me)

---

### Post by Lisiano on 2011-09-24
Why not start a new vnc session then (A clean desktop with only a terminal open)?
In Ubuntu you need to first install a VNC server like TightVNC```
sudo apt-get install tightvncserver
```
Then just start TightVNC
```
vncserver
```
It will show you on what display it created a X session, for example :1. Now just use any VNC client and connect to 5000+$DISPLAY, in this example, 5001.
To kill the session, type```
vncserver -kill :1
```

Also, doesn't KDM do the multiple local X sessions? I can easily create new sessions in KDE on the same user and switch between them with Ctrl+Alt+F#. All "instances" don't share open programs. And you can do something like a Remote Login with KDM, not sure how it works though.

---

### Post by aschmidtm on 2011-09-25
```
sudo apt-get install xauth
```

Have you tried 0.0 for the display?

---

### Post by Higgs1 on 2011-09-25
> **Lisiano said:**
> Why not start a new vnc session then (A clean desktop with only a terminal open)?
In Ubuntu you need to first install a VNC server like TightVNC```
sudo apt-get install tightvncserver
```Then just start TightVNC
```
vncserver
```It will show you on what display it created a X session, for example :1. Now just use any VNC client and connect to 5000+$DISPLAY, in this example, 5001.
To kill the session, type```
vncserver -kill :1
```Also, doesn't KDM do the multiple local X sessions? I can easily create new sessions in KDE on the same user and switch between them with Ctrl+Alt+F#. All "instances" don't share open programs. And you can do something like a Remote Login with KDM, not sure how it works though.

Thank you for the suggestion. It's not exactly what I wanted but It'll work. Here's some problems I have when I follow your instructions:

1) When I start i get only a terminal, so I'm guessing I need to tell it to start programs when I connect. How do I configure it to do the same start up process as I when I log in to the computer the normal way? 

2) Whenever i press the key 'd', it toggles a "make all windows invisible" mode. How do I make it not do that?

3) How do I do it over ssh? I haven't tried it yet but here's my guess (assuming the new X session is on :1):
ssh -f -L localport:localhost:5901 remoteuser@server tightvncserver
And then connect to localhost on localport. Is this correct?

And then ultimately I'd still like it on ctrl+alt+f#, if it can do that and 1-3 then thats exactly what I wanted.

Also, on the server I used "tightvncserver" to start the server because "vncserver" doesn't work as well. On the client i use Vinagre as my VNC viewer.

---

### Post by Lisiano on 2011-09-26
1) Anything you put in /home/$USER/.vnc/xstartup will be started when you create a session.

2) I want to know that myself.

3) In Vinagre you can tell it to use a SSH tunnel, I assume Vinagre will understand that by localhost you mean that machine.

---

