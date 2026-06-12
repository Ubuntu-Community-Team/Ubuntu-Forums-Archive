---
title: "Windows to Ubuntu migration help."
date: 2006-07-15
forum: Desktop Environments
---

### Post by martymart on 2006-07-15
I currently have two workstations and one server. One workstation is a dual boot with windows xp and Ubuntu, the other is windows XP only and the server is windows 2000. The server is used for centralised storage and as it is on 24 hours a day and has low power consumption I use it for downloading large files. Currently I have the windows machines set so that the my documents folder is stored on the server so that it accessible from either workstation, which means that I can access my outlook file (.pst) from both computers.

Here are my questions:
1. Can I store my home directory on the server.
2. Can I have a single file for my emails that is accessible from both computers.
3. Can I convert or use the Outlook .pst file in ubuntu
4. Would I be better off converting the server to a ubuntu server and how easy would this be as the current server is NTFS. Also would the ubuntu server do all the jobs that my windows 2000 server did. If I set up a ubuntu server would it be better to set up a domain server with users log on details stored on that. Can a ubuntu server run as a file server and domain name server?
5.I have a windows mobile 5 device, how well do these integrate with ubuntu and which mail client is best suited to windows mobile devices?
6. The workstation that only has windows XP on it does not have ubuntu on it as it has a raid 0 arrary set up on it. The raid device is a HighPoint HPT370/372 and is biult in to the motherboard and is set up in a menu straight after the bios screen has loaded. There I can create and destroy and set up differing types of raid array and change the sector size etc. Is this a hardware raid or software? I have briefly tried to install ubuntu on this raid array and it does not detect the raid array but simply two 80GB drives (the individual components of the array). Will Ubuntu work on this raid array? Do I need to recreate the array with no file system on it as it has an NTFS on it at the moment.
7. The windows XP client also has a ATI 9600 pro graphics card, I have hear that ATI cards can be problematic. Is this the case for this card?

That is all I can think of right now but I am sure that I have loads more questions for you all.

The main reason that I want to migrate now is that no matter what precautions I take I seem to end up battling spyware, ad-ware and virus constantly despite being behind a HW firewall and having anti-virus software and spyware installed.

Thanks for you time in reading my long, convoluted, jumbled up mess of a post and taking the time to help me.

Martin.

---

### Post by martymart on 2006-07-15
-- Bump ---

---

### Post by martymart on 2006-07-16
I also forgot to mention that I use the windows XP maachine with ATI 9600Pro for watching movies on the TV, will this be possible?

---

### Post by Schalken on 2006-07-16
1. As far as I know you can make your home directory anywhere by going to 'System -> Administration -> Users and Groups' and changing the home directory location for the user. You *may* (I haven't tried it) be able to change the location to a remote directory (i.e. on your server) by using [ftp://user:pass@server/path](ftp://user:pass@server/path) (for FTP) or smb://user:pass@server/path (for a windows share).

3. I can see that Novell Evolution (included with Ubuntu) can import Outlook .cvs and .tab files. You could try pointing the importer to the .pst file and seeing what happens, or you can try another email application and export from that into Evolution.

7. The Radeon 9600 and Radeon 9600Pro are listed as supported on the BinaryDriver howto page ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) and the xorg radeon driver page ([http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html)](http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html)), however  you may need to use ATI's binary drivers (as per the howto) to use the card's TVout capabilities.

---

### Post by viraptor on 2006-07-16
> **martymart said:**
> 1. Can I store my home directory on the server.
You can. Just copy contents of /home dir to server and mount /home from there. NFS could be the best choice, but if you want windows to use it too, then samba is good. Just make sure you use correct rights, etc. Enabling acls to use ntfs' rights is a good idea.

