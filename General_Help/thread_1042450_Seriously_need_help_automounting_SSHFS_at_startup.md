---
title: "Seriously need help automounting SSHFS at startup"
date: 2009-01-17
forum: General Help
---

### Post by Predtech on 2009-01-17
Hi guys, 
ok i have read article after article about how to automount an SSHFS filesystem and i almost have it but i am obviously missing something so here are the details:
My /etc/fstab line looks like this:
**sshfs#xxxxx@xxx.xxx.x.x:/media /media/server fuse comment=sshfs,users,exec,uid=0,gid=0,allow_other,reconnect,transform_symlinks,BatchMode=yes 0 0**
I also have a folder named "**if-up.d**" located at **/etc/network/** with a "**mountsshfs**" file that contains:

[B]#!/bin/sh
#
# This script will try to mount all fstab entries which contain
# the list of networks in the comment option. The list of the networks
# contains the network addresses on which the fstab should be mounted
#
# for example, the following fstab entry will be processed by the script:
# 
# //srvname/folder /mnt/homedrv cifs comment='192.168.16.0,10.2.16.0',username=user,password=pswd,domain=IE,noauto 0 0
#
# The option comment contains the list of network addresses in single quotes
# seperated by commas. If the computer is on one of these networks
# the script automatically mounts the filesystem //srvname/folder to the
# mounting point /mnt/homedrv. The fstab entry should have noauto option
# specified.
#
# This script extends the script provided at [http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312)
# More information can be found at [http://www.vitvar.com/blog/?p=12](http://www.vitvar.com/blog/?p=12)
# Tomas Vitvar (tomas-at-vitvar-dot-com)
    
# Not for loopback
[ "$IFACE" != "lo" ] || exit 0

# returns true if input contains nothing but the digits 0-9, false otherwise
isa_number () {
    ! echo $1 | egrep -q '[^0-9]'
    return $?
}

# returns true if the given uid or username is that of the current user
am_i () {
        [ "$1" = "`id -u`" ] || [ "$1" = "`id -un`" ]
}

# takes a username or uid and finds it in /etc/passwd
# echoes the name and returns true on success
# echoes nothing and returns false on failure 
user_from_uid () {
    if isa_number "$1"
    then
        # look for the corresponding name in /etc/passwd
        local IFS=":"
        while read name x uid the_rest
        do 
                if [ "$1" = "$uid" ]
                        then
                                echo "$name"
                                return 0
                        fi
        done </etc/passwd
    else
        # look for the username in /etc/passwd
        if grep -q "^${1}:" /etc/passwd
        then
                echo "$1"
                return 0
        fi
    fi
        # if nothing was found, return false
        return 1
}

# Parses a string of comma-separated fstab options and finds out the 
# username/uid assigned within them. 
# echoes the found username/uid and returns true if found
# echoes "root" and returns false if none found
uid_from_fs_opts () {
        local uid=`echo $1 | egrep -o 'uid=[^,]+'`
        if [ -z "$uid" ]; then
                # no uid was specified, so default is root
                echo "root"
                return 1
        else
                # delete the "uid=" at the beginning
                uid_length=`expr length $uid - 3`
                uid=`expr substr $uid 5 $uid_length`
                echo $uid
                return 0
        fi
}

# Gets the i-th number from the ip address
get_num() {
        i=0
        for num in `echo "$2." | egrep -o "^[0-9]*\." | sed "s/\.//"`; do
		i=$(($i+1))
                if [ $i -eq $1 ]; then
                        echo $num
                fi
        done
}

# Returns true if we are on the network specified as the input parametr 
# otherwise returns false
on_network() {
        # parse the network to test
        a1=`get_num '1' $1`;
	a2=`get_num '2' $1`; 
	a3=`get_num '3' $1`; 
	a4=`get_num '4' $1`

        # get all live networks we are currently on
        for line in `ifconfig | egrep -o "inet addr:[0-9.]*.*Mask:[0-9.]*" | sed "s/inet addr://g" | sed "s/ .*Mask:/--/g"`;
        do
                # get the ip and mask of the network
                ipaddr=`echo $line | grep -o "[0-9.]*"`
                mask=`echo $line | grep -o "\-\-[0-9.]*" | sed "s/\-\-//g"`

                # parse the ip address
                i1=`get_num "1" $ipaddr`; 
		i2=`get_num "2" $ipaddr`; 
		i3=`get_num "3" $ipaddr`; 
		i4=`get_num "4" $ipaddr`
		
		# parse the mask
                m1=`get_num "1" $mask`;   
		m2=`get_num "2" $mask`;   
		m3=`get_num "3" $mask`;   
		m4=`get_num "4" $mask`

                # test if we are on this network
                if [ $(($i1&$m1)) -eq $a1 ] && 
		   [ $(($i2&$m2)) -eq $a2 ] && 
		   [ $(($i3&$m3)) -eq $a3 ] && 
		   [ $(($i4&$m4)) -eq $a4 ]; then
                        return 1
                        exit
                fi
        done

        # no matching network found
        return 0
}

# unmount all shares first
sh "/etc/network/if-down.d/umount-networks"

while read fs mp type opts dump pass extra
do
    # check validity of line
    if [ -z "$pass" -o -n "$extra" -o "`expr substr ${fs}x 1 1`" = "#" ];
    then
        # line is invalid or a comment, so skip it
        continue

    # check if the line is a line with list of networks
    elif echo $opts | grep -q "comment='.*'"; then

	# get the network list
        networks=`echo "$opts" | grep -o "comment='.*'" | grep -o "'.*'" | sed "s/'//g" | sed "s/,/ /g"`
	
        for net in $networks; do
        	if on_network $net; then
		        # get the uid of the mount
		        mp_uid=`uid_from_fs_opts $opts`

		        if am_i "$mp_uid"; then
                	        # current user owns the mount, so mount it normally
		                { sh -c "mount $mp" &&
                	          echo "$mp mounted as current user (`id -un`)" ||
                                  echo "$mp failed to mount as current user (`id -un`)";
		                } &
               		elif am_i root; then
	                        # running as root, so sudo mount as user
               		        if isa_number "$mp_uid"; then
                               		# sudo wants a "#" sign icon front of a numeric uid
	                                mp_uid="#$mp_uid"
               		        fi
	                        { sudo -u "$mp_uid" sh -c "mount $mp" &&
               		                echo "$mp mounted as $mp_uid" ||
                               		echo "$mp failed to mount as $mp_uid";
	                        } &
               		else
	                        # otherwise, don't try to mount another user's mount point
               		        echo "Not attempting to mount $mp as other user $mp_uid"
	                fi
			break
		fi
	done
    fi
    # if not an sshfs line, do nothing
done </etc/fstab

wait[/B]



Also i have a folder named "**if-down.d**" located at **/etc/network/** with a "**umountsshfs**" file that contains:

[B]#!/bin/sh

# read each line from the /etc/fstab
while read line; do
        # check if the line has the network list in the comment
        if [ `echo $line | grep -c "comment='.*'"` -gt 0 ]; then
                # get the filesystem 
                fs=`echo $line | awk '{ print $1 }'`

		# unmount the filesystem if it is mounted
		mounted=`grep "$fs" /etc/mtab | awk '{ print $2 }'`
		[ -n "$mounted" ] && { for mount in $mounted; do umount -l $mount; done; }
        fi
done < "/etc/fstab"[/B]


I also changed the rights for both scripts by using:
**sudo chmod 601 /etc/network/if-up.d/mount-networks**
**sudo chmod 601 /etc/network/if-down.d/umount-networks**

I have Fuse installed along with all other necessary programs, openssh, sshfs...
I am added to the group of Fuse also on both server and client.
I generated a key pair by using:
**ssh-keygen -t rsa**
Then copied it onto my server by:
[B]sudo touch /usr/bin/ssh-install-key ;
sudo chmod a+w /usr/bin/ssh-install-key
echo "cat ~/.ssh/id_rsa.pub | ssh \${1} \"cat - >> ~/.ssh/authorized_keys\"" \
     > /usr/bin/ssh-install-key
sudo chmod a-w+x /usr/bin/ssh-install-key[/B]

I can mount the ssh share anytime WITHOUT using "**sudo**" by simply using:
**mount /media/server** and it'll mount immediately.
If i shut down networtking then the share unmounts like it's supposed to according to the script but i just CAN'T seem to get the share automounted on system boot.


Can anyone PLEEEEEEEEEEEASE help me get this to automatically mount every time my pc boots/reboots/restarts the network.

If i didn't already shave my head, i'd be pulling my hair out by now, lol.

---

### Post by Predtech on 2009-01-17
bump!

---

