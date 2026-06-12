---
title: "user reports as member of same groups twice"
date: 2009-05-26
forum: General Help
---

### Post by mintonman on 2009-05-26
Hi all,

I have been trying to set up shared access to a directory on a fileserver for a number of users, and have made a range of changes to groups and users as I have gone along.

My main user now reports that it is a member of the same groups twice, i.e.:

[INDENT]main@desktop:~$ groups main
main adm dialout cdrom tape audio video plugdev users scanner fuse lpadmin netdev admin **sbgroupfiles sbgroupvision** sambashare **sbgroupfiles sbgroupvision**

main@desktop:~$ id main
uid=1000(main) gid=1000(main) groups=1000(main),4(adm),20(dialout),24(cdrom),26(tape),29(audio),44(video),46(plugdev),100(users),104(scanner),107(fuse),110(lpadmin),116(netdev),119(admin),**1001(sbgroupfiles),1003(sbgroupvision)**,126(sambashare),**1001(sbgroupfiles),1003(sbgroupvision)**
[/INDENT]

This is after running grpck and restarting. /etc/groups only has one entry for each of the two repeated groups. No other users on the same machine are "in the same group twice"

Any ideas why this might be happening, whether it will cause problems, and how I might sort it out? 

many thanks!

Mark

---

### Post by mintonman on 2009-05-26
More on the above:

Actually, there is one noticeable problem that this user is already reporting, unlike all others - a remote drive mounted in fstab with nfs doesn't automount for this user. 

when I mount from the command line I get:

mount.nfs: access denied by server while mounting

- again, this is not reproducible with other users on the same machine - they mount the remote drive fine at login. 

could this be connected with the repeated group membership thing in any way?

thanks again for any help,

Mark

---

