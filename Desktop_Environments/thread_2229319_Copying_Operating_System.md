---
title: "Copying Operating System"
date: 2014-06-12
forum: Desktop Environments
---

### Post by Geoff_Lane on 2014-06-12
Folks,

I have a 250GB hard drive with 4 partitions;

1. Ubuntu 12.04
2. swap
3. Vista
4. Vista recovery

I have bought a new 500 GB HD and would like to copy over.

Is dd the easiest?  I can resize afterwards but am not sure how long this will take.

I have copied numerous smaller images using dd but am wondering if I can do it in stages.

Any suggestions appreciated.

Geffers

---

### Post by A Bunny on 2014-06-12
Hello Clonezilla is a great option for cloning hard drives

See here [http://clonezilla.org/](http://clonezilla.org/)

Just download the iso ( [http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php) ) and burn it to a disk or usb drive and run it as a live distro.

Hope this helps
A_Bunny

---

### Post by C.S.Cameron on 2014-06-12
I have heard a lot of good things about clonezilla but prefer dd myself.

You should be able to clone the hard drive in one step.
I have successfully used the form "dd if=/dev/sdx of=/dev/sdy", sdx being the disk to copy from and sdy the disk to copy to.
Make no errors.

It will probably be an overnight operation depending on machine speed.

---

### Post by A Bunny on 2014-06-12
Yes dd should work as well even though the time can be a bit long :)

Hope that option works for you.
A_Bunny

---

### Post by oldfred on 2014-06-12
Understand with any clone you cannot have both drives plugged in when you reboot one of them. They have duplicate UUIDs and that is not allowed. Or booting one drive may use a partition on another drive corruption both.

You have to change UUIDs, edit fstab, reinstall grub2 and possibly some other fixes. Not sure about Windows and what changes may be required.
But best not to erase old drive until you know everything works as expected.

 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by C.S.Cameron on 2014-06-14
> **oldfred said:**
> Understand with any clone you cannot have both drives plugged in when you reboot one of them. They have duplicate UUIDs and that is not allowed. Or booting one drive may use a partition on another drive corruption both.

You have to change UUIDs, edit fstab, reinstall grub2 and possibly some other fixes. Not sure about Windows and what changes may be required.
But best not to erase old drive until you know everything works as expected.

 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

Is this true? I have done this cloning a number of times and found the UUID's slightly different, Like a comma in one and not in the other.

---

### Post by sudodus on 2014-06-14
Yes, I am rather sure it is true. The UUIDs are also cloned, which is OK if you avoid booting into one of them while the other drive (with identical UUIDs) is connected.

---

### Post by Geoff_Lane on 2014-06-15
> **A Bunny said:**
> Hello Clonezilla is a great option for cloning hard drives

See here [http://clonezilla.org/](http://clonezilla.org/)

Just download the iso ( [http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php) ) and burn it to a disk or usb drive and run it as a live distro.

Hope this helps
A_Bunny

Thanks Bunny, used Clonezilla before but due to computer problems wanted to do without graphics if possible.

Geoff

---

### Post by Geoff_Lane on 2014-06-15
> **oldfred said:**
> Understand with any clone you cannot have both drives plugged in when you reboot one of them. They have duplicate UUIDs and that is not allowed. Or booting one drive may use a partition on another drive corruption both.



Thanks oldfred, I didn't realise that but do now.

As it is a laptop it wont matter as it would be a replacement.

Geffers

---

### Post by sudodus on 2014-06-15
> **Geoff_Lane said:**
> Thanks Bunny, used Clonezilla before but due to computer problems wanted to do without graphics if possible.

Geoff

Clonezilla runs in text mode (with menus, but still in text mode).

---

### Post by Geoff_Lane on 2014-06-19
> **sudodus said:**
> Clonezilla runs in text mode (with menus, but still in text mode).

Thanks sudodus, I had forgotten that.

geffers

---

