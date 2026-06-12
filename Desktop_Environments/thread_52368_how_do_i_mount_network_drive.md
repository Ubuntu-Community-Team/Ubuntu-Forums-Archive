---
title: "how do i mount network drive?"
date: 2005-07-27
forum: Desktop Environments
---

### Post by arjay1 on 2005-07-27
Sorry to ask this again.  I have googled and search these forums till my head spun but still not quite sure how to do it.

This is my system:  I have two kubuntu boxes linked through a samba-based network.  I am using Opera as my browser.  

This is my problem: each time I download mail or add a bookmark on one machine, I want it to be updated on the other machine.

I have been advised in the Opera forum to have both Opera ini files point to the same mail and bookmark locations on one machine.  This means having one machine point to folders on a networked drive.  Unfortunately Opera won't recognise a samba share or ip address.  I am told I have to "mount the network drive etc etc."

Can someone explain how I would do that?  I presume it would have to be mounted during boot and that means a change to the static part of fstab?  if so, I can't figure out what the static line should look like.

This is my fstab at the moment:

[I]# /etc/fstab: static file system information.


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1

/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppya  auto    rw,user,noauto  0       0
[/I]

Any help greatly appreciated

TIA

---

### Post by crispingatiesa on 2005-07-27
If both boxes are running kubuntu U don't need Samba to make them talk.

I'm assuming that U have defined the same workgroup or domain in both machines.

Do U have shared directories defined?
Do U have remote loging activated?
Can U see the shared directories of each machine?

Please, could U be more specific about what can U see in each box etc?

---

### Post by wrtrdood on 2005-07-27
Use NFS for this.  You will need the nfs-server (I think Ubuntu calls it nfs-kernel-server) and portmap running (do both systems).  Then look at the syntax for **exportfs** for adding the directories you want to see mounted on the other machine(s).  The file used to define this is /etc/exports which also controls the permissions for the exported filesystems.  When you get that correct, export the filesystems with sudo exportfs -a (you may need to restart nfs first - /etc/init.d/nfs-kernel-server restart).

  For simplicity, you should designate one system as the host and the other as the client.  It will make it a lot easier to support.  

On the system you need to mount this directory (the client), first create a mount point such as /home/opera or something like that.  You can then mount the other system's (the host) directory using: sudo mount -t nfs system1:/<exported directory> /home/opera

The syntax for adding it to the /etc/fstab is:

   <server>:</path/of/dir> </local/mnt/point> nfs <options> 0 0

Options to consider would be something like: 

    soft,intr,rsize=8192,wsize=8192,nosuid

You could set up a single home directory on the host, say /allhomes, and export it to the other system then place the common files here for both systems to use.  Then, only changes need to be made on the host system.  Alternatively, you can export whatever directories you need and mount them on the other system.

Keep trying.  We'll get this figured out yet.   :grin: 

Rich

---

### Post by varunus on 2005-07-27
You can also use shfs for this; it will let you mount a directory on one computer on the other using ssh.  There's a howto in the Tips and Tricks forum on how to install shfs; here's some paraphrasing:

Open a terminal, type:
```

sudo apt-get install shfs-source shfs-utils
sudo module-assistant build shfs
sudo module-assistant install shfs
sudo chmod a+s /usr/bin/shfs*

```

shfs is now installed.  To mount a folder on the other computer, you can use the command:
```

shfsmount username@othercomp:/path/to/wanted/folder /directory_to_mount_in

```

If you want to do this on bootup, add the following line to the end of your /etc/fstab file:
```

username:password@othercomp:/path/to/wanted/folder /directory_to_mount_in   shfs  defaults 0 0

```

