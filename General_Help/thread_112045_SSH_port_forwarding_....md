---
title: "SSH port forwarding ..."
date: 2006-01-03
forum: General Help
---

### Post by stv on 2006-01-03
What is the conventional wisdom on opening my firewall for openssh (port 22)?

ssh -v gives:

OpenSSH_4.1p1 Debian-7ubuntu4, OpenSSL 0.9.7g 11 Apr 2005

I have a DLink DI-604 (up-to-date firmware 3.51) router connected to my Comcast cable modem. The 604 has a tool called Virtual Server ... I would have called it port forwarding, but maybe I've got my buzz words wrong. In any event, the 604 has a public IP on the WAN side and I tell the router I want port 22 to get forwarded to, say, my 10.10.32.11 address on the private LAN side.

Anyone who wants to can walk down the Comcast IP list and scan for open ports will find my 22. Indeed, I can telnet to the WAN IP port 22 & sure enough, I get a SSH prompt (not that *I* know what to do).

My understanding is that OpenSSH is strong as heck and this is not A Really Bad Idea. Am I mistaken?

I hope this is true, because the tunneling features for SSH will come in handy (but that's another post).

Thanks

---

### Post by gnu2tux on 2006-01-03
SSH is a strong method of security, but passwords are still it's biggest problem where you have bad passwords.

If you are worried about security, change the port for ssh from port 22 to a random port above 1024 and forward that instead, because you will be less of a target to port scanners.

Regards,

Al.

---

### Post by earobinson on 2006-01-03
good passwords are key..... the longer the better, the less words the better, numbers and text is beter.

---

### Post by PMO6022 on 2006-01-03
You can also install a tool like denyhosts: [http://denyhosts.sourceforge.net/]("http://denyhosts.sourceforge.net/") There is also an excellent how to on this site (ubuntuforums).  Essentially, it scans your logs and blocks ip's that have exceeded a set number of failed login attempts.

---

### Post by GeneralZod on 2006-01-03
I always use public-key authentication nowadays.

---

