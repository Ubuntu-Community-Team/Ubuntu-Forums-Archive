---
title: "TightVNCserver setup help"
date: 2009-01-31
forum: General Help
---

### Post by Shaided on 2009-01-31
I only have ssh access to my server (running Ubuntu server edition of course) & I'm not very good with the terminal (why I need help) so I decided to install tightvncserver on here (that was the only part I knew how to do "sudo apt-get install tightvncserver") but now I need the terminal commands to run tightvncserver & change the password from the terminal.

~ I really don't like putty right now

---

### Post by pytheas22 on 2009-01-31
I think you can start tightvncserver by typing just:
```

tightvncserver
```

(you may need to use 'sudo' with it).

If you want to install a VNC server that will automatically start itself, however, check out [this tutorial]("http://ubuntuforums.org/showpost.php?p=5229232&postcount=458").  It gives you a more streamlined setup than tightvncserver, plus you don't need to ssh in first every time you want to start a VNC session--the session is automatically launched when your computer boots.

---

### Post by Shaided on 2009-01-31
I found out how to run it but I really need to know how to change its port 
~ You have no idea the anxiety that comes over you when you have a perfectly good server but can't properly access it
~ I'm trying to get connected to it from a vista comp if that matters
~ Am I getting mixed up when I think all I have to do to get connected from the viewer is hostip:port

---

### Post by pytheas22 on 2009-02-01
> ~ Am I getting mixed up when I think all I have to do to get connected from the viewer is hostip:port 

You probably need to specify the screen, not the port.  In most cases (not sure with tightvncserver in particular), the screen number corresponds to the port in that if the server is running on port 5900, the screen number will be 0, 1 for port 5901, etc.

So basically, if your server is running on port 5900, enter this in tightvncviewer to connect:
```

ip-address:0
```

If the port is 5901, use:
```

ip-address:1
```

etc.

I don't know how to change the port number that tightvncserver uses--I'm sure you can figure it out by typing 'man tightvncserver'--but the default port is probably 5900.

---

### Post by p_quarles on 2009-02-01
You don't need to select a display when starting the server, as it will automatically use the first unlocked display. If it doesn't use display 0 (it will tell you after running the command), you will need to specify the display in the client. 

To set a password:
```
tightvncpasswd
```
To set screen size (a good idea), you can use the -geometry argument:
```
tightvncserver -geometry 1280x1024
```
The server does not need to be and *should not* be run with sudo.

---

### Post by HermanAB on 2009-02-01
SSH can do everything VNC does only better.  Try this:
$ ssh user@server gnome-panel

Cheers,

Herman

---

### Post by fragos on 2009-02-01
For what it's worth 8.10 Canonical supports vino for vncserver and vinagre for vncviewer. I still use xtightvncviewer, more out of habit, which also works with vino as the server.

---

### Post by KeyserSoze93 on 2009-02-01
If you and your server are not on the same LAN, and you only have access to port 22 (SSH), you can still do what is call tunnelling.

Open two terms on your client:

Term 1:
```

ssh -L 5901:your-server:5900
(at your server) tightvncserver

```

Then keeping it open, run your vnc client (i use xtightvncviewer, but as fragos says, ubuntu comes with vinagre), and point it to localhost:1

In actual fact, localhost:1 it port 5901 on your client, which we have used the ssh process to forward to port 5900 (the default port that tightvncserver should server from) on your server, so that should be what you'll get.

---

### Post by crackmac on 2009-03-18
I believe you need to have the "-Y" flag in that command.

$ ssh -Y user@server gnome-panel

This is one of the cooler things I've seen in a while... I loves SSH.

--Kevin


> **HermanAB said:**
> SSH can do everything VNC does only better.  Try this:
$ ssh user@server gnome-panel

Cheers,

Herman

---

### Post by dumdadum on 2010-04-10
> **crackmac said:**
> I believe you need to have the "-Y" flag in that command.

$ ssh -Y user@server gnome-panel

This is one of the cooler things I've seen in a while... I loves SSH.

--Kevin

You maybe love ssh, but there seems to be a problem at my end. Unless I'm doing it wrong, I don't see how your line of command works. Here's what I did:

ssh -Y someone@192.168.2.17 gnome-panel

The response I got is the following :

Cannot open display: 
Run 'gnome-panel --help' to see a full list of available command line options.

Also, it seems to work for you as it runs gnome, or so it seems. Well what if you were to run fluxbox? Is there a way to use ssh as a vnc viewer too? If so, do you think you need to elaborate the command you printed out? Because if I can  do everything with ssh and uninstall tightvnc that would be awesome.

Waiting for a response,
Dumdadum

---

