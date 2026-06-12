---
title: "Mount samba cifs network share using network names instead of IP addresses"
date: 2006-07-05
forum: Desktop Environments
---

### Post by TuxCrafter on 2006-07-05
Dear fellow tuxers, :KS 

I had the problem that IP address of computers on my network where dynamic. This was causing problems with mounting scripts.

Information:
Windows NetBios network share name: 
```
windows-me6000
```

How does men get the IP address:
```
nmblookup windows-me6000
```
This will give me:
```
querying windows-me6000 on 145.52.123.255
145.52.123.227 windows-me6000<00>
```

Now I only want to know the IP address:
```
nmblookup windows-me6000 | tail -n 1 | cut -f 1 -d ' '
```
This will give me:
```
145.52.123.227
```

This is a standard simple way of mounting:
```
sudo mount -t cifs //145.52.123.220/E$ /mnt/windows-e
```
This is a better way:
```
sudo mount -t cifs -o credentials=/home/Jelle/.creds_me6000,uid=500,gid=500,file_mode=0664,dir_mode=0775 //145.52.123.220/E$ /mnt/windows-epia/
```

Now instead of using  a IP address you try this
```
sudo mount -t smbfs -o username=xxx,password=xxx //windows-me6000/E$ /mnt/windows-epia/
```

But smbfs wil not always work, I made a script that will do the job
```

#!/bin/bash

R=$(cat /etc/redhat-release)
echo $R

ipaddress=$(nmblookup windows-me6000|tail -n 1|cut -f 1 -d ' ')
echo $ipaddress

#Mounting a windows network share
su - -c "mount -t cifs -o credentials=/home/Jelle/.creds_me6000,uid=500,gid=500,file_mode=0664,dir_mode=0775 //$ipaddress/E$ /mnt/windows-epia/"

#su - -c "mount -t cifs -o credentials=/home/Jelle/.creds_me6000,uid=500,gid=500,file_mode=0664,dir_mode=0775 //145.52.123.220/E$ /mnt/windows-epia/"

cd /mnt/windows-epia/
ls -hal

```

Useful tools
```
. /etc/bash_completion
```
```
smbtree
```
```
smbc
```

Give some feedback if it was helpful

---

### Post by Thund3rstruck on 2006-07-05
I'm sure this won't help but you need DNS. We use a Win2003 Active Directory server with DHCP/DNS. Since all the linux/BSD clients get IPs from the server they also get A-records created as well so all my devices (Tivo/XBOX/MythTV/etc/) are available by name. 

Other than using a DNS/DHCP I can't see how to accomplish this..sorry

---

### Post by TuxCrafter on 2006-07-05
Found out that using the old smbfs mount type will work like this:

```
sudo mount -t smbfs -o username=xxx,password=xxx //windows-me6000/E$ /mnt/windows-epia/
```

This wil work!!
(i cant use this on fedora core 5 no smbfs support)

I also found a tool called "smbc" witch will give you a network map that will show every computer on the local network with a shared port:-\"

This will give me the ip of a network sharename
```
nmblookup windows-me6000|tail -n 1|cut -f 1 -d ' '
```

So the tools are there so why is there no tool for gnome - xfce that support everyting

---

### Post by TuxCrafter on 2006-07-06
and here is the solution of mounting without the ipaddress:

```
#!/bin/bash

R=$(cat /etc/redhat-release)
echo $R

ipaddress=$(nmblookup windows-me6000|tail -n 1|cut -f 1 -d ' ')
echo $ipaddress

#Mounting a windows network share
su - -c "mount -t cifs -o credentials=/home/Jelle/.creds_me6000,uid=500,gid=500,file_mode=0664,dir_mode=0775 //$ipaddress/E$ /mnt/windows-epia/"

#su - -c "mount -t cifs -o credentials=/home/Jelle/.creds_me6000,uid=500,gid=500,file_mode=0664,dir_mode=0775 //145.52.123.220/E$ /mnt/windows-epia/"

cd /mnt/windows-epia/
ls -hal
```

---

### Post by ChrisG_UK on 2007-02-18
Thanks for posting this. This has helped me a lot. Any chance you could expand on this a little to make it happen automatically when the system boots up?

A lot of other posts mention configuring mounts in fstab. I tried that but it seems you can only do that if the host is in the hosts file. Obviously you can't do that when the host address is dynamic.

---

### Post by TuxCrafter on 2007-02-18
You can make a custom script for your needs (based on my script) and than let this script executed in the boot process.

/etc/rc.local
add a line in the above file before the exit command like this:
path/to/my/script.sh

or maybe
exec /path/script.sh

google for rc.local

---

