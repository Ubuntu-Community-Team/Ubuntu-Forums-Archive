---
title: "SmartMedia / CompactFlash drive doesn't automount"
date: 2005-05-27
forum: Desktop Environments
---

### Post by cinematography on 2005-05-27
My MMC/SD drive no longer automounts when I put in my photo disk. The drive light turns on fine, but I have no way of accessing the pictures on that disk. I'm a newbie and any help would be greatly appreciated.

---

### Post by cinematography on 2005-05-28
:(

---

### Post by cinematography on 2005-05-28
:(

---

### Post by sb73542 on 2005-05-28
Please plug in the card, then goto a terminal and type "sudo dmesg > /home/your-login/dmesg1.txt" (without the quotes).  Then open that text file and post the last 10 lines or so.  This card worked before, you said?

---

### Post by cinematography on 2005-05-28
Yes, it was working before. It was working beautifully. I would put in the card and an icon would come up. I did unmount the card by right clicking / unmounting it though. Maybe that messed up something? 

Here is the text file made from the command you gave me:

And THANK YOU for your reply. I've been waiting almost 2 days for a resonse. :(

---

### Post by cinematography on 2005-05-28
[QUOTE=thrift]you can try to open a terminal(right click on background and click open terminal) and then type some commands such as the following:

sudo bash
enter your password and hit enter
cat /proc/scsi/usb-storage

this should give you a list of all SCSI hardware Linux is aware of.  This should show an entry for your compact flash drive, as disks on a USB bus are accessed through the kernel's SCSI emulation.

In example my results of cat /proc/scsi/scsi:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: MAXTOR   Model: ATLAS15K_18WLS   Rev: DT60
  Type:   Direct-Access                    ANSI SCSI revision: 03
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic  Model: USB Storage-SMC  Rev: 0207
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic  Model: USB Storage-CFC  Rev: 0207
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 02
  Vendor: Generic  Model: USB Storage-MMC  Rev: 0207
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 03
  Vendor: Generic  Model: USB Storage-MSC  Rev: 0207
  Type:   Direct-Access                    ANSI SCSI revision: 02

You can see the third device in the list is my CFC or compact flash drive.  Since it is the third device in the list it lets me know something about how Linux references the device.  The first device in the list is sda, the second is sdb, the third is sdc, and so on and so fourth.

so if you had your third SCSI device as the Compact flash drive you would do the commands I am about to show you in an attempt to gain access to it:

mount /dev/sdc /mnt
ls /mnt

If you have a differenct device, such as the first SCSI device, you would use that device to reference it, so for the first SCSI device you would try mount /dev/sdb /mnt

The ls /mnt is just a way to see a list of the files on the disk assuming the commands worked.  It is possible that right after the mount command Ubuntu could just show you the files in a new window.

If you can see the files on your compact flash disk when you ls /mnt and Ubuntu has opened no window for you to view them you can open nautilus(file manager) window and go to File->Open Location... Type in /mnt in the box and click open and you should have the ability to view your pictures.

When you are done looking at your pictures(before you remove the media from your compact flash drive) you need to type in the terminal:

umount /mnt/

This is to make sure the device can be removed safely.

Good luck, hope it works.[/QUOTE]


> sudo bash
enter your password and hit enter
cat /proc/scsi/usb-storage
This is what I get after entering those commands:

me@ubuntu:~$ cat /proc/scsi/usb-storage
cat: /proc/scsi/usb-storage: Is a directory

I guess that's a good thing. :???:



And I tried all of the following as root: 
mount /dev/sdc /mnt
mount /dev/sdb /mnt

And none worked. ](*,)


I'm sorry for not getting it to work. Thank you though for your time and response.

---

### Post by thrift on 2005-05-28
Sorry, I meant cat /proc/scsi/scsi.

From the dmesg you posted earlier I figured out your scsi device anyay, so you don't need to do that unless you are interested.

It is /dev/sdb for your compact flash.

If you have the card plugged into the compact flash reader and you try to

sudo mount /dev/sdb /mnt
<enter password if applicable>

Do you get an error?

If you do this could be very telling.
Does it work on any other computers?

---

### Post by cinematography on 2005-05-28
> me@ubuntu:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic  Model: USB SD Reader    Rev: 1.00
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi3 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic  Model: USB CF Reader    Rev: 1.01
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi3 Channel: 00 Id: 00 Lun: 02
  Vendor: Generic  Model: USB SM Reader    Rev: 1.02
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi3 Channel: 00 Id: 00 Lun: 03
  Vendor: Generic  Model: USB MS Reader    Rev: 1.03
  Type:   Direct-Access     

> me@ubuntu:~$ sudo mount /dev/sdb /mnt
Password:
mount: No medium found

This makes no sense. It was JUST working a couple of days ago.

---

### Post by cinematography on 2005-05-28
Additional note: My drive is internal. 

It looks something like this. 

SmartMedia ------------ MMC / SD 
CompactFlash I/II --- MS/MS PRO

---

### Post by derrick1985 on 2005-05-28
sudo /etc/init.d/dbus-1 restart

---

### Post by cinematography on 2005-05-28
[QUOTE=derrick1985]sudo /etc/init.d/dbus-1 restart[/QUOTE]
> me@ubuntu:~$ sudo /etc/init.d/dbus-1 restart
 * Stopping Hardware abstraction layer:                                  [ ok ]
 * Stopping system message bus:                                          [ ok ]
 * Starting system message bus:                                          [ ok ]
 * Starting Hardware abstraction layer:                                  [ ok ]

What do I do now? :)

