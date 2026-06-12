---
title: "Wireless card not detected on Ubuntu under VMware Player"
date: 2011-07-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KaloyanYordanov on 2011-07-30
I want to say that im new and i like Linux  but i have some problems.  

========================================
My Specs: Dell Inspiron N5010 Win7 64bit (notebook)
Integrated Wireless Card: DW1501 Wireless-N WLAN Half-Mini Card (I have drivers for Win 7)
Second USB Wireless Adapter: Realtek RTL8192C USB (I have drivers for Win7 // Linux -kernel 2.6.18 ~ 2.6.35 from mini CD comming with the adapter)
========================================

Im curently using Win 7 x64 and running in same time "Ubuntu"or "Other Linux 2.6.x kernel" under VMware Player 3.1.4-385536 with Black Track 4 Final(ISO) loaded in CD/DVD. Using this method:

[http://www.youtube.com/watch?v=7idbM...eature=related](http://www.youtube.com/watch?v=7idbM...eature=related) !! Not sure if Networking settings is right.. bridget or NAT? 

Wireless(integrated) is working under Win7 64bit,With manually downloadet drivers (dell.com) afrer installing Win7.  Fn+F2 is not working under Linux.I want to use the USB Wireless Adapter(Realteck) for the Guest Machine ("Ubuntu"or "Other Linux 2.6.x kernel")


---The problem is that i want to use USB Wireless Adapter (Realteck) in Guest Machine

-I want to know how to check my wireless card.And how to install drivers (The drivers for the USB adapter are *.tar )

-How to search for wireless networks and connect to one of them.

-How to turn on/off wireless.

---

### Post by SeijiSensei on 2011-07-30
Virtual machines usually don't talk to the wireless cards directly.  Instead, the virtual machine manager creates a virtual Ethernet for the guest machine.  In the Ubuntu machine, try opening a terminal and entering the command "ifconfig" at the prompt.  Do you see an entry with an IP address?

---

### Post by KaloyanYordanov on 2011-07-31
Yes you are right :) And ifconfig says:

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
..and some zeros down for packets,errors,drops and etc

=================================================================================================
I was reading this days,and maybe i should buy second USB Wireless device for the Guest Machine

[http://communities.vmware.com/message/1484955](http://communities.vmware.com/message/1484955) <- Is it true?

Is there any other way to make Guest machine to use Wireless not like virtual Ethernet?

---

### Post by SeijiSensei on 2011-07-31
I can't help with VMWare; I use VirtualBox to run VMs.  If you're not especially committed to VMWare, I'd recommend giving VirtualBox a try instead.  It's very easy to install.

Take a look at [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) for details.

You might have better luck with this question in the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum.  If you can't move it there yourself, click the "Report Abuse" button on the left and ask a moderator to move it for you.

---

### Post by varunendra on 2011-07-31
> **KaloyanYordanov said:**
> Yes you are right :) And ifconfig says:

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
..and some zeros down for packets,errors,drops and etc

=================================================================================================
I was reading this days,and maybe i should buy second USB Wireless device for the Guest Machine

[http://communities.vmware.com/message/1484955](http://communities.vmware.com/message/1484955) <- Is it true?

Is there any other way to make Guest machine to use Wireless not like virtual Ethernet?I have been using VMware (Workstation, Player, Server) and VirtualBox for almost 3 years now. The info on the forum you linked above is absolutely true and complete. [s]There's no option or workaround to make any PCI based card directly or indirectly visible to the guest OS unless it falls under the same catagory as the VM provides by default (sound, video and Ethernet LAN) - the most generic type (virtualized) hardware.[/s] [COLOR=DarkRed][COLOR=Red]**Correction:** [/COLOR]**A VM can only 'see' the hardware which is included in its list of hardware, and so far there is no option to include a PCI based wireless card in that list of (virtual) hardware. The VM will still be able to use the physical machine's connection (of any type) through its virtual Ethernet interface which is connected to the physical machine's wireless interface over a virtual bridge/switch.**[/COLOR]

Apart form this, since USB is the only supported interface that allows connecting an external hardware to the VM, you are limited to the use of only USB based devices to make them directly visible to the guest OS.

Also, as already emphasized on the forum you linked, make sure to only choose such a USB device which is supported by linux if you decide to go this way, and keep in mind that USB devices can not be made visible to both host and guest at the same time (but I'm sure you don't need this anyway). That is, as soon as you connect the device to the guest, it is (logically) disconnected from the host OS.

---

### Post by KaloyanYordanov on 2011-07-31
I keep understanding new and new things ,but not everything is clear to me.Linux is still very new and strange for me(witch combination with VMware Player is more complicated to me) . I started new Topic here. I have some more question in common now here [http://ubuntuforums.org/showthread.php?p=11105087#post11105087](http://ubuntuforums.org/showthread.php?p=11105087#post11105087)

And i have reported this Topic for closing :)

---

### Post by varunendra on 2011-07-31
Topics are closed in rare cases. ("closed" means no more posts are allowed):)

If you think the purpose of a thread (that you started) is solved, then you can (and you SHOULD) mark it as [solved]. Follow my signature to see how.

By the way, the new thread you started is just a duplicate of this one. It is not recommended (in fact, avoided) in this forum. As you are already getting active attention/support on this one, the other one doesn't make much sense to me. :)

---

### Post by lisati on 2011-07-31
If this thread is solved, please mark it as such. Your other thread has been closed.

---

### Post by KaloyanYordanov on 2011-07-31
Its not solved ,I still have questions .!! SEE FIRST POST(EDITED)!! :)

