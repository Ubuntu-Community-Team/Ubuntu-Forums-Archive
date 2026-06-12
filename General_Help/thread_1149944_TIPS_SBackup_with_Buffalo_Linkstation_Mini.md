---
title: "TIPS: SBackup with Buffalo Linkstation Mini"
date: 2009-05-05
forum: General Help
---

### Post by Diskdoc on 2009-05-05
I bought a Buffalo Linkstation Mini to store backups on. The drive has an "auto" feature that spins down the drive automatically after inactivity. Windows software included on CD would spin up the drive when it was used. Of course, there were no GUI Linux-solution readily available but with good support from the Buffalo support forums I've finally arrived at a BASH-script for doing backups with SBackup. Can probably be improved, but it works.

A Gnome-Applet for activating/deactivating the drive would be nice, but I don't know how to make those.

```
#!/bin/bash
#
# Buffalo Linkstation Mini+Sbackup Service file used by anacron
# Version 0.2 by Olof Englund, 04.2009 

interface=ra0
mountpoint=/media/Backup
ipshouldbe=192.168.1.2
ethernet=aa:bb:cc:dd:ee:ff
subnet=192.168.1.255
ip=`ifconfig $interface | gawk '/inet addr/{sub(".*:", "", $2);print $2}'`

echo "IP address is $ip"

if [ "$ip" != "$ipshouldbe" ]; then 
	echo "IP address for interface $interface is not $ipshouldbe. Exiting."
	exit
fi

i=0
if [ -x /usr/sbin/sbackupd ]; then
	while [ $i -lt 5 ]; do
		wakeonlan -i $subnet $ethernet
        	sleep 20
		let "i += 1" 
	done

	check=`cat /etc/mtab | grep -c $mountpoint`

	if [ "$check" = "0" ]; then 
		echo "check = $check. $mountpoint not mounted. Mounting."
		mount $mountpoint
	fi

	/usr/sbin/sbackupd &
	
	echo Sbackups PID is $!
	sbackup=$!

	while ps -o pid $sbackup | grep -q $sbackup; do
		wakeonlan -i $subnet $ethernet
       		sleep 20
	done

	echo "SBackup complete. Unmounting $mountpoint"
	umount $mountpoint
```

---

### Post by jpeddicord on 2009-05-11
Moved from Tutorials & Tips; tutorials need to be a set of instructions and not simply a script to run. Please see [http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396) for more information. Thanks! :)

---

