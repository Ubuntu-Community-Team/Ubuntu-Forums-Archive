---
title: "vmnet connection to physical device"
date: 2007-02-07
forum: Desktop Environments
---

### Post by pmgeahan on 2007-02-07
Folks - 

I recently installed VMWare Server on Edgy.  I have three network interfaces(eth0-2) in my machine, one of which is intended for use only by one particular virtual machine.  

If I bring the interface up(ifup eth2) before I start the vm, the connection works fine from inside the virtual machine.  If I don't, then I get a failure on startup because the bridged interface isn't up.

I'd like to bring up and take down eth2 solely as a function of when vmnet0 is up and down.  In other words, if I bring up vmnet0, I want eth2 to come up automatically, and the same for bringing it down.

Is there any easy way of doing this?  I considered writing a script, but I can't help but think this is a problem someone else already solved.  Anyone have an idea?

Thanks!

---

### Post by veloce on 2007-02-08
I don't think I can be too much help here - I'd guess that a script is the way to go.  It's a little difficult to work out what you are meaning as well.  I assume that eth0-2 refer to actual connections on your host? 

Just one comment, although you get an error bringing up the vm when eth2 is not up, when eth2 comes up your vm should then recognise that its up and (depending on virtual os I suppose) start using it. 

I think this works for all vm bridges, but there is some comment about vmnet0 (the default bridged network) doing bridging better than others. I have eth0 as wired and eth1 as wireless - only one will be operational at any time - and vmnet0 bridges to the available connection - the others appeared to have difficulty.

Veloce

---

### Post by pmgeahan on 2007-02-08
Yes, eth2 is  a physical ethernet card; I have three.  The one is purely dedicated to the operations of that virtual machine.  

Somehow, I've gotta think there's a way to tie vmnet to a physical device; but, for the moment, I think I'll work on that script.

---

### Post by veloce on 2007-02-11
Why not leave eth2 up all the time?

For security, I have a virtual firewall between my host only network (with all the rest of the vms) and the outside world (bridged to the one physical adapter in the machine.)

I use IPCop and limit it to 32mb of ram so it's very low overhead on the system.

---

### Post by pmgeahan on 2007-02-11
To make a long story short, I don't leave eth2 up because of security regs at my workplace; that particular network is supposed to be restricted access.  When I run the VMWare image on my machine, they're OK with that, but just leaving it open when the image is down is more than they want to do.

---

### Post by veloce on 2007-02-11
Yeah, understand that.  I too have to be consistent with the IT department's requirements.  (In my case they are pretty helpful as they would like to move more of us to linux!)

I can't quite see how you're going to do the script.  Will the vm bring the interface on the host up, or will the host check to see if the vm is "live"?

---

### Post by pmgeahan on 2007-02-11
Right now, VMWARE images are only for this 'special' network.  So the script will be a wrapper that brings up eth2, then starts VMWare, and after VMWare shuts down, brings it down.

Sort of ghetto, but it should work.  I need to figure out some problems with routing/DNS on that area anyhow, so I might solve two birds with one stone.

---

