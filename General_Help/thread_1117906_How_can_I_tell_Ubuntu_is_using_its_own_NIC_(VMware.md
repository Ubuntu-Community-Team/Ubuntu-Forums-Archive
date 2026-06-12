---
title: "How can I tell Ubuntu is using its own NIC (VMware)"
date: 2009-04-06
forum: General Help
---

### Post by garethsimpsonuk on 2009-04-06
Hi,

I have Ubuntu running as a virtual machine on W2k3 using vmware workstation. 
I have 2 NICs and selected bridged networking at setup. I was wondering if anyone knew how i could determine if Ubuntu is actually using its own NIC instead of sharing the W2K3's one.

I'm new to virtualisation.

Thanks

---

### Post by 3Miro on 2009-04-06
You can do ifconfig from Ununtu trminal and see info for the NIC.

I don't know how VM Ware works, but Virtual Box emulates a virtual NIC and then it can be set up to use the host one either via NAT or "shared" where the virtual machine and the host get two separate IPs from the DHCP. In fact that way they are both viewed as separate computers. That can be done with one NIC only.

---

### Post by garethsimpsonuk on 2009-04-06
thanks for the reply.

yes i used to use virtual box and it seems a bit more complicated with VMware. here's what i've done:

edit-virtual network editor - assigned VMnet0 to my second NIC

then:

vm - removable devices - network adaptor - settings - custom, assigned second NIC

it seems to be working fine but i would like to test if each os is using their own network card

thanks for the reply

---

