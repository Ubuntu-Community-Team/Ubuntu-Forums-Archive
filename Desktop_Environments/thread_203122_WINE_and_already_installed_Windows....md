---
title: "WINE and already installed Windows..."
date: 2006-06-24
forum: Desktop Environments
---

### Post by evil_elman on 2006-06-24
I'm trying to use Wine with my current Windows installation. I feel it's taking too long to reboot just to do something quick that requires Windows so I thought I'll give Wine a shot. The installation was made from the repos (0.9.9).

I've got an NTFS partition with Windows and the first thing Wine complains about is that it's unable to write to anything on this partition. Many applications won't run and most will have no functinality. Those that don't write to the file system work fine, though.

Also, I'm finding it quite hard to find any relevenat or up-to-date documentation on Wine.

Questions:
* Can I make it work on an already working Windows XP installation on an NTFS partition? 
* If not, can I convert an NTFS file system to FAT32 which is writeable?

---

### Post by Joey French on 2006-06-24
1) As far as I know, you cannot use an existing partition in wine, because wine creates it's own fake windows partition in which to do it's business. I have had wine running for a while, and had a windows partition back in the day, and never the two did meet.

2) I think that changing your NTFS to FAT32 will cause you to lose everything on that partition so it may be more effort than it's worth. 

If you are interested in running a windows environment in linux, why not give VMWare a shot? It seems a lot easier than the other alternatives, and has worked quite well for me in the past. Plus, VMWare player is free and easy to use.

Good Luck!
Joey French

---

### Post by ifokkema on 2006-06-24
[QUOTE=Joey French]1) As far as I know, you cannot use an existing partition in wine, because wine creates it's own fake windows partition in which to do it's business. I have had wine running for a while, and had a windows partition back in the day, and never the two did meet.[/QUOTE]
I'm not too sure, but I think you can select where this fake partition is. Therefor, you can just set it to whatever directory/mount point. Using a real windows directory should make Wine work better, because it has loads of native DLL's then.

[QUOTE=Joey French]2) I think that changing your NTFS to FAT32 will cause you to lose everything on that partition so it may be more effort than it's worth.[/QUOTE]
I believe there is an upgrade functionality in Windows to change from FAT32 to NTFS.... maybe the other way around works, too. Did you look for a Windows tool to change your filesystem type?

[QUOTE=Joey French]If you are interested in running a windows environment in linux, why not give VMWare a shot? It seems a lot easier than the other alternatives, and has worked quite well for me in the past. Plus, VMWare player is free and easy to use.[/QUOTE]
I second that! Only downside to the player (also in the reposotories nowadays!) is that you can't just install Windows under it. You need an preconfigured Virtual Machine. But you can download VMware server for free, and create a new virtual machine from that :)

---

### Post by lamego on 2006-06-24
It is possible to use a "real" windows partition mapped to a windows drive on Wine without problems, if it is NTFS it will be read-only because of the linux ntfs module.
There is no utility on windows to convert from NTFS to FAT32.
There was a project which supported NTFS write access, it worked at the time I have tried (some years ago), you can check it at [http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/) .

---

### Post by evil_elman on 2006-06-24
Thanks for allt the input guys! Really appreciate it.

I knew there was a tool ('convert') in Windows to convert FAT32 drives to NTFS. I had to use it before since Acer only supplies a rescue disc in FAT32.

I've tried out Wine for the last couple of hours and got a couple of apps working (when I figured out the file system layout i Wine compared to Linux). 
I either SE|PY + MTASC / Flash 8 works I'm going to settle for that. Otherwise I'll have to keep my Windows partition for a bit longer I think.

I also tried to install VMplayer but it gave me certain error messages, most notably that it couldn't connect to the internet for whatever reasons.

Anyway, I'll see if I've got the motivation to experiement with VMserver as well. It might not be as hard to deal with as I imagine but Wine will have to come first, for now... :-)

---

### Post by raptros-v76 on 2006-06-24
wow. i have an acer laptop also. i got rid of windows completely, just because there is nothing in windows that i need

---

