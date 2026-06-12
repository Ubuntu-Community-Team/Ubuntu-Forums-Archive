---
title: "FreeDOS, VMWARE"
date: 2006-07-08
forum: Desktop Environments
---

### Post by jISh on 2006-07-08
Couple questions. I've been toying with VMWare Server and FreeDOS on and off for most of the day.

Installing it was a real hassle. It randomly selected options from the menu, it won't boot if I choose the first option in the list (after installing) which was Use All Available RAM, and all sorts of crap. Think it failed to install one important display file during installation as well.

My main question is, since I finally managed to get it working, how can I share files between my actual hard drive, and the virtual hard drive thing inside VMware. I did download and install SAMBA, and shared the folder I want to access inside DOS, but don't know how to get to it from DOS.

Also, for some reason DOS, when at the C:\> promt, uses 100% CPU power (at some points during the install it used no CPU power, so there's obviously some flaw here).

I'd like to get this working, I started this idea for a shot at some old-school DOS gaming, but I want to use VMWare for other purposes in the future, so that's why I'm not bothering with DOSEmu.

---

### Post by jISh on 2006-07-09
Fell way off into the depths of the forums :(

---

### Post by jISh on 2006-07-09
Well, it looks like I just wasted the previous 3 hours of my Sunday. F***!

I got FreeDOS installed fine in VMWare now, I got the program "DOSIDLE" installed to solve the CPU consumption problem.

I can't get my CD-ROM to work in this AT ALL, though. Not my real CD-ROM, I'm trying to mount ISO images. No matter what, there's always SOME ERROR that prevents ATAPICDD.SYS from loading. I am so unbelievably pissed off right now, it looked like VMWare had made some changes to the CONFIG.SYS or something, it pointed to the ISO image I had mounted to load the install CD...

But no matter what I cannot assign it a drive letter. It's the last bloody step I need so I can copy files over to the DOS partition. (yes, I was using mkisofs and mounting them with VMWare).

Seriously, I don't believe nobody on this board has never done this before. There has to be a solution...

---

### Post by jISh on 2006-07-09
Bump.

---

### Post by frup on 2006-07-10
Don't know if im going to be much help, i had no problem installing it a few days ago, i just selected one for nearly every option. 

The CD stuff possibly could be happening because of the .vmx file config (i dont use the server version yet though) for me theres some config about ide1:0 and you can make it present (true or false) start connected (true or false) and choose whether to load it straight from a CD-drive or iso... is all that set up correctly?

I haven't got it networked yet, would you mind telling me? also is their anyway to browse the internet on it or anything?... before i figured out you could network in VMware i was just loading the to my localhost on ubuntu where i had the files i wanted to copy (and thats how i worked out i could probably network too :) ) ... hope all that isnt completely useless :S lol

---

### Post by jISh on 2006-07-10
I don't know how to network. But if I figure it out, I'll be sure to post here. In fact if I ever get this entirely figured out, I'll write a guide on it.

In the meantime, could you please tell me how you connected to the VmWare local host in order to copy files?

Also, I severely messed up my CONFIG.SYS trying to get the CD drivers to work, since yours works, could I see it? :D Thx!

---

### Post by kd7swh on 2006-07-10
Dosbox is another dos emulator that uses few cpu cycles and is great for gaming.

---

### Post by jISh on 2006-07-10
Thanks, but I had a horrible slowness in trying to play games in DosBox. I fed it almost all of my CPU power and OMF:2097 was a sluggish beast (on my 2.6GHZ P4..)

Besides, I know people have done this FreeDOS on VMWare thing, something simple like transferring files over has gotta be possible.

---

### Post by jISh on 2006-07-11
Bump.

---

### Post by Thund3rstruck on 2006-07-11
can't say I've ever attempted to install DOS in VMWare server but to network them you do the same thing you do on 2 physical computers. 

If you have samba installed on your Linux host the you need to create samba users (i think the command is smbpasswd -a UserName), the user account needs to be the same as your DOS/Win user crudentials. 

Then you need to share folders and define rules for your samba server via smb.conf (/etc/samba/smb.conf, if i remember right)
I think there is a web-based tool called webmin (but again, its been a while since I did this)

Once thats done you map via dos: net use x: \\ServerName\ShareName /PERSISTANT:NO

Hope This Helps...

---

### Post by jISh on 2006-07-11
Okay, I got the samba part set up, and my folder shared, now about the dos mapping part...

Do I do it in CONFIG.SYS? Also, would there be a special program or driver I'd need to install into DOS to make this work?

The x: \\Servername\Sharename part, server name is the name of my installation (FreeDOS is the name)?? And sharename is the folder inside of it I want to share? So say I made a folder called vmtrans, it'd be:
net use x: \\ServerName\ShareName /PERSISTANT:NO ??
^note, that didn't work, so i figure I interpreted it wrong or I need a driver/file.

I never networked back in the DOS days, so I'm clueless at that :(

---

### Post by jISh on 2006-07-12
Bumpage.
If I ever get this all figured out, I'll be sure to write a guide so nobody else has to go through this wall of seemingly unsolvable problems :O

---

### Post by lamego on 2006-07-12
To network with the guest system you will need DOS TCP/IP support on your guest, I don't believe FreeDOS comes with it.
Found [this]("http://freedos.sourceforge.net/freedos/news/technote/157.html") on google, give it a read.

---

### Post by VirtuAlex on 2006-07-12
I did not run FreeDOS, but I have DRDOS running on my vmware. I'm able to mount iso as cdrom. If it would be any help here are my config files:
config.sys
```
DEVICE=C:\DRDOS\EMM386.EXE NOEMS I=B000-B7FF
DEVICEHIGH=C:\CD1.SYS /D:CDROM1
SHELL=C:\COMMAND.COM C:\ /E:512 /P
BUFFERS=15
FILES=30
FCBS=4,4
LASTDRIVE=Z
HISTORY=ON,512,ON
DOS=HIGH,UMB
```
autoexec.bat
```
@ECHO Off
PATH C:\DRDOS;C:\
VERIFY OFF
PROMPT [DR-DOS] $P$G
SET DRDOSCFG=C:\DRDOS
LOADHIGH MSCDEX.EXE /D:CDROM1 /V
REM NWCACHE 7136 1024 /LEND=ON /DELAY=OFF
```

---

