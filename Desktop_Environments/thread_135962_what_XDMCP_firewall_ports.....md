---
title: "what XDMCP firewall ports...."
date: 2006-02-24
forum: Desktop Environments
---

### Post by encompass on 2006-02-24
I need to let xdmcp threw my firewall... for my local network... What ports do I have to open.I know xdmcp works now... because I can take down the firewall and it works.
And secondly, will sound work over xdmcp?
Thanks to everyone that has helped me so far...

---

### Post by soongwoo on 2006-02-27
The XDMCP protocol will send and receive data on port 177/UDP. But the actual connections will be made to the local port 6000/TCP. It is safe to allow connections since the xserver has an own security layer.

Please refer to :
 - [http://ubuntuforums.org/showthread.php?t=32045&page=2&highlight=xdmcp](http://ubuntuforums.org/showthread.php?t=32045&page=2&highlight=xdmcp)
 - [http://x.cygwin.com/docs/faq/cygwin-x-faq.html#tbl-xdmcp-ports](http://x.cygwin.com/docs/faq/cygwin-x-faq.html#tbl-xdmcp-ports)

soongwoo

---

### Post by encompass on 2006-03-05
But I don't have the foggiest how to allow that port to be open with iptables.  I need some advice on how to do that.  If I start alowing ports... I think I will have to allow them all with iptables not with firestarter... because if I work with firestarter after that point it will override my settings.
So.. the question for you answer is, how do I let that port be open?

---

### Post by KermitJr on 2006-03-07
Just a note, but if you want sound, look into LTSP.  THere is a sound daemon and it works/even uses xdmcp.

The next question is what firewall are you turning off? The on at home to access from outside of home?

---

### Post by encompass on 2006-03-07
No I have that working with XVNC running threw inet that works five... but I just let those ports open and it works.  I need to alow different ports 177udp in this case... how do I allow udp ports threw?
and cool, thanks for the sound thing... that does help...

---

### Post by SirMsquared on 2008-02-15
XDMCP uses UDP port 177 to communicate, then uses the normal X windows TCP port 6000 to establish the connection.  Note that with X windows the remote machine connects to the local machine, not the other way around.

Assumptions:
[LIST]
[*]Linux on both local machine and remote machine
[*]Both machines allow any outgoing connections, but restrict incoming connections
[/LIST]
Note that the remote machine is the machine you are logging into, and the local machine is the machine you are sitting it (ie: your workstation).

On the local machine:
[LIST]
[*]iptables -I INPUT -p udp --sport 177 -j ACCEPT
[*]iptables -I INPUT -p tcp --dport 6000 -j ACCEPT
[/LIST]

On the remote machine:
[LIST]
[*]iptables -I INPUT -p udp --dport 177 -j ACCEPT
[/LIST]

If you seem to be able to connect, but don't get a login screen (ie: you get a black or grey screen with an 'X'-shaped mouse cursor), run "netstat -a | less" on the local machine to see what port your local machine is listening on for the X session, and open that port up.

Note that the iptables commands above will only work until you reboot your machine.  I'm not familiar enough with Ubuntu to help you make them persistent.  Sorry.  :-)

---

### Post by jcmoore on 2008-02-15
[COLOR="Red"]Note that the iptables commands above will only work until you reboot your machine. I'm not familiar enough with Ubuntu to help you make them persistent.[/COLOR]

/etc/rc.local seems to work well for me...

---

