---
title: "help needed with installing Red Alert 2 with wine"
date: 2006-02-17
forum: Gaming &amp; Leisure
---

### Post by DaMaster_Architect on 2006-02-17
hello,

recently I downloaded wine 0.9.6 (from source) so I could install some simple windows games. However, when trying to install Red Alert 2, I get the following error(s):
[I]
rian@ubuntu:/media/cdrom0/RA2/SETUP$ sudo wine SETUP.EXE
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
[/I]

I have searched the internet, and this forum, to solve the problem. However, I can't find anything. I guess it has to do something with missing dll files, or a wrong configured virtual C drive. Eventhough I don't know how to solve these problems. I haven't rtried other windows executables so far, so I don't know whether the same problem occurs with other problems.

Could someone please help me?

Thanks in advance!

---

### Post by LordBug on 2006-02-17
Secdrv.sys is part of the SecuROM copy protection system.  Not sure how well WINE works with this.  My current understanding is "not well"

---

### Post by DaMaster_Architect on 2006-02-17
I see. Thanks for the quick reply!

maybe it's an idea to delete this file and burn the other files of the cdrom at another disc? I'll try.

by the way, I can get other games (worms2) installed flawlessly.

---

### Post by meastp on 2006-02-17
The best solution would be to install RA2 on a windows-machine. Apply 1.006-patch. Apply no-cd patch. Copy RA2-folder to linux. wine Ra2.exe

It works for me!

IPX LAN-gaming:

apt-get install ipx
sudo modprobe ipx
sudo ipx_interface add -p eth0 802.3 0x12345678

Last number, 12345678, is the network number, and must be the same on every machine, and also the frame type (802.3).

(**sudo** wine Ra2.exe)

---

### Post by boredg on 2007-06-19
double post. :S

---

### Post by boredg on 2007-06-19
i just installed ra2 via the method meastp mentioned, i.e. installin it on windows and then bringing it over to linux and running it on wine. the game itself seems to work, but the problem is that theres no sound :S the game doesnt even seem to detect any sound hardware present! im running ubuntu fiesty, on an acer 5024wlmi, im pretty sure its an ac'97 sound card.. any ideas?

---

### Post by Nehvrook on 2007-06-19
You probably need to set the sound drivers in Wine (Try OSS but if it doesn't work try ALSA, and then set it to emulation and see if one of those settings work for you, this fixed the same problem in Starcraft for me)

You can change the wine settings with "winecfg" in a terminal

---

