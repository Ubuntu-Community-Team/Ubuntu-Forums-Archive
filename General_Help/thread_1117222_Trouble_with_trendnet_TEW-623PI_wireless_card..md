---
title: "Trouble with trendnet TEW-623PI wireless card."
date: 2009-04-05
forum: General Help
---

### Post by emoXodus on 2009-04-05
I have had trouble with my trendnet TEW-623PI wireless card.



Someone on #ubuntu (irc.freenode.net) helped me use ndiswrapper.  I installed it and he told me to do:

```
ndiswrapper -i /path/to/drivers/bcmwl5a.inf
```



I did that and it worked fine.  He then said that I should do:

```
ndiswrapper -l


```

It displayed this:

```


 netr28 : driver installed

 	device (1814:0601) present

 rt2860 : driver installed

 	device (1814:0601) present


```

I was told that this was good, and that I should reboot my computer.



However following a reboot, it didn't work, and when it booted up it took much longer and said something about waithin for cman to start.



Does anyone know why it didn't work.



And ill give Ben Crisford (my helper) the link to this post if you have any questions for him.

---

### Post by Ben Crisford on 2009-04-05
Yes, Ben Crisford (his helper) did receive a link to the post :D.

---

### Post by Ben Crisford on 2009-04-06
I'll give it a BUMP for you mate ;).

---

### Post by wrose51106 on 2009-04-06
Ive had issues where ndiswrapper fails to load after a reboot, lets see if it is there.

Terminal ---> sudo lsmod | grep ndiswrapper

Does anything appear? Or does it drop you back to the command line as if nothing happened?

Is this a USB or PCI card? Chek to see if the system see is.

Terminal ---> lsusb     or lspci for whichever the card is.

---

### Post by emoXodus on 2009-04-06
its a pci card and it is detected, just unknown to the system

---

### Post by wrose51106 on 2009-04-06
Lets start from the beginning, I do not know what all has been done.

Head into package manager, we are going to remove then reinstall the following 2 packages:

1) ndiswrapper-common
2) ndiswrapper-utils-1.9

Now we need to configure Ndiwrapper to startup with the machine so it is running. Open a terminal, then type...

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Once this is done, reboot the machine and open a terminal up, lets make sure ndiswrapper is accounted for and present.

sudo lsmod | grep ndiswrapper

It should throw a couple of lines back at you, if not, redo the previous step. I have seen it take a few takes to get in there right :/

Once this is done the hard part begins. Locate the latest driver for your card. (I am refencing revision 3 of your card for the following) 

Download the driver file, open and go Drivers\winxp\ now extract the x86 directory somewhere.

Once this is done crack that terminal back open and navigate yourself there, once there....

sudo ndiswrapper -i rt2860.inf

I believe I got the filename right that you will need to use. If not, make changes where needed.

Now that the driver is installed, lets make sure everything is good.

sudo ndiswrapper -l

This command will list the driver. the install command used the letter I while the listing used L, both lowercase. Let us know.

-Bill

---

### Post by emoXodus on 2009-04-07
i just did all that and my internet isnt working, im pretty new to this and i dont know much of what im doing it would be pretty convenient to have someone to remotely do thin for me

---

### Post by wrose51106 on 2009-04-07
Your going to have to explain what part is not working and or your having problems with. Follow my guide and lets see what is or isn't working.

-Bill

---

### Post by 73ckn797 on 2009-04-12
I just fixed a weak signal with the Trendnet TEW-423Pi wireless card in Jaunty & Intrepid.

After reading this thread I found the graphical solution. Perfect for a new user to use and understand.

In Synaptic Package Manager look for "ndisgtk". selecting that will also load the other necessary ndiswrapper files. Once installed you will find it under System/Administration as wireless drivers. Insert the CD that came with the card and copy the WINXP directory from the drivers dirctory to your download or document directory.

Open the new program and from there select the *.inf file from the directory you copied off of the disk. Once that is completed reboot your system. You may have to re-enter any password(s) for the wireless access.

There is also this thread about doing this via terminal but I like to provide graphical solutions as much as possible. Let me know how this works for you. I went from 10% signal strength to 95% in Jaunty. The router is only 10 feet away. The Intrepid signal went from 8% to 95% and that computer is at the other end of the house and upstairs from where the router is.

Thanks to [wrose51106]("http://ubuntuforums.org/member.php?u=781947") for much of this basic info regarding copying off of the CD.

---

