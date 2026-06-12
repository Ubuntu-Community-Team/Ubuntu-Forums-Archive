---
title: "Mount an ISO via Samba - possible?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by morphos on 2006-07-08
I searched the forums and web before I posted, did my homework, but couldn't find an answer to this. I :blushes: have a fileserver running Windows<!> on my home network with multiple DVD ISOs on it.  I've easily done this on Windows of course with file-sharing and Daemon Tools.  The goal is not transfering the whole DVD image locally every time I want to fire up an episode of Futurama for example.  

If you have any info on the commands necessary to pull this off, or have an idea for doing something different that solves the problem, please let me know.

---

### Post by exclipy on 2006-07-09
How are you mounting them when they're on a local disk?

---

### Post by morphos on 2006-07-09
locally, I'm using the tip from ubuntuguide.org...

 How to mount/unmount Image (ISO) files without burning

    * Read #General Notes
    * To mount Image (ISO) file 

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

    * To unmount Image (ISO) file 

sudo umount /media/iso/

######

But I'm still looking for a way to mount an iso through samba/windows share.

---

### Post by Thund3rstruck on 2006-07-09
I also have a W2K3 server and I mount over the network all the time.

```

sudo mount /media/server/files/Microsoft/Office2003/Office2003.iso /media/iso/ -t iso9660 -o loop

```

or you can use this script.. if you have trouble remembering the command or mount iso a lot

It easiest if you make a link (ln -s) to /usr/bin or save this script somewhere in your path (such as ~/bin)

```

#!/bin/bash
#Script: mountiso script
#Author: thund3rstruck
#Purpose: mounts an iso file
#
#usage: ./mountiso.sh [Path]
            
path=""

mountIso(){
sudo mount "$path" /media/iso/ -t iso9660 -o loop
echo "Mounted "$path" to /media/iso"
}

if [ -n "$1" ]; then
     path="$1"
     mountIso
else
	clear
	echo "You must pass a filename to the script!"
	echo "[Usage] ./mountiso.sh /etc/myIso.iso"
	read file
	    if [ -n "$file" ]; then
		path="$1"
		mountIso
            fi
fi

```

---