> **martymart said:**
> 2. Can I have a single file for my emails that is accessible from both computers.
Probably - haven't tried, but I'd suggest a typical solution here. Open a IMAP server - courier, or dovecot. Dovecot is easier to set up IMHO. You can store your emails there as you want - IMAP supports folders, so it's almost the same as storing them on your disk. And it's fast - it's not the same as polling everything from / synchronizing to POP3.
For address book - LDAP (OpenLDAP) can store it.
If you set up both of daemons - you'll be able to use mail without problems from any location without import / export of files.

> **martymart said:**
> 4. Would I be better off converting the server to a ubuntu server and how easy would this be as the current server is NTFS. Also would the ubuntu server do all the jobs that my windows 2000 server did. If I set up a ubuntu server would it be better to set up a domain server with users log on details stored on that. Can a ubuntu server run as a file server and domain name server?
You can set up ftp for files, and you can set up samba. They share the same files on my server and I haven't got problems with that yet (though ftp is used for downloading mainly).
DNS - bind / whatever - you can set up caching nameserver with no problems.
Domain server - samba takes care of that. If you decide for LDAP for address book, you can also use it for authorization back-end. Samba can send logon scripts, show home dirs locations, authorize windows users and map domain user names to local unix (/ ldap) uids and logins.

> **martymart said:**
> 6. The workstation that only has windows XP on it does not have ubuntu on it as it has a raid 0 arrary set up on it. The raid device is a HighPoint HPT370/372 and is biult in to the motherboard and is set up in a menu straight after the bios screen has loaded. There I can create and destroy and set up differing types of raid array and change the sector size etc. Is this a hardware raid or software? I have briefly tried to install ubuntu on this raid array and it does not detect the raid array but simply two 80GB drives (the individual components of the array). Will Ubuntu work on this raid array? Do I need to recreate the array with no file system on it as it has an NTFS on it at the moment.
Kernel supports HPT37X chipsets, so if that's a raid one, it should be visible after loading that module. Be sure to create an initrd with that module preloaded, if you want to boot from partition on that raid device.
If disk is configured as hardware raid, it should be visible regardless of filesystem. But for linux - yes - you have to remove ntfs, as it's not fully supported yet.

---

### Post by martymart on 2006-07-16
How do I load the HPT3xx module? Do I have to use a special boot parameter? If so what?

Thanks for every ones help thus far,

Martin

---

### Post by martymart on 2006-07-16
I have installed the server edition of ubuntu as a dual boot with win 2K. Do I have to install samba to read and share the other NTFS disks in the server or can I use NFS and some other program?

Martin

---

### Post by martymart on 2006-07-16
Is there any way of converting my NTFS files to ext3 or am I best just backing up the data to another hard drive.

Martin

---

### Post by mrwilloby on 2006-07-16
> **martymart said:**
> I have installed the server edition of ubuntu as a dual boot with win 2K. Do I have to install samba to read and share the other NTFS disks in the server or can I use NFS and some other program?

Martin

Did using the server edition solve your RAID troubles?  I'm going through a similar thing right now where I want Ubuntu on my IDE Primary Master and I want a RAID 0 array through an add-on card with two other HDs for just storage space.  The drives were showing up individually and in the wrong order during the Partition section of Xubuntu setup so I just set it up with the RAID card removed.  I now get problems when I start the computer with the card in.  It is a hardware RAID configuration, so I'm not sure why it isn't detected.

I have Windows XP on hda1
Xubuntu on hda2 with swap at hda5

When booting with the card plugged back in I get the error:

ALERT! /dev/hda2 does not exist. Dropping to a shell!

I think putting the RAID card in changes the lettering of the drives.

---

### Post by brickbat on 2006-07-17
" 	Is there any way of converting my NTFS files to ext3 or am I best just backing up the data to another hard drive."

It depends how much data it is.  I have tried a few solutions.  

Firstly whatever you do, DON'T convert the NTFS drive to Fat32.  I did that and it stuffed up the filenames.

If it's not too much data then backing up is good.  Alternatively, there is now an apparently very reliable ntfs driver that lets you read and write ntfs.

Ciao
BB

---

