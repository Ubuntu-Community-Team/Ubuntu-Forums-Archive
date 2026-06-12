---
title: "VNC and xfce"
date: 2005-04-01
forum: Desktop Environments
---

### Post by gab10 on 2005-04-01
Can anyone tell me how to set up VNCserver to work with xfce? It works flawlessly in Gnome, but no matter what I try I can't get it working with xfce.

---

### Post by 47stoney47 on 2005-04-07
I have the same problem over here.  I spent 2 days troubleshooting my vnc just to see it work in gnome with no problem.  If anyone has any info please let us know.

---

### Post by ubuntu_demon on 2005-04-07
[QUOTE=47stoney47]I have the same problem over here.  I spent 2 days troubleshooting my vnc just to see it work in gnome with no problem.  If anyone has any info please let us know.[/QUOTE]
 I've got it working using xfce4 in hoary (without gnome,gdm and ubuntu-desktop)

Just install hoary and enter "custom" at the bootprompt.

after installation :
$ sudo apt-get update
$ sudo apt-get install xfce4 xserver-xorg vncserver

I would also recommend to at least install the packages : xfce4-goodies mozilla-firefox

You can reconfigure your xserver by :
$ sudo dpkg-reconfigure xserver-xorg

---

### Post by 47stoney47 on 2005-04-07
Thanks for the reply.  Problem is that i have all those packages already.  And i dont' understand how my xorg config can mess up my vnc.  Any input you could drop on that would be great

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=47stoney47]Thanks for the reply.  Problem is that i have all those packages already.  And i dont' understand how my xorg config can mess up my vnc.  Any input you could drop on that would be great[/QUOTE]
 make sure you haven't closed ports 5901 and 22 with firestarter or another firewall. (if you are behind a firewall/gateway and you want to have acces with vnc if you are not at home you should forward this ports to your pc)

to install ssh on your serverbox and your clientbox :
$sudo apt-get install ssh 

to install vncserver on your serverbox :
$sudo apt-get install vncserver

To connect to your box using ssh simply type :
$ ssh box
where box is the ip adress or name of the box

To startup vncserver log into the remote system using ssh :
$ ssh username@box
$ vncserver :1

When your client is a windows machine you can use putty ( [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) ) as sshclient and you can download a vncviewer from [www.realvnc.com](www.realvnc.com)

to connect use the terminal server client or just the command "vncviewer"

IMO : it's in most cases useless to have more than 1 graphical environment installed on a pc that you want to login remotely

In my case vnc works fine (I have only xfce4 installed on my server/gateway)

If there is more than 1 graphical environment you could attach a monitor and mouse and when you login choose xfce4 session and make it the default one. Most likely vnc will also start into xfce4 then.

If there are other problems with vnc you can edit your /etc/vnc.conf (I have set my colors to rgb888 this was necessary for windows)

---

### Post by jarcogna on 2008-06-10
I think the bit you are missing is "startxfce4" in your ~/.vnc/xstartup file.

Just comment everything else out, and add the line startxfce4.

Startxfce4 is part of the package xfce-utils.

Hope this helps.

---

