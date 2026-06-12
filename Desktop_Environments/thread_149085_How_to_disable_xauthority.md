---
title: "How to disable xauthority?"
date: 2006-03-23
forum: Desktop Environments
---

### Post by Alastair Rae on 2006-03-23
I am evaluating using Ubuntu as a workstation instead of using X server on windows. 
I cannot get xauth to work but cannot figure out how to disable it.

I work with multiple X clients on a variety of platforms. Since I am on a secure network I would like to be able to just do xhosts +.

Please help or I shall have to abandon the experiment and go back to M$ windows.

---

### Post by yota on 2006-03-23
Hi, I'm not sure I've understood your problem... can you be more specific: what do you want to achieve? What's the issue with "xhost +"?

Anyway I'll try: forgive me if this is useless.
If you have 2 machines, let's say machine A and machine B, and you, sitting on machine A do the following:
```

xhost + (on A!)
telnet/ssh B
export DISPLAY=ip.adress.of.A:0
xclock

```

should see an xclock that runs on machine B but shows itself on A.
This way B serves the application (cpu time, disk...) and A is the X server.
A common misbelief is that A is the Xwindow client since A is the client computer that connects to the B server.

Hope this helps.

---

### Post by Alastair Rae on 2006-03-23
Thanks but I know xhosts + is supposed to work. I've been working way for years but am not used to working with xauth. We have a large number and variety of non-Linux xclients so xhosts + is by far the simplest way to work.

I know it's not secure but on a private network it is a lot easier. 

I read somewhere else that gdm only uses xauth so I guess that answers my own question - you can't disable xauth.

I will keep on struggling with xauth ...

---

### Post by claes on 2006-03-23
Easier should be to tunnel x in ssh.

ssh -X user@server

just start the xclient on the ssh server and the gui should apear on the machine you ssh'ed from.

Claes

---

### Post by steve.horsley on 2006-03-23
it's **xhost +** not **xhosts+** and it does work. See this quote:
> steve@StevesPC:~$ xhost +
access control disabled, clients can connect from any host
steve@StevesPC:~$

So if you say it's not working, you must be trying to do something different to what we think. Can you explain exactly what you are trying to do and what bit isn't working? Imagine we all have really poor imaginations (too close to the truth sometimes).

---

### Post by Alastair Rae on 2006-03-24
Just because xhost says clients can connect from any host, does not mean that clients can connect! They still have to pass the xauth test.

From a terminal on your ubuntu desktop, try this:

> xhost +
mv .Xauthority .Xauthority~
xterm

Your xterm will fail to run because you don't have xauth configured.

I work on multiple *nix server boxes. So I  run lots of xterms from other hosts on my desktop. With any X server software I've used in the past, xhost + is all that is necessary. On Ubuntu it seems you have to fiddle about with xauth also.

I think my problem is actually to do with broken DNS reverse lookup and stupid DCHP server. A static IP address might be all it takes to get xauth working but would prefer.

---

### Post by yota on 2006-03-24
I forgot to mention that you have to set "DisallowTCP=false" in /etc/gdm/gdm.conf (the default is true... i've changed it lot of time ago!)

Check if your Xserver is running with that option with
```

ps -ef |grep X

```

---

### Post by Alastair Rae on 2006-03-30
Security continues to get in my way. 

In order to set up xauth on a remote box, I need to do rsh. But rsh and rcp have been hijacked by ssh so I can't even communicate with my test machines. Installing  the rsh-client package restores the old-fashioned way so I'm happy again.

---

