---
title: "apt-get and using other installers behind school proxy"
date: 2009-04-22
forum: General Help
---

### Post by Free Thinker on 2009-04-22
The tech staff have tried to help me get this to work by allowing access to the Oxford University mirror and configuring my laptop to use that as the source in 'Software Sources'. However, it still just times out. (this is when I run sudo apt-get update or try to install any software through add/remove applications, synaptic or the terminal) 

Prior to getting the tech staff's help it just paused on the ip for ubuntu's archive then timed out. So nothing's really changed...

So my computer is unable to update itself, and since I go to a boarding school it means I go months without getting fixes and updates for ubuntu, which are pretty essential. Using ubuntu is fairly mundane with limited internet access, and is basically like using windows. :( It especially becomes annoying when I'm trying to get hardware drivers.

What I don't understand is that I can ping mirror.ox.ac.uk without problems and even tracert manages to reach it. Then why isn't apt-get working?

---

### Post by StuartN on 2009-04-22
Can you browse the web with Firefox? Can you send email? Do your other internet applications work?

If so, then try System->Administration->Software Sources and select another server near you. (Don't forget that Jaunty is released tomorrow, so the server load will be high). If your other internet applications work and Synaptic does not, then perhaps you have a firewall restriction either on your computer (sudo ufw status - "not loaded" if the firewall is off) or on the school network.

---

### Post by Free Thinker on 2009-04-22
> **StuartN said:**
> Can you browse the web with Firefox? Can you send email? Do your other internet applications work?
All applications work except for installers, apt-get, wget, bittorrent and pidgin. I'm only bothered about the former three though.

> If so, then try System->Administration->Software Sources and select another server near you. (Don't forget that Jaunty is released tomorrow, so the server load will be high). If your other internet applications work and Synaptic does not, then perhaps you have a firewall restriction either on your computer (sudo ufw status - "not loaded" if the firewall is off) or on the school network.
Since 'sudo ufw status' returns 'not loaded'; I'm assuming it's the school's firewall that's the problem. When the tech guy tried to make an exception for me, he said something about trying to make it "equivalent to updating anti-virus". So I think he tried to get the server to permit my apt-get's and updating as if it's a user's anti-virus automatically updating. 

This failed though.

---

### Post by StuartN on 2009-04-22
Does apt-get update or apt-get upgrade fail in terminal? If they do fail, but you have internet access otherwise then it may be a network firewall. It should not be blocked though because a standard setting is FTP (port 21) or HTPP (port 80) - I have no idea how to check you apt settings.

You can still bypass any firewall if you already know what package you want to install or upgrade, by browsing to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and selecting packages there. The link is right at the bottom of each package page.

---

### Post by Free Thinker on 2009-04-23
> **StuartN said:**
> Does apt-get update or apt-get upgrade fail in terminal? If they do fail, but you have internet access otherwise then it may be a network firewall. It should not be blocked though because a standard setting is FTP (port 21) or HTTP (port 80) - I have no idea how to check you apt settings.
Ports 21 and 80 are open on the proxy that I use firefox with, if apt-get only uses these then there must be a way to configure it to work through that proxy. Problem is I think I've tried everything I can.


> You can still bypass any firewall if you already know what package you want to install or upgrade, by browsing to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and selecting packages there. The link is right at the bottom of each package page.
Thanks, I'll do this for now. 

I'd still like to see if there's a way to do it through terminal though, just for ease-of-use and so that I can use synaptic package manager etc.

---

