---
title: "/home mounten to ext2 filesystem in a file on a ntsf network drive"
date: 2009-06-26
forum: Desktop Environments
---

### Post by abebakker on 2009-06-26
I want to mount my /home directory to a NTFS partition on my windows 2003 server.
So this is what I have done .

I created a fie on my NTFS share and created a Linux Filesystem within the file:

[I]cd /path/to/windows2003/share
dd if=/dev/zero of=linuxfilesystem bs=4096  count=10000000
sudo mkfs linuxfilesystem[/I]

Then I mounted it as my newhome

[I]sudo mkdir /mnt/newhome
sudo mount -o loop  /path/to/NAS/storage/linuxfilesystem /mnt/newhome[/I]


I copied the data from /home to /mnt/newhome 



[I]cd /home/
find . -depth -print0 | cpio --null --sparse -pvd  /mnt/newhome/[/I]

 And set the right security.
 
[I]chown -R username:username /home/username
chmod 644  /home/username/.dmrc
chmod 644 /home/username/.ICEauthority[/I]

Then I modified the FSTAB file:

*gksu gedit /etc/fstab*
 Wijzig het mountpoint van /home
 [I]# Entry for /dev/sda7 :
/path/to/windows2003/share/linuxfilesystem  /home  ext2  loop 0 0 [/I]
 

*sudo mount –a*

So far so good. But if I reboot the PC he says that he can't find my /home directory.
When I logon to a failsafe terminal and do a Sudo mount -a, logoff and logon again everything works fine.

Why does the /home directory not mount automatic on boot?

---

