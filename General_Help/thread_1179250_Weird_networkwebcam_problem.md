---
title: "Weird network/webcam problem"
date: 2009-06-05
forum: General Help
---

### Post by blackxored on 2009-06-05
Using Jaunty 9.04
Hi, I just recently installed a Logitech QuickCam Pro 5000. 
But suddenly after configuring an asterisk server on my work, when using the video feature of Ekiga, my network gets deconfigured over and over again. I disabled some tcp/udp protections, but without result. I'm pretty lost in here, 'cause the camera seems to be detected well by uvcvideo. I've put the syslog entry after disconnecting and connecting the camera again, running ekiga (3.2.0ubuntu2), and initiating a video talk in [http://paste.ubuntu.com/189100/](http://paste.ubuntu.com/189100/).
Anyone has an idea why this is happening?
EDIT: I've missed three lines may help, actually they seem pretty interesting:
> 
Jun  5 12:14:16 desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 8) 
Jun  5 12:14:16 desktop NetworkManager: <info>  (eth0): device state change: 8 -> 2 
Jun  5 12:14:16 desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40). 


UPDATE: Well, actually I've enabled those tcp antiflood protections again. That seems to make any difference at all. 
But actually, the network gets disconnected in the exact moment I start sending video over Ekiga, so actually it seems there's a bug with the client or the usb card, but I can't know for sure. I've downloaded ekiga-3.2.4 from [http://ekiga.org](http://ekiga.org), I'll do week-end packaging to see if I can solve with a upgrade. If not, then at least will see if I can find another workaround for this, it's getting me crazy. 

Any ideas are welcome.

---

### Post by blackxored on 2009-06-08
Well, actually packaging Ekiga 3.2.4 didn't solve the problem, so I'm a pretty lost in here. Suggestions welcome, please.

---

