---
title: "Remote Desktop with a GUI"
date: 2008-11-18
forum: Desktop Environments
---

### Post by globex on 2008-11-18
Wow, I would have never thought this to be so difficult on a Linux machine... here is what I want.

I have a computer running Ubuntu 8.10 and I have a computer running Windows XP. I want to be able to have the Ubuntu computer viewable on my Windows XP computer via some sort of remote desktop application (LogMeIn, RealVNC, NoMachine).

In other words, I want Ubuntu to be the server and Windows to be the client.

LogMeIn doesn't have a server for Linux.
RealVNC doesn't have a GUI for Linux, and I can't figure out how to install it via konsole commands.
NoMachine doesn't seem to have a free server for Linux.

Can I get some help please?

---

### Post by eppo on 2008-11-18
i use tightvncserver.
sudo apt-get install tightvncserver
then type tightvncserver as the user you want to start the vnc server as. it will prompt you for a password.
then on the windows box grab a copy of tightvnc for windows, and start up the client. the target will be something like ipaddress:1

---

### Post by globex on 2008-11-18
> **eppo said:**
> i use tightvncserver.
sudo apt-get install tightvncserver
then type tightvncserver as the user you want to start the vnc server as. it will prompt you for a password.
then on the windows box grab a copy of tightvnc for windows, and start up the client. the target will be something like ipaddress:1

Well that was easy as can be! Thank you very much.

---

### Post by globex on 2008-11-18
Appears that tightvnc doesn't work with KDE. I even tried this: [http://ubuntuforums.org/showthread.php?t=44836](http://ubuntuforums.org/showthread.php?t=44836)

But when I connect to it via tightvnc client on Windows it loads a GNOME session. How do I get it to show what's currently on the Linux machine's screen?

*EDIT* I've also tried tightvnc and realvnc via krfb and I still see a GNOME session.

---

### Post by sauce345 on 2008-11-18
Ubuntu comes with a built vnc server.  I believe it is under system->preferences->remote desktop.  Any the most secure way to do this from anywhere is set up an ssh tunnel.

Install the ssh server:
sudo apt-get install openssh-server

Now make sure you set a password under the remote desktop and also un-check the user confirmation.

Now if your just on your network install, download putty on the xp machine and run it.  Fill in your ip address for your linux box and click on make sure it is set to ssh.  Then under connection click on data and input your username.  Then expand the ssh on the left and click on tunnels.  Add <your ip>:5900 then for port add 5900.  Now connect with putty and minimize, download and install tightvnc (you just need the viewer) and when you open type 127.0.0.1 or localhost then type the password set on the linux box for remote viewing and BAM your controlling your linux box. :)

If you want to do this from anywhere change your router to forward port 22 to your linux box.

---

### Post by globex on 2008-11-18
I've tried using the built in vnc server (krfb), but whenever I connect to it (via tightvnc or realvnc) it loads a GNOME session, not the KDE session that is currently running.

---

### Post by sauce345 on 2008-11-18
I know this probally doesn't help but that is obviously something in the krfb config file.  It must be loading a default value, i have no idea what the file is or where it is at but i am guessing that is what you have to change.

---

### Post by globex on 2008-11-18
I restarted the computer and now I'm able to connect via krfb, however as soon as I connect the client windows shows a frozen KDE desktop and I can't click or move or do anything. I've tried several VNC clients. The computer isn't crashed, but the client's content is frozen. Any ideas?

*edit* Alright, it looks like there's a problem with the client? Because if I click on things in the frozen client window, things move around correctly on the server side. Except of course all I see on the client is a frozen image.

*edit2* I found the issue here [http://bugs.kde.org/show_bug.cgi?id=162493](http://bugs.kde.org/show_bug.cgi?id=162493) but no solution.

---

### Post by compuco on 2008-11-26
Have you resolved this issue as I too would like to have this working.

---

### Post by Nixie Pixel on 2008-11-26
> **sauce345 said:**
> Now connect with putty and minimize, download and install tightvnc (you just need the viewer) and when you open type 127.0.0.1 or localhost then type the password set on the linux box for remote viewing and BAM your controlling your linux box. :)

If you want to do this from anywhere change your router to forward port 22 to your linux box.
Where am I downloading and installing tightvnc to, the server or the XP machine that I am connecting to the server with?

I tried taking these steps, and I have a valid SSH connection to my linux box, but I tried running TightVNC from my XP machine and am unable to connect via the instructions above.  Should I be installing the TightVNC viewer on the linux box (through my SSH tunnel)?

Thanks!

~Nix

---

### Post by Nixie Pixel on 2008-11-26
Ok, I installed tightvncviewer on the server, but it won't let me connect, it says it can't open the display.

---

### Post by t.s on 2008-11-26
Try installing realVNC on windows and use Vinagre (default remote desktop viewer on Ubuntu)..

good luck (well, I have it run smoothly accessing windows PC from my Linux box. I hove it can do vice versa).

---

### Post by Stephen_at on 2008-11-26
Nomachines do a free Client and Server for Linux. I've got it running here. They even ship debian packages. The Windows client is free too and it works very well.

Download the three packages from 

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

 and install them on your linux box

Download the Windows Client

[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)

and install it and off you go.

Dont forget that these are "new" sessions. That if your machine is running you dont get the existing desktop on you linux box. You get a whole separate login (with the ability to disconnect and reconnect later without logging out)

---

### Post by ugm6hr on 2008-11-26
> **t.s said:**
> Try installing realVNC on windows and use Vinagre (default remote desktop viewer on Ubuntu)..

good luck (well, I have it run smoothly accessing windows PC from my Linux box. I hove it can do vice versa).

Yes you can. It works flawlessly.

Not sure why others have had issues - I only use Gnome.

---

