---
title: "RDP from to Ubuntu with 22.04"
date: 2022-05-10
forum: Desktop Environments
---

### Post by netwizard.x1 on 2022-05-10
Hello,


I tried to connect from my Ubuntu 20.04 to Ubuntu 22.04 LTS via RDP. In the options Remote Desktop is enabled, port 3389 is also LISTEN (via ss -ltrpn) but I can't establish a connection via Remmina. Even with the latest version (via PPA) of Remmina I can initialize the connection, but I get the message that the security protocols are set wrong. But even via "automatic detection" I can't establish the connection. If I use the quick connection I get a password and user input prompt but the set password does not work.

---

### Post by TheFu on 2022-05-10
I vaguely remember in the 22.04 release notes, there is some information about RDP changes.
If you aren't forced to use RDP, perhaps an alternative solution like x2go would work better?

---

### Post by ActionParsnip on 2022-05-11
What desktop environment do you use no the remote system?
Why are you wanting to RDP across? What are you planning to do on the remote system that needs the full desktop session

---

### Post by netwizard.x1 on 2022-05-15
I connect from Ubuntu 20.04 to 22.04 both are the standard (gnome) Ubuntu versions.

I simply want a remote session which is encrypted and does not need to deactivate 
encryption on the client side. For sure I could use ssh in order to tunnel the connection.

---

### Post by ajgreeny on 2022-05-15
I wonder if RDP works with a wayland system which is what a default 22.04 now uses by default.

I do not know or use RDP so can not check that out, nor do I use Ubuntu, Xubuntu being my choice which so far can not use wayland.

---

### Post by #&amp;thj^% on 2022-05-15
> **ajgreeny said:**
> I wonder if RDP works with a wayland system which is what a default 22.04 now uses by default.



+1
I wonder if we could see this to be sure.
```
systemctl --user status gnome-remote-desktop.service
```

---

### Post by TheFu on 2022-05-15
> **netwizard.x1 said:**
> I connect from Ubuntu 20.04 to 22.04 both are the standard (gnome) Ubuntu versions.

I simply want a remote session which is encrypted and does not need to deactivate 
encryption on the client side. For sure I could use ssh in order to tunnel the connection.

**x2go** uses the NX protocol which leverages existing ssh for authentication.  The downside is that Gnome3+ aren't supported due to some choices by the Gnome team.  Also, Wayland isn't supported because x2go is based on X11.

OTOH, getting x2go working should be 5 minutes of effort. It pretty much always "just works".  [https://bytexd.com/x2go-ubuntu/](https://bytexd.com/x2go-ubuntu/) is a guide for installation on 20.04 and 22.04. Don't worry when they say "remote server" ... that can be a remote desktop machine too. Doesn't matter.

---

### Post by ActionParsnip on 2022-05-30
> **netwizard.x1 said:**
> I connect from Ubuntu 20.04 to 22.04 both are the standard (gnome) Ubuntu versions.

I simply want a remote session which is encrypted and does not need to deactivate 
encryption on the client side. For sure I could use ssh in order to tunnel the connection.
Yes, but what do you do on the remote system? Why are you RDPing to the server in the first place?

---

