---
title: "Remote Access"
date: 2009-02-11
forum: General Help
---

### Post by pedrom169 on 2009-02-11
I leave my ubuntu machine on at home whilst it downloads files etc and when i used to have windows i used logmein to access it remotely becasue i am on a windows network at work.

Logmein is a windows application only. (searched everywhere for away).

I was wondering is there anyway of remoting in from my windows machine from work?

Thanks.

If its any use my ubuntu pc is connected via a wireless router and is ubuntu 8.04

---

### Post by pedrom169 on 2009-02-11
anyone?

---

### Post by mozkill on 2009-02-11
yes, you can do it.  Ubuntu comes pre-installed with VNC  protocol and there is a "Remote Desktop Protocol" control panel if you can find it.

then on your XP machine at work, just open VNC client and connect to it.  keep in mind that it might not be encrypted.  im not sure how to enable encryption with VNC but i know its possible i think.


If , for some reason, you cannot open the firewall port from the outside world to your linux machine (which is unlikely),  then in that case "Logmein Hamachi" will give you a method of creating a secure VPN passthrough in order for your work machine to get to port 5900 on the linux computer.   In that case, who cares if VNC protocol is encrypted or not...


There is a rumor that FreeNX has better performance but im not sure if its true:
[http://ubuntuforums.org/showthread.php?t=1968&highlight=freenx+howto](http://ubuntuforums.org/showthread.php?t=1968&highlight=freenx+howto)

---

### Post by yknivag on 2009-02-11
Or you could use VNC (so long as your workplace doesn't block port 5900 on their firewall)

---

### Post by JK3mp on 2009-02-11
> **yknivag said:**
> Or you could use VNC (so long as your workplace doesn't block port 5900 on their firewall)

Most with any decent security do though... :(

---

### Post by sr20ve on 2009-02-11
You could also just install vncserver and configure port forwarding on your router. Then just download a vncviwer on your work computer and you should be able to access it.

You might also want to setup and account on dyndns.com as your home IP may periodically change.

---

### Post by Jac3510 on 2009-02-11
More details on the vnc suggestion:

1. set up a pptp server on your Ubuntu machine. From the terminal, type:

sudo apt-get install pptpd

2. Set up your pptp.conf file by typing:

sudo nano /etc/pptp.conf

Edit the last two lines with your local IP and a range of IP's, for example:
> #localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245
localip 192.168.1.64
remoteip 192.168.1.234-245,192.168.1.254
3. Next, set up your user name and password by typing:

sudo nano /etc/ppp/chap-secrets

Add a line at the bottom as follows:

*your_user_name* pptpd *your_password* "*"

You can add as many users as you want that way. Just give each their own line. Next, make sure your ports are properly forwarded. Since every router is different, either consult your manual or check out [http://portforward.com](http://portforward.com).

4. If you have a dynamic IP, go to [www.dyndns.com](www.dyndns.com) and set up a free account there.

5. In Ubuntu, click System->Preferences->Remote Desktop. Allow others to control your desktop, require a password, and DO NOT ask for confirmation.

6. Go to [www.realvnc.com](www.realvnc.com) and download the free standalone server for Windows (if you are wanting to connect from a windows machine at work). Install the client to that machine.

7. On Windows XP ('cause I refuse to learn Vista), click "Create a new network connection" in the My Network Connections page. Create a VPN connection, provide your public IP or dyndns address and then connect to your home computer using the user name and password created above. Then, open VNC and connect using the password you enabled, and you are good to go.

That should be everything. I'm sure somebody can tell you if I missed a step. It's been a little while since I set mine up.

---

