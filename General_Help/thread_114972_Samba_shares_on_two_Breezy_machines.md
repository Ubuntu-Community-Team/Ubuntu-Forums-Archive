---
title: "Samba shares on two Breezy machines"
date: 2006-01-09
forum: General Help
---

### Post by eqisow on 2006-01-09
OK, so I just connected a second computer to my home network. Both computers are running Ubuntu 5.10. On the first computer, when I go to System --> Administration --> Shared Folders the window opens and then just hangs. If I right click a folder in nautilus and click share folder, nothing happens. Computer 2 should be set-up if the GUI configuration actually works correctly, but I'm stumped by the problem on the first computer. Anybody have a suggestion?

---

### Post by eqisow on 2006-01-09
When I try to run the 'Shared Folders' program in the terminal (gksudo shares-admin) this is the error message I get:

(shares-admin:18590): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
*** glibc detected *** double free or corruption (fasttop): 0x0822a020 ***

---

### Post by eqisow on 2006-01-09
OK, so I was able to get the 'Shared Folders' Program running again by deleting  the share entries in the NFS config file. (I had previously tried setting up NFS unsuccessfully) Now I have set up both computers to share the folders I wanted shared using the GUI tool, but nothing shows up on either computer when I go to Places --> Network. Is further set-up necessary? If so, what do I need to do to set-up file sharing successfully?

Edit: nfs-common and nfs-kernel-server are both uninstalled. I am now trying to use samba. samba, samba-common, and smbfs are all installed.

---

### Post by eqisow on 2006-01-09
OK, so I installed webmin and the samba module for it in an atempt to get samba configured correctly. However, I wasn't sure what the default login was for webgmin, and stupidly got myself locked out of the sebmin server. Is that temporary? And what is the default login supposed to be?

Edit: I found a couple of sources citing the default login as admin and the default password as being blank, but this did not work for me.

---

### Post by eqisow on 2006-01-09
So I still can't get logged into webmin, but I've been doing some stuff manually using [this]("http://doc.gwos.org/index.php/Share_files_using_Samba") as a guide. After editing my smb.conf file I tried to mount a shared folder manually as per the instructions in the link. The error message I got was:

10356: Connection to samba failed
SMB connection failed

I have attached a copy of my smb.conf file in case it would be helpful. I'd really appreciate some feedback, even if you don't have a definite solution. I feel like I'm talking to myself. :(

---

### Post by Zimmer on 2006-01-09
[QUOTE=eqisow]So I still can't get logged into webmin, but I've been doing some stuff manually using [this]("http://doc.gwos.org/index.php/Share_files_using_Samba") as a guide. After editing my smb.conf file I tried to mount a shared folder manually as per the instructions in the link. The error message I got was:

10356: Connection to samba failed
SMB connection failed

I have attached a copy of my smb.conf file in case it would be helpful. I'd really appreciate some feedback, even if you don't have a definite solution. I feel like I'm talking to myself. :([/QUOTE]
Hi, from the attached config file I notice you haven't set any authentication.
> 
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

..removing the semicolon before  security=user would be a start, but you probably have not set up any Samba users either, so that won't have an immediate impact.
setting  < security = share > would..but you need to mount a location as a share for Samba to see it. (I notice your conf has a share defined for [Music] so set security to share and see if that appears on the network).
Have a look here for general Samba Networking issues for user methods , posts #5 - #9
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)
and these, as there are many methods to mount shared folders, some more secure than others...
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
[http://ubuntuguide.org/#sharefolderstheeasyway](http://ubuntuguide.org/#sharefolderstheeasyway)
As for talking to yourself, I do it all the time, that way I always get a good conversation ;). Rest assured people are looking at the threads, they might need some time to gather resouces for a decent response...but they DO look...
Regards

---

### Post by eqisow on 2006-01-10
Thanks for the reply Zimmer. Unfortunately, I haven't had the chance to try any of that since I have been having trouble with GRUB after switching one of the machines to Kubuntu. (not entirely true, I uncommented the line you suggested shortly after my last post and I had already added users using 'sudo smbpasswd -a namehere) I have noticed, however, that when running Knoppix 3.9 on machine A, I can see machine B on the samba network. This should mean that at least one machine was, indeed, configured correctly. Both machines were configured exactly the same as far as I could tell. Might there be any reason as to why Knoppix would see the other computer but Ubuntu wouldn't?

---

### Post by Zimmer on 2006-01-11
You haven't given both computers the same name, have you?
Knoppix would have configured its own temporary network config, which you could access for clues...
As a rule, to get networking right with XP I have a linux user name on the Ubuntu box , set up as a Samba user and it is the same name and Samba password as my user on XP .
If you followed the user instructions correctly here
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)
and have shares mounted (via your config) there should not be a problem.
Try sharing the home directories in the config files by
[homes]
   comment = Home Directories
   browseable = yes
Regards

---