### Post by dumdadum on 2010-04-10
> **Shaided said:**
> I only have ssh access to my server (running Ubuntu server edition of course) & I'm not very good with the terminal (why I need help) so I decided to install tightvncserver on here (that was the only part I knew how to do "sudo apt-get install tightvncserver") but now I need the terminal commands to run tightvncserver & change the password from the terminal.

~ I really don't like putty right now


Personnaly, a good server admin knows his way around commands. Thats why I prefer Slackware. The closest I could find to fit my needs. (= I use putty to ssh on my puters from work everyday. Coolest thing ever invented. No need for fancy GUI. Just a simple command does it all. Its actually the power of Unix/Linux, where Microsoft Windows fails. Thats my opinion.

So, to respond to your request, if you hardly know your way around command line, yesterday was a good day to start learning. (= Especially if you manage servers. (=

Cheers,
Dumdadum

---

### Post by pytheas22 on 2010-04-10
> You maybe love ssh, but there seems to be a problem at my end. Unless I'm doing it wrong, I don't see how your line of command works. Here's what I did:

ssh -Y someone@192.168.2.17 gnome-panel

The response I got is the following :

Cannot open display:
Run 'gnome-panel --help' to see a full list of available command line options.

That command should work.  You probably have issues with getting the X forwarding working.  To troubleshoot it further, I'd ssh in with just
```

ssh -X someone@192.168.2.17
```

Then try launching a simple X11 application via the ssh session, such as xclock, by typing:

```
xclock
```

in the ssh session.  If there's something wrong with your X11 server configuration that might give you a better hint of what.

> Also, it seems to work for you as it runs gnome, or so it seems. Well what if you were to run fluxbox? Is there a way to use ssh as a vnc viewer too? If so, do you think you need to elaborate the command you printed out? Because if I can do everything with ssh and uninstall tightvnc that would be awesome.


The command forwards gnome-panel, not the entire gnome session (although you could forward the entire gnome session by typing gnome-session instead, but that would require a lot more bandwidth).  You could probably do a similar thing with Fluxbox and forward just the menu you need to launch applications, but I haven't used Fluxbox in a while and don't know which command you'd need to call the Fluxbox menu or panel (does it even have a panel?  I forget).  Depending on your needs that may or may not be sufficient.

To answer the larger question, VNC and ssh are fundamentally different things, so you can't really "use ssh as a vnc viewer," but you might be able to use ssh with X11 forwarding to replace the functionality that you currently get from tightvnc.

---

### Post by dumdadum on 2010-04-10
> **pytheas22 said:**
> That command should work.  You probably have issues with getting the X forwarding working.  To troubleshoot it further, I'd ssh in with just
```

ssh -X someone@192.168.2.17
```Then try launching a simple X11 application via the ssh session, such as xclock, by typing:

```
xclock
```in the ssh session.  If there's something wrong with your X11 server configuration that might give you a better hint of what.



The command forwards gnome-panel, not the entire gnome session (although you could forward the entire gnome session by typing gnome-session instead, but that would require a lot more bandwidth).  You could probably do a similar thing with Fluxbox and forward just the menu you need to launch applications, but I haven't used Fluxbox in a while and don't know which command you'd need to call the Fluxbox menu or panel (does it even have a panel?  I forget).  Depending on your needs that may or may not be sufficient.

To answer the larger question, VNC and ssh are fundamentally different things, so you can't really "use ssh as a vnc viewer," but you might be able to use ssh with X11 forwarding to replace the functionality that you currently get from tightvnc.

Yeah well I use tightvnc, it works well. Configuration is really simple too. What I usually do is disable the tightvncserver, and only enable it when I need it. So I first login by ssh, activate the server manually, and make a tightvnc connection.

Plus right now I've got other issues. I'm a Slackware user, and I'm trying to compile Audacity, and it just wont work. So I would like to get Audacity working on my box rather than learn about X11 forwarding. Maybe in the futur.

Thanks for the post though. I'll look into it eventually.

Cheers,
Dumdadum

---

### Post by danpav2881 on 2012-05-22
> **dumdadum said:**
> personnaly, a good server admin knows his way around commands. Thats why i prefer slackware. The closest i could find to fit my needs. (= i use putty to ssh on my puters from work everyday. Coolest thing ever invented. No need for fancy gui. Just a simple command does it all. Its actually the power of unix/linux, where microsoft windows fails. Thats my opinion.

So, to respond to your request, if you hardly know your way around command line, yesterday was a good day to start learning. (= especially if you manage servers. (=

cheers,
dumdadum

tdc

---

### Post by oldos2er on 2012-05-22
Please don't bump old threads. Closed.

---

