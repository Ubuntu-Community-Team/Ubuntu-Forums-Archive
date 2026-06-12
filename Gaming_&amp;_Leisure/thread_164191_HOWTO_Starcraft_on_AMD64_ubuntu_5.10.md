---
title: "HOWTO: Starcraft on AMD64 ubuntu 5.10"
date: 2006-04-22
forum: Gaming &amp; Leisure
---

### Post by Iesos on 2006-04-22
I just bought a new system and wanted to try out StarCraft in linux. There where several problems i encountered along the way and this is a sumrize of how I did, and it worked for me (non of the other StarCraft guides on this forum did work for me).

To begin with one need to install Chroot, which is a sort of 32-bit eviornment on your 64-bit system. (I'm very new to linux so I don't know much, please correct me if I start telling lies.) To install chroot follow this howto:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)
I had to alter one step to get it working, where it says 

$ sudo mkdir /chroot/media/cdrom0

I also had to add 

$ sudo mkdir /chroot/usr/share/fonts

But try it first as it says in the HowTo. Without this I'd got an error message when I tried to run Synaptic32 later. When you have got the synaptic32 up and running: 

Install wine.

This can be done either in synaptic32 or by

$ dchroot -d
$ sudo apt-get install wine

When wine is installed you need to get in to the 32-bit enviorment i.e. you should write

$ dchroot -d

from here you should run winecfg:

$ winecfg

Here you need to check your Drives setting. Make sure that your CDRom directory is correct. Example: For me it says:

D:       /media/cdrom0/

Then you can exit winecfg. Try to insert you starcraft cd at this point and mount it. (to me it is)

$ sudo mount /dev/hdc /media/cdrom0

It might complain over that /media/cdrom0 doesnt exists. then you need to:

$ sudo mkdir /media/cdrom0

and try mount it again.  (You are working in your 32-bit enviornment thats why the mountpoint might not exist)
If you have succeded in mounting the cd, run the setup:

$ wine /media/cdrom0/setup.exe

And complete the setup as you would in windows. (If broodwar: unmount the starcraft cd and mount the broodwar cd. Then run the broodwar setup)
Now you should have installed StarCraft. Try to run it:

$ wine ~/.wine/drive_c/Games/Starcraft/starcraft.exe

(obs: thats my location of the game).
At this point there are often errors (I just got error free). The errors I've got:

1. Insert the cdrom.
To solve this, make sure that the cd is mounted (In the 32-bit enviornment) and that the mountpoint is the same as the one in winecfg, and that the drive is of type CDROM (not Local hard drive. sometimes this cannot be altered then you need to wipe out your .wine folder and start all over agian, instructions further down).

2. Direct Draw error.
I don't get the reason for this problem. I solved it by this sequence (OBS this removes all of the information in the .wine folder, I will not be held responsible for any losses, make sure to back up eventual saves or other files)

$ sudo rm -rf ~/.wine/
$ sudo apt-get remove wine
$ sudo apt-get install wine
$ winecfg

Add the mountpoint for the cd and then install and try to start the game again. At this point it worked for me. But wine is a mysterious thing (almost like windows :-) ), so if it doesnt work, try some of the other HowTo's on wine installation. I have tried most of them, and none did work (as good as this). 

Good luck and I hope to meet you on Battle.net!

---