Careful with storing your password in the fstab file though.  You may want to use passwordless authentication for ssh; look that up on Google (you'll have to generate a key for the computer).

---

### Post by arjay1 on 2005-07-27
WOW!!  What a lot of good advice.  My only problem now is deciding which system to use.  I did hear that NFS was pretty good, but could be a bit slow?  Never heard of shfs - is that a sort of front-end for ssh?

I'll give one of these a try tomorrow and let you know the result.

For crispingatiesa:

Yes I have the same workgroup name for each system.  I don't know anything about remote login(g).  I can see the shared directorites on both machines just fine - EXCEPT - the opera directory is actually ".opera" in my home/user/ directory and nothing seems to like a directory that starts with "."  I can get as far as opening the directory, but, for example, opera.ini (the file I need to change on the other machine)  won't open in sudo gedit or whatever. I have made it to share and goodness knows what else but I can't open it.  It keeps asking for the share name and password but doesn't accept anything I type in.

I'll try some of these other solutions and see what happens.  I never thought much of Win XP but at least you can make a whole drive, if necessary, able to share with a couple of clicks ...

Linux is a nightmare in this regard for a newbie.  But I ain't giving up!!

---

### Post by crispingatiesa on 2005-07-27
If you have defined a workgroup, then go to: Places > Network Servers, then U'll see the two computers , open the one U want to connect browse down to the file U want to share and right cklick , select connect to this server. It will ask you a name for the share and will show you a folder in your desktop with the choosen name. 

Then try to point opera to this file in your desktop or wherever you saved the link.

---

### Post by arjay1 on 2005-07-28
crispingatiesa

Sory - don't follow you.  Are you using gnome or KDE?  All I can find is KDE Menu - Remote Places - Samba Shares, or Storage Media. 

If I open Samba shares it gives me workgroup and then I can drill down to a couple of shared folders that have been set up in smb.conf on the other machine.  However it won't let me open the .opera directory that is shown as shared.  It just asks for the user/password (which I enter but it refuses them).  If I open Stroage Media I just get the drives on this machine.

If you have any idea how I can find network servers I should be on my way ...

---

### Post by arjay1 on 2005-07-28
varunus

Tried to install shfs as you suggested - even had a look at the original instructions in your link.  However module-assistant won't build.  I downloaded module-assistant and utils but when i ran the build instruction it reported: 


*Bad luck, the kernel headers for this kernel version could not be found  and you did not specify other kernel headers to use. *

There are a couple of versions of this error around - one in this forum but he didn't get any replies re a cure for the problem.  So I am kinda stuck

I tried apt-get for a compiled version but it reports none available?

---

### Post by arjay1 on 2005-07-28
varunus - solved this one.  The lack of linux headers for the 2.6.10 kernel was solved by inserting the following line in your instructions:

module-assistant prepare.

Tip came courtesy of Terence's Pages at [http://www.ocf.berkeley.edu/~tmtong/howto/debiantips.php](http://www.ocf.berkeley.edu/~tmtong/howto/debiantips.php) - an interesting bunch of tips about all sorts of things.

Anyway, for the benefit of other readers the sequence should look like this:

sudo apt-get install shfs-source shfs-utils
sudo module-assistant prepare
sudo module-assistant build shfs
sudo module-assistant install shfs
sudo chmod a+s /usr/bin/shfs*

I haven't tried the rest of your guidance but thought I had better post this update on my earlier post.

I make progress  ... I think!

---

### Post by arjay1 on 2005-07-28
varunus

Got stuck again.  shfs is installed ok but I am a bit confused as to what should be on which computer.  Can I make sure that I have this right?

I have Opera installed on both computers.  The copy on A (let's say this is the host) has to point to a specific flie , opera.ini in the .opera directory on computer B (the client?)

I have install shfs on computer A, thinking that I need to have the .opera folder on B accessible on A by mounting it on A.   

On Computer A, I enter the following in terminal as root:

*shfsmount [email]rjoss@rjoss:/home/rjoss/.oper[/email]a /home/rjoss/operashare*.  To me this means find the .opera folder on Computer B, located in /home/rjoss, and mount it here on A at /home/rjoss/operashare.

When I do this I get a report* no such name or service*.  However, Computer B _is_ rjoss@rjoss.  

If I try the ip address instead *shfsmount [email]rjoss@192.168.1.3/home/rjoss/.oper[/email]a /home/rjoss/operashare* I get *connection denied: port 22*.

The same happens if I try the above command with my password inserted:

[I]shfsmount rjoss:password@rjoss:/home/rjoss/.opera /home/rjoss/operashare.
[/I]
Does this mean that iptables or something is blocking port 22?  I have enabled the various networks and ip addresses in samba but not in iptables (if that is what you are supposed to do)?

Can you tell me if I am on the right track?

TIA

Richard

---

### Post by arjay1 on 2005-07-30
varunus (or anybody whose interested)

 I have managed to get the network drive's folder that I want from another machine, mounted in my home directory on this machine. But when I mounted it I got:

[I]The authenticity of host '192.168.1.3 (192.168.1.3)' can't be established.
RSA key fingerprint is 27:1a:46:ab:cd:b8:23:2d:db:46:24:be:35:15:a2:aa.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '192.168.1.3' (RSA) to the list of known hosts.[/I]

The ip address 192.168.1.3 is the other machine. Can you help me with info about where shfs would have written this info (i.e. where the list of known hosts is kept)?

EDIT - GOT THE INFO THANKS ANYWAY

---

### Post by henok on 2008-04-26
I find it easier to work with sshfs than ssfs.

# install sshfs
sudo apt-get install sshfs

# create a directory
sudo mkdir /media/netfolder

# make yourself the owner of the directory
sudo chown jsmith /media/netfolder

# add yourself to the "fuse" group
sudo adduser jsmith fuse

# load fuse module
sudo modprobe fuse

# restart machine or logoff and log back in
sudo reboot

# mount
sshfs machine2.research.ibm.com: /media/netfolder

# unmount
fusermount -u /media/netfolder

---

