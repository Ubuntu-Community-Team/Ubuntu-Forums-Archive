---
title: "Cannot connect to X server remotely"
date: 2009-03-30
forum: Desktop Environments
---

### Post by snibbets on 2009-03-30
Hi there. I would like to know how I allow connections to the GNOME X server.  I can't use SSH to forward the X11 packets, because SSH is not installed on the remote system and I don't have root access to install it.  I have set DisallowTCP=false in /etc/gdm/gdm.conf, restarted GDM, run xhost +, and set the DISPLAY variable on the remote machine.  Using Wireshark I found that packets were being sent to my Ubuntu machine for port 6000, but there were no replies to the remote machine.  However, if I try to connect to port 6000 from and to my local Ubuntu machine a connection is established.  What am I missing?  Any help would be appreciated, because I am at a loss as to what is wrong.

---

### Post by Khaele on 2009-04-10
Hello,

I did exactly as you did and it works for me. As it's described in the post of aajax ([http://ubuntuforums.org/showthread.php?t=1068214]("http://ubuntuforums.org/showthread.php?t=1068214")) this is what you have to do:

> Here is what i found -

- changing /etc/X11/xinit/xserverrc to remove the "-nolisten tcp" option has no effect. Implication is that this script is not used when starting X (Xorg) on Ubuntu.
- with gdm (Ubuntu) there is a GUI called gdmsetup which shows a security tab which contains a checkbox that is used to specify whether or not the X server listens for TCP connections. Changing the setting is effective.
- with gdm (Ubuntu) there is also a file, /etc/X11/gdm/gdm.conf, where an option called DisallowTCP may be used (also seems to be the default) for preventing the X server from listening for TCP connections.
- with kdm (Kubuntu) there is a configuration file, /etc/kde3/kdm/kdmrc, which contains a statement with an option called "ServerArgsLocal=-nolisten tcp". Commenting this statement was ineffective but explicitly setting the option to null (ServerArgsLocal=) does cause the X server to listen for TCP connections.

Don't forget to add the xhost + (adding each server would be really safer..) in your rc.local.

I use stunnel over this to forward ports of my Windows host to my ubuntu vmware... I know all of this is a bit crappy, but I had to find a quick solution.. I'll setup ssh X11 forwarding while sudoing, etc in a near future...

---

