---
title: "Viewing windows pc over network"
date: 2006-01-02
forum: General Help
---

### Post by gslater on 2006-01-02
Hi

I have just installed Ubuntu onto my new pc and I wish to access the files from my old windows pc over the network.  I have file sharing turned on on my windows pc but when I go into file browser I cant seem to access the other pc.

I have tried the "connect to server" function and then specified a windows share that I wish to connect to but it is asking me for a password.....I know I do not have a passowrd on my windows PC and I tried my password on my Ubuntu pc....but it is not letting me in

Any suggestions?

---

### Post by TrinitronX on 2006-01-02
You need to be using samba to get this working.  I had some troubles with firestarter blocking connections to a windows 98 PC on my network, but after adding the machine's IP to the whitelist in firestarter, I was able to connect.

Try doing the following:
Test to see if you can get a netbios table from the machine.
```

nmblookup -A <insert IP of your windows machine here>

```

Now you can try getting a share list from the machine.  You may need to input your password for the windows machine after executing the command.  To try it without getting prompted for a password, add the -N flag to the end of the command.
```
smbclient -L<insert machine's name here> -I <insert machine's network IP here>
```

If you don't know the name of your windows machine, it should be listed in the netbios table which you got before.  If both of these commands were successful so far, you can now try mounting a share on the machine.  To do this, first make a mount point.
```

cd /media
sudo mkdir <insert whatever folder name you want here>

```

Remember the mount point's path, because you need to use it in the mount command:
```

sudo mount -t smbfs //<machinename>/<sharename> /media/<mountpoint folder> 

```

If your shares are protected on the remote machine, you may get prompted for the username and  password.  To avoid being asked this, add them into the command line:

```

sudo mount -t smbfs -o username=<username>,password=<password> //<machinename>/<sharename> /media/<mountpoint folder>

```

Now change directory back to the mountpoint and try to get a file listing.  If it worked, you can browse the files on the remote machine.  If it didn't work, you will get an empty directory listing (unless the actual share has no files in it :p)

If it didn't work, post the error message you are getting here

---

### Post by Jason_25 on 2006-01-02
It's alot easier just to click places > network servers.

---

### Post by zentus on 2006-07-22
This works great for me when the share isnt visible in places - network servers.  However i have to follow this procedure every time i restart my machine.  Would anyone know how to do it permanently?

---

### Post by razor7 on 2006-07-22
You may want to add a cron job for that, or just add a mount line to etc/fstab

---

### Post by calx on 2006-07-25
```

calx@rasta:/media/ameibein$ smbclient -L AMEIBEIN -I 192.168.0.88 -N
Domain=[AMEIBEIN] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        Media           Disk
        DVD             Disk
        New (E)         Disk
        ADMIN$          Disk      Remote Admin
        Shares          Disk
        C$              Disk      Default share
Domain=[AMEIBEIN] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

calx@rasta:/media/ameibein$ sudo mount -t smbfs //AMEIBEIN/Shares /media/ameibein/Shares
[B]mount: wrong fs type, bad option, bad superblock on //AMEIBEIN/Shares,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

calx@rasta:/media/ameibein$ dmesg | tail
[17265328.344000] sd 2:0:0:0: rejecting I/O to device being removed
[17265328.344000] sd 2:0:0:0: rejecting I/O to device being removed
[17265328.344000] sd 2:0:0:0: rejecting I/O to device being removed
[17265328.344000] sd 2:0:0:0: rejecting I/O to device being removed
[17265328.344000] sd 2:0:0:0: rejecting I/O to device being removed
[17265328.344000] sd 2:0:0:0: rejecting I/O to device being removed
[17280653.144000] smb_fill_super: missing data argument
[17280666.204000] smb_fill_super: missing data argument
[17280722.760000] smb_fill_super: missing data argument
[17281102.964000] smb_fill_super: missing data argument

```

Any ideas?

> **TrinitronX said:**
> If it didn't work, post the error message you are getting here

---

### Post by TrinitronX on 2006-07-28
ok... so from this output, it looks like it's a filesystem problem (most likely).  Make sure you've got the "smbfs" package installed in synaptic, or simply do a:
```
sudo apt-get install smbfs
```

The second thing that could be causing the problem would be from netbios name stuff going wrong.  I'm assuming your machine with the shares has the IP: 192.168.0.88 on your home network, and is named "AMEIBEIN".  Also, from what it looks like, it's set up to be in the "AMEIBEIN" domain?  If that samba output is right, you might want to change that computer to be in a workgroup instead.  Otherwise, that's fine.

If it's a netbios problem, you can test the "smbclient -L AMEIBEIN -I 192.168.0.88 -N" command without the -I <IP ADDRESS> option to check if your computer is translating the name to a network IP.

It most likely is the filesystem problem though, so check that first.

---

