---
title: "WakeOnLAN on mini 10"
date: 2009-09-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fjgaude on 2009-09-15
Has anyone figured out how to use WOL on the mini 10?

I've downloaded and installed **wakeonlan** software but from down the LAN the mini will not come out of sleeping. I've tried SSH, ping, don't know what else to try.

Oh, the BIOS has WOL enabled.

Thanks for any suggestions!

---

### Post by SteveDee on 2009-09-15
Try running this from a terminal:-
ifconfig
...this will give you the ethx identity, then run:-
sudo ethtool ethx
...where x is the correct number for your ethernet port. This will show you if "Wake-on" is enabled.

If it is, try this on remote machine:-
wakeonlan -i 192.168.0.255 00:12:34:56:78:9a
...but using your broadcast IP and appropriate MAC number.

---

### Post by fjgaude on 2009-09-15
Thanks, this gives me much to try... my wol support shows a 'g' and 'pumbg', not sure if it means I have it or not.

I am not able to ping the sleeping mini from my main box. Will keep trying things to see if I can make it work. Anymore suggestions?

---

### Post by SteveDee on 2009-09-16
> **fjgaude said:**
> Thanks, this gives me much to try... my wol support shows a 'g' and 'plumg', not sure if it means I have it or not.

I am not able to ping the sleeping mini from my main box. Will keep trying things to see if I can make it work. Anymore suggestions?

The wake-on codes have the following meanings:-
              p  - Wake on phy activity
              u  - Wake on unicast messages
              m  - Wake on multicast messages
              b  - Wake on broadcast messages
              a  - Wake on ARP
              g  - Wake on MagicPacket(tm)
              s  - Enable SecureOn(tm) password for MagicPacket(tm)
              d  - Disable (wake on nothing).  This option clears  all  previous options.

So code "g" indicates it is correctly set for use with wakeonlan. (you can type: "man ethtool" in a terminal to get full information).

I've just confirmed, on a computer here, that a sleeping computer does not respond to Ping. The network interface only responds to a "Magic Packet" ([http://en.wikipedia.org/wiki/Magic_packet](http://en.wikipedia.org/wiki/Magic_packet)).

And just to clarify; its the handsome prince that needs wakeonlan installed, not the sleeping beauty machine. The broadcast IP is basically the sleeping machine IP but the last digit cluster is 255 (xxx.xxx.xxx.255). Likewise the MAC number is that of the sleeping machine.

I hope this helps.

---

### Post by fjgaude on 2009-09-16
Okay, and thanks once again... I get it... will have it working soon. <smile>

Later, down the lines...

Seems the NIC doesn't get power when the mini 10 is sleeping. Likely has something to do with how the OS, 8.04, handles the sleep mode. Ah, well...

---

