---
title: "Auto mounting network drive after wireless conn is established"
date: 2008-11-14
forum: Desktop Environments
---

### Post by PowerEngine on 2008-11-14
Hi everybody.
I only connect to the network after I login and connect my wireless card .. I was wondering if there is a way to auto-mount a network drive after this connection has been established. or maybe with a delay after booting or logging in.

Thank you very much in advance for any help ...

---

### Post by ohzopants on 2008-11-14
How good are you at scripting?

If *I** were attempting this I'd probably write a simple bash script to check the SSID of my wireless network (to make sure it's the right one, so I don't try to mount shares that don't exist) and to check whether they are already mounted.  Then just make it run as a cron job.

* I say "If I..." for a reason: I'm not the best scripter in the world and there may also be a much easier way to do this that I'm unaware of.

---

### Post by bford16 on 2008-11-14
You don't say how you are sharing you files.  If you are using Samba, you should be able to see your files on demand, whenever you open the share from the desktop, once you connect.

If you are sharing files **FROM** a *nix machine only **to** *nix machines, you can use NFS to share your files.  See: <http://nfs.sourceforge.net/nfs-howto/>

---

### Post by PowerEngine on 2008-11-15
ohzopants :
-----------
I'm not that good at scripting but I am a fast learner :)
and I would appreciate it if you could show me a sample script of how to do that. What interests me in your approach is that you check if you were connected to the right network before attempting the mount.

bford16 :
---------
I am using Samba. The network folders are on NAS (Network attached storage) which is of NTFS format.
I don't get how you can see the files (Drives) from the desktop before you do the mounting ?!

---

### Post by bford16 on 2008-11-15
PowerEngine,

You don't say what your network mix is, but I am going to assume that your shared folders are hosted on a Linux machine.

Ubuntu has some graphical front-ends for Samba, but I have found that the surest way to get folders shared is to edit /etc/samba/smb.conf.  Since 'gedit' is installed, you might as well use that.  Press Alt+F2, then```
gksudo gedit /etc/samba/smb.conf
```There are three things to edit.

Workgroup.  You may want to set up a workgroup if you share to Windows machines.

Security (in the 'Authentication' section.  Setting security=user will force users to enter a username and password to access the shared folders.

Finally, you need to enter something to show Samba what you want to share.  Somethig like this, added to the end of the file, will work just fine.```
[shared]
path = /media/shared/shared
available = yes
browsable = yes
public = yes
writable = yes

```This sets up a shared folder, accessible by all users, with read&write access.

---

### Post by PowerEngine on 2008-11-17
Hi Pros .. before we get all technical let's have some popcorn :popcorn:

alright ..down to business .. :)


my network is like the following :

Laptop :
---------
OS : Ubuntu.
Connectivity method : wirelessly connected to the network.

This is my personal laptop and it is not the file server.

NAS ( Network attached storage ):
---------------------------------
Disk format : NTFS 
Connectivity method : connected to the router with an ethernet cable.

- This is the file server (the folders that I want to mount are hosted here)
- This is a home network, the NAS ip address is internal (192 ..etc )


The wireless connection is established after logging in -> entering the password of the wireless network.

I hope this info is more clear and helpful in defining the problem.

---

### Post by ohzopants on 2008-11-18
I'd really rather not provide you with a sample script, since I really have no idea where to even start.  I know it can be done, but I'm just not that good and (no offense) I'm not going to google it for you.  Check out iwconfig for figuring out which network you are connected to.

You may want to look at a program called smb4k.  It's a KDE program, but it still runs fine in Gnome.  It's a very nice little samba graphical  frontend for mounting windows shares.

Also (I'm on a windows pc, so some of the wording may be off a little), try going to Places -> Connect to Network (...?).  This should pop up a dialog box asking about the details of your server and if you connect successfully once it should then be listed under Places.  From then on when you click on that server under places your drives should be mounted automagically.

---

### Post by PowerEngine on 2008-11-18
Thanks ohzopants :KS:KS .. the Places -> Connect to Network .... is a decent solution. :)  it does the trick for me.

But I noticed that when I do this mounting ubuntu takes longer to halt and restart. I looked at the "boot" log , but it says nothing has been added yet.

Just to complete the topic .. is there a way to umount the mounted automatically before halting ( restart or power off ) ?

---

### Post by sauce345 on 2008-11-18
I think i can help you.  I recently did the same type of thing.  I have windows shares on my network that i want to mount automatically.  At first i wrote a bash script and did the trick but i still was running the bash script to mount them.  

The thing to do is to edit your fstab.  This is located at /etc/fstab.  You will want to add a line like this:

//netbiosname/sharename /media/sharename cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

The smbcredentials file is a file you make with your user and pass for the shares.  The format of the file is:

username=YOURUSERNAME
password=YOURPASSAWORD

This file can be put anywhere and make sure that you use a . in front of it so that it is hidden.  Its really quite easy.  After editing the fstab you can type sudo mount -a or restart your computer.

