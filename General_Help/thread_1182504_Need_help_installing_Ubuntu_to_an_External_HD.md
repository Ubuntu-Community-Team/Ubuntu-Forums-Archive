---
title: "Need help installing Ubuntu to an External HD"
date: 2009-06-09
forum: General Help
---

### Post by sendblink23 on 2009-06-09
I have an Acer 3680 custom Laptop

That has a Primary Hard Drive of 160gb & an External Flash Hard Drive of 15gb(which has been made into *internal)

All I want is to Install the Ubuntu 8.10 on to the Flash HD (Especially That it does not touch anything of the other regular Primary HD)

*Example as in I simply press F12 (boot Option Menu) and Select the Flash Drive to boot, to be able to access Ubuntu 8.10  <---  This is what I want to do. *In other words not having to Dual Boot from Grub, just using F12 to boot to it.

"Little Test Story - *Today" 
I had previously had installed in this laptop, OS X(in the Primary HD), did install Ubuntu on to the Flash HD afterwards using Guided - use entire Disk & selecting ONLY the Flash HD ...  soon after done & restarting, the computer directly booted into Linux (tried even to stop in  Grub to see if it had OS X in the menu.. but it was not there. So, Restarted the machine and booted with F12, chose the Flash HD to boot.... and it gave me Error *No Boot, so assumed it installed a Swap or something to my Primary HD  (*Flag) to make the Flash to Boot Grub. So I decided to boot from Live CD, head into Gparted.. found that it did add a Flag Boot into my Primary HD (in other words it ruined the OS X boot). So then went into Linux to see if I could see & access the Data of the OS X.. and yes it appears that Primary HD was Mounted with the data of OS X

Anyways.. blah long confussion info I know..   so I simply decided to Format Everything... and make this Post, to try my Idea differently, by installing first Ubuntu to the Flash .. and afterwards, installing OS X into the Primary *That way it will work my plan of simply using F12 to choose which to Boot.. I just want a safe way.. so it does not TOUCH ANYTHING of the Primary HD when installing Ubuntu to my Flash HD


Hope someone can help out with simply installing Ubuntu *ONLY* to the Flash Drive

---

### Post by sendblink23 on 2009-06-09
anybody wants to help me out? (30 minutes only 1 Read) I  have helped out 4 threads while waiting for any type of simple help on mines

---

### Post by sendblink23 on 2009-06-09
Found This, and it seems it is exactly the issue that happened to me in my *Little Story*

> FROM: blazemore (April 16th, 2009)

go ahead and try for yourself if you want to put Ubuntu on an external HDD. There has been many searches on getting Ubuntu on an external HDD, so I&#8217;m posting this. I do warn you though, if you try this with your internal HDD in, you might damage it. Also, you will probably fail at this, just as a heads up. OK, now down to the instructions.

1. Format your external HDD to ext3 or FAT32 or whatever you want it to be, it doesn&#8217;t matter as long as you wipe the hard drive clean.

2. Check your BIOS and make sure you are enabled to boot from an external USB device. (If you dont know what BIOS is then I highly recommend you don&#8217;t try this)

3. Put your copy of Ubuntu into the CD tray, turn off the computer, and remove your internal HDD. (If you leave it in very bad things will happen and you will lose everything).

4. Boot the computer from the CD and run a live session, make sure the external HDD is unplugged. (If you&#8217;re external HDD is plugged in at startup then the system will not boot)

5. Once it has booted, plug in the external HDD and wait for it to mount.

6. Click on the &#8220;Install&#8221; icon on the desktop, go through the language and time-zone steps, until the partitioner starts up.

7. Click on the second option that says &#8220;Guided - Use entire disk&#8221;. There should only be one drive that is found (sda), use it. If there is more than one drive in then exit the partitioner immediately, turn off the computer, and take out that other drive.

8. Partition the disk, it will unmount, but that is normal, go get a coffee or something because it will take longer than usual.

NOTE: If you get an error installing GRUB or anything else then you have to restart the installation. This may happen sometimes due to the fact that you are using USB.

9. After the installation the CD will prompt you to reboot, restart the system, let it load, and voila!



So, I guess all I need is someone to help to insert a Command, so that I Unmount my Primary Hard Drive (so it is not readable upon Ubuntu Installation Process)

Obvious I need it this way.. since Hello I do not want to skrew up my laptop by opening it up(I'm no tech builder).. to disconnect the Hard Drive LOL =P 

Anybody know how to do this (unmount primary HD) with the Ubuntu Live CD??
*NOTE* In my BIOS there is no way to change anything(it doesn't even have a Advance Area), Acer Blocked it :(

---

### Post by Cheesemill on 2009-06-09
When you do a normal Ubuntu installation it defaults to placing the boot loader on the first hard drive (your internal) no matter where you install Ubuntu. There is no need to remove your drive though, just follow the following steps:

When partitioning make sure you choose to install to your external disk.
Then (and this is the important bit) on the last page of the install screen click advanced and you will be asked where you want to install the boot loader. Just select your external drive for example sdb (not sdb1) and your problem is solved.

Cheesemill

---

### Post by sendblink23 on 2009-06-09
OMG thanks... I always wondered  what was the purpose of that last page button *Advanced (I always assumed it brought you back to the partition page) :P

Well thank you so much


I wonder why nobody makes this tutorial around Using exactly what you mentioned at the end simply choosing *Advanced and choose where to install boot grub

;)

---

### Post by sendblink23 on 2009-06-09
Thanks to Cheesemill .. here is the METHOD to do it, if anybody else wants it


**Easiest method to install Fully Ubuntu OS on a USB Hard Drive or Flash Drive, using Ubuntu Live CD**

Super Simple - *THIS IS THE CORRECT WAY* Using the Normal GUI Installation

Boot with Live CD

Connect USB Device (Once detected right-click "unmount")

Choose Install from Desktop

After the language, keyboard etc.. and enter the choose where to install Ubuntu area, Choose use Guided Entirely and select the USB Device HD

Do all the normal filling username, password... and when you get to the final Page Where you choose to begin the Process *Click the Button Advanced*

In there choose where to install the Boot Grub - Just select the USB Device HD and Ok

And confirm the Instalation Process


THERE YOU GO DONE! Full Ubuntu Install on a USB Device Hard Drive / Flash Drive

*no coding, or partitioning.. or casper thingy .. Just Regular Install GUI of Ubuntu Live CD

---

