---
title: "Desktop environments on servers"
date: 2007-03-02
forum: Desktop Environments
---

### Post by honiball on 2007-03-02
How much of a bad idea is it to run Gnome or Kubuntu on a server?

I know they use system resources, but I like the user-friendly interface (seeing as I am relatively new to Linux and don't know all the bash commands).

I have 1GB of RAM, and running Ubuntu 6.06 as a LAMP Server.  I installed ubuntu-desktop as well.  I intend to use it as a file, intranet, and SQL server.  

Will the desktop negatively affect my servers performance, and by how much?

---

### Post by fourchannel on 2007-03-03
I'm not sure how to put this, so I'll recite my experience of my server.

I have a pentium 2 , 450 mhz, 128mb 6 G system HD, 40 G data HD, and keyboard, video, and mouse switcher tower, that uses the mouse, keys, and monitor of another desktop. Whenever anyone wants to download a song or whatever, they switch over the inputs, download it; once it's finished they switch back and can listen to that song via FTP, HTTP, SFTP, or Samba.

The system runs (24/7):

Limewire
FTP server
HTTP server
SSH server
Samba server
NTP server
FoldingAtHome

Even though it seems like it would die, the system stays relatively responsive. It runs openbox. Stay away from KDE or Gnome if you want to greatly save on computing power.

The OS is Breezy (5.10), and the system is installed on the 6 gig drive. The swap partition is on the other harddirve (it really, really helps to cut down on thrashing).
I am ok with it's performace. It is not blazing, it gets the job done with a little slugishness, but only a little.
There is also blackbox, for insane minimalistic resource usage. If the performace gap from blackbox to openbox is several feet, the gap between openbox and KDE or Gnome is miles.
For a system with a lot more cpu power, you should be fine running openbox. You would probably even be ok running KDE or Gnome, but it would be a very noticable hit.



[Here is a link to installing openbox.]("http://doc.gwos.org/index.php/Openbox_GnomeStraight")

[I also like this thread, it is the one I used to install openbox on my server.]("http://doc.gwos.org/index.php/Openbox_Gnome")

EDIT: I didn't quite comprehend your post the first time around. If you are somewhat new to linux (like I was when I put the server together in April of 2005), then I would recommend using Gnome. It is what I did with the 450mhz system, and it was damn slow. But I eventually got used to using the command line. From there I started apache for the HTTP server. A little ways into the summer I switched over to openbox. It most definately took time and some uphill learning curve treking. Was it worth it? Hells yeah it was.

---

