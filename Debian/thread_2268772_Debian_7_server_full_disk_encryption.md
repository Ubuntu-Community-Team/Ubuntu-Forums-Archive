---
title: "Debian 7 server full disk encryption"
date: 2015-03-11
forum: Debian
---

### Post by Drenriza on 2015-03-11
Hi all

Im planning on creating a Debian 7 server system with owncloud for storing data about my personale and business life, and share this amoung my own devices and family.
But i would like to use full disk encryption (since partition encryption dont secure the boot capability of the device), for the reasons that if someone somewhere oneday snags the server, the data on it will be encrypted.

My question is here if their is anything you can recommend for strong full disk encryption over multiple volumes.
I have Googled the subject and LUKS with keyfiles for different volumes seems populiar. But is this the way to go, or is their something else out their
you would recommend me using?

Anyone with a super guide or things i should be aware of?
Please share.

Posts / articles i have found usefull so far
[https://www.debian-administration.org/article/692/Look_before_you_leap_into_Disk_Encryption](https://www.debian-administration.org/article/692/Look_before_you_leap_into_Disk_Encryption)

Hope i can get some feedback and ideas.
Thanks on advance.
Kind regards.

---

### Post by TheFu on 2015-03-11
There are known boot attacks against full disk encryption. Any expert or government agency can get passed this today. It will keep wannabes and non-linux people out.  Realize that with whole disk encryption, those partitions are decrypted when the system is running and when the FBI shows up, they bring equipment to keep power on the system for transport back to their lab.
[https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html](https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html) - check for the LUKS comment.
[https://security.stackexchange.com/questions/39306/how-secure-is-ubuntus-default-full-disk-encryption](https://security.stackexchange.com/questions/39306/how-secure-is-ubuntus-default-full-disk-encryption)
[http://askubuntu.com/questions/97196/how-secure-is-an-encrypted-luks-filesystem](http://askubuntu.com/questions/97196/how-secure-is-an-encrypted-luks-filesystem)

Any ports that allow DMA on the server are a risk too.  Firewire, PCMCIA, displayport and probably whatever new port Apple is pushing is a risk too. Performance trumps security too often.

OwnCloud has many security issues, so don't just put it on the internet without requiring a VPN. The core developers appear to be doing the right things related to security, as best they can.  If you care about real security, don't trust HTTPS. We are better off using openvpn and ssh with keys that we control on both sides, IMHO.

Might be worth looking at Seafile and rsync (over ssh) too.  I've been using rsync for 15 yrs and know it works. Seafile is trying to be owncloud, but written in a language that isn't php. I don't know anything more about it.

If you just need access to files from anywhere, ssh/scp/sftp works with 1 open port and ssh-keys make it possible to do securely. Be certain to setup fail2ban to block all those brute-force attacks, even if you don't go with just ssh/scp/sftp/rsync+ssh as a solution. After all, everyone needs an ssh server on every box they have, right?

Hopefully, my display of ignorance isn't too much.

---

### Post by HermanAB on 2015-03-12
Well, some paranoia is good.  Do use full disk encryption - it does work to protect data at rest.  Someone who tries to hack it will ry a few passwords and get locked out.  Then he'll reboot and will be even more locked out.  When the machine is sold on Ebay or when the HDD controller or motor goes bust, the data will be safe in data heaven.

For sharing with friends and family, try Retroshare.

---

### Post by deadflowr on 2015-03-12
Thread moved to the ***Debian*** sub-forum

---

### Post by Drenriza on 2015-03-13
> **TheFu said:**
> There are known boot attacks against full disk encryption. Any expert or government agency can get passed this today. It will keep wannabes and non-linux people out.  Realize that with whole disk encryption, those partitions are decrypted when the system is running and when the FBI shows up, they bring equipment to keep power on the system for transport back to their lab.
[https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html](https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html) - check for the LUKS comment.
[https://security.stackexchange.com/questions/39306/how-secure-is-ubuntus-default-full-disk-encryption](https://security.stackexchange.com/questions/39306/how-secure-is-ubuntus-default-full-disk-encryption)
[http://askubuntu.com/questions/97196/how-secure-is-an-encrypted-luks-filesystem](http://askubuntu.com/questions/97196/how-secure-is-an-encrypted-luks-filesystem)

Any ports that allow DMA on the server are a risk too.  Firewire, PCMCIA, displayport and probably whatever new port Apple is pushing is a risk too. Performance trumps security too often.

OwnCloud has many security issues, so don't just put it on the internet without requiring a VPN. The core developers appear to be doing the right things related to security, as best they can.  If you care about real security, don't trust HTTPS. We are better off using openvpn and ssh with keys that we control on both sides, IMHO.

Might be worth looking at Seafile and rsync (over ssh) too.  I've been using rsync for 15 yrs and know it works. Seafile is trying to be owncloud, but written in a language that isn't php. I don't know anything more about it.

If you just need access to files from anywhere, ssh/scp/sftp works with 1 open port and ssh-keys make it possible to do securely. Be certain to setup fail2ban to block all those brute-force attacks, even if you don't go with just ssh/scp/sftp/rsync+ssh as a solution. After all, everyone needs an ssh server on every box they have, right?

Hopefully, my display of ignorance isn't too much.

Thanks for the articles which was a pleasure to read.
As i understand one of the problems is that if you leave your machine alone the hardware on the device can be compromised, where the encryption key at boot is stored and than
sent to someone else.

I dont intend to hold out organisations like the FBI, but i like the discussion. If they manage to pull the server over on a movable PSU and move it away.
How do they get past the login screen without getting locked out that than will require a system reboot?

What does DMA stand for in this case?

> **HermanAB said:**
> Well, some paranoia is good.  Do use full disk  encryption - it does work to protect data at rest.  Someone who tries to  hack it will ry a few passwords and get locked out.  Then he'll reboot  and will be even more locked out.  When the machine is sold on Ebay or  when the HDD controller or motor goes bust, the data will be safe in  data heaven.

For sharing with friends and family, try Retroshare.


Paranoia is a strong word :) Most of all im tired of the turns IT security is taking in general and i want to beef my own up.
Also when my ISP is trying to scan my local network, and my celiuare providor does DPI and so on and so forth. Than i think to myself "... NOPE!"

So i have blocked out my ISP by removing their device and directly connecting my own, i do VPN og my smartphone.
I got a radius service on my wifi, because why not :) and so on and so forth.

The full disk encryption comes in because i want to secure my data if a device is stolen, lost / other. The idea is to run encryption on all my devices that contains data.
But i want to do it right and understand the concepts behind ect.

---

### Post by TheFu on 2015-03-13
There are many ways to break into a running system with local access and sometimes with network access. It comes down to knowledge. If the attacker believes that encryption is involved, they will keep the system running in the hopes to avoid having to fight with that as well.  Many disk encryption tools allow the user/installer to make a small mistake that leaves a tiny crack for access to the system. Security is hard. Trying to merge security with convenience is really hard, without making one of those tiny mistakes.  After all, reports claim that deeply frozen RAM can be read to pull encryption keys.

DMA - direct memory access. This allows a device connected to a DMA port to have root access to RAM - DMA - direct memory access. 

DPI is not performed by a network scan. Look up "bluecoat" and see some of the systems they sell to governments. Think inline, wire-speed, packet/traffic analysis - that includes encrypted traffic. No small task for an entire country. I think there are free versions of that technology, it is just 8-10 yrs behind capabilities of Bluecoat equipment.

I own my cable modem - yet Comcast can change any of the settings without my approval. They've done it when I was on the phone. Just because you own the equipment, don't confuse that with controlling it on someone else's network.  DSL and cable modems have long worked in this way.  I don't know of any purchased home routers that allow the ISP control.  BTW, I worked on a CPE management project at a very large ISP with wifi-G was new. It is THEIR network. Always know that.

I agree on full-disk encryption for portable devices. I'm torn on how useful that is for servers with controlled access - including a family home. Just look at Ms. Clinton running an email server using a business ISP connection in her home for some period of time. I don't think she ran it there for very long.

There is a nearly infinite amount of reading/videos if you are into security.

---

### Post by Drenriza on 2015-03-13
> **TheFu said:**
> 
DPI is not performed by a network scan..

Situations from two different companies you just merged their :)

---

