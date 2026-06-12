---
title: "KDE, openoffice and opening files through samba"
date: 2006-01-07
forum: Desktop Environments
---

### Post by greatshape on 2006-01-07
HI,
I've got a fileserver in my network. 
I've got a samba share on it containing openoffice calc files.
So on my desktop i go to network,myworkgroup,server,file and i open it.
The file gets loaded and i can edit it. When i hit save, i don't get any complaints, it just saves. 
BUT...When i re-oopen that file on the server again, all my changes are gone !
I found out that the file isn't saved on the server but at the local dir /var/tmp/kde-cache-yves/krun 
And that's not what i want. 
If i open a file on the network, edit and save it again, it should be saved on the networkserver, and NOT local. :confused: 

Does anyone have a solution for this? 
Regards, Steve

PS In gnome this works perfect.

---

### Post by jferrando on 2006-01-07
The best way of working with an smb server is mounting the partition: this gives access to all apps, and is the only way that works decent.
You will need the smbfs package installed. In my case, I have an entry in **/etc/fstab** for the share:
//192.168.8.5/datos  /home/jferrando/surera  smbfs  credentials=/etc/smbc.jordi,uid=1000,gid=1000,auto  0  0

The file **smbc.jordi** contains:
[I]username = jordi
password = mypassword[/I]
And is chmod 600, owner root.

And I mount it using
$ sudo mount /home/jferrando/surera

Because it does not auto-mount on start-up of the system... hope anybody can help with this.

You can also use
*$ mount -t smbfs ...*
But I don't remember exactly the syntax.

---

### Post by greatshape on 2006-01-07
[QUOTE=jferrando]
You can also use
*$ mount -t smbfs ...*
But I don't remember exactly the syntax.[/QUOTE]

For the moment there is no passwd on that share
I tried this , but as you see no luck.. 
```

yves@Linux:~$ sudo mount -t smbfs //192.168.2.135/home/shared/ /mnt/server
mount: wrong fs type, bad option, bad superblock on //192.168.2.135/home/shared/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

yves@Linux:~$   
yves@Linux:~$ sudo mount -t smbfs //192.168.2.135/shared/ /mnt/server
Password:
mount: wrong fs type, bad option, bad superblock on //192.168.2.135/shared/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

yves@Linux:~$                                

```

As you can see, i created a dir /mnt/server to mount it to, so that's not the problem.
Any idea's?

---

### Post by GeneralZod on 2006-01-07
smb4k is a nice GUI for creating smb mounts - you might want to try that out and see if it's useful.

---

### Post by greatshape on 2006-01-07
ok, got it,
smbfs was not installed :rolleyes: 
```

sudo mount -t smbfs //192.168.2.135/shared /mnt/server

```

Now take a look if it will sove my problem

---

### Post by jferrando on 2006-01-07
Here is an script that works on my system. Copy it on a file mountsmb.sh, chmod 755, and execute:
$ sh mountsmb.sh

[I]#!/bin/bash
#Mount samba filesystems
echo "Mount samba filesystems"
echo -n "Usuer windows: "
read username
echo -n "Password windows: "
read -s password

umount -l /home/jferrando/datos
mount -t smbfs //localhost/datos /home/jferrando/datos -o username=$username,password=$password,uid=jferrando,gid=jferrando
[/I]

Please check that the **smbfs** package is installed (with synaptic or whatever)

---

### Post by greatshape on 2006-01-07
Ok, solved.
Added this to /etc/fstab
```

#mount smb shares
//192.168.2.135/shared /mnt/shared smbfs uid=1000,gid=1000,auto 0 0

```

I had some permissions issue's first(files opened read-only), 
but after some chowning and chmod's
everything works fine :-)

Tnx guys

Steve

---

### Post by greatshape on 2006-01-07
[QUOTE=GeneralZod]smb4k is a nice GUI for creating smb mounts - you might want to try that out and see if it's useful.[/QUOTE]

Hey, tnx sure interesting to take a look at!

Regards, steve

---