---

### Post by SeijiSensei on 2011-07-31
> **varunendra said:**
> I have been using VMware (Workstation, Player, Server) and VirtualBox for almost 3 years now. The info on the forum you linked above is absolutely true and complete. There's no option or workaround to make any PCI based card directly or indirectly visible to the guest OS unless it falls under the same catagory as the VM provides by default (sound, video and Ethernet LAN) - the most generic type (virtualized) hardware. Since USB is the only supported interface that allows connecting an external hardware, you are limited to the use of only USB based devices to make them directly visible to the guest OS.
VirtualBox creates a virtual Ethernet interface for the guest VM, then offers a variety of ways to connect the VM to the network.  The default is to use NAT, which lets the VM connect out to the network, but doesn't support inbound connections without some additional routing and perhaps firewalling rules as well. You can also choose other networking modes like bridging.  That makes the VM appear to have the same IP address as the host's external address; in my case that's an address assigned to my wifi adapter.

If you mean that I can't have the guest talk directly to the host's networking hardware, that's certainly true, but with VirtualBox it doesn't matter much in practice.  It sounds like the OP can't figure out how to make his Ubuntu VM see the external network at all.  Notice that ifconfig in his case shows only lo with no other interface.  I just booted my OpenSUSE VirtualBox guest; it has an eth0 interface with an address in 10/8 that's provided by VB's built-in DHCP server.

---

### Post by varunendra on 2011-08-01
> **SeijiSensei said:**
> VirtualBox creates a virtual Ethernet  interface for the guest VM, then offers a variety of ways to connect the  VM to the network......
....If you mean that I can't have the guest  talk directly to the host's networking hardware, that's certainly true,  but with VirtualBox it doesn't matter much in practice.
After re-reading my post I realized that I made a terrible mistake by including this line-
> **varunendra said:**
> There's no option or workaround to make any  PCI based card directly or indirectly visible to the guest OS unless it  falls under the same catagory as the VM provides by default (sound,  video and Ethernet LAN) - the most generic type (virtualized)  hardware..
SeijiSensei, thanks for bringing that to my attention. Perhaps my brain  was pretty messed up when I wrote it, sorry for that, I'm correcting  that mistake in my original post.

What I meant was that 'any' VM (in VMware or VBox, and am sure about  same for others as well) can only see the hardware that the virtualization  platform - VMPlayer in OP's case - provides by default. Since this  'default' hardware does not include a (default or optional) PCI-based  wireless interface, there's no way to make a VM 'see' a pci-wireless  card in its list of hardware. So USB is the only way to make it 'see' a  wireless interface.

But it is certainly possible (and a default behaviour) to make the  host's wireless connection and network available to the guest OS by  means of the VMs virtual ethernet interface. In this case, the platform  (VMPlayer/VBox...) does the job of 'talking' to the wireless card,  whereas the VM itself only 'sees' and 'talks' to its virtual ethernet  interface.

This is just like a computer which does not (and can not) have a  PCI-wireless card, but can still have a connection through its ethernet  interface which connects it to another machine which is sharing its  wireless connection over a bridge/switch. This bridge is virtual in a  VM's case. Hope this rough diagram makes up for my dodgy English:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Phy-VMNet.jpg[/IMG]

---

### Post by varunendra on 2011-08-01
@KaloyanYordanov,
I missed your 'changed' questions :)
> **KaloyanYordanov said:**
> Not sure if Networking settings is right.. bridget or NAT?
..

---The problem is that i want to use USB Wireless Adapter (Realteck) in Guest Machine

-I want to know how to check my wireless card.And how to install drivers (The drivers for the USB adapter are *.tar )

-How to search for wireless networks and connect to one of them.

