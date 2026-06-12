---
title: "Sharing emails between ubuntu and xp"
date: 2006-06-06
forum: Desktop Environments
---

### Post by bohboh on 2006-06-06
I have ubuntu installed on another hard drive and set to dual boot. I have also created a fat32 partition and use that to share files between the 2 os's.

My questions is this, is it possible to share emails? I would like to have one client in ubuntu and one in xp and for them to both have the same data directory, i.e. the place where all the emails are stored. 

My current client is "The Bat" and i dont think i can get a "the bat" equivalent for ubuntu. So i need a client which can use the same data directory. This i assume will not be possible and so have thought about using thunderbird, but this would require moving five years worth of emails, folders and filters etc which i am not too keen on doing (but will have to if given no other choice).

What do others do to share emails?

TIA

---

### Post by mdurham on 2006-06-07
Thunderbird works fine for sharing email between Windows & Ubuntu.
But, I was using Outlook on Windows, so I had to export all old email and import it to Thunderbird. This works, but I found there is some sort of limit on how many emails Thinderbird could import, it would just hang if trying to import too many in one go. So I had do export/import in chunks. Sorry I cant remember the size that Thunderbird was happy with but it might have been about 1000 emails. It was a real pain, I do remember that!

---

### Post by bohboh on 2006-06-07
Is it safe to access the datafiles from xp and ubuntu?

I mean, will opening the files up in ubuntu make them non-accessible in xp and vice versa.

---

### Post by bluenova on 2006-06-07
[QUOTE=bohboh]What do others do to share emails?[/QUOTE]

I use IMAP rather than POP3 to access my emails, so they are all stored on the email server, and I can access them from any client any place.

---

### Post by bohboh on 2006-06-07
[QUOTE=bluenova]I use IMAP rather than POP3 to access my emails, so they are all stored on the email server, and I can access them from any client any place.[/QUOTE]

So how does IMAP exactly work?

Can i take my existing folder structure and transfer it? OR will i still need to create it by hand.

Can i still have a local copy for backup and to take around with me, so basically i can view my email from within the IMAP web interface and i can update my local copy on my laptop / pc by doing a send and receive.

If i set up the folder structure in the imap account, and then do a "Check email", will it replicate the structure within my email client?

---

### Post by bluenova on 2006-06-07
Nope, the fact that you have an exisiting collection of emails is a problem. Most email providers will let you conenct by IMAP, and in your email client you just select IMAP rather than POP3.

IMAP:
IMAP stands for Internet Message Access Protocol. It is a method of accessing electronic mail or bulletin board messages that are kept on a (possibly shared) mail server. In other words, it permits a "client" email program to access remote message stores as if they were local. For example, email stored on an IMAP server can be manipulated from a desktop computer at home, a workstation at the office, and a notebook computer while traveling, without the need to transfer messages or files back and forth between these computers.

IMAP's ability to access messages (both new and saved) from more than one computer has become extremely important as reliance on electronic messaging and use of multiple computers increase, but this functionality cannot be taken for granted: the widely used Post Office Protocol (POP) works best when one has only a single computer, since it was designed to support "offline" message access, wherein messages are downloaded and then deleted from the mail server. This mode of access is not compatible with access from multiple computers since it tends to sprinkle messages across all of the computers used for mail access. Thus, unless all of those machines share a common file system, the offline mode of access that POP was designed to support effectively ties the user to one computer for message storage and manipulation.

---

### Post by bohboh on 2006-06-07
[QUOTE=bluenova]Nope, the fact that you have an exisiting collection of emails is a problem. Most email providers will let you conenct by IMAP, and in your email client you just select IMAP rather than POP3.

IMAP:
IMAP stands for Internet Message Access Protocol. It is a method of accessing electronic mail or bulletin board messages that are kept on a (possibly shared) mail server. In other words, it permits a "client" email program to access remote message stores as if they were local. For example, email stored on an IMAP server can be manipulated from a desktop computer at home, a workstation at the office, and a notebook computer while traveling, without the need to transfer messages or files back and forth between these computers.

IMAP's ability to access messages (both new and saved) from more than one computer has become extremely important as reliance on electronic messaging and use of multiple computers increase, but this functionality cannot be taken for granted: the widely used Post Office Protocol (POP) works best when one has only a single computer, since it was designed to support "offline" message access, wherein messages are downloaded and then deleted from the mail server. This mode of access is not compatible with access from multiple computers since it tends to sprinkle messages across all of the computers used for mail access. Thus, unless all of those machines share a common file system, the offline mode of access that POP was designed to support effectively ties the user to one computer for message storage and manipulation.[/QUOTE]

IMAP sounds like a solution BUT will require me to create the folder structure. But that leaves the issue of my existing emails which i definately cant lose.

I think i will need to transfer my emails to thunderbirds format, there is a page explaining this in the mozilla forums which i will try. 

(scroll to the bottom)
[URL="http://forums.mozillazine.org/viewtopic.php?t=16245&highlight=bat"]http://forums.mozillazine.org/viewtopic.php?t=16245&highlight=bat
[/URL]

---

### Post by mdurham on 2006-06-07
To answer bohboh's question:
> Is it safe to access the datafiles from xp and ubuntu?

