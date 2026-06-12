---
title: "usbdisk write error"
date: 2006-12-23
forum: Desktop Environments
---

### Post by xenonbachaim on 2006-12-23
hi, im new to linux. installed ubuntu on my laptop. everything seemed to be working fine until i did the update. after that im unable to write to any external usb drive. ive tried usb flash drive, memory card reader, external usb HD.. all of them im able to read from but not write to. all are either ntfs or fat32 file systems.

ive tried different fixes such as ejecting the drive but not unplugging and then manually mounting it again but nothing has worked. ive searched and searched and the links below suggest a solution that says to remove the evms package. 

[http://ubuntuforums.org/showthread.php?t=265269](http://ubuntuforums.org/showthread.php?t=265269)

[http://www.ubuntuforums.org/showthread.php?t=267893&highlight=fstab+mount](http://www.ubuntuforums.org/showthread.php?t=267893&highlight=fstab+mount)

[http://www.linuxquestions.org/questions/showthread.php?t=251293](http://www.linuxquestions.org/questions/showthread.php?t=251293)

supposedly the evms package was installed after the update. i tried using the synaptic package manager to remove it but according to synabtic its not even installed. 

now im stuck...

any help is very much obliged... :)


btw this is the error i get when i try to copy a file to the drive

Error while copying to "/media/usbdisk".

  ive tried changing permissions..

    Couldn't change the permissions of "usbdisk" because it is on a read-only disk

---

### Post by kidders on 2006-12-23
Hi there,

You shouldn't really be writing to NFTS filesystems with Linux. Afaik it's not a smart idea. As for the FAT ones, whether you can write depends on a few things:

[LIST]
[*]Whether the output of **mount** indicates the filesystem is mounted read-only.
[*]Whether the UID & GID maps and umask are permissive enough to give you write access. FAT filesystems don't support permissions, so these have to be selected manually, usually in /etc/fstab.
[*]If there is something wrong with a filesystem, it will often be mounted read-only, so you can take a look without causing more damage.
[/LIST]

---

### Post by xenonbachaim on 2006-12-24
thanks for the reply...
the thing is that it used to work fine before the update. both read and write. i know its something simple and i dont want to have to re install ubuntu and skip the update. ](*,)  


going back to windows is not an option. im going to stick to this and see how much my brain can handle. 

so if someone has some very long command that i can just copy and paste to terminal and fix the problem it would be nice... :???:

---

### Post by xenonbachaim on 2006-12-24
update....


found what i was looking for... 

[http://ubuntuforums.org/showthread.php?t=217009&highlight=usbdisk+ntfs](http://ubuntuforums.org/showthread.php?t=217009&highlight=usbdisk+ntfs)

---

