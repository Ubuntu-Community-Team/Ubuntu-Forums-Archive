---
title: "Yet Another VNC Question"
date: 2006-01-07
forum: Desktop Environments
---

### Post by shawnerz on 2006-01-07
All,
I have a headless machine running Ubuntu.  I can ssh to it using putty.  My question is how do I start the VNC server from the command line?
Thanks in advance,
-Shawn

---

### Post by btdown on 2006-01-07
> vncserver -rfbport 80 -geometry 1280x997 -depth 24
Is what I use... -rfbport specifies the port you want it to run on. I use port 80 as my workplace firewall blocks basically everything. If you dont specify rfbport it defaults to like 5800/5801/5900/5901 cant remember which. Also i have had problems when I set the depth above 24, so dont do it.

---

### Post by riiidaa on 2006-01-07
[QUOTE=shawnerz]All,
I have a headless machine running Ubuntu.  I can ssh to it using putty.  My question is how do I start the VNC server from the command line?
Thanks in advance,
-Shawn[/QUOTE]

It's already running if you do top and can see vino-server.

I haven't worked out how I can get it to allow connection after reboot without having to console into the server directly JUST to log into Gnome so I suspect we are in the boat...

Can anyone give us a clue as this server is blinkin noisey and i wanna be able to stick it well out the way of earshot :razz:

---

### Post by shawnerz on 2006-01-07
Wow! That was a very fast reply. :)
I am getting an error saying "command not found"
I thought it might have been a file path issue, so I did a ./vnc....  same result.
If I attach the keyboard, mouse and video and start the server in Ubuntu Remote Desktop, it works fine.  I'm just trying to start the server without having to be in front of the box.
Thanks,
-Shawn

---

### Post by riiidaa on 2006-01-07
[QUOTE=shawnerz]If I attach the keyboard, mouse and video and start the server in Ubuntu Remote Desktop, it works fine.  I'm just trying to start the server without having to be in front of the box.
-Shawn[/QUOTE]

We are in exactly the same boat then

---

### Post by riiidaa on 2006-01-07
[QUOTE=riiidaa]We are in exactly the same boat then[/QUOTE]

YES, I have a solution, go into Gnome on the server then click System > Administration > Login screen setup 

in here you can get over our problem by ticking:

Automatic login, and selecting your username :D

There are other tabs with all sorts of GDE goodies - have a butchers


#ps - twigged this after a search and reading [http://ubuntuforums.org/showthread.php?t=102438&highlight=vnc+server](http://ubuntuforums.org/showthread.php?t=102438&highlight=vnc+server)

---

### Post by shawnerz on 2006-01-07
riida,
Can I do that from the ssh login?  I don't think it will work.  

I'm on a Windows machine and connnecting to my (Ubuntu) linux machine via ssh (I'm using putty to make the ssh connection).

The end result is to start the VNC server so I can connect to the linux box from the Windows box with VNC.

Thanks,
-Shawn

---

### Post by riiidaa on 2006-01-07
[QUOTE=shawnerz]riida,
Can I do that from the ssh login?  I don't think it will work.  

I'm on a Windows machine and connnecting to my (Ubuntu) linux machine via ssh (I'm using putty to make the ssh connection).

The end result is to start the VNC server so I can connect to the linux box from the Windows box with VNC.

Thanks,
-Shawn[/QUOTE]

if vino-server [vncserver] is running from boot  up then you don't have to kick it off manually using ssh. (This is not ideal for you?)

The instructions i have presented expect you to be able to go to the machine with a keyboard, mouse and monitor just to make the prescribed configuration change. (Go to the physical box to set this up, a one off)

After that then you can remove the monitor etc and be 2100 milles away if you really wanted bacause after reboot you can log in using vncviewer from whatever remote location you wanted.

This is working for me now, i just need to adjust the resolution vnc server projects cos its a tad postage stamp like for the minute...

- 

if I have our wires crossed and you are actually talking of ssh for a reason that perhaps isn't all that clear, i.e. you want the remote desktop connection to your box to be encrypted then i think you need to bin vnc server and putty right out the window and set up x11 forwarding with an ssh client that's got proper x11 support = a project I'm not gonna tackle just yet

---

### Post by shawnerz on 2006-01-07
I am using ssh for two reasons: 1, it's (relatively) secure and 2, the windows box and the linux box are behind two spearate firewalls/routers that have the VNC port (port 5900) blocked.  The ssh ports (port 22), are open on both ends.

Is the solution to my problem as easy as 'service start vino-server.'?

---

### Post by riiidaa on 2006-01-07
[QUOTE=shawnerz]I am using ssh for two reasons: 1, it's (relatively) secure and 2, the windows box and the linux box are behind two spearate firewalls/routers that have the VNC port (port 5900) blocked.  The ssh ports (port 22), are open on both ends.

Is the solution to my problem as easy as 'service start vino-server.'?[/QUOTE]

Nope, with what you've said the bit about scrapping vnc server and going x11 applies - you need to edit 2 lines at least in your sshd config and then get a better ssh client for windows - I'm told Cygwin is the one you want over putty any day - as it supports proper x11 forwarding over ssh.

I wanna do this cos it'd be more secure than vnc and basically forwards your actual Xsession to your windows box. More sophisticated and complicated i think so I'll not run before I can walk as they say, (Ironic as I'm actually a wheelchair user) however THATS gotta be what your ultimately after!

HTH

---

### Post by riiidaa on 2006-01-07
See [http://ubuntuforums.org/showthread.php?t=113627](http://ubuntuforums.org/showthread.php?t=113627) about x11

See [http://www.cygwin.com/](http://www.cygwin.com/) for a proper ssh client, apparently it supports x11 far better than putty

---

