---
title: "NIC Problem (Not Working) ASUS Board/Marvell"
date: 2006-04-03
forum: Desktop Environments
---

### Post by paradox101 on 2006-04-03
New to Ubuntu.

Was running Suse 10. fine, but was recommended Ubuntu and now I have issues. More than usuall that is. ;P

I have an Asus board with a Marvell built in. No activity lights on either my NIC or my router, which is a motorola off my Comcast cable modem. The system shows the device is there and it is active, but it's not..? ](*,) Here's what I've found so far..

IPv6 was installed as default, buuuut... I don't have anything capable of running IPv6. In fact, since it's so new, I don't know why it was installed at all. Is this the source of my problem? And if so, how do I roll back to 4?

Since I don't have network I cannot apt get ANYTHING!!  Help please.

---

### Post by Zimmer on 2006-04-04
Have a look here, this might help the IPv6 question.
[http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798)

---

### Post by paradox101 on 2006-04-04
Well I thought it was IPv6, but evidentally my NIC is just not initializing. I've checked everything I can think of..

NIC shows "Active" and IFconfig shows in active as well.

What are my options. I downloaded the drivers and put them on a cd-rom but I can't seem to get the damn things off the cd-rom to bunzip!

I put the drivers on my thumbdrive but the USB drive doesn't want to cooperate and mount!

](*,)

---

### Post by Zimmer on 2006-04-04
Which drivers did you download? and pls explain why you cannot get them from the CD. Is the CD mounted? Can you browse it?
Here are some more links I googled which may be of interest to you..they are mostly old stuff, though.
[http://devel.reinikainen.net/docs/how-to/a4740kbp/](http://devel.reinikainen.net/docs/how-to/a4740kbp/)
[http://www.leenooks.com/Marvell+Yukon+88e8050+PCI-E+ASF+Gigabit+ethernet+controller](http://www.leenooks.com/Marvell+Yukon+88e8050+PCI-E+ASF+Gigabit+ethernet+controller)
[http://www.ubuntuforums.org/archive/index.php/t-77985.html](http://www.ubuntuforums.org/archive/index.php/t-77985.html)
Regards
ZImmer

---

### Post by paradox101 on 2006-04-04
[QUOTE=paradox101]Well I thought it was IPv6, but evidentally my NIC is just not initializing. I've checked everything I can think of..

NIC shows "Active" and IFconfig shows in active as well.

What are my options. I downloaded the drivers and put them on a cd-rom but I can't seem to get the damn things off the cd-rom to bunzip!

I put the drivers on my thumbdrive but the USB drive doesn't want to cooperate and mount!

](*,)[/QUOTE]

OK moving forward or off Ubuntu because the support doesn't seem to be here.

My NIC works because I was running Suse 10.0 fine before installing Ubuntu.

Does anyone have any ideas for me to look towards? ifconfig shows the drivers are there.

as stated above system shows NIC is active/enabled but I have no blinky lights! ARGH!! Router works!

HELP!!

For some reason when I try to **cp** the file off the cd it won't come off -error "directory or file does not exist. CDROM mounted = yes, browseable = yes, I cannot even drag and drop from it.

---

