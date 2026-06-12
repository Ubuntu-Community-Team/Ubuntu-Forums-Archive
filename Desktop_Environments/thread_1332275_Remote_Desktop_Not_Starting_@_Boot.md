---
title: "Remote Desktop Not Starting @ Boot"
date: 2009-11-20
forum: Desktop Environments
---

### Post by xcurtisx on 2009-11-20
Good day. I recently install 9.1 and configured the built in VNC server so I can remote to it from my vista box.
I got it all working and was happy, until I rebooted the Ubuntu box. The system doesn't start the remote desktop server at boottime even though it is listed in the "start Up" utility.
How do I fix this or is this a known bug and being worked on?
I did search but didn't find many ideas on how to fix, more just alteritive options.
Would rather fix the pre-package tools.
Thanks!
:p

---

### Post by xcurtisx on 2009-11-21
Bump.. since we have gotten no love.
:D

---

### Post by gerowen on 2009-11-21
I have the same issue, I run 9.10 server edition and installed Gnome so I could do some graphical configuration, and if I reboot I have to actually get on the server, open and close the preferences window for the Remote Desktop and then it works.

---

### Post by doas777 on 2009-11-21
how did you configure your network card settings? through the gui, or in your /etc/network/interfaces file?

in ubuntu, they use gnome-network-manager for network connections, but it runs after the user has logged in. prior to login, the network is off-line. they do it that way for wifi connectivity, since many wifi users connect to many different networks, so connection would have to start after the user could interact and choose one.

the best fix, is to configure your interfaces file. if your network configuration resides there, it will start at boot, not at login.

here is a guide to manually configuring your network connection:
[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

---

### Post by gerowen on 2009-11-21
> **doas777 said:**
> how did you configure your network card settings? through the gui, or in your /etc/network/interfaces file?

in ubuntu, they use gnome-network-manager for network connections, but it runs after the user has logged in. prior to login, the network is off-line. they do it that way for wifi connectivity, since many wifi users connect to many different networks, so connection would have to start after the user could interact and choose one.

the best fix, is to configure your interfaces file. if your network configuration resides there, it will start at boot, not at login.

here is a guide to manually configuring your network connection:
[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

The issue isn't the network connection, it's the fact that the built-in Ubuntu Remote Desktop daemon doesn't start until you actually log on, open the preferences window and close it again.  This isn't a huge issue for me now, I do all of my maintenance and changes via SSH, but it'd still be nice to know how to get it to start the Remote Desktop daemon on startup/login.

P.S. Just in case I missed what you were trying to say, I did configure my connection manually via command line.

---

### Post by xcurtisx on 2009-11-21
I will look when I am back at the oiffcer where the box is, but I think (if memory serves) that I can ping the IP (static 192..) once the computer is at log in. But can not VNC. Like I said will have to check. I used the network config tool that comes stock form the right click on the network icon in the upper tray - didn't take note of the name.

---

### Post by xcurtisx on 2009-11-21
> **marcusdean.adams said:**
> The issue isn't the network connection, it's the fact that the built-in Ubuntu Remote Desktop daemon doesn't start until you actually log on, open the preferences window and close it again.  This isn't a huge issue for me now, I do all of my maintenance and changes via SSH, but it'd still be nice to know how to get it to start the Remote Desktop daemon on startup/login.

P.S. Just in case I missed what you were trying to say, I did configure my connection manually via command line.
That is what I thought it was and if a service is meant to start "at boot time" then it must in my opinion. This is a bug then.

---

### Post by xcurtisx on 2009-11-23
Bump - 
any new suggestions?
anyone know if this bug has been reported?

---

### Post by doas777 on 2009-11-23
it;s not really a bug, per se. vino was designed to work as you describe. it shares the interactive session, and it cannot do that, if there isn't an interactive session. 

there are a couple of options.
1) install freenx. I use it and love it. ([https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX))
2) install a full vnc server ([https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC))

---

### Post by xcurtisx on 2009-11-23
> **doas777 said:**
> it;s not really a bug, per se. vino was designed to work as you describe.

there are a couple of options.
1) install freenx. I use it and love it. ([https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX))
2) install a full vnc server ([https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC))

Just so I am clear - you use the built in remote desktop server, set to start at boot time.
Its doesn't start at boot time = working as intended?:o

---

### Post by doas777 on 2009-11-23
> **xcurtisx said:**
> Just so I am clear - you use the built in remote desktop server, set to start at boot time.
Its doesn't start at boot time = working as intended?:o

are you sure the server itself is not starting, or is it that it is not allowing you to connect to it?
regardless the ubuntu configuration for vino requires the sharing of a session. this cannot occur if there is not yet a session. the server may be started, and just rejecting, or it may have attempted to start, realized that it lacked a precondidtion (a session to share), and aborted then.

additionally, the reason that it is set up this way, is because the settings are per user. if we shared a machine, you might allow vnc connections to share your session, but I might disable it. how does the machine know whether to allow or deny, until it knows who is logged in? 

look into freenx. I think you;ll like it.

lastly, setting a service to start at boot, may cause it to launch before X. since vino requires X, it is likely crashing because it has been reconfigured to start at boot.

---

### Post by gerowen on 2009-11-23
Well I'm not sure if it was part of a recent update, but mine seems to work now.  I've done a couple of remote restarts as a test and it seems to be kicking on as intended now.  Try making sure you have installed all of the updates because I didn't change anything other than installing updates.

---

