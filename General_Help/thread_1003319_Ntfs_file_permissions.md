---
title: "Ntfs file permissions"
date: 2008-12-06
forum: General Help
---

### Post by smartygoldenfish on 2008-12-06
hi, i have 2 user accounts A [admin], B[normal user].
Now i run use A.
i have  a ntfs partition and want a folder and contents to be denied to B.
so i used chmod

chmod o-rwx myfolder

[i think chmod o-x myfolder should also do since it generates "Access Denied"]

but the directory permmissions before chmod and after chmod [seen by ls -l] havent changed, and B can easily see the files of the folder!

How can i resolve this.
Also cant i just tell ubuntu the name of the user B and apply chmod instead of using "o" that stands for other users.
Do i need root permissions to do this. i ntfs partitions are mounted by me myself, and i think i am owner of the folder as well. Note: I dont get any error messages also.

---

### Post by psusi on 2008-12-06
NTFS does not store unix style file permissions, so when you mount an NTFS volume, the permissions have to be faked.  This is typically done by allowing access to the desktop user who mounted the volume and nobody else.  How are you mounting your volume?  If you set it up in /etc/fstab, then you must have added the proper uid/gid/umask options to allow yourself access.  Unless you set the umask to allow everyone access, then it should already be set up to only allow you access.

---

### Post by smartygoldenfish on 2008-12-06
> **psusi said:**
> NTFS does not store unix style file permissions, so when you mount an NTFS volume, the permissions have to be faked.  This is typically done by allowing access to the desktop user who mounted the volume and nobody else.  How are you mounting your volume?  If you set it up in /etc/fstab, then you must have added the proper uid/gid/umask options to allow yourself access.  Unless you set the umask to allow everyone access, then it should already be set up to only allow you access.

when i start pc, the partitions are auto mounted. I have done by changing fstab. I have used ubuntu tweak to allow everyone access them easily.
I think you mean deny access to B THE WHOLE PARTITION, well thats not my aim. B has own files in that partition  [over 20GB, no option to copy to ext2]. So, what can i do for folders in that partition. 
it just struck me, if i could use something called "Virtual files" in linux. What i think is:
1. deny access to that partition to B
2. Make a mount point [/mnt/folder] for the folder in that partition, which B needs to access.

so it will prevent B from accessing my files, and allow to access own files.
but i dont know how to do this. i am not sure it will work..

---

### Post by psusi on 2008-12-06
Ahh, nope... can't do that.  Permissions on an NTFS mount are for the whole volume.

---