For all the information you need about this check out this awesome post: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by PowerEngine on 2008-11-18
Thanks sauce345 .. but this only works if you are connected with ethernet. because the network connection has to be established before linux reads the fstab to mount the partitions. otherwise it will not be able to recognize the network address 192..... and thus won't mount all the partitions in the fstab.

On the other hand ohzopants's approach works in a situation similar to mine.
----------------

The only thing though is that I am not able to find the location where samba mounts these network folders.. I only see them in my places menu and a shortcut on my desktop..but I don't know where they are mounted in the filesystem.
I need to know the mount location because on my network folder I have a TrueCrypt folder, and I need to know the path to feed it to TrueCrypt to mount my volume from the network folder.

---

### Post by sauce345 on 2008-11-18
PowerEngine, you do not need to be connected with ethernet first.  If the network is unavaible when the computer reads the fstab it just does not mount them.  Then when on the network type:

sudo mount -a

And it will either throw an error because something is not specified right or it will mount the network drives properly.  I use it with my wireless all the time.  

Anyway not sure if this helps because of your Truecrypt and unfortunely i don't know a lot about truecrypt.

---

### Post by PowerEngine on 2008-11-19
That is correct. sorry I didn't notice that you mentioned the mount -a.
Thanks a million for your help.
------------------------------
Is there a hint regarding the path of the mounted folders using the graphical interface (ie Places -> connect to server .. ) ?

Cheers..

---

### Post by ohzopants on 2008-11-19
I don't think that folders you access that way are actually mounted.
If you open the shared drive in Nautilus and press Ctrl+L you should see the path of the folder.  I'm pretty sure it will start with smb:// which means it's accessing it via samba and not as a local directory.

---

### Post by PowerEngine on 2008-11-19
aha .. yes it does start with smb:// 
so Samba doesn't mount network folders in local disk to access them ?

---

### Post by mtn on 2009-08-21
> **sauce345 said:**
> PowerEngine, you do not need to be connected with ethernet first.  If the network is unavaible when the computer reads the fstab it just does not mount them.  Then when on the network type:

sudo mount -a

And it will either throw an error because something is not specified right or it will mount the network drives properly.  I use it with my wireless all the time.  

Anyway not sure if this helps because of your Truecrypt and unfortunely i don't know a lot about truecrypt.

Hi, I seem to be having the same problem. I'm running Ubuntu Janty Remix on an Eee PC 701. I have everything set up to the point that after start, up, if I execute ```
sudo mount -a
``` in a terminal, then my network folder is mounted to the local folder, as set up in fstab```

//192.168.1.20/Peter-on-Network /home/peter/Peter-on-Network	smbfs	auto,credentials=/root/.smbcredentials,uid=1000,umask=000,user	0 0
```

I'm setting this up for my technically illiterate father, so, I need the network folder to mount at start up - without the need to open a terminal and run a command. 

I am assuming the folder is not being mounted automatically because the wireless network connection is not established before fstab is executed?! Any suggestions would be much appreciated...

---

### Post by DuckSedo on 2009-09-09
Hi all,

I am having an identical situation to PowerEngine. 
Two questions on using /etc/fstab and mount -a
1) How does it take the SSID of the network in account? a.k.a. How do i prevent mounting things on the wrong network? (Can the SSID be used in the path for the credentials?)
2) I which script should i place the mount -a in order for the mounts to be done without any special user action?

---

### Post by DuckSedo on 2009-09-09
An ugly solution:
In the login script start a second script in the background; 

second.sh&


second .sh contains:

sleep 1
mount -a



increase the sleep time if needed.

---

### Post by feizex on 2009-09-25
Hi,

I am also looking for a solution to mounting network shares after wireless is connected.

As noted earlier, entering network shares into /etc/fstab doesn't work because wireless is not connected when mount all happens.

I happen to be running WICD to do connection because it avoids needing to put in default keychain password every time you boot (I have autologin set). Try it, it is pretty easy to setup. [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

NOTE: if using WICD and you only have wireless NIC, you should delete wired (eth0?) connection profile in WICD or it will sit there trying to get DHCP on non-existant NIC for 3 minutes or so. And it will wait till that times out before connecting to wireless.

Now back to my point... On googling, I found that WICD has a function to run script after connect. This may be what you need. Do your mount script and have WICD run it after wireless is connected!

Regards,
Feizex.

PS. please excuse any inaccuracies, I still have my linux training wheels on. =)

---

### Post by DeusEx on 2009-10-29
take a look here.\
[http://ubuntuforums.org/showthread.php?t=1161166&highlight=smbfs+auto+mount](http://ubuntuforums.org/showthread.php?t=1161166&highlight=smbfs+auto+mount)

---

### Post by jesperborgstrup on 2011-10-12
Hi all!

Since I wanted to accomplish the same thing, but couldn't find any useful information about it, I wrote a small article about how I got it to work on my Ubuntu 11.04:

[Ubuntu: Automatic mounting of Samba share when connected to a wireless network]("http://jesper.borgstrup.dk/2011/10/ubuntu-automatic-mounting-of-samba-share-when-connected-to-a-wireless-network/")

Hope it will help somebody :-)

---

