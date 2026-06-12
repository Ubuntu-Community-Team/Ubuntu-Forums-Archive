---
title: "autofs cifs indirectly not working for me ( nfs works fine )"
date: 2011-05-01
forum: Desktop Environments
---

### Post by ddd-222 on 2011-05-01
on ubuntu 10.10 i am setting up autofs.
I was able to properly configure direct 
and indirect NFS file systems When I try
CIFS  I can get it to work directly. 
When I tried to get it to work indirectly
 I got some errors.

I manually executed the auto.smb and it
 was outputing extra lines (without line
 continuation) and the smbclient command 
was failing ( bad options ) so I manually
 edited the script to fix the smbclient 
options and to output exactly the
same format as the working, direct 
multi-line CIFS mapping file:

mount_point1 -options ://server/share1
mount_point2 -options ://server/share2

the original form didn't seem to work
in a direct mapping, so i didn't continue
 down that route:
-options \
mount_point ://sever/share \
mount_point2 ://sever/share2

But the automount still doesn't work. I 
turned up the logging error to debug in 
/etc/default/autofs. syslog doesn't
 actually show the options and the 
attempted mount command. It does show
these things for the nfs indirect 
automount. It does show that it is trying 
to mount something onto the correct 
directory:

<edited syslog excerpt>
: attempting to mount entry /mnt/samba/server.domain.com
: dev_ioctl_send_fail: token = 438
: handle_packet: type = 3
: handle_packet_missing_indirect: token 439, name server.domain.com, request pid 16349
: failed to mount /mnt/samba/server.domain.com


Any suggestions on what the problem 
might be and how to proceed?

thanks

---

### Post by ddd-222 on 2011-05-06
i tried this on linuxmint and it works fine. I think there is a problem with autofs on ubuntu with cifs. On the other hand, i noticed ( on mint ) that cifs automounts  will mount every shared folder when ever you touch any shared folder. This is definitely not what i want/need. the server has about 20 shared folder and i never need more than one or two. I decided to just use direct automounting. that works fine for me.

---

