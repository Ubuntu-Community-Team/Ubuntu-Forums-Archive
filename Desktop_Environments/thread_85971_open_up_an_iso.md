---
title: "open up an iso?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by ArcadePride on 2005-11-03
A friend of mine sent me an iso file of a data dvd, and when i went to open it up, i relized that kubuntu would only alow me to burn it. I was looking on apt-get, and i couldn't find a program that would let me handel an iso like a ziped file, and not a disc image. In the end i had to transfer the iso file to my windows partition and then the files back again after I had opened it with a zip program.

Is there anything on apt-get that can solve this little issue? :(

---

### Post by carbon-12 on 2005-11-03
Try:

sudo mkdir /mnt/iso/
sudo mount -o loop -t iso9660 name_of_image.iso /mnt/iso/

---

### Post by aysiu on 2005-11-03
You can run ISOs with an emulator like *qemu*

---

### Post by kvidell on 2005-11-03
[QUOTE=carbon-12]Try:

sudo mkdir /mnt/iso/
sudo mount -o loop -t iso9660 name_of_image.iso /mnt/iso/[/QUOTE]
I agree with this method. It's how I do most things ISO related.
- K

(yay! 500th post!)

---

### Post by invalid on 2005-11-03
I use qemu, as well.

Cheers,
Cb

---

### Post by rlange on 2005-12-04
Very nice info. I have done this and was able to mount the iso. Now to unmount is the command??

sudo  unmount -o loop -t iso9660 name_of_image.iso /mnt/iso/

then to remove the iso directorys what is the command as I have only read permissions for the iso directory??

thanks

---

### Post by Josip Lazic on 2005-12-05
[QUOTE=rlange]Very nice info. I have done this and was able to mount the iso. Now to unmount is the command??

sudo  unmount -o loop -t iso9660 name_of_image.iso /mnt/iso/
[/QUOTE]

sudo umount /mnt/iso

---

### Post by Boxed on 2005-12-05
Now that wheretalking about opening/mounting cd images, is there a similar command for mounting a bin/cue image?

---

