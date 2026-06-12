---
title: "Video memory in VirtualBox problem"
date: 2010-07-06
forum: Desktop Environments
---

### Post by Kognit on 2010-07-06
Hello!

My friend finally decided to switch to Ubuntu. Because of the nature of his work, he is compelled to use VirtualBox. When we have installed it i noticed that when you assign video memory the max value is 128 MB. That is a big problem for him because he has Nvidia with 512 MB and he needs 512 Mb and not only 128. I installed Guest aditions but the windows 7 in Virtual Box is really slow and not appropriate for his work. 
Is there any way to assign more video memory?

The next questions is if you could play games in VB without problems  which would otherwhise run smoothly  on Win 7 separated partition?

Please help!

---

### Post by Fire_Chief on 2010-07-06
Ok, you've got a lot of moving parts here so let's take this one bit at a time...

1. What kind of work does your friend do in Windows? What applications is he using? Does he run many heavy apps at once?
2. The general slowness of the VM is more likely due to not giving it enough regular RAM in the VirtualBox settings for the VM. For Windows 7 you really should use 1.5-2 GB of RAM at a minimum for it to run well without swapping like mad.
3. Loads of Video RAM is mostly useful for high-end applications (i.e. CAD, A/V production, professional photography) or high-end gaming. In either case, a VM will not perform as well as a native install of Windows. This is mostly due to the emulated VM hardware that VirtualBox presents to the Windows guest.
> The next questions is if you could play games in VB without problems which would otherwhise run smoothly on Win 7 separated partition?

Again, that depends on the game(s) you are playing. Minesweeper? Sure, no problem. World of Warcraft? Not likely. Accelerated 3D support is sketchy at best in VBox and is still pretty new. As this is more of a niche need in the virtualization market, I would not expect Oracle (current owner of VirtualBox) to invest tons of time or effort into this aspect.

The short answer is if it's a Windows only game, it will run best in Windows on native hardware. :(

If you upped the RAM in the VM to the minimum recommended amount and still find Windows 7 to run unacceptably, then running natively is the best option. Unfortunately then you must choose whether to dual boot, run just Windows on that hardware, or run Windows on a second machine. If he just wanted to play around with Ubuntu, he could either run it via Wubi or run Windows 7 natively and run Ubuntu in Virtualbox.

Cheers!

---

### Post by Kognit on 2010-07-06
Thanks for the quick reply!

My friend has assigned 1,7 GB of RAM to VB. He primarily uses Windows for Adobe Collection, especially After effects and Ilustrator. He uses, of course, Windows for games too, like COD, NFS Shift and the like. Hard stuff for resources.

As i can see from you reply there just isn't any solution in VB for my friend. So he has to do a double boot or the Wuby, just the way you put it.

One more question - is there any other emulator that would suit my friend better?

Once again thank you for your reply.

I will deliver the sad news to the friend :(

bye

---

### Post by maelzner on 2011-01-01
You can change the .xml file under the path. 

 /home/*your username*/.Virtualbox

1. Locate "Machines" folder 
2. Locate the folder of the VM that you want to change.
3. Locate the xml file. 
4. Open the File with Text Editor 
5. Look for this code **<Display VRAMSize="128" monitorCount="1" accelerate3D="true" accelerate2DVideo="true"/>**
6. Change Value to **VRAMSize="256"**
7. Save and Close
8. Then Check the Gui if changes were applied. 

VB can allow a maximum of 256 Mbs

[IMG]http://www.webxide.com/images/VM256.jpg[/IMG]

---

### Post by Kognit on 2011-01-03
Thx, i will tell him and he will try it out. Thx for the info

---

### Post by Astrals on 2012-05-16
Ubuntu 12.04 this technique still works but the file for me is "/home/****/VirtualBox VMs/****/*.vbox

Make sure virtualbox is not running when changing file.
Then make sure the 3D and 2D acceleration is ticked in vbox for desired os after editing file.
For windows os install "VBoxGuestAdditions" in safe mode.
This will enable you to install applications/games with base (minimal) install of 256mb.

Hope this helps.

---

### Post by nothingspecial on 2012-05-16
Thank you for the extra information, but please don't bump old threads to the top.

Closed.

---

