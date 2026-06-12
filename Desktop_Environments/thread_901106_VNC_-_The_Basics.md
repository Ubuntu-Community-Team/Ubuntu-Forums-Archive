---
title: "VNC - The Basics?"
date: 2008-08-26
forum: Desktop Environments
---

### Post by elbarto_87 on 2008-08-26
Hi all,

I Have a few novice questions about useing XVNCviewer to use the remote desktop capabilities of Ubuntu.

Firstly, I will be hopefully using this this to help setup family and friends with Ubuntu, as they are all setup with XP or older at the moment and are havening the same troubles I had (viruses etc).

I have another laptop here on my local network, which i was able to view the desktop by simply typing

```
vncviewer 192.168.1.68
```

That worked great, but then made me want to find out how to connect to a comuter running ubuntu that wasn't on my local network (as will be the case when my family and friends use ubuntu).

I found this guide which I think is something along the lines of what I will need to do [http://ubuntuforums.org/showthread.php?t=383053](http://ubuntuforums.org/showthread.php?t=383053) but it is pretty indepth and also mentions that "Realistically, there really isn't a reason to encrypt VNC traffic".

What I would like to know is, what is the easiest way I can use vncviewer to access a remote desktop that is not on my local network. Can I just use a similar terminal comand to the one above or is it a little more complicated then that.

Thank You

Regards Jake

---

### Post by ilrudie on 2008-08-26
Realistically there is a good reason to encrypt vnc traffic.  Sending cleartext passwords is **always** a bad idea.  No its not likely that someone is sniffing your traffic or even cares but thats no excuse for not having security.  You never know.  Make an ssh tunnel for the vnc traffic.

---

### Post by elbarto_87 on 2008-08-26
So is it safe to assume that everybody uses a "ssh tunnel" for this purpose? If so, does that mean that the person that I am trying to connect to has to go through the that guide (in the link) I posted?

I am just curious as to what exactly is required to use vncviewer on an external network. I mean, my IP address is 192.168.1.65 or something like that. There must be 1000's of people with that address, so how do I use terminal to tell vncviewer to connect to the address I want. Do I need a VPN?

As you can tell, my knowledge of IT is not great at the moment, but it is slowly expanding with every seemingly stupid question I ask. I just hope I don't frustrate to many of you in the process.... :)


Regards Elbarto

---

### Post by ilrudie on 2008-08-26
Tunneling VNC is probably a common use for ssh tunneling but it is not the only use.  Not everybody understands that VNC is not secured so not everybody will tunnel it.  There is also probably a subset of VNC users that use an IPSEC tunnel or a VPN instead of ssh.

You can't connect to a private IP ([http://tools.ietf.org/html/rfc1918](http://tools.ietf.org/html/rfc1918)) directly over the internet.  You will have to find the users public IP and they will likely have to setup port forwarding if they have a NAT masquarading router (common consumer router).  A VPN is another alternative to setting up port forwarding AND ssh tunneling but it may be more difficult to setup on consumer routers (not sure, never tried).

---

