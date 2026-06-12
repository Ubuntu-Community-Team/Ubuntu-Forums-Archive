---
title: "i need to transfer ntsf files to my other pc"
date: 2006-08-31
forum: Desktop Environments
---

### Post by theprince on 2006-08-31
i was running my pc on windows until i encountered some software conflict that kept restarting my comp everytime i tried to load it, even if i tried safe mode.
 
my only option is to reinstall windows, but i dont want to lose my files (documents, pictures, music, etc)

so i booted the computer with ubuntu. of course, i can only access my files on the drive as read only, as they are in ntfs.  what i want to do is get those files onto my other computer which is running on xp.  

i tried doing this using my flash drive but i couldnt write to it. assumably it is also in ntfs.  

what device should i use / program i can install to get the files out of there and safely onto my other pc?

anyone know? would really appreciate it, thanks.

---

### Post by orb9220 on 2006-08-31
You could check that the flash is fat32 then both should read and write. If it is not fat32 format it. Or copy files to a dvd and transfer that way.

---

### Post by neymac on 2006-08-31
Try boot with Ubuntu live CD, and using Gparted format the flash device as fat32, then copy the files to it and then to the other machine.

---

### Post by theprince on 2006-09-04
i tried using my ipod.  i tested it by using a random small picture and it worked. transfered right over.

but now, a day and a restart later, its not working.  i dont know what it is, files are just not transfering from the read only drive over to the ipod anymore.  its formatted in fat32 for sure, i checked through text editor. and i checked the properties, read write and execute are all checked under owner.  i put that picture back to the desktop, and then tried transfering that over again.  it worked. files just arent transfering to the ipod


any ideas?

---

### Post by theprince on 2006-09-04
that is, transfering from the _read only drive_ to the ipod

---

