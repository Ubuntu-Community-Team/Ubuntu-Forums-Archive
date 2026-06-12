---
title: "General help needed setting up an SMB file server"
date: 2008-12-20
forum: General Help
---

### Post by palmboy5 on 2008-12-20
My goal:
I'd like to set up a Network Attached Storage system that will share two hard drives onto the network to be accessed by Windows-based PCs. Extras like web and SSH servers would be nice too, just for fun. 
After all setup is complete, the system needs to work simply by plugging in power and ethernet, then pressing the power button. Pressing the power button again will cause it to fully shut down. No mouse or keyboard.
The OS drive is a 16GB USB flash drive and therefore rules out Windows-based solutions, but I am unfamiliar with Linux so I need your help. ):P

First off, I currently have 8.04 server edition installed since it seems like the most sensible choice, but this whole lack-of-GUI thing is killing me. :confused: I would assume the desktop edition can do everything I need as well, once the needed software are installed... Should I install the desktop or server edition?

Thanks!

---

### Post by dcstar on 2008-12-20
> **palmboy5 said:**
> My goal:
I'd like to set up a Network Attached Storage system that will share two hard drives onto the network to be accessed by Windows-based PCs. Extras like web and SSH servers would be nice too, just for fun. 
After all setup is complete, the system needs to work simply by plugging in power and ethernet, then pressing the power button. Pressing the power button again will cause it to fully shut down. No mouse or keyboard.
The OS drive is a 16GB USB flash drive and therefore rules out Windows-based solutions, but I am unfamiliar with Linux so I need your help. ):P

First off, I currently have 8.04 server edition installed since it seems like the most sensible choice, but this whole lack-of-GUI thing is killing me. :confused: I would assume the desktop edition can do everything I need as well, once the needed software are installed... Should I install the desktop or server edition?


Installing the **ubuntu-desktop** package will add everything to the server install.

---

### Post by Zack McCool on 2008-12-20
Some may find this out of place for the Ubuntu forums, but the very best solution for you would likely be the FreeNAS project.  Download the iso, install it to the machine (has a very small footprint, and will work with as little as 128M of RAM), most configuration is done during the install.

Once that is done, it needs no further local interaction.  Boot it, and it runs.  All future config can be done via the included web interface, which is quite simple to use.  It offers SMB, SSH, NFS, Apple, and even iSCSI.  It also has a built-in bittorrent client and an rsync daemon.  It is based on FreeBSD.

The only slight difference from your request would be that I would still recommend a proper shutdown to just hitting a power button.  While this would probably work, it would be better to just do a shutdown from the web interface...

---

### Post by palmboy5 on 2008-12-20
By pressing the power button to shut down I don't mean an abrupt power off, I mean to have the power button trigger the shutdown procedure and then I wait until the lights/fans/etc turn off before doing anything. From what I see in Ubuntu desktop edition, the power button causes a menu to pop up asking what to do (and does nothing in server edition). I want it to just skip that and pretend I clicked on Shutdown in that menu.

FreeNAS does sound almost perfect. I originally overlooked it because I saw this project as a reason for me to formally dive into the world of Linux, but I'll take a look. 
Probably an insultingly stupid question for Ubuntu AND FreeNAS, but are their data transfer abilities multithreaded? My NAS is based off an Atom 330 which would be too slow for gigabit ethernet if only one core/thread was used.

---

### Post by Rapture2k4 on 2008-12-20
You can change what the power button does in the power options under Administration. I have my NAS box do a graceful shutdown when I press it or sleep when I hold it for 5+ seconds.

---

