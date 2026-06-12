---
title: "How would i get this to work? (Two Linux machine, one moniter)"
date: 2005-11-23
forum: Desktop Environments
---

### Post by MaxDougal on 2005-11-23
I have the machine I'm on now, with a Windows and Ubuntu partition. And I also have a much older machine running Ubuntu only. The plan was to install a server on the old one, but I only have space for one moniter at my desk. Would I still get internet acess if I used up the only ethernet to remote desktop (I assume this is how I would do it)? Would they share internet? What would happen to old computer's internet when I booted into Windows? Can I remote desktop to a Linux machine from windows?

---

### Post by ed_d on 2005-11-23
For 2 machines, on the ethernet, why not get a hub? Also, can use VNC to use one monitor between the 2 systems, or can get a kvm that is for only 2 systems.

---

### Post by ebrowne on 2005-11-23
I think you need a router and a KVM (Keyboard Video Mouse) you can purchase a KVM at most computer stores

---

### Post by bullfrog on 2005-11-23
all you need is a switch box from tiger direct or almost any computer store. have one my self.  good luck bullfrog:cool:

---

### Post by fimbulvetr on 2005-11-23
Here's what I do:

I have a wrt54g wireless router, it has 4 ports on the back. Any linksys (or other reputable vendor) cable/router will do this easily. I have a laptop with ubuntu and a server with ubuntu, they both run on the router and the same network with a shared connection. The server doesn't have a monitor, but I enabled XDMP on it and  then I have any number of XDMP clients/SSH X forwarding that allow me to either run a (smaller, terminal server style) full desktop or single applications that look just like they're running locally, and they're fast too.

---

### Post by az on 2005-11-23
[QUOTE=MaxDougal]Would I still get internet acess if I used up the only ethernet to remote desktop (I assume this is how I would do it)? Would they share internet? What would happen to old computer's internet when I booted into Windows? [/QUOTE]

Well, I thin it would be overall safer to put two NICs in your linux box and use that for internet sharing (NAT or masquerading)  Your linux box would be your router for your windows box.  Your windows box would go to the internet through your linux box and you would have a safe firewall.

You can do remote desktop, yes.  Using two 100 Megabit NICs, you will not even notice that you are not on the local machine.  You will get very good performance, unless you want 3d acceleration.

But perhaps what will best suit your needs is a KVM.  They are great for running two boxes with one monitor.  I bought one that is finicky with some optical mice, so make sure that your hardware will work.  I am cheap, so that may be the problem.

---

### Post by nix4me on 2005-11-23
KVM Switch.

I have 5 machines on a KVM.

Ubuntu, Ubuntu, WinXP, Debian, IPCOP

nix4me

---

