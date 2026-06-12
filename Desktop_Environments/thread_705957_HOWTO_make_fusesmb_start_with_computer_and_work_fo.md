---
title: "HOWTO: make fusesmb start with computer and work for all users"
date: 2008-02-23
forum: Desktop Environments
---

### Post by syadnom on 2008-02-23
Goal:
Make fusesmb start with the computer with an init script and give all users access to the smb network via fusesmb

Method employed:
Create a fusesmb user with fusesmb.conf file and run scripts for user in init scripts

i wont explain how to:
create a user
create fusesmb.conf

first step, create the 'fusesmb' user and create file /home/fusesmb/.smb/fusesmb.conf
fill in appropriate details for your network.
example:> 
[global]
workgroups = WORKGROUP, OTHERWORKGROUP

uncomment "user_allow_other" from /etc/fuse.conf

build a basic init script:
> sudo gedit /etc/init.d/fusesmb

paste this:
> #!/bin/sh
# Start/Stop fusesmb /media/Network

case "$1" in
'start')
	su fusesmb -c "fusesmb /media/Network -o allow_other" >/dev/null 2>&1 </dev/null
        RETVAL=$?
        ;;
'stop')
	su fusesmb -c "fusermount -u /media/Network"
        RETVAL=$?
        ;;
'restart')
	su fusesmb -c "fusermount -u /media/Network" >/dev/null 2>&1 </dev/null
	su fusesmb -c "fusesmb /media/Network -o allow_other"
        ;;
*)
        echo "Usage: $0 { start | stop | restart }"
        RETVAL=1
        ;;
esac
exit $RETVAL


save that, then make it executable

> sudo chmod 755 /etc/init.d/fusesmb

make the "Network" folder
> 
sudo mkdir /media/Network
chmod a+wrx /media/Network

now add the script to /etc/rc2.d
> 
ln -s /etc/init.d/fusesmb /etc/rc2.d/S20fusesmb

i suggest installing sysv-rc-conf
> apt-get install sysv-rc-conf
now run
> sysv-rc-conf
you can edit various programs startup this way, I just went down to fusesmb and selected runlevels 2,3,4,5 because other network programs are that way, just selecting 2 is fine but inconsistant with other startups.

now you should have a /media/Network mount that shows up on the desktop of any user and is useable by any user and it starts up with the system!

you can also do
> sudo /etc/init.d/fusesmb restart
if you make changes to the /home/fusesmb/.smb/fusesmb.conf

i also linked that to /etc for easy access
> sudo ln -s /home/fusesmb/.smb/fusesmb.conf /etc/fusesmb.conf

goodluck and good smb browsing!

notes: this is usefull on small networks or home networks where 1 username per server will handle all your browsing needs, if you need users to login to the fileserver with their own authorization, you can use this for regular stuff and use another fusesmb in a user's home folder for those mounts.  this is a pretty basic init script and is designed for very basic smb browsing. thanks

---

