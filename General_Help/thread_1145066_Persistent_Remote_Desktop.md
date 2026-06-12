---
title: "Persistent Remote Desktop"
date: 2009-05-01
forum: General Help
---

### Post by Mobby on 2009-05-01
Hi,
  I've tried to do some research and I've seen quite a bit of documentation but I've not quite found how to do the thing I want to achieve. I have a Windows XP setup which works nicely and I would like to see if the equivalent is possible in Ubuntu and if it is then get some hints/guides on how to achieve it. So here goes...

Current setup:
  * Windows XP at home wired to router (WRT54g with Tomato firmware).
  * Cable broadband going through WRT54G which is running an SSH Server.
  * Windows XP at work. Cygwin with openssh.
  * I have set up SSH tunnelling to go through my router at home. This allows me to remote desktop into my windows box at home (normally blocked by works firewall) and it is done securely as well. This also means I don't have to open the RD Windows ports direct to the internet (i.e. port forwarding), the only outside port is SSH and the tunnel sorts out the rest for me. A pretty standard setup for this type of thing I think. 
  * I have also set up a wake-on-lan script on the router so it will wake up my PC. I use the SSH to the router to invoke the script and wake up my PC. Once the PC is up and running the SSH tunnel is set up and I can remote desktop into the PC.

The bit I would like to achieve through Ubuntu:
-----------------------------------------------
  * I use Windows XP Remote Desktop client to log in at home. I do my thing and I can leave the session running and come back to it when I want to.
  * Or if the machine was already running, once the tunnel is established I can re-attach to the running session with Remote Desktop.

...So can I achieve this with Ubuntu?

What have I tried?

Ubuntu Remote Desktop:
  Well if you enable the remote desktop option in Ubuntu as far as I'm aware this is a VNC server and requires the user to be already logged in so the desktop is showing. So to achieve this I would need to automatically log in my user account on startup, which I don't want to do as there are multiple accounts on the PC.

Freenx:
  Tried this only quickly (not had much time to play with this) and although I got it working it didn't quite do what I wanted. When I logged in it showed me a completely new desktop, rather than the setup I have for the account I thought I was logging into. Is there a freenx setup which achieves the same as my windows setup?

So to summarise I would like to:
   * Be able to attach to an existing session (E.g. I logged into the PC at home one evening and left the PC on. The next day I decide to attach to the existing session once I was in work). At this point I would like to see it as I left it the day before.
   * Be able to start my PC up (that bit is already done and working), give it chance to startup and then remote desktop into the PC without having to auto-login any user.

Sorry for the long post. Hopefully this is in the right section and I've tried to search around but I'm getting a bit lost and confused.

Thanks in advance,
Mobby :confused:

---

### Post by Brandon Williams on 2009-05-01
This is not exactly what you're looking for, but close (I think).

With VNC, you can have multiple sessions active at any particular point in time. If there are multiple users on the system, then you can have a separate VNC session for each user, and you would simply connect to the correct VNC session to get the correct user's desktop.

If there is no active session for the specific user, you simply SSH to the box and start the server before starting up the VNC client.

It's possible to configure VNC to autostart when you try to connect to the port if it isn't already running and to do it in such a way that you can log in as whichever user you want. However, IIRC, it's difficult to do it in such a way that other users would not be able to easily get access to a session for another user. Starting the VNC session as the intended user gives that user greater control over who may or may not have access.

A shortcoming of this approach is that if what you want to do is share an active session that was not originally a VNC session, you still have to have direct graphical login access to the machine. I don't mind this, since I never share out a session that wasn't originally a VNC session. Instead, when I want local access to the desktop, I login on the machine and then run the VNC client in full screen mode.

---

### Post by Mobby on 2009-05-01
Hi,
  Firstly thank you very much for the reply. My comments inline...

> **Brandon Williams said:**
> This is not exactly what you're looking for, but close (I think).

With VNC, you can have multiple sessions active at any particular point in time. If there are multiple users on the system, then you can have a separate VNC session for each user, and you would simply connect to the correct VNC session to get the correct user's desktop.

If there is no active session for the specific user, you simply SSH to the box and start the server before starting up the VNC client.

*[COLOR="Blue"]So once the VNC server is started, when I connect via the VNC client I would get the same desktop appearence as if I were logging in locally?[/COLOR]*

It's possible to configure VNC to autostart when you try to connect to the port if it isn't already running and to do it in such a way that you can log in as whichever user you want. However, IIRC, it's difficult to do it in such a way that other users would not be able to easily get access to a session for another user. Starting the VNC session as the intended user gives that user greater control over who may or may not have access.

*[COLOR="Blue"]It would not be a problem as the other accounts would not be logging in remotely at all, they wouldn't know how to ;) I just didn't really want to auto-login a particular account on startup.[/COLOR]*

A shortcoming of this approach is that if what you want to do is share an active session that was not originally a VNC session, you still have to have direct graphical login access to the machine. I don't mind this, since I never share out a session that wasn't originally a VNC session. Instead, when I want local access to the desktop, I login on the machine and then run the VNC client in full screen mode.

*[COLOR="Blue"]Sorry I think you've lost me a little bit with this last part :) I would still like to be able to login normally when I'm at home and use the PC as normal. Just should that "normal" session be logged in, when I'm in work I would like to be able to attach to it and carry on using it.  [/COLOR]*



So as far as I understand from what you say I could do this...

Start Machine:
* Get the machine running.
* SSH in as the desired user.
* start the VNC server.
* Connect using VNC Client.
* I would see desktop as if I had logged in locally.

Existing Session (i.e. logged in at home previously)
* The VNC Server would have already been started because I logged in locally.
* Simply attach VNC Client to existing session.

Have I got the right idea? It won't surprise me if I haven't :D

Once again many thanks for your help!
Mobby.

---

### Post by Mobby on 2009-05-01
Sorry I must admit I didn't read the VNC guide but since you have suggested it I did a little reading...

So if I have VNC running in "Service" mode I should be able to achieve what I'm looking for. I.e. if the PC has just started once I connect to it I will just be shown the noraml Ubuntu login screen. So I would log in via the Ubuntu log in screen as if I were sat at the machine and carry on as normal. Where as if I had already started the machine and logged in locally, when I connect via the VNC client I would just see the desktop as I left it (i.e. logged in, locked, etc.).

Does this sound correct?

Thanks,
Mobby.

---

### Post by Brandon Williams on 2009-05-01
That sounds mostly correct ... the only issue is your desire to be able to reboot remotely. If you SSH into the box and start the vncserver running, it won't be associated with a local login session, so I don't think that you will be able login locally and get that desktop to pop up.

Instead, you would have to login locally and then, within the local environment, use the vnc client to connect to the locally running vncserver. This can lead to problems if both the local login session and the vnc session are using the same window manager and/or desktop manager. It's a bit painful (but possible) to get around these problems. I can give you details of how this might be accomplished if you decide to go this route.

I don't use the vino server, which is better integrated with Gnome, IIRC. It may be that the functionality you're describing is specific to the vino vnc server. Hopefully, someone more familiar with vino will comment.

---

### Post by Mobby on 2009-05-01
Ok great, I'll have a play around and I'll post back here when I get any further. Thank you very much for your help. I'm on holiday for the next week so it might be a while before I post back so don't think I've given up :D 

If anyone else has any suggestions please feel free to comment, I'll check it all out when I get back.

Once again many thanks.
Mobby.

---

### Post by Brandon Williams on 2009-05-01
[This thread](http://ubuntuforums.org/showthread.php?t=983991) might also be of interest to you, if you haven't already seen it.

---

