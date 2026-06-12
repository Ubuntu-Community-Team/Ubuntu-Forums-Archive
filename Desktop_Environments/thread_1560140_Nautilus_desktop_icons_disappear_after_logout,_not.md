---
title: "Nautilus desktop icons disappear after logout, not restart"
date: 2010-08-24
forum: Desktop Environments
---

### Post by worm blain on 2010-08-24
Hello all, bit of a puzzler here.

I have a Lucid installation which I've imaged and pushed to several computers on the network at my office.  The system authenticates network users with Active Directory using Kerberos, and mounts NFS shares from a Lucid server downstairs using pam_mount.  It all works quite smoothly most of the time, but I get desktop icons in Gnome only on the first login.  If I log out, then log in as a different user (local or network, it doesn't matter), the desktop icons are all gone.  Everything else looks normal, and I can open a Nautilus window and view any location on the hard drive just as expected.  If I use the run dialog or a terminal window to execute [INDENT]killall nautilus
[/INDENT]the icons are restored.  This works whether any instance of a file browser window is open or not.

I have noticed similar, but far less consistent, behavior with gnome-panel.  Every once in a while the panels will fail to appear when I log in, but I can restore them with [INDENT]killall gnome-panel
[/INDENT]When I run either command, everything works fine until the next login.

If I reboot the machine, I get everything back again for one login.  Then the desktop icons will disappear, and I have to kill Nautilus and let it restart in order to get them back.

I expect I'm missing something important here, but I don't know where to look next.  I'll appreciate any advice.

---

### Post by worm blain on 2010-08-26
Hello?  Anybody out there?

---

### Post by pixelplumber on 2010-09-14
Hi, registered to post a reply as I have come across the same issue today.  

I've just set up a 10.04 LTSP server, that is in my case authenticating  with winbind and pam_mount'ing home directories/desktop folders via  CIFS from a samba server (not using NFS as winbind can handle SIDs & ACLs better).

The same thing occurs, the first user can successfully view all assigned volumes , however any subsequent users will be missing common volumes on the desktop.  They are still accessible inside the mounted directory.

A bit more detail, I mount:

[LIST]
[*]personal documents folder (unique server traget for each user - this is always visible as a volume on the desktop)
[*]shared public folder (because everyone gets this mount, it only shows on the first login)
[*]shared folders for groups (ie: accounting/office/warehouse shered folders.  These display for the first logged in user)
[/LIST]
The work around that I can think of at the moment is to pam_mount the folders onto the users desktop and use gconf-editor to flip the apps > nautilus > desktop > volumes_visible knob to disable the volumes showing up as well as the mounted folders.  The drawback with that is it will hide all volumes - including USB sticks that are plugged in I think.  

I'm also wondering if I can faff about with hal policies (usr/share/hal/policies/) to try and fix it.

My mtab looks like this post pam_mount:

```
--SNIPPED to shorten---
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
pam_mount folders below
//samba-server/user1 /home/user1/Documents cifs rw,mand,nosuid,nodev 0 0
//samba-server/redirect/user1/Desktop /home/user1/shares/windows-desktop cifs rw,mand,nosuid,nodev 0 0
_**//samba-server/public**_ /home/user1/shares/public cifs rw,mand,nosuid,nodev 0 0
//samba-server/sales /home/user1/shares/sales cifs rw,mand,nosuid,nodev 0 0
//samba-server/user-2 /home/user-2/Documents cifs rw,mand,nosuid,nodev 0 0
_**//samba-server/warehouse**_ /home/user-2/shares/warehouse cifs rw,mand,nosuid,nodev 0 0
_**//samba-server/public**_ /home/user-2/shares/public cifs rw,mand,nosuid,nodev 0 0
gvfs-fuse-daemon /home/user-2/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=user-2 0 0
//samba-server/user3/home/user3/Documents cifs rw,mand,nosuid,nodev 0 0
//samba-server/redirect/counter/Desktop /home/counter/shares/windows-desktop cifs rw,mand,nosuid,nodev 0 0
_**//samba-server/warehouse**_ /home/counter/shares/warehouse cifs rw,mand,nosuid,nodev 0 0
**_//samba-server/public_ **/home/counter/shares/public cifs rw,mand,nosuid,nodev 0 0
gvfs-fuse-daemon /home/user3/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=counter 0 0
gvfs-fuse-daemon /home/adminuser/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=adminuser0 0
```I'm wondering if its caused by multiple references to the same server targets (bold/underlined above).  Perhaps gnome-mount or gnome-vfs-daemon or gnome-volume-manager only parse the first occurrence of a particular entry?  Don't know enough about how gnome auto mounts volumes on the desktop yet, but I'll have a poke about.

It seems to be a cosmetic issue for me, the folders are still mounted and accessible for all logged in users.

Did you work out a solution?

---

### Post by JoTaB on 2011-03-07
I have this exact same problem, mounted volumes show up for the first user, but not for the second that is logged in. Does anyone have a solution to this? Or any idea what part of nautilus that needs to get fixed?

Best regards!

---

### Post by Hashiru on 2011-03-30
Ehhm, it might be a really stupid idea for a workaround, but maybe if you make a group and chown or chmod the desktop folder/icons it might work.

I don't know a lot about networking, but this seemed to be a problem for my webserver once.

---

### Post by oasit on 2012-06-11
It seems that you have to mount general shares to /media and personal shares to ~.
If private shares have the same path (e.g. /path/office) only the first logged in user will see the volume icon. If the path differs (e.g. /path/%(DOMAIN_USER) each user will see his volume icon.

A share is shown for all users if its mounted to /media.
You have to adjust the gid to the group that should have the right to access this share. Otherwise the group is set to the group of the first logged in user. 
The only drawback of this solution is if the a user logs out. In this case pam_mount removes the share and all other users wont see the shared volume in Nautilus. To have the share mounted again the user has to choose 'Switch User' and log in (this will trigger pam_mount again and mount the share).

Here is an example for a global share in pam_mount.conf.xml:
```
<volume options="domain=mydomain,gid=group_of_this_share,dir_mask=0770,file_mask=0770"  fstype="cifs"
server="my-files.example.com" 
path="my_globalshare/General"
mountpoint="/media/General"  
 />
```

---

