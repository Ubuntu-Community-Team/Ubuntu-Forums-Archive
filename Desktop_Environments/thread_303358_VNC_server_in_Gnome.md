---
title: "VNC server in Gnome"
date: 2006-11-20
forum: Desktop Environments
---

### Post by allebone on 2006-11-20
Hi there

I have just installed Ubuntu 6.10 x86 on a laptop at home. 

After installation I set-up via login screen prefs for Gnome to auto login using the only user (peter).

I then set-up under remote desktop prefs users to be able to access the desktop via VNC with a password and no confirmation.

I then tested this from a windows machine using UltraVNC. This worked correctly and I could control the screen after typing in the password.

However if I restart the Ubuntu box, after it auto logs in i cannot access the box via VNC. The error states incorrect password. Resetting the password resolves this issue.

The password contains alphanumeric characters and an asterisk only.
I have tried different passwords. This did not help.

No updates or additional software was installed.
I have subsequently installed openssh-server. This allows me access to the command line after a reboot (using putty). However I cannot figure out how to reset the password via the command line for the VNC server, and don't know why rebooting loses the password every time.
I have tried typing "vncpasswd" at the terminal. This does not appear to reset the password so am unsure what this command is doing, however it is possible that i need to restart the VNC server after doing this but don't know how.

Any suggestions on how to reset the password via ssh, or make the password persistent would solve my problem.

Kind regards
Peter

---

### Post by allebone on 2006-11-20
To add to the discussion - 

The reason why I wanted auto login was because I did not know how to enable the VNC server at the login screen. I dont believe this to be possible as it seems to bind to a user. 

However if you can explain how to enable the VNC server at the login screen so auto login can be disabled, this will be even more helpful.

Peter

---

### Post by Quietlife on 2006-11-20
For what it's worth I use the following procedure under 6.06 :

Install your choice if vnc sever.
Install xinetd (may be different under upstart/6.10)

in /etc/xinetd.d create a file called Xvnc which looks like :
```
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :3 -query localhost -geometry 1100x900 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}
```

you will also need to create the /root/.vncpasswd with

```
vncpasswd /root/.vncpasswd
```

now connect to 5901 (NOT 5900) with your vnc client.

et. voila login screen.

You will of course want to change the resolution, depth and port to values more suitable to your own config.

Hope this helps.

UPDATE
This does not share the console gui it creates a new x session. I.E. it does not "take control" over the remote desktop - it simply creates a headless gnome/x session.
ENDUPDATE

UPDATE 2
You will also need to enable xdmcp to honour indirect requests - under 6.06 this is found in :
System -> Administration -> Login Window
On the tab named "Remote" hit "Configure XDMCP" and put a tick in the "Honour indirect request" check box.

After all this both xinetd and gdm (gnome destop manager I think) will need restarting.
ENDUPDATE 2

---

### Post by allebone on 2006-11-20
Hi there

I have thought of this but this is not a solution for me due the the reasons that you have pointed out.

I need to be able to take over the desktop that is currently logged in as I wish to have items open that I can then login remotely and monitor etc.

Is there anyway to reset the password after it has forgotten it?

Peter

---

### Post by Quietlife on 2006-11-20
Sorry I'm afraid I have no idea, BUT just a thought.

If you were to run your apps in a "headless" session, there is nothing stopping you from connecting to that session via vnc from the machine itself.

I.E.
Startup your machine and log in, then kick off a vnc session to the "headless" x session on the same box and run what you need to, disconnect from vnc and log out of your box. Now go to another machine and vnc into the already pre-configured session with all the bits you need.

Not choice, but if all else fails........

Hope you find a solution.

---

### Post by tbresson on 2006-11-20
I have the exact same problem with my Ubuntu 6.10.

I had no problems with 6.06 and my 6.10 install is a fresh clean install. It's like the password is not saved when rebooting or something.

---

### Post by allebone on 2006-11-20
Hi there - I opened this question and now considerer it closed.

The answer is there is a bug in the Vino package.
This will be released as a **security** update when a fix is available.
Please see the website for details on this and a workaround for people who cannot wait for the security fix.

[https://launchpad.net/distros/ubuntu/+source/vino/+bug/65795](https://launchpad.net/distros/ubuntu/+source/vino/+bug/65795)

This page is not always available for some reason.

Kind regards to those who responded to my post
Peter

---

### Post by Mr Green on 2006-12-03
I hope they fix this soon. I can understand how bugs like this slips through the testing but I can't understand why it isn't fixed yet. It's a pretty severe bug in a very important part of the OS!

---

