---
title: "File manager doesn't see Windows network share contents"
date: 2004-12-11
forum: Desktop Environments
---

### Post by stoneguy on 2004-12-11
I've been tweaking samba and hosts files, and managed to get Windows shares' contents on other machines visible in firefox by using URL smb://machinename/sharename, so I know that things are OK at the samba level.

However, I can't seem to connect to the shares via the desktop or nautilus. Computer brings up a Network icon, below which are icons for the other machines, but clicking on any of them gives "the folder contents could not be displayed".

I noticed a hoary bug relating to this at [https://bugzilla.ubuntu.com/show_bug.cgi?id=4031](https://bugzilla.ubuntu.com/show_bug.cgi?id=4031)
Anyone know if it also pertains to warty? I'd hate to have to wait til next year to be able to access my Windows shares. 

Any chance of a backport on this one when it's resolved?

---

### Post by jdong on 2004-12-11
Hmm, do you have smbfs installed? The smb browser in Nautilus works for me in Warty.

Backporting fixes from Hoary to GNOME would be a messy task, and I think I'd be dipping into hot water by  messing with core Ubuntu packages!

---

### Post by stoneguy on 2004-12-12
Thanks for the tip. After a bit of research though, I'm not sure I want to go to smbfs. There are major vulnerabilities against it, plus it's being deprecated in favour of CIFSfs (which I don't know the status of in any version of Ubuntu).

If I'm going to be running a Linux box, I have to be able to move files between it and the Win systems around the house. This could turn out to be a real showstopper.

---

### Post by jdong on 2004-12-12
[QUOTE=stoneguy]Thanks for the tip. After a bit of research though, I'm not sure I want to go to smbfs. There are major vulnerabilities against it, [/QUOTE]

WHAT?

---

### Post by stoneguy on 2004-12-14
[QUOTE=jdong]WHAT?[/QUOTE]

I wouldn't lie to you  [-X  See

[http://www.securityfocus.com/bid/11695](http://www.securityfocus.com/bid/11695)
[http://www.securityfocus.com/archive/1/381420](http://www.securityfocus.com/archive/1/381420)

---

### Post by FictionPimp on 2004-12-14
I just did a standard reinstall of warty on a blank hard drive. After a quick apt update/upgrade, I am able to browse my windows shares, but only by going into nautilus, clicking on file and then connect to server and entering the server as 192.168.1.101/ShareName. It then prompts me for my windows user/pass as expected and makes a nice littel share icon on my desktop.

Not sure if that helps you, I just wanted to let you know my exp with the matter.

---

### Post by jdong on 2004-12-14
We aren't using smbfs support in the kernel, we're using libsmbfs --- a part of Samba and libgnomevfs2.

The smbfs package is just a simple way of getting the samba clients installed, instead of going into libsamba-whatever crap that nobody's gonna remember.

Nautilus does _NOT_ use mount -t smbfs to access smbfs in the kernel.

---

### Post by kirsche on 2005-01-30
Hi,

I'm running into the same problem.
But it works for me when i connect to a "custom server"

---

### Post by suoko on 2005-04-22
Unfortunately I have the same problem: Samba is working for every samba browser but evolution.
xfsamba4, for example, correctly see samba shares.

Is it a problem of nautilus in gnome 2.10 or ubuntu? 
I remember nautilus in gnome 2.8 (tryed with fedora) worked perfectly...

---

### Post by kernst on 2005-04-26
[QUOTE=stoneguy]However, I can't seem to connect to the shares via the desktop or nautilus. Computer brings up a Network icon, below which are icons for the other machines, but clicking on any of them gives "the folder contents could not be displayed".[/QUOTE]
Try temporarily disabling your firewall, if you've got one running. On this Debian Sarge (close enough, right?) system I wasn't seeing my *own* machine (running Samba) in Nautilus' "Windows Network" window, but after shutting down the firewall, browsing inexplicably started working. Or maybe not inexplicably, I'm just too tired to figure out why. For the Samba shares to show up, I believe I did have to make sure that the "LM Announce" option was set to "Yes" in smb.conf. (At the time there were no other Windows machines on the LAN to prompt Samba to start sending browse information in the "lm announce = auto" mode.)

Point being, you might want to scrutinize the output of 'iptables' for anything that looks like it's blocking incoming UDP traffic (which if I'm not mistaken is the protocol used for browsing). I'm using Lokkit on the Debian machine and the incoming UDP filters were a little, er, over-zealous, blocking everything except DNS query replies from my ISP. I don't have the patience to fix the problem right now, but I have a feeling it involves opening up 137, 139 or 445 for incoming UDP. At least I *know* the firewall was instigating the problem.

For what it's worth...

--Kevin

---

### Post by anotherunixnut on 2006-10-16
Sometimes you need to add your host info to the default networking host profile in the system config folder. 


192.168.1.2 myserver.mydomain  myserver

usually: /ect/sysconfig/networking/profiles/default/"hosts"  

That way when you click on the icon, the system can put an IP on the server or smb alias to find it.

---

