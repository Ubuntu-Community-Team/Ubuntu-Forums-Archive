---
title: "how to relocate /usr to another partition?"
date: 2006-08-12
forum: Desktop Environments
---

### Post by kadil on 2006-08-12
Hi,

I installed dapper in qemu, with only a 2G partition.Very quickly ran out of space. I have added another 4G partition as /dev/hdb1 and I want to move /usr to the new partition. I thought I would use mc to copy it for me, but there are so many options around copying symlinks and attributes, how should I copy  or move it over. Obviously then i would ammend "/etc/fstab"

Anyone have some guidance,I don't want to trash my system.

Thanks,
Kim

---

### Post by NewWithoutClue on 2006-08-12
Do you have a live CD? If so, why don't you boot that.. mount the 2 gig and 'mv <mount point of 2gig>/usr <mount point of 2gig>/usr_temp' ... edit the mount points in fstab to mount your new partition to /usr and 'mv <mount point of 2gig>/usr_temp/* <mount point of 2gig>/usr/' that's how i would go about it.. but then again i've never done this.

Regards,
Paul

---

### Post by kadil on 2006-08-14
Not brave enough to do a "mv" sorry, I tried a "cp -r -p", renamed mu usr to usr_temp and set up fstab and it crashed bigtime.


Reversible 

Oh Well....

---

### Post by huygens on 2006-08-14
If you do not trust 'cp' and 'mv', then try 'tar' :)

As suggested before, boot on your Live CD. Take care that the partition where /usr is actually mounted (probably in /media/hda1) and that the new 4GB partition is also mounted (lets assume in /media/hda5). Then, perform the following (I assume that it is /media/hda1, but update it to your own configuration). In addition, I assume that you want to use the 4GB new partition only for /usr, not for something else.
Finaly, be aware that you must be "root" to perform these steps, that's why I use sudo.
```
cd /media/hda**5**
sudo tar cpf - -C /media/hda**1**/usr * | sudo tar xpf -
sudo mv /media/hda**1**/usr /media/hda**1**/usr-old
``` 
The 'tar' command is often used to make backup and restore. When used as root, it shoud preserve user, groups, rights, links, etc. (but it costs nothing to force it by using the 'p' option). So with this command you should be able to properly copy your /usr directory to its new partition.
The last command above is just renaming your old /usr partition. You can remove it (sudo rm -Rf /usr-old) once you've check that your system is working (see later).
You could then mount the partition as /usr. But, before you reboot your system and try it, you need to edit and update the file /media/hda**1**/etc/fstab. It is advised to make a backup of it before editing it:
```
sudo cp /media/hda**1**/etc/fstab /media/hda**1**/etc/fstab.usr
``` Then, add the following line to the fstab file (again update it accordingly to your configuration, here it is assumed that the partition is in ext3 format):
```
/dev/hda**5**    /usr     **ext3** defaults    1 2
``` 
Now, you should be done, reboot your system and see if it is booting correctly. Once logged in, you can be sure that everything went fine. If you're still supicious, launch Firefox ;) it is in /usr, so if it is working then you're done :)

In case, it fails (who knows, I might have forgotten one step), just boot back to your Ubuntu Live CD and once done, restore the fstab file and rename the /usr-old directory to its original name:
```
sudo cp /media/hda**1**/etc/fstab.usr /media/hda**1**/etc/fstab
sudo mv /media/hda**1**/usr-old /media/hda**1**/usr
``` 
Huygens

---

### Post by OMA2k on 2008-07-02
I know this thread is almost two years old, but I'd like to thank huygens for this easy to follow step by step tutorial (found it in a Google search). It's the easiest I've found for this subject (move /usr to a different partition), and it really works!

There's only one caveat. After renaming the "usr" folder to "usr-old" you **must** create a new empty "usr" folder by typing:

```
sudo mkdir /media/hda**1**/usr
```
(as always, substituting hda**1** with whatever the actual device is)

Since you didn't mention it, I didn't do that, and then Ubuntu stalled during boot just saying "fail!", and took me a couple of hours to realize an empty folder was needed to mount the filesystem with fstab. After creating that empty "usr" folder from the LiveCD, Ubuntu finally booted perfectly with "usr" running from the new location. I know it's basic stuff, but I'm relatively new to Ubuntu, so it took a while to figure that out.

Anyway, thanks a lot for your tutorial!

---

### Post by huygens on 2008-07-03
Thank you OMA2k for mentioning the caveat and proposing a solution. I am sorry that it did not work for you the first time.
As I am now still travelling around the World, I am not using Ubuntu, or any computer (a part in some internet café from time to time). I will most probably follow your remark and update my post when I will be back home.
Thanks a lot for your comment anyway.

Huygens

---