### Post by palmboy5 on 2008-12-21
I tried apt-get ubuntu-desktop and it went ahead and downloaded and installed everything but with several errors near the end. All efforts to boot after this cause it to freeze/fail early in the loading of the OS. I decided to just install desktop edition instead, but apparently whatever server edition was doing to the drive screwed it over. I get varying errors, the most absurd one being [http://www.mylilsite.net/images/ubuntuerror1.jpg](http://www.mylilsite.net/images/ubuntuerror1.jpg) :roll:

GParted couldn't do anything and had once told me that it could not find a mountpoint.

Currently formatting to FAT32 in Vista.. What else does Linux have that can deal with these problems? It would be embarrassing if Linux couldn't fix this while Windows could.

EDIT:
Oh, and for FreeNAS, I downloaded the .img of the most recent RC2 and opened it in Nero only for Nero to say "The entered block size does not correspond to the image length. The block size may be wrong. Do you want to correct the value or ignore the problem?" Choosing 'correct' asks for disk info I don't know, so I chose 'ignore'. The burned disk isn't even bootable.

---

### Post by palmboy5 on 2009-07-25
OK, after many months using FreeNAS as one person had suggested, I've decided that I still want to do a linux-based server instead. FreeNAS being based off FreeBSD needs UFS formatted drives which IMHO is just way too out there compared to ext3/4 and NTFS. But really it's because I want to be able to try stuff like XBMC on the server, among other stuff that needs more than just a WebGUI. A linux terminal I can SSH into from afar would also be great to have.

Anyway, on to my current question. How do I share an ext4 formatted drive in Ubuntu on the SMB **without any password prompting and with full read/write access**? Setting the share through the GUI lets me have full read/write access provided I enter my linux user/pass. Setting the share through samba's smb.conf or w/e allows no password prompting but no write access. ARGH!:(

---

### Post by cbraxton on 2009-07-25
> **palmboy5 said:**
> ...How do I share an ext4 formatted drive in Ubuntu on the SMB **without any password prompting and with full read/write access**? Setting the share through the GUI lets me have full read/write access provided I enter my linux user/pass. Setting the share through samba's smb.conf or w/e allows no password prompting but no write access. ARGH!:(

The following are the relevant parts of an smb.conf that I use for that purpose. It will permit guest read/write access to a shared directory, and creates files and directories with permissions for access by all users:

```

# Samba server configuration

[global]
    ; Basic server settings
    netbios name = SERVER1
    workgroup = WORKGROUP

    ; security settings
    security = share
    guest account = nobody

# Shared files (read/write)
[SHARED]
    comment = "Shared files"
    path = /home/SHARED
    valid users = nobody,@users
    guest ok = yes
    browseable = yes
    writeable = yes
    force group = nogroup
    create mode = 0666
    force create mode = 0666
    directory mask=1777
    directory mode = 0777
    force directory mode = 0777

```

---

### Post by palmboy5 on 2009-07-26
I copied your settings and so far it seems to be working, thanks!

Lets see how far I can get before another road block. :P

---

### Post by palmboy5 on 2009-07-27
Slightly unrelated question, what is a good checksum program that is preferably similar to ExactFile for Windows? At the least, I want a program that can create and read SHA512 digests of certain directories and its subdirectories.If it can support ExactFile's .exf digests (which are text-based), that would be great too.

---

### Post by palmboy5 on 2009-07-27
I've been checksumming my data that I've been copying back into a newly ext4 formatted and checked drive (in GParted), thus a heavy load on the server, and I keep losing my connection with the network share.. SSH'ing into the server also fails, I can't even get a login prompt. Checking on the actual Ubuntu desktop, there is no evidence of failure. Direct manipulation of the drive from the server desktop itself still works.

The checksums that manage to finish before another disconnect, pass.

What's going on?? :(

---

### Post by palmboy5 on 2009-07-28
The server's network share keeps going down still when under the load of something like checksumming of data on the storage HDD (750GB SATA). 

I tried copying many GBs of data onto the OS's drive (80GB IDE) and checksumming that data several times and the connection never died.

Unmounted the storage HDD to Check it in GParted and it was fine. Mounted back to try again with checksumming and the connection died in less than 15 minutes (pretty normal of this problem, and VERY annoying).

What should I do? :confused:

---

### Post by t4thfavor on 2009-07-28
You should look into turning up logging on the samba daemon, also watch the logs for failures during a period of heavy use. 

you can watch the logfiles from the terminal with this command.
```

watch tail -n 50 somelog.log

```

Sounds fishy that the SATA drive is the only one breaking. Also maybe try an fsck (File system check) on that device while its unmounted.

I also have a samba share on an ext4 drive, how many GB do you have to copy before it dies, maybe I will give it a try as my share is very light use only.

---

### Post by palmboy5 on 2009-07-28
The ExactFile checksumming (whether its doing a single file at a time, or 4) usually fails to finish a 21GB directory due to the connection dying. It HAS finished that directory before though, yesterday. One directory that I have not been able to finish at all, ever, is 77GB.

I should note that there seem to be two types of connection dying. One will come back to life by itself in perhaps 10 seconds, and the other is permanent and I have to reboot the server physically because SSH and shares go down together. Also, copying all my data to the server is fine, but copying back out from the storage HDD has the same problem as checksumming. I am currently testing to see if copying from the 80GB IDE has any problems. EDIT: copying from the 80GB was fine.

Could you tell me how to turn on the samba logging and what settings I should use? Thanks!

---

### Post by t4thfavor on 2009-07-29
I never had to turn it on, but I think there are settings in the samba.conf file.

I always have good lick reading dmesg output, and looking through /var/log/daemon.log. There may be others in the /var/log folder that could interest you, perhaps something like

```

cat /var/log/messages|grep samba

```
That will print the log "messages" to the screen filtering all lines that do not contain "samba".

---

### Post by palmboy5 on 2009-07-29
I don't know which log files to look at, so I did
```
vcn64ultra@Diamondville:/var/log$ cat *.* | grep samba
Jul 26 01:39:47 Diamondville sudo: vcn64ultra : TTY=pts/1 ; PWD=/home/vcn64ultra ; USER=root ; COMMAND=/usr/bin/nano /etc/samba/smb.conf
Jul 26 01:45:45 Diamondville sudo: vcn64ultra : TTY=pts/1 ; PWD=/home/vcn64ultra ; USER=root ; COMMAND=/usr/bin/nano /etc/samba/smb.conf
Jul 26 01:59:49 Diamondville sudo: vcn64ultra : TTY=pts/1 ; PWD=/home/vcn64ultra ; USER=root ; COMMAND=/usr/bin/nano /etc/samba/smb.conf
Jul 27 05:08:32 Diamondville sudo: vcn64ultra : TTY=pts/0 ; PWD=/home/vcn64ultra ; USER=root ; COMMAND=/usr/bin/nano /etc/samba/smb.conf
Jul 27 05:09:07 Diamondville sudo: vcn64ultra : TTY=pts/0 ; PWD=/home/vcn64ultra ; USER=root ; COMMAND=/usr/bin/nano /etc/samba/smb.conf
2009-07-25 23:56:53 install samba-common <none> 2:3.3.2-1ubuntu3
2009-07-25 23:56:53 status half-installed samba-common 2:3.3.2-1ubuntu3
2009-07-25 23:56:54 status unpacked samba-common 2:3.3.2-1ubuntu3
2009-07-25 23:56:54 status unpacked samba-common 2:3.3.2-1ubuntu3
...
2009-07-25 23:59:16 status unpacked samba 2:3.3.2-1ubuntu3
2009-07-25 23:59:16 status unpacked samba 2:3.3.2-1ubuntu3
2009-07-25 23:59:16 status unpacked samba 2:3.3.2-1ubuntu3
2009-07-25 23:59:16 status unpacked samba 2:3.3.2-1ubuntu3
2009-07-25 23:59:17 status unpacked samba 2:3.3.2-1ubuntu3
2009-07-25 23:59:17 status half-configured samba 2:3.3.2-1ubuntu3
2009-07-25 23:59:19 status installed samba 2:3.3.2-1ubuntu3
2009-07-25 23:59:19 configure samba-doc 2:3.3.2-1ubuntu3 2:3.3.2-1ubuntu3
2009-07-25 23:59:19 status unpacked samba-doc 2:3.3.2-1ubuntu3
2009-07-25 23:59:19 status half-configured samba-doc 2:3.3.2-1ubuntu3
2009-07-25 23:59:19 status installed samba-doc 2:3.3.2-1ubuntu3
```

which just looks like the logs of installing samba.

In the /var/log/samba/ directory, I checked 
```
vcn64ultra@Diamondville:/var/log/samba$ watch tail -n 50 log.smbd
Every 2.0s: tail -n 50 log.smbd                                                            Wed Jul 29 01:27:14 2009

[2009/07/28 15:49:18,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/07/28 16:31:30,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/07/28 16:43:53,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
...
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/07/28 20:05:36,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/07/28 20:05:36,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/07/28 20:14:37,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/07/28 20:14:37,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/07/28 20:14:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/07/28 21:09:53,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/07/28 21:52:18,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
```

I don't know if any of that is useful.. :\

---

### Post by palmboy5 on 2009-08-02
The network disconnect issue was most likely caused by a variation of
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252307](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252307)

My server does use the 8111/8168 and Ubuntu did choose to load r8169 for it. I have compiled a r8168 driver from realtek.com's tarball and so far have not had any network issues.

---

