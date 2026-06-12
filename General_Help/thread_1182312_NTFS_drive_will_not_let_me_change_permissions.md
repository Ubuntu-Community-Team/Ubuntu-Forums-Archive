---
title: "NTFS drive will not let me change permissions"
date: 2009-06-08
forum: General Help
---

### Post by coskierken on 2009-06-08
HI All!  I have second drive formatted in NTFS.  I have it in that format so I can read it from XP on my dual boot.  The problem is, I cannot change my permissions from root for the drive, even when I try in sudo.  Has anyone run across this?  Thanks in advance.

---

### Post by synapsys on 2009-06-08
Is the drive mounted? You can not change permissions on a drive while it's mounted no matter who you are.

---

### Post by coskierken on 2009-06-09
yes the drive is mounted.  It would not show up on the desktop if it was not.  I can access it read all files and change permissions on file in root.  This is the problem.  I am able to change in root and share a folder, but then the permissions will revert to only root.  It is very strange.  I was able to see the other machince on my network by only putting in the ip address.  I cannot mount the shares if I go only by the name, so it appears name is being blocked, but not the ip address.  I checked the firewall and made sure the ports were not blocked and that the ip of the other machine is not blocked.  

One other on the laptop is that the connection info is stating I only have a 1 MB/s wireless connection.  This is an intel chip in this laptop!  The laptop has a full connection to the network and is only 10 feet from the router!  The one file I managed to transfer was only showing a max of 2 MB/s transfer.  ](*,)I have my work in research on these problems.:-(

---

### Post by sedawk on 2009-06-09
NTFS is a filesystem from Microsoft, changing permissions off an
NTFS filesystem with linux tools (chown, chmod) might not have
the expected results. (I currently do not have an NTFS file system
here to test what works and what not).

Do you have any problems creating new files as the normal
user (or as root)? (This is something I have done regulary with Ubuntu
because write performance on my system on an NTFS disk is 6-10 times
faster with Linux than with XP - I blame lots of copy-protections
drivers messing up XP). This never needed any special action from my
side.

I guess you share the data of the NTFS drive with SMB (samba).
Part of the samba software is a tool the NetBios nameserver (nmbd)
which is responsible (also) for mapping names to IPs.
There might be something wrong with the configuration of nmbd on your
server. You can also configure if your shared folders are browsable.
E.g. when you enter the name of the server in windows you might
not see a list of shares because browsing shares is disabled!

---

### Post by justleen on 2009-06-09
sedawk is right.. You cant changes permission on NTFS.. you can only change permission on the mount point

---

### Post by coskierken on 2009-06-09
So, can I go into Vista, via my dual boot, and make sure sharing is enabled and will that let it share?  Just curious before I copy all the old data out and reformat.  I really don't want to do this as sometimes I access the drive in Vista (I know...Vista:cry: but I use it to play games).  

Any help on the network problems?  Thanks!

---

### Post by coskierken on 2009-06-09
sedawk, thanks.  I don't have any problem creating files on the NT partition as the normal user.  I can finally access the drive, via "smb://19x.xxx.x.x" only, and not by the name of computer via workgroup.  I will look at the nmbd and see what is happening.  Strange.  

The final is looking into the slow transfers and why it only shows only 1 MB/s connection!

---

### Post by sedawk on 2009-06-09
A value of 1 MB/s would be typical for a 10 Mbit WLAN.
If you have a faster WLAN have a look at "link quality" when
running the command "iwconfig". As you said the router
is not far away, so you should see something like 70% or better.
By looking at the output of "dmesg" or the modules
loaded ("lsmod") you can try to find out what WLAN chipset you
are using. Then check if there are any known problems with
Linux or the combination of your WLAN chipset and the router.

---

### Post by coskierken on 2009-06-09
I got it.  Reset the router when I got home and see 54MB.  all is good, except I have secure it now.  Still have to look at the nmbd.

---

