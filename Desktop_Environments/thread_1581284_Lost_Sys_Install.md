---
title: "Lost Sys Install ?"
date: 2010-09-24
forum: Desktop Environments
---

### Post by lotusalive on 2010-09-24
I accidentally installed dhcp-3, & uninstalled dhcp-client on my Desktop 9.04 installation. My Desktop is giving me these errors when I boot into kernel-19-Generic (Recovery Mode):

1) Internet Browser: 
> Firefox can't find the server at start.ubuntu.com

2) Synaptic:
> Could not resolve security.ubuntu.com

Are there any steps I can take to salvage my installation ?:confused:

---

### Post by pricetech on 2010-09-24
You'll have to set your IP, Subnet, Gateway, DNS Servers manually.  After that you should be able to reinstall the client.

---

### Post by lotusalive on 2010-09-24
:KSYAY! TYSM Pricetech !  ISP is giving me a hard time over their not supporting Linux.  I don't really know if I have all the correct addresses to set it up myself.  I could just ask them what you have said, & not tell them I'm using Linux !  I'll give that a go first:P  Thanks again.:)

---

### Post by lotusalive on 2010-09-25
If someone can help me, I'm still a bit lost on HOW to get my Network Configured properly.  Current 'Problems' are as follows:

1) Netgear N150 Router for 2 PC's:
a) eMachine running Ubuntu only, as when I first installed Linux 1.5 years ago, I did not read the Docu first, to protect hda (W's driver ?), so that now I have no access to original NTFS, & eMachines site download, will NOT reinstall the driver by itself.  They also would not send me a Boot CD when requested from Telephone Support, so all I have is the OS Disk Vista, that will not install without hda (proprietary driver? access).  This Sys Install is configured with an NTFS Partition, this one drive never picks it up.  [I DO now have a second drive, with ribbon cable, as of yesterday, but have not attached it to this machine yet.]

b) Second PC is Dell also, running W's 2000, har, just for guests.

2) Router is off both machines currently (using Modem & Live Disk to be here): a) Router wasn't working with 'Dynamic' Setting at their site (?) EVER, changed it to 'Static' until this problem with P2P for Skype Installation, last Wed.  I changed it back to 'Dynamic,' at the Netgear Site, still not working, & I suppose I better go back to 'Static' IP, with the Router connected, or I won't have an OS, at this point.  Although, ISP claims they are doing Dynamic...

3) Configured Network Setting with P2P, but it is still not connecting me to Internet, same msg as above, NOR to Synaptic, as if Sys is broken.  ISP said I MUST USE IPv4, but when I saved P2P as a 'Location,' it says ONLY 'ip6' (same as IPv6 ? program I have installed along WITH IPv4...)  :confused:

See how much trouble a non-programmer can get into & BE ?  :confused:  I feel so bad about troubling someone to understand me & help me untangle this.  But if someone does know, many thanks in advance for some guidance.

P.S. localhost in Network Settings shows a different address for this PC than I use for ISP.  Does that matter ?

---

