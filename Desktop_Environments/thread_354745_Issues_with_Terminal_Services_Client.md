---
title: "Issues with Terminal Services Client"
date: 2007-02-06
forum: Desktop Environments
---

### Post by chapterthree on 2007-02-06
Hi All,

When I'm connected to a Windows box via RDP or RDPv5 with the Terminal Services Client, any time I move a window, there is a 'Hall of Mirrors' type of affect (see screenshot).

And for those clever eyes, this occurs with all Windows boxes, including non-vmware images.

Any ideas what is causing this?

---

### Post by stealth17 on 2007-02-08
> **chapterthree said:**
> Hi All,

When I'm connected to a Windows box via RDP or RDPv5 with the Terminal Services Client, any time I move a window, there is a 'Hall of Mirrors' type of affect (see screenshot).

And for those clever eyes, this occurs with all Windows boxes, including non-vmware images.

Any ideas what is causing this?

yeah mine is doing the exact same thing. I've tried all sorts of settings and no luck. I'm looking for a new client see how that goes...

** EDIT:** No such luck. I tried rdesktop and it did the same thing even at very low colors and 56k settings. I'm connecting to a lan computer, it shouldn't do that. Perhaps the video driver? I'm running the latest "nvidia" driver currently...

**EDIT2:** Perhaps this could be the problem?

[QUOTE=error shows in shell while running nvidia-settings]Error: API mismatch: the NVIDIA kernel module has the version 1.0-8774, but
this client has the version 1.0-8776.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.[/QUOTE]

I also cannot get the transparency to work in Fluxbox or any other app that supports it. I've tried all sorts of things. Could that be related?

---

### Post by jpneron on 2007-02-08
For what it's worth, I use the 'krdc' desktop client, and it doesn't do that. 

You should be able to install it from the repository. It's a KDE program, so it'll drag along some other KDE stuff, but I've found it to be a better client than the Gnome one.

Good luck!

Jean

---

### Post by veloce on 2007-02-08
Does it do it when you are in full screen mode?

I'm getting excellent performance with rdp to local vms.

Veloce.

---

### Post by stealth17 on 2007-02-08
> **jpneron said:**
> For what it's worth, I use the 'krdc' desktop client, and it doesn't do that. 

You should be able to install it from the repository. It's a KDE program, so it'll drag along some other KDE stuff, but I've found it to be a better client than the Gnome one.

Good luck!

Jean
I type "rdp:/192.168.1.104" and it comes up "Establishing Connection" but never goes further. Is there something more I need to know?

EDIT: I also tried "rdp:/192.168.1.104:3389" and it gets past the establishing connection but stays at authentication forever....

---

### Post by jpneron on 2007-02-08
Actually, I checked again, and the reason I don't see the hall of mirrors effect is that 'Show Window Contents while dragging' is turned off on our server. I'm connecting to Windows Server 2003, running Terminal Services, and that option cannot be turned on.

So, krdc may not help after all. I can't even turn on the option to try it. When I drag a window, I just see an outline of the window, not the contents.

Oh well, my intentions were good...:) 

Jean

---

