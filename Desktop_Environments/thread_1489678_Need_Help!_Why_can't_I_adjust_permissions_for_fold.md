---
title: "Need Help! Why can't I adjust permissions for folders and files on NTFS USB drive?"
date: 2010-05-21
forum: Desktop Environments
---

### Post by Oberon Prime on 2010-05-21
Hello,

First off I want to apologize for the fact that the first several paragraphs go into something seemingly unrelated to the subject of this thread. However I want to be sure that those who choose to lend me a hand understand where I'm coming from and why I'm asking that question.

I just recently switched from Windows Vista to Ubuntu 10.04. So far I've been loving it mostly. But their is one oddball thing I haven't been able to get working. That is a pair of shared folders located on my NTFS external drive connected via USB2.

The drive was automatically mounted on first boot and has full read/write access for owner (which is my username) right out of the gate. For this reason I assumed I would be good to do this.

I've been unable to get it working in Ubuntu. As it stands now I've manually added them to smb.conf, added them to the Samba Server Configuration and finally by right clicking the folder in nautilus and choosing Sharing Options. All with varying results

At best it will show the shares under the computer but not allow access. I've also cleared out all of these for those folders to try them individually or in different orders. What I found was that using Sharing Options first gives this error and sets nothing up. But either of the other two will at least show the share albeit with no access.

> 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

What I've discovered is that if I use just the Sharing Options from Nautilus on any folder located on my ext4 partition or the internal NTFS partition then it will ask if applicable to adjust the permissions and though nothing appears in smb.conf that it works more or less just fine.

Having played with "ls -l" I discovered that by default that ownership of the folders on the external NTFS is set to myself and that permissions are 700. On the ext4 partition ownership is set to myself and permissions on folders 711. The folders on the internal NTFS partition has an ownership of "root" and permissions set to 777

From here I tried to use "sudo chmod" via a terminal to manually change permissions for folders on all 3 partitions and I can do so for the ext4 and the internal NTFS owned by root. But no matter what I cannot for the external NTFS.

The main thing is I want to know why I can't adjust those permissions on the external. I'm convinced that something to do with the way USB drives work by default must be impacting this but I could not find a single thing anywhere to confirm this much less to offer a solution.

The second thing is that I installed and used mountmanager to automatically mount the internal NTFS and according to that softwares options the setup for both it and the external NTFS are the same. But if that is true then why is the external owned by me and the internal by root and the resulting permissions are completely different?

If I can figure out how to take control of my partitions and adjust permissions then I'm certain getting the samba shares setup will follow.

Any help that can be offered would be greatly appreciated.

Regards,
Oberon Prime

---

### Post by SlidingHorn on 2010-05-21
I'm not 100% sure this will fix your problem, but it's probably worth a read in your case: [Click Here]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by Oberon Prime on 2010-05-22
Based on all my trial and error. I am very confident its something to do with how the system is mounting the external drive. The mechanism in play seems to mount it with me as the explicit owner and permissions of 700. When I try to change permissions on any individual folder or file on the drive in the Properties dialog in Nautilus it lets me click the checkbox once to highlight it red but when I click it the second time to check it immediately unchecks itself.

When I use chmod from the terminal I get no error and even a confirm that it was successful if I use the -v switch but once again no change.

I am able to change permissions at will on the ext4 partition that ubuntu resides on and as such I can share folders there. I can also change permissions on the internal NTFS partition and as such share folders from there. This leads me to be fairly certain this isn't a samba issue or an ntfs issue.

I used MountManager to setup the automount on the internal NTFS drive so I told it to use the exact same settings on the external. But it seems the the fact that its a USB device overrides because even after a restart it still treats the two drives differently.

I have to assume that somewhere how Ubuntu handles external drives is documented and as such somebody would be able to confirm this is a default behaviour, and perhaps more importantly where to go to change that.

---

### Post by jerome1232 on 2010-05-22
NTFS is a microsoft file system and does not support Linux style permissions. afaick chown and chmod won't do a thing when used on any microsoft filesystem (fat or ntfs)

Instead permissions are determined for the entire drive at mount time. 

You could mount it with more permissive ...permissions. I'm unsure of how to get Ubuntu's automatic mounting system to do that but hopefully that's a nudge in the right direction for ya.

---

### Post by Oberon Prime on 2010-05-22
> **jerome1232 said:**
> NTFS is a microsoft file system and does not support Linux style permissions. afaick chown and chmod won't do a thing when used on any microsoft filesystem (fat or ntfs)

Instead permissions are determined for the entire drive at mount time. 

You could mount it with more permissive ...permissions. I'm unsure of how to get Ubuntu's automatic mounting system to do that but hopefully that's a nudge in the right direction for ya.

I'm away from my box for the weekend so I cannot test. But I think this makes sense. The ntfs partition on the internal drive was given a different set of default permissions at mount time. I thought I had tried to change the permissions on the test folder. But as I'm thinking on it at this point it had what I needed to start with so I probably didn't need to. All I had to do was add an extra line under the global section of /etc/samba/smb.conf to allow for the fact that it was owned by root.

So assuming this is right then that must mean I need to force ubuntu to establish the permissions on the usb drive to be more permissive as you put it.

Does anybody know why the system would automatically assign the usb drive an owner of "user" and give the drive 700 for permissions but then when mounting the internal ntfs partion assign it to "root" with different permissions. Where is this done how can the defaults be changed?

---

