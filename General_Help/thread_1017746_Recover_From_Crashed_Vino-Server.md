---
title: "Recover From Crashed Vino-Server?"
date: 2008-12-21
forum: General Help
---

### Post by bc90021 on 2008-12-21
All,

My vino-server program seg-faulted as seen in the output from dmesg:

[4279158.019694] vino-server[6485]: segfault at 280bf654 eip 08061eb3 esp bfc53690 error 6

I have done a couple of hours worth of searching on the internet, and have no found a satisfactory way to restart vino-server.

The closest answer I have found is to run "/usr/lib/vino/vino-server &".  However, when I SSH to the box and run that command, I get the following:

user@host:~$ No protocol specified

(vino-server:14940): Gtk-WARNING **: cannot open display: :0.0

[1]+  Exit 1                  /usr/lib/vino/vino-server

It seems ridiculous to me that:

1)  This is not easy.
2)  There is no documentation for this process.
3)  There is no man page for vino-server.
4)  Vino-server is not a service that can be stopped and started in /etc/init.d.
5)  I might be required to reboot the machine in order to fix this issue.

Note that I do NOT want to reboot the machine.  I am aware that that may be necessary; however, this being a simple service there should be a way to restart it that does not require rebooting the machine.

Any help would be greatly appreciated.

Thanks.

---

### Post by cariboo on 2008-12-21
There is no vino-server command. THe only two vino commands are vino-preferences and vino-password. To start vino on your server you will need x-forwarding. Use this command:

```
ssh -X user@server
```

Then run vino-preferences.

Jim

---

### Post by bc90021 on 2008-12-21
Jim,

Thanks for the reply.  I have done what you suggested.  When I do ssh -X user@server, I am logged in to the remote machine.  Running "vino-preferences" from the command line gives me the vino-preferences screen on my local machine.

However, I am still unable to use VNCViewer to connect to the remote machine.

If I run "/usr/lib/vino/vino-server &" with the ssh -X command, I can connect, but I don't get the VNCViewer window.  However, that executable definitely does exist, and it's definitely what starts GNOME's remote desktop.

Thanks for your help.

---

### Post by bc90021 on 2008-12-21
Running "/usr/lib/vino/vino-server" using X forwarding through SSH is not proving to be useful.

In essence, the VNC Server is trying to use the local machine's X to run VNC Server, which isn't helpful.  I can run it, and I can connect, but it creates a loop.  I can see this because when I kill the terminal in which vino-server is running, the connection dies.

I need a way to restart the vino-server on the remote machine - this should be MUCH easier than this...

---

### Post by bc90021 on 2008-12-23
Bump... anyone got any ideas?

---

### Post by Ms. Phitt on 2008-12-26
This seems to work:

[http://ubuntuforums.org/showthread.php?t=266981]("http://ubuntuforums.org/showthread.php?t=266981")

---

### Post by GreenN00b on 2009-05-13
Had a similar issue and after some research I found a solution.

Assuming you have a machine running with user x logged in and vino-server not running use the following steps to start it:

1. ssh to that machine and authenticate as x
2. sudo -s to become root
3. export DISPLAY=:0.0
4. xhost +
5. exit from root shell using exit
6. export DISPLAY=:0.0
7. start vino-server using /usr/lib/vino/vino-server

---

### Post by khaeru on 2009-11-09
I was having the same problem as bc90021, and the solution in the thread linked to by Ms. Phitt didn't work.

GreenN00b's suggestion worked, but I didn't need to take the step of opening a root shell:
```

user@local:~$ ssh remote
user@remote:~$ DISPLAY=:0.0 /usr/lib/vino/vino-server&
[1] 9211
```
...at this point vino-server began spitting out messages to the command line. I used Vinagre as usual from the local machine to connect. When my VNC session was done, I typed Ctrl+C in the ssh session to return me to a prompt, and then:
```

user@remote:~$ kill -HUP 9211
[1]+  Hangup                  /usr/lib/vino/vino-server
```

To go back to bc90021's comments:
> 
1) This is not easy.
2) There is no documentation for this process.
3) There is no man page for vino-server.

Agreed, this is bad. See LP#[lpbug]292994[/lpbug].

> 4) Vino-server is not a service that can be stopped and started in /etc/init.d.
There is a reason for this. As far as I can tell, vino allows access only to an active session of the user who starts it. If albert wants to allow remote access, but bill doesn't, they establish this by enabling/disabling vino individually. If albert isn't logged in, no instance of vino-service runs for him; this saves resources.

There are instructions elsewhere about how to set up VNC servers that will give you the GDM login screen when you connect, and allow you to log in as any user. However, these don't give you the option to connect to an existing GNOME session. I would like to see this integrated with the desktop; currently it takes some work to set up.

> 5) I might be required to reboot the machine in order to fix this issue.
Turns out not :)

---

### Post by dushuahuja on 2010-07-17
Thanks khaeru - that worked for me (finally)
I'm using a mythbuntu setup - and the system logs in automatically. Is there any way to make sure that the server starts automatically without having to give this command via ssh.

---

### Post by phazei on 2011-02-06
> **GreenN00b said:**
> Had a similar issue and after some research I found a solution.

Assuming you have a machine running with user x logged in and vino-server not running use the following steps to start it:

1. ssh to that machine and authenticate as x
2. sudo -s to become root
3. export DISPLAY=:0.0
4. xhost +
5. exit from root shell using exit
6. export DISPLAY=:0.0
7. start vino-server using /usr/lib/vino/vino-server

Hate to bump this old thread, but it's the only one I've found that's come closer to helping.
I'm trying to be able to remote into the VNC server so I can see the login screen after the system boots and isn't logged in yet.  If I do this, then vino-server does actually run and shows me connecting, but then it gives the error 

> 06/02/2011 12:42:22 AM Advertising security type 18
06/02/2011 12:42:22 AM Advertising security type 2
06/02/2011 12:42:22 AM Client returned security type 2

** (vino-server:1858): WARNING **: VNC authentication failure from 'xxx.cox.net'

06/02/2011 12:42:30 AM rfbAuthPasswordChecked: password check failed
06/02/2011 12:42:30 AM Client xxx.cox.net gone



I'm using a password that works if I manually log in from the server locally.  But it doesn't read the correct password when I manually start vino-server or something.

Is there a better way to do this now?  Or any other ideas ?

---

### Post by InnerBushman on 2012-11-27
As for U11.10 the vino-server can be restarted from terminal by running:
```
vino-preferences
``` OR from Menu:
```
Applications -> Internet -> Desktop sharing
```Then in preferences window that will open, disable and re-enable the sharing completely. Clear and then set back the box for:
```
[ ]Allow users to view your desktop.
```This will successfully restart vino-server with all the proper settings.


Cheers,
Bushman

PS: this post is not to solve the old case, it's for new users having problem restarting their vino. Hope that helps anyone.

---

