---
title: "VNC and Firestarter"
date: 2009-01-29
forum: Desktop Environments
---

### Post by theharlequin on 2009-01-29
I'm sorry if this has been covered in a post before. I searched and didn't find anything that matched my issues.

To make a long story short, I recently rebuilt my box - installing firestarter. I followed the instructions on how to VNC into my server ([http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html) and [http://ubuntuforums.org/showpost.php?p=771174&postcount=61](http://ubuntuforums.org/showpost.php?p=771174&postcount=61)) to the 't'. 

In firestarter I have the default VNC ports open to my local IP (5900-5901) and have a policy to allow all connections from 192.168.1.XXX (which is my internal IP). The VNC ports are also forwarded to my server's IP address through my wireless router. 

But for when I try to connect to 5900 or 5901 I am blocked. When I try to VNC from my XP laptop using TightVNCViewer, I get the errors: 5900 - Invalid protocal, 5901 - Failed to connect to server. 

When I try to VNC from the localhost, I get these errors: 5900 - reading version failed: not an RFB server? 5901- unable to connect to host (connection refused 111). 

From what I can understand firestarter and my router are configured properly.

I know it must be a firewall issue because when I had no firewall running in the past it worked fine, until I got hacked and had to reformat (hence the firewall). Any help is appreciated

---

### Post by RomanIvanov on 2009-03-23
I have the same problem, did you found the workaround ?

---