-How to turn on/off wireless.
Which of the Bridge/NAT will be better depends upon what you want to achieve with the networking. If it is just Internet connection, any one would do (even "no networking" will do if you are going to use the USB adapter for it). For a specific purpose, you need to explain it to us so that we can suggest accordingly. For a general description/suggestion, it is already there in the VMware forum you linked in your second post: [http://communities.vmware.com/message/1484955](http://communities.vmware.com/message/1484955) (read post #5):
> .... 
You have 3 choices for how the guest networking is set up;
 
 
NAT  = Works in almost all situations, the guest Virtual Machine essentially  hides behind the host as far as the network is concerned.  You can do  most things except share printers or file shares from the guest.  Will  likely be the easiest for you to use.
 
 
Bridged  = Guest appears as it's own machine on the network.  Does not work with  some wireless router configurations, is only needed if you want other  machines to access your guest Virtual Machine from the network.
 
 
Host  Only = Limited network connectivity, essentially the guest VM can only  reach the host from a networking perspective.  Typically used when only  purpose of the guest is testing something that is running on the host....
---To connect the USB adapter to the guest machine, you have to connect it to the host first. Once it is detected, you can connect it to the running guest machine through **Virtual Machine > Removable Devices** menu.

- After connecting it to the guest, you can check whether it was detected or not by the guest 'BackTrack4' using the following commands:
```
lsusb
```and
```
lshw -C network
```To install the drivers, extract the contents of the .tar file to a folder, then look for some 'readme' or 'install' file in it. There should be one containing the instructions for installation. Typically, it is a sequence of three scripts - **configure > make > make install**. But it may differ.

Once the USB adapter is installed and UP, it will automatically detect wireless networks. As far as I remember, BT4 requires manual enabling of the network by using **ifconfig <your network interface****> up **command. However, I'm not aware if there's also a manual step required to connect to a wireless network.

To turn off wireless, you can use the command **ifconfig <your wireless interface> down**. To turn it on, just change 'down' to 'up'. I don't remember if there was a more elegant way to do this like NM in Ubuntu.

---

### Post by KaloyanYordanov on 2011-08-01
The wireless in now working,and his name is wlan0
-scan for networks OK :)
-join network OK ;)
-turn off/on OK :)

I want also monitoring mode,but after typing:

iwconfig wlan0 mode monitoring
Error for wireless request "Set Mode"(8B06) :
    SET failed on device wlan0 ; Invalid argument.

I have installed the drivers:

There was install.sh in driver folder so i used in Terminal  "./install.sh" . Right?

I have readet a lot ,and i found that Realtek is not making drivers that are supporting monitoring mode ,so my stock drivers are useless for this ,but is there other way to make monitor mode to work?

---

### Post by varunendra on 2011-08-01
> **KaloyanYordanov said:**
> The wireless in now working,and his name is wlan0
-scan for networks OK :)
-join network OK ;)
-turn off/on OK :)
Would you mind telling us if there are some non-obvious steps you are following to do these? I mean just a mention of how you are doing these. Just for sake of others looking for help on similar issues :)


> **KaloyanYordanov said:**
> There was install.sh in driver folder so i used in Terminal  "./install.sh" . Right?If the driver installed and is working now, it must be right.. ;)

> **KaloyanYordanov said:**
> I have readet a lot ,and i found that Realtek is not making drivers that are supporting monitoring mode ,so my stock drivers are useless for this ,but is there other way to make monitor mode to work?Um.. I've no idea about this. As for 'workarounds', maybe [chili555]("http://ubuntuforums.org/member.php?u=35909") could help you.

Anyway, since the original problem is solved now, I'd request you to please tell us how you managed to get it working and mark this thread as [solved]. For the monitoring mode support, you may wish to either PM [chili555]("http://ubuntuforums.org/member.php?u=35909") to see if he can help, or if it is really important, I'd suggest to post a new thread for it with suitable title.

---

### Post by KaloyanYordanov on 2011-08-02
1. There was install.sh in driver folder so i used in Terminal "./install.sh"

2. "ifconfig"  checking the wireless adapter name - wlan0

3. "/etc/init.d/wicd start"   -to start the adapter

4. "ifconfig wlan0 up"          -maybe this is not needet :)

5. "sudo iwlist wlan0 scan"       -scan for wireless networks

6.   "iwconfig wlan0 essid <name> key:l <pass>"
                   or
     "iwconfig wlan0 essid <name> key s:<pass>"        to connect to network with pass :)

7. When i want to turn off Wireless adapter  "ifconfig wlan0 down"

---

### Post by AbodiSattar on 2011-08-07
did not work with me 

i use dell INSPIRATION N5010 windows 7 32-bit 

i use vmware to open backtrack 5 but it dont active the DW 1501 half mini card

?????

can any one help?

---

### Post by varunendra on 2011-08-07
> **AbodiSattar said:**
> did not work with me 

i use dell INSPIRATION N5010 windows 7 32-bit 

i use vmware to open backtrack 5 but it dont active the DW 1501 half mini card

?????

can any one help?
AbodiSattar, Welcome to the forums :)
As this thread is marked [Solved], you should post your question in a new thread of your own. You may then post a link to that thread here so that we can follow.

By the way, as heavily discussed in this thread, a virtual machine can not see an inbuilt wifi card as 'wifi'. It will see a virtual 'ethernet' interface which then communicates to the actual wifi card in the background. If it seems confusing or you want a direct solution, please post your question in a new thread and we can discuss it in detail there.

Thank you.

---

