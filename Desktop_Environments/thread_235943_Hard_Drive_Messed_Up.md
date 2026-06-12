---
title: "Hard Drive Messed Up?"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Poptart on 2006-08-14
Okay. I've got a problem, and I'm just going to lay it out from the beginning, so bear with me.

I installed the OEM version of Dapper Drake on my desktop several days ago. When I did this, I included a seperate partition for my /home directory. Everything went really well. After I got my desktop installed I copied my laptop's files over to my /home directory and then installed XUbuntu on my laptop. I then decided I wanted to use Windows for something and looked up restoring GRUB, decided it wans't too difficult and set about doing that.

I put a second harddrive in my desktop machine and booted into the Windows XP Pro install session. It got to where it finished copying over the files and then wouldn't go any farther. I have a feeling my second drive is bad. I gave up on it and decided to just reinstall GRUB and get back into Ubuntu.

So, I follow the instructions and pop in my Alternative Install CD and hit "Rescue Mode." It won't go into Rescue Mode. It gives me an error and says it cannot complete the action. So, I pop in my Live CD, which, it turns out, is bad. My roommate is downloading a new Live CD to burn for me right now, but in the mean time I've hooked the harddrive with the OEM installation on it up to my portable case and thusly to my laptop (with XUbuntu).

In XUbuntu I type "fdisk -l" and recieve:

[I]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.[/I]

When I attempt to "mount /dev/sda1 /media/sda1" I recieve:

*mount: you must specify the filesystem type*

When I attempt to "mount -t ext3 /dev/sda1 /media/sda1" I recieve:

*mount: special device /dev/sda1 does not exist*

The same goes for any of the other special devices on the list.

What I want to know is if there's any way I can salvage my /home directory. That's all I really care about. I can reinstall no problem, but I might cry if I lose all my files. *laughs*

Thanks in advance for any help!

---

