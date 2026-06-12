---
title: "Logmein type program for Ubuntu?"
date: 2009-06-24
forum: General Help
---

### Post by jras20 on 2009-06-24
Is there a logmein type program that will work under Ubuntu and windows?  I'd like something that I can have to control my laptop from work if I needed to.  I like that about logmein.  But if theres another one just like it that will work then that would be great.
Thanks.

---

### Post by madverb on 2009-06-24
Use VNC. You just need to redirect port 5900 to your PC from your modem/router.
System > Preferences > Remote Desktop

---

### Post by CyberJack on 2009-06-24
You can also install freenx (nomachine.com). Server runs only under linux but the client software is available for linux and windows. It uses ssh (port 22).

---

### Post by snek on 2009-06-24
afaik FreeNX only starts new sessions unlike LogMeIn which takes over the current session like the standard VNC server does that comes with Ubuntu. 

I can imagine having a seperate program like LogMeIn is nicer though, it easily traverses firewalls and the client doesn't get blocked too easy by a strong corporate/edu firewall. Also the option to use a browser is quite nice, something the default VNC server of Ubuntu doesn't seem to support. (Correct me if I'm wrong)

---

### Post by hibliss on 2009-06-24
> **snek said:**
> Also the option to use a browser is quite nice, something the default VNC server of Ubuntu doesn't seem to support. (Correct me if I'm wrong)

I don't really see why this is a benefit. 

VNC requires open ports, but there are workarounds. What I do is have a VPN setup in my router (DD-WRT firmware), and I VPN to my router, then the VNC connection to my home desktop is a local address, no port issues.

---

### Post by jras20 on 2009-06-24
I'm going to try VNC maybe, I'm new to that.  I like how easy logmein is.  Is VNC the same just about?

---

### Post by hibliss on 2009-06-24
> **jras20 said:**
> Is VNC the same just about?

No.

---

### Post by madverb on 2009-06-25
Yes it is very similar. LogMeIn just makes it easier to get past firewalls and is more useful to help someone out quickly. Rather than telling them how to put a hole in their firewall for VNC.
Since it is for your own computer and your own access to your computer it is exactly what you need.

---

### Post by little_penguin on 2009-09-16
I recently discovered **NTRConnect**, it's multi-platform (Linux, Windows and Mac). When you download the installer, it detects your OS automatically.In the free version, you're limited to 2 computers. It's fairly fast and security can be enhanced by key cards. 
 
I usually use NoMachine NX which has in-built ssh encryption to connect to my computer, but NTRConnect is easy to set up and handy if you want to control your desktop from any web browser when you're on the road:
 
[www.ntrconnect.com]("http://www.ntrconnect.com")
 
Regards,
LP

---

### Post by ChumleyEX on 2009-09-16
I use an ssh tunnel to access all the computers on my network via vpn or remote desktop.

---

