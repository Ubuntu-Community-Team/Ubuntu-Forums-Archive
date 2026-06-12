---
title: "Making hard drive icons on desktop...?"
date: 2010-07-02
forum: Desktop Environments
---

### Post by haywirepc on 2010-07-02
Greetings and salutations...

I switched after some years from vector linux to xbuntu. Your software repositories won me over I think...

So far, xbuntu is very similar to vector linux but I'm trying to do a few things and I'm confused.

I wanted to get rid of home file system and so on icons and did. I wanted to place some icons to access the two physical hard drives. In vector, I could have a launcher and use thunar /mnt/hda/ To access the first drive and thunar /mnt/hdb for the second drive...

So I look in mnt and see nothing in xbuntu... Maybe I'm just wrong its been a long time since I configured and customized my last linux box.

Can someone help me get icons on the desktop for both physical drives?

Thank you all very much in advance for any help...

Loving the switch so far...

Steven

Hope you guys know what I mean and can help.

---

### Post by robsoles on 2010-07-03
do I understand your question correctly: You wish to (and used to) have the drive containing the partition that is naturally mounted at '/' also mounted at '/mnt/_drive_identifier_from_dev' ???

If you are talking about HDDs that are not actually naturally mounted by being part of the file-system then, after you mount them by double-clicking them in 'computer', they will mount at '/media/_drive_uuid_or_file-system-label' and you can arrange to have that happen each time the system is started in fstab with not so much fiddling besides.


To the best of my understanding, if these drives are already mounted then it is undesirable to mount them again at some other point in the file-system because this can lead to easily wiping out your OS and data in very few steps indeed!

Are these drives manually partitioned? Are they part of an LVM? Did you let the installer partition them when you installed? Answers to one or more of these will speed along the best response I expect you can hope for regarding your desirable way to access your file-system(s).


Edit here: Can you find and open 'Disk Utility' - it's under "System"->"Administration" in my flavor of this distro.

---

