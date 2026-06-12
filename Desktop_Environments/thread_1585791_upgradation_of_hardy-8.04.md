---
title: "upgradation of hardy-8.04"
date: 2010-10-01
forum: Desktop Environments
---

### Post by prudra on 2010-10-01
I have pre-installed ubuntu-8.04 on my netbook with bios-access locked by password and I have not been supplied with the password. I want to upgrade ubuntu to a higher version. Not having the bios-access password I cannot use an installation-usb. Is it possible to upgrade through broadband network and how?
Thanks for help.
P.Rudra.

---

### Post by julio_cortez on 2010-10-01
Well, the first thing that comes to mind is that if the netbook has the BIOS locked by a password and you don't know it, probably you're not the owner of the netbook.
So, the first thing I'd suggest you to do is ask the owner if 10.04 can be installed or if the netbook just needs 8.04 for some particular reason (and if the owner says there's no problem installing 10.04 I'd ask also for the BIOS password).

If you're told that the netbook HAS to be on 8.04, probably there's a reason, so I wouldn't mess with it further. If you're told that 10.04 can be installed, then, if you have the BIOS password you're free to do what you want.
If you still aren't provided with the BIOS password, have you already considered the [network upgrade]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade")?

---

### Post by sikander3786 on 2010-10-01
Not sure if there is a direct path of upgrade from 8.04 to 10.04. Haven't done it but what I have read somewhere is that you have to upgrade release by release. 

It will be better to do a fresh installing, after backing up your data, and of course after you get the Bios password. :-)

---

### Post by julio_cortez on 2010-10-01
> **sikander3786 said:**
> Not sure if there is a direct path of upgrade from 8.04 to 10.04I thought there was, by reading what is written on [this]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade") Ubuntu.com page:
> **Upgrade from 8.04 LTS to  10.04 LTS**

 **Network  upgrade for  Ubuntu desktops (Recommended)**

 You can  easily  upgrade over the network with the following procedure.   
 
[LIST=1]
[*]  Press Alt-F2 and type update-manager --devel-release   
[*] Click  the **Check** button to check for  new  updates.  
[*] If there are  any updates to install, use the **Install   Updates**  button to install them, and press **Check** again after  that is complete.  
[*]A  message  will appear informing you of the availability of the new  release.  
[*] Click **Upgrade**.   
[*]Follow the on-screen  instructions.   
[/LIST]


I'm also suggesting a "clean" reinstall maybe with the 10.04.1 CD but if it's not feasible I think that the network one could be tried :)

---

### Post by prudra on 2010-10-02
> **julio_cortez said:**
> I thought there was, by reading what is written on [this]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade") Ubuntu.com page:


I'm also suggesting a "clean" reinstall maybe with the 10.04.1 CD but if it's not feasible I think that the network one could be tried :)

I followed this procedure, but only a new kernel  2.6.24.28-generic was added to the menu.lst . But the OS remained 8.04 . Further on it is showing that the system is up-to-date.

But a serious problem has introduced. The touch-pad mouse on the netbook is not working and the only option available now is the usb-mouse. How shall I rectify this?

The password problem is that my broadband provider offered a free netbook with pre-installed ubuntu if i paid in advance 3-years' payment for infinite download. They didn't tell me that it is 8.04 version and an OEM machine. I planned to create an installation-usb by #dd if=xxxx.iso of=/dev/sda bs=4M on my other laptop which unfortunately has only 38GB HD memory. When I proceeded to use the usb on the netbook I found that usb-access is password protected. I corresponded with the supplier but they refused to give the password. I know that it is highly objectionable business practice. But pursuing a legal route in this part of the world is extremely expensive and also harassing. So I am saddled with with this OEM machine with a lower version OS.

But please attend to the touch-pad problem.
Thanks.
P.Rudra.

---