I'm on day 3 now with this problem.  ](*,) 

Thank you all so much for your help. :)

---

### Post by derrick1985 on 2005-05-28
[QUOTE=cinematography]What do I do now? :)

I'm on day 3 now with this problem.  ](*,) 

Thank you all so much for your help. :)[/QUOTE]

try inserting your compact flash card and then try the command.

---

### Post by cinematography on 2005-05-28
[QUOTE=derrick1985]try inserting your compact flash card and then try the command.[/QUOTE]
I did it with the card in the slot and nothing happened. I did it out of the slot and nothing happened. I'm going to try rebooting now and see if that helps. I'll post the result in this post.

Edit: That didn't work either. UGG!! I'm going to try it from the Live CD now. brb.

Edit: Yep. There is nothing wrong with the hardward because it worked PERFECTLY from the LiveCD. I put the 255mb card into the slot, and an icon showed up on the desktop. One of the updates or a program I installed maybe is messing up my flash card drive. ](*,)

---

### Post by derrick1985 on 2005-05-29
[QUOTE=cinematography]I did it with the card in the slot and nothing happened. I did it out of the slot and nothing happened. I'm going to try rebooting now and see if that helps. I'll post the result in this post.

Edit: That didn't work either. UGG!! I'm going to try it from the Live CD now. brb.

Edit: Yep. There is nothing wrong with the hardward because it worked PERFECTLY from the LiveCD. I put the 255mb card into the slot, and an icon showed up on the desktop. One of the updates or a program I installed maybe is messing up my flash card drive. ](*,)[/QUOTE]

Could be. I know there is a dbus error floating around with hoary, which is supposedly fixed in Breezy.

---

### Post by thrift on 2005-05-29
Looks like something is messed up with DBUS or the kernel(I know there was an upgrade for the kernel in hoary not too long ago, maybe within a week).  I would submit a bug report to the kernel guys or the DBUS guys and see if they can help.

---

### Post by thrift on 2005-05-29
I just tested mine to see, and mine doesn't work now either hah.
Submit a bug report and I'll submit one to match in a couple days.  That should get some attention to this problem.

---

### Post by cinematography on 2005-05-29
Okay, so it's not me. Whew. So where should I send this bug report and what should I say? [https://bugzilla.ubuntu.com](https://bugzilla.ubuntu.com) ? I'm not even sure how to describe this. Should I just say something like "An update is keeping my internal flashcard drive from updating."

---

### Post by thrift on 2005-05-29
Just tell them to the best of your knowledge what is going on.  Tell them when you try to mount the device it's giving you an error and the error it gives.  Be very verbose. bugzilla.ubuntu.com is the correct site.

---

