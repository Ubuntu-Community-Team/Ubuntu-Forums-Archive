---
title: "Wake on LAN and Soft-off"
date: 2006-08-03
forum: Desktop Environments
---

### Post by subzero79 on 2006-08-03
I've been playing around for two weeks aprox. to get working the WOL function in my NIC hardware (nforce). So finally i've got it working for waking up the PC from inside the LAN, and finally today from outside the LAN (from WAN or internet). One of the tricks for getting this thing to work is BIOS setting, enable both WOL and the soft-off functions. So when i am in windows i soft-off by pressing the power button in the front of the case for no more than 4 seconds). Then with tools like wol or wakeonlangui.exe i send the magic packet and the PC wakes up, then i am able log in remotely and do whatever i want to do.

However with Ubuntu dapper i haven’t been able to perfom a soft-off with the poweroff button or shutting down through the gui to this soft state (S5 acording to ACPI) in such a way that i would WOL that PC with magic packets. 

Is there a way to enable soft-off? Or maybe shutting down through the console with a specific command.?

---

### Post by nickb834 on 2006-10-05
this is probably more to do with Linux driver for your NIC not enabling WOL functionality and completely shutting down your NIC when you shutdown.

This was exactly my problem, and the fix is detailed below.

run this in terminal before you power off and see if you can WOL after:

```
sudo ethtool -s eth0 wol umbg
```

if that works for you create a script in

/etc/init.d/

with this in it:

```

#!/bin/bash
ethtool -s eth0 wol g
exit

```

Save it as 'wakeonlan' if you like and make sure you make it executable:

```
chmod a+x wakeonlan 
```

then run this to create startup links:

```
update-rc.d wakeonlan defaults
```

finally run 'wakeonlan' which should return you to cli prompt with no errors.

Shutdown and try to send a magic packet to Ubuntu machine to wake up - all should be well.

Incidentally the options that are specified after the 'wol' portion of the ethtool command are as follows:

              u  Wake on unicast messages
              m  Wake on multicast messages
              b  Wake on broadcast messages
              a  Wake on ARP
              g  Wake on MagicPacket(tm)
              s  Enable SecureOn(tm) password for MagicPacket(tm)

I only selected 'g' for the startup script I used as I suspect that options u m b will wake the machine up irrespective the source / dest.

They may however only affect the type of MagicPacket to wakeup from ie broadcast / unicast / multicast - MagicPackets.


HTH

Nick

---

### Post by subzero79 on 2006-10-05
Thnks for the reply. But the final answer to this was a bug in nforce4  mobos. The forcedeth driver reverses the MAC address when you halt the system. The magic packet has to be sent with the reverse MAC to the PC. The WOL works well with the right MAC when you shutdown from windows. Thats the trick. I find this answer in the kernel web page.


bye

---

### Post by njparton on 2007-11-02
nickb834: do you have any more information for what the "umb" WOL functions can actually be used for?

I've just upgraded from an onboard NIC (supporting g only which I could wake up with a magic packet) to an intel pro NIC card that also supports umb as well as g.

I'm hoping I can get my ubuntu PC to wake up on either TCP or UDP packets too.  Will this be possible?

---

### Post by nickb834 on 2007-11-02
> **njparton said:**
> nickb834: do you have any more information for what the "umb" WOL functions can actually be used for?

I've just upgraded from an onboard NIC (supporting g only which I could wake up with a magic packet) to an intel pro NIC card that also supports umb as well as g.

I'm hoping I can get my ubuntu PC to wake up on either TCP or UDP packets too.  Will this be possible?


wake on lan is UDP by default IIRC, it used to be on port 0 but is now most commonly on port 7 or 9.

So the answer to your question is - yes it is possible because this is already how it works......

you only need to worry about the 'b' switch as this is the "Broadcast" that we want to wake up on. Unicast and multicast relate to routing types which you don't really need to get into for wake on lan to work.

---

### Post by njparton on 2007-11-03
Thanks for your reply.

Well, I can wake my PC by using m or b when I try and access the share via my comupter (just what I was after).

However, it now also just wakes spontaneously after 2-3 mins of sleeping. I'm wondering if my router is broadcasting to it and waking it up?

This happens whether I use m or b alone.

Hmmm, any ideas?

---

### Post by markiep on 2008-03-01
Just wanted to say THANK YOU! :guitar::popcorn:::)

---

