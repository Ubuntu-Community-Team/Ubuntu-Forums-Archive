---
title: "Samba HELL!!!"
date: 2010-03-31
forum: Desktop Environments
---

### Post by hooge1kanobi on 2010-03-31
Okay. So I'm new to Ubuntu from Windoze.

All in all figuring things out with forum help and video tutes on the tube.

Here's my deal.  I have a Laser printer connected to my 9.10 machine. Drivers installed and all is well.  9.10 Desktop is wired to my home router/network.  I'd like to share this printer to XP home, Vista and 7 machines (also on the network).  Everything I've read says Samba is the way to do it.  I installed via "sudo apt-get install samba" and a few other things.  Sharing is now enabled but I've never been able to get to the printer from the other machines so I thought lets see if I can just share up a folder!  I followed [this Tutorial]("http://www.youtube.com/watch?v=89hjWOb8qmY&feature=related"). In the process my smb.conf file got Nuked!  It was left blank!  So I used Synaptic to remove all of my Samba packages and started over.  Now I was working with another [tutorial]("http://www.jonathanmoeller.com/screed/?p=1168") and after the "**sudo gedit /etc/samba/smb.conf**" I get the following reply:

(gedit:2519): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory

Can some one please help me figure out what I've screwed up and get me back on track so I don't have to revert to windoze?

Thanks!

---

### Post by captain_171 on 2010-03-31
Hey take a peek at Webmin that will make samba setup so much easier.
No lines to edit and it just works.

[http://www.webmin.com/](http://www.webmin.com/)

Any questions reply back K.

---

### Post by lisati on 2010-03-31
I took a break for dinner before responding, and like the webmin suggestion.
I've also successfully used the tutorial [here]("http://ubuntuforums.org/showthread.php?t=202605") with more than one version of Windows & Ubuntu

---

### Post by AlexanderDGreat on 2010-05-05
Hey, pls. check this basic setup on Samba Lucid Lynx, it worked for me:

[http://www.jonathanmoeller.com/screed/?p=1590]("http://www.jonathanmoeller.com/screed/?p=1590")

---