I mean, will opening the files up in ubuntu make them non-accessible in xp and vice versa.

It seems perfectly safe for me, I've been doing it for ages. Both XP & Ubuntu can read from the pop server. Why don't you try it?

---

### Post by jakev383 on 2006-06-08
[QUOTE=mdurham]To answer bohboh's question:


It seems perfectly safe for me, I've been doing it for ages. Both XP & Ubuntu can read from the pop server. Why don't you try it?[/QUOTE]
Out of curiosity, what permissions do you use on the FAT32 share in fstab? I have umask set to 0000, and I seem to have run into issues; emails downloaded in Ubuntu don't show when I boot into XP. Looking at the files in Ubuntu, they're root:root and 777.

---

### Post by mdurham on 2006-06-08
Here's my fstab, thunderbird data is on vfat hda7
> # /etc/fstab: static file system information.
#
# <file system> <mount point> 	<type>	<options>			<dump><pass>
proc			/proc			proc	defaults			0		0
/dev/hda4		/				ext3	defaults,errors=remount-ro 0	1
/dev/hda6		/home			ext3	defaults			0		2
#
/dev/hda1		/media/hda1		ntfs	nls=utf8,umask=0222	0		0
#/dev/hda2		/media/hda2		vfat rw,users,gid=users,umask=0002,uid=1000,utf8=true,exec,dev,auto 0 	0
/dev/hda2		/media/hda2		ext3	defaults			0		0
/dev/hda5		/media/hda5		ntfs	nls=utf8,umask=0222	0		0
/dev/hda7		/media/hda7		vfat	rw,users,gid=users,umask=0002,uid=1000,utf8=true,exec,dev,auto 0 	0
/dev/hda9		/media/hda9		ext3	defaults			0		0
#
/dev/hda8		none			swap	sw					0		0
/dev/hdc		/media/cdrom0	udf,iso9660 user,noauto		0		0
/dev/fd0		/media/floppy0	auto	rw,user,noauto		0		0
#


---

### Post by fred.cpp on 2006-06-08
You can do this:
open the thunderbird profile manager.
1) select create a New profile.
2)select a folder where you want to store the profile files (a Fat32 partition is a good idea, but NOT in the windows one!). Create the profile.
3) configure your mail accounts as needed
4) Switch to your other OS
5) Open profile manager and select create new profile
6) select the path where your profile is stored and create the profile.

That's all!
Now you can acess the same profile from windows and ubuntu, but there are some limitations:
**DON'T USE THEMES OR EXTENSIONS** or the profile, stored e-mails and other stuff will be corrupted.
It's not a good Idea to hibernate the computer when thunderbird Is open and boot in the other OS, may cause the same data corruption.
I've done this with 3 OS's(winXP, ubuntu, OSX), but remember, Nothing is safe under Windows, so use this under your own Risk :-\" 
Regards 8)

---

### Post by mdurham on 2006-06-08
I don't use themes but I do use extensions without problems (so far anyway!)
Maybe it would depend on which extensions are used?
I wonder if they have fixed the limited number of imports? Maybe it wasn't the number of emails, it could be the data size that's the problem???

---

### Post by bohboh on 2006-06-10
Well i have managed to export all my emails from the bat to thunderbird and am able to access them from ubuntu, xp and my laptop which is also xp. (Not at the same time though, would that be a problem? trying to access them at the same time from two different machines, guess it would be)

So all is well. :D 

Thanks.!

---

### Post by jgcamp99 on 2006-06-11
One of the reasons I went with Ubuntu, it has Ximian Evolution, it's probably the closest you'll get to MS Outlook for more than just email. On other distros, I needed Mozilla's Firefox and Thunderbird, even Sunbird for calendar. With this version of Evolution, I haven't bothered updating anything but Firefox from Mozilla.

[http://www.novell.com/products/desktop/features/evolution.html](http://www.novell.com/products/desktop/features/evolution.html)

Sounds like you want to do something similar/identical to this on a localized level ?

Built-in Microsoft Exchange Support
Users can communicate directly with built-in WebDAV support, eliminating the need to maintain separate IMAP e-mail server access to support Linux and UNIX users.

From within Novell Evolution, users can view, edit and update e-mail, address books, calendars and task folders on the Exchange server.

Using existing global address lists, users can access names, addresses and contact information from the Exchange Global Address List.

Public folder support allows users to share documents and files in existing Exchange public folders. They can also create new public folders for collaboration.

Through the Manage Permissions feature, users can control access to personal and public folders, calendars and task lists.

With the proper authorization, users can open other users' calendars or shared folders.

The Out-of-Office Assistant helps users create custom vacation or notification messages that run on the Exchange server.

Through the Calendar Delegation feature, users can set permissions to allow others to view their calendars. Users can also delegate permission to a colleague (for example, an administrative assistant) to accept and schedule meetings in their calendars.

Direct resource booking reserves resources such as conference rooms or vehicles for your meetings and appointments.

The new mailbox- and folder-size features display Exchange server quota notifications to keep mailbox sizes down.

---

### Post by weizilla on 2006-06-25
Is there any way of sharing Evolution e-mails between Ubuntu and Windows XP? I used Thunderbird for a brief period just for that purpose but I hated it because I liked Outlook 2003 so much better.

---

