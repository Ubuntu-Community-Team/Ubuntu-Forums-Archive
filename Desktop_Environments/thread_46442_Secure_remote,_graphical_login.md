---
title: "Secure remote, graphical login?"
date: 2005-07-04
forum: Desktop Environments
---

### Post by speedsix on 2005-07-04
Have read lots of info about the forum but I'm not getting anywhere.

I want to log into my home ubuntu machine from my windows box at work without tieing up the machine at home, similar to terminal services for windows.

I've looked at tslp but it looks a little overkill for what I need, I also try to follow the vnc4server faq in the HOW_TO section but couldn't seem to get hte server to run.

Many thanks 

Dom

---

### Post by X3N on 2005-07-04
As far as i know, VNC would tie up your box at home because it is just like a remote desktop controlling tool. 

I think your best bet would be to install openssh-server on your computer at home and use something like "putty" in windows to login. This wouldn't give you gui though.
The only ways i can think of to do that would involve installing an X server on your windows machine at work and using something like X11 forwarding on ssh or XDCMP, which i've done in cygwin before, not very easy to setup on windows though.

i'd be tempted to use a live distro at work and use ssh -X

---

### Post by speedsix on 2005-07-05
Thanks..

So with X is the X windows server the machine with the input/output devices (keyboard/screen etc.) and the client the hardware end?


Cheers

DOm

---

### Post by cwaldbieser on 2005-07-05
The X-Server is really the X *Display* Server.  It is the machine with the monitor attached.

There are comercial packages for Windows like Exceed that provide a decent X Server for Windows.  You can use Cygwin to set it up yourself, but it takes a little work to configure it, and it is a bit slow.  My best experience has been with Topologilinux-- a Linux installation that lives in a file on your Windows partition ([http://www.topologilinux.com/)](http://www.topologilinux.com/)).

VNC with your Ubuntu machine as the VNC Server doesn't have to tie up your home machine.  Some packages like vncserver create a "virtual desktop" on the X Client that gets sent to your display server.  If you want it to be secure, though, you will still need to forward it through an SSH tunnel.

---

### Post by daedalus_nl on 2005-07-08
work ------------[ X session ] ---> home
(windows)                           (ubuntu)


this setup is easy  :)

1st - install cygwin on your work computer
link: [http://www.cygwin.com/]("http://www.cygwin.com/")

you only need to install the X components




[list]
[*]remark: select uninstall on everything, then, select the X components (fonts, x-server etc etc
[/list]do not forget to put   *c:\cygwin\bin*   in your PATH on your work computer


2nd - install ssh on your ubuntu computer
[i]sudo apt-get install ssh


[/i]3rd - install a ssh client on your work computer
putty is a good one
Putty download link:  [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html")

now you just have to create the PuTTy X Window Configuration
howto: [http://www.msi.umn.edu/user_support/xclient/xwin_config.html]("http://www.msi.umn.edu/user_support/xclient/xwin_config.html")

[list]
[*]for information about forwarding port 22 to your inside home computer,see [http://portforward.com/]("http://portforward.com/")
[/list]4rd - startup   X on your work computer (*c:\cygwin\usr\X11R6\bin\XWin.exe*)

 and login to your home computer using ssh
after that, start your x session :   [i]gnome-session


[/i]in a nuttshell connecting from your work to your home computer

---

### Post by jcohen on 2005-07-08
This can be easily done with VNC. Ubuntu's included remote desktop runs VNC on the running X server (port 5900). However, if you install vnc4server yourself and set it up, you can run virtual VNC sessions so that your home PC could be used while you VNC in. You can multiple virtual desktops. It'll just increase the port by one- from 5901.

First, you'll need to install a few packages:

sudo apt-get install vnc4server xvnc4viewer

You can then edit /etc/vnc.conf if you would like to change the default resolution or color depth. the default is 1024x768@16 bit which should be sufficient for most uses.

By default VNC will startup a very basic session with a terminal window and little more. 
You can change this by editing /home/username/.vnc/xstartup.

This is what my .xstartup file looks like:

#!/bin/sh

[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
#vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
startkde &

I imagine you could replace "startkde &" with "gnome-session &" to run gnome.

Now, to start the server type "vnc4server" as the user you want to run VNC from. It'll ask you for a password which you should set.

If you would like to automate vnc to start on boot you can create a simple init script Here's my /etc/init.d/vncserver script:

#!/bin/sh

su vnc -c /usr/bin/vnc4server 

In this case vnc is the user that's running vnc.

after creating the script run "sudo update-rc.d vncserver defaults" to add the init script

Then "sudo apt-get install rcconf" and run "sudo rcconf". Select the new vncserver option to start vnc on boot. 

Since you are using VNC over the internet I would HIGHLY RECOMMEND YOU TUNNEL VNC OVER SSH. Otherwise all traffic is sent unencrypted other than the VNC password. this means any password you enter or information sent while the VNC session is running can be sniffed.

If you are using putty in windows you can tunnel VNC over ssh quite simply. Bring up putty and choose Tunnels. Make sure local is selected. Type 5901 as the source port and use localhost:5901 as the destination. Then login to the SSH server to forward the port. You would then connect to the vnc session from localhost:1 on the windows box. 

You can also do this easily on Linux as well. 

ssh -L 5901:localhost:5901 remoteserverip
xvnc4viewer localhost:1

---

### Post by daedalus_nl on 2005-07-08
[QUOTE=jcohen]
This can be easily done with VNC. 
--/cut/--
[/QUOTE]
This is nice, but like the topic starter said:

[QUOTE=speedsix]
I want to log into my home ubuntu machine from my windows box at work without tieing up the machine at home, similar to terminal services for windows.
[/QUOTE]
and that is not using vnc, because you take over the console.
using x over ssh, you get a terminal service like service

by the way: do you know this one:
linux terminal server project      link: [http://www.ltsp.org/]("http://www.ltsp.org/")

---

### Post by jcohen on 2005-07-08
He said he read a vnc 4 server howto and he didn't understand it, so I assumed he was looking for instructions to setup VNC. Anyways, I found a very interesting set of instructions which allows you to use XDMCP login over VNC. When a user connects to your machine with VNC, he'll see the gdm login screen. He can then login as any user  and get a virtual desktop on port 5901 so you can still use your system at home on port 5900.  

See [http://ubuntuforums.org/showthread.php?t=42941](http://ubuntuforums.org/showthread.php?t=42941) for details

Also, make sure that you change 5900 to 5901 (step #3) so that you log into a virtual desktop rather than your desktop at home. The line in /etc/inetd.conf should look like this: 

5901    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none

---

### Post by professor_chaos on 2005-07-08
theres also a commercial program called winaxe.
Its a remote login gui and wont "tie" up your computer.

---

### Post by speedsix on 2005-07-09
Thanks chaps, I'll look into each of these methods.

Much appreciated btw  :) 

Dom.

---

