---
title: "&quot;xhost +&quot; does not work?"
date: 2009-03-16
forum: General Help
---

### Post by firsttimeuser on 2009-03-16
Hi, i am trying to run some command on remote server and set the display back to my own box, 

so on local host, I run

$ xhost +
access control disabled, clients can connect from any host


and on the remote server I run
export DISPLAY a.b.c.d:0.0 #(a.b.c.d is my box)
./command

and I got the following error message:

gnome-system-monitor: cannot connect to X server a.b.c.d:0.0


and according to tcpdump, the connection was sent to my host, but somehow my host denied the request, as below

11:31:32.274226 IP eng.34650 > laptop.x11: S 4028987451:4028987451(0) win 5840 <mss 1460,sackOK,timestamp 3389467743 0,nop,wscale 7>
11:31:32.274805 IP laptop.x11 > eng.34650: R 0:0(0) ack 4028987452 win 0                                           

What could be wrong here? thanks

---

### Post by firsttimeuser on 2009-03-16
bump

---

### Post by Khaele on 2009-04-10
Look around this thread:

[http://ubuntuforums.org/showthread.php?p=7047296]("http://ubuntuforums.org/showthread.php?p=7047296")

---

