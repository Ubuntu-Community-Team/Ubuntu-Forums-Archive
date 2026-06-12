---
title: "Issuing commands to desktop via remote shell"
date: 2009-01-17
forum: Desktop Environments
---

### Post by cheeken on 2009-01-17
I apologize if I am posting this in the incorrect forum.

I would like to remotely ssh into my Ubuntu box and issue commands which require a display (a la [FONT="Courier New"]gedit[/FONT]) through my ssh console and have it use my desktop display.

I have achieved success in doing this on Redhad and SLED (running [FONT="Courier New"]Xvnc[/FONT]) by assigning the DISPLAY environment variable to the appropriate value (:0.0, for example).  However, Ubuntu presents other difficulties which seem to be tied into [FONT="Courier New"]xauth[/FONT].

After setting DISPLAY and issuing a command like [FONT="Courier New"]gedit[/FONT], I am returned the following error.

```
myuser@myhost:~$ gedit
Invalid MIT-MAGIC-COOKIE-1 keycannot open display:
Run 'gedit --help' to see a full list of available command line options.
```

If I peek at my desktop's environment - specifically the  XAUTHORITY variable - and apply that same value to my shell session, the command runs properly.  But I would like to get this working without having to touch the desktop at all.

Any thoughts are greatly appreciated.  Thanks!

---

### Post by albinootje on 2009-01-17
> **cheeken said:**
>  I would like to remotely ssh into my Ubuntu box and issue commands which require a display (a la [FONT="Courier New"]gedit[/FONT]) through my ssh console and have it use my desktop display.


You should use :
```

ssh -X username@your_machine

```
for that.
Make sure that X11 forwarding is enabled in the ssh and sshd configuration of both machines.

In Ubuntu Hardy it is :
> 
$ grep -i X11 /etc/ssh/sshd_config 
X11Forwarding yes
X11DisplayOffset 10


---

### Post by cheeken on 2009-01-17
Thanks so much for the response.

I had actually given that approach a shot with no luck.  I am able to ssh -X successfully, and sshd_config contains the appropriate settings.  (Should ssh_config, in the same directory, also have those two lines?  They are commented out in mine.)

Unfortunately, I still get the "magic cookie" error in this -X session.

I noticed that DISPLAY is set to "localhost:11.0" in the -X session.  If my desktop is on port 0, shouldn't it be set to "localhost:0.0" or something similar?  Perhaps the problem lies therein?

---

### Post by albinootje on 2009-01-17
> **cheeken said:**
>  Unfortunately, I still get the "magic cookie" error in this -X session.


Let's say that your current machine is called comp A, and your remote host is called comp B.
Then comp A will need the X11 forwarding enabled on the ssh client that you use, and the config file for that is /etc/ssh/ssh_config.
Comp B will need to have X11 forwarding enabled in the ssh server, which means looking at /etc/ssh/sshd_config if editing that is needed.
Also, your remote host (comp B) will need to have the xauth command installed and in the PATH.

There's also the "ssh -Y" command, read these :

```

man ssh
man ssh_config
man sshd_config

```

And with ssh -X working as it should, there should absolutely no DISPLAY errors to worry about.

Beware.. you will need a (let's call it) "direct" ssh connection, using su or sudo on either or both sides of the connection will mess up things!

---

### Post by cheeken on 2009-01-17
Oops!  After reading your very precise explanation, I realized that I did not frame my problem clearly.  Sorry about the confusion; let me try again.

I have my Ubuntu machine, A, my other machine (not necessarily Ubuntu or even Linux), B, and a graphical app., such as gedit.  

I am ssh'ing into A from B.  I do **not** want to spawn a gedit window on B; I want to spawn one on a desktop of A - and I want to call this application from my ssh shell.  It can be assumed I know the port of the display I want to spawn gedit on, but I *don't* know the location of the Xauth file that desktop is using (if that makes any sense - I'm not really 100% sure what I'm talking about :)).

Again, sorry about not explaining clearly.  Please let me know if you need any more details.

---

### Post by albinootje on 2009-01-17
> **cheeken said:**
>  I have my Ubuntu machine, A, my other machine (not necessarily Ubuntu or even Linux), B, and a graphical app., such as gedit.  


[... misread]
As far as i can tell from my past and sparse experience with MacOSX and MS-Windows as clients in this setup, you would need to run a X alike software for this to work out of the box.

It's perhaps also possible without this, but I wouldn't know.

Here's a start :
[http://x.cygwin.com/](http://x.cygwin.com/) for MS-Windows, and..

[http://developer.apple.com/opensource/tools/X11.html](http://developer.apple.com/opensource/tools/X11.html) 
[http://cc.uoregon.edu/cnews/summer2002/xonx.html](http://cc.uoregon.edu/cnews/summer2002/xonx.html)
for MacOSX.

And it might be easier to just run VirtualBox with some minimal Linux distribution as guest VM inside the other OS.

---

### Post by The Cog on 2009-01-18
Just re-wording that, I gather you want to SSH into your Ubuntu box and use the SSH shell to launch a graphical app that appears on the Ubuntu box, not the box you are sitting at. As though the user had launched it.

I tried to do that once - I would like to SSH to my home PC from work and make xeyes appear full-screen while my son using the puter, as a practical joke. He'd think it cool that I could do that. I don't know how to do it though.

---

### Post by albinootje on 2009-01-18
> **The Cog said:**
> Just re-wording that, I gather you want to SSH into your Ubuntu box and use the SSH shell to launch a graphical app that appears on the Ubuntu box, not the box you are sitting at. As though the user had launched it.

Thanks for pointing that out again! 
I did misread that before :(

---

### Post by cheeken on 2009-01-19
> **The Cog said:**
> Just re-wording that, I gather you want to SSH into your Ubuntu box and use the SSH shell to launch a graphical app that appears on the Ubuntu box, not the box you are sitting at. As though the user had launched it.

Yes, this is precisely which I aim to do - thank you for stating it clearly.  Sorry about the confusion.

I will note that **I have gotten this to work** by ssh'ing into the Ubuntu box, su'ing to appropriate user, and setting the DISPLAY and XAUTHORITY environment variables to those of the desktop session.  After exporting those variables, any graphical application I launch in my ssh shell appears on the desktop as intended.

So doing this is a matter of figuring out the value of DISPLAY and XAUTHORITY on the desktop session (unless there's an easier way).  It's easy to figure out what the value of the DISPLAY variable should be, **but I don't know how to figure out which Xauth file the desktop session is using** (to set the value of XAUTHORITY) - and I don't know if there is a way to figure that sort of thing out outside of the desktop itself.

Any ideas?  Thanks again for all your help.

---

### Post by The Cog on 2009-01-19
The command **who** will tell you who is logged on on tty7 which is the GUI console. It looks to me like it would be that user's ~/.Xauthority file.

---

### Post by txcrackers on 2009-01-20
If you have the user's password, you *can*] ssh into the box, even if the user is logged in on that box. When SSH is tunnelling X, it uses a special DISPLAY setting (typically 10:0), so anything that attempts to write to X ends up piped back to your display and never to the "default" display.

---

