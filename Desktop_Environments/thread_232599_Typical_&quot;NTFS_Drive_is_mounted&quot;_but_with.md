---
title: "Typical &quot;NTFS Drive is mounted&quot; but with a twist... no permissions to access."
date: 2006-08-08
forum: Desktop Environments
---

### Post by andrader on 2006-08-08
Ok, I just thought that I would give Ubuntu a try... my Windows XP installation crapped out for the billionth time... so thought I would try this distro instead of reinstalling XP yet again.  Am running the 6.06 version of Ubunto... and tried all the normal things found on the web forums.

My problem is that when I try to change the permission on the FORMERLY Windows NTFS drive... cuz the messages I am getting is that I cannot access the drive due to the lack of permissions... even though I have root (i.e. access to "sudo"), it won't let me change them.  They are all ghosted on the properties window.

Any idea guys?  Did something with how Windows last touched this drive leave them in a state that they are orphaned in terms of permissions.... i.e. no permissions?

Anybody have any clue... would appreciate it.

Thanks.... Rick

---

### Post by computergroove on 2006-08-08
This is a total shot in the dark - sudo gedit /etc/fstab. If you had a xp pro machine you could slave the drive and reset the  permissions of the data, save the data you need and format it for future use.

---

### Post by tzulberti on 2006-08-09
You should look at the how-to section that tells you what to do. Writting permission are initially disable since writing in a ntfs partitions is experimental...

---

