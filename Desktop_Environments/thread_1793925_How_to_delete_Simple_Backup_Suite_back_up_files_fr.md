---
title: "How to delete Simple Backup Suite back up files from hdd?"
date: 2011-06-30
forum: Desktop Environments
---

### Post by Geezanansa on 2011-06-30
Hiya Folks,

As the hours googling and searching forums are not proving very productive to finding the info I need for resolving the problem I am having with Ubuntu 11.04; I try posting here.

As a new ubuntu user I am enjoying learning more about how my pc works.  I have recently upgraded to 11.04, the only hard drive in my system is 120GB and Simple back up suite has filled my hard drive with corrupt back up files aswell as a warning window when back up suite tries to run and hard drive low space warning window.

When I try to delete back up files there is a file permissions window telling me I don't have permission.

I have tried to reconfigure Sbackup and  as the schedule tab is greyed out and unavailable I am trying to find a way to deactivate Sbackup and remove all the back up files on the hdd.

How do I deactivate/uninstall Sbackup.?
How do I delete saved back up files.?

Thanks in advance.

---

### Post by coffeecat on 2011-06-30
I have no experience of sbackup/simplebackup, but I have read reports of it doing odd things. To answer your first question, do you have sbackup or simplebackup? Both are listed in Synaptic but they are different apps. Whichever, open Synaptic (in Natty press the Windows/super key and type "syn" and Synaptic will appear in the list of possible apps in the dash). Now search for sbackup (plus sbackup-gtk) or simplebackup, whichever you have, and mark them (right-click) for complete removal. Then click on apply.

As far as your second question is concerned, it sounds as though sbackup has saved its backup files with restrictive permissions and/or ownership. Where are the files stored? Open a terminal and cd to the relevant directory and post the output of this command:

```
ls -la
```

If you need help with the cd-ing bit, post back with details of where the files are. The output will tell us what the permissions are on the files and what to do about them.

---

### Post by Geezanansa on 2011-06-30
Thanks for guidance coffeecat.:KS

:popcorn:
I  read somewhere that Simplebackup and sbackup were the same.  Using  unity to view installed apps I had Simple Back up configuration as well  as other Simple Back up launchers.

Following your advice coffeecat using synaptic search shows two apps sbackup and simplebackup.
Synaptic confirmed sbackup as installed and simple backup not.

After marking installed apps for complete removal and applying synaptic does not indicate sbackup or simplebackup.

Using unity apps button I still have Simple Back up launchers installed!

Update Manager installed a flashplayer update only.

Hope this is making sense!

My  hdd still has lowspace due to the saved backup files. The saved sbackup  files are in my home folder which are viewable through file manager.


I  would welcome a step by step guide on how to cd as i really do not know  code but do appreciate cd means change directory so its a start:razz:  I can open terminal:grin: as well as copy n paste :eek:.


Thanks again.

---

### Post by coffeecat on 2011-06-30
> **Geezanansa said:**
> I  read somewhere that Simplebackup and sbackup were the same.

Clearly not so, considering...

> **Geezanansa said:**
> Synaptic confirmed sbackup as installed and simple backup not.

However...

> **Geezanansa said:**
> After marking installed apps for complete removal and applying synaptic does not indicate sbackup or simplebackup.

Excellent! :)

> **Geezanansa said:**
> Using unity apps button I still have Simple Back up launchers installed!

You mean the launcher icons in the left launcher bar? Simply right-click on the unwanted ones and untick "Keep in Launcher".

> **Geezanansa said:**
> My  hdd still has lowspace due to the saved backup files. The saved sbackup  files are in my home folder which are viewable through file manager.

Do you mean in your home folder itself, or in a sub-folder of home?

If you mean in the actual home folder, open a terminal, and post the output of:

```
ls -la
```

You won't need to cd anywhere. If the backup files are in a sub-folder, you'll need to cd into the sub-folder first, with:

```
cd *name_of_subfolder*
```

Substitute the folder name for *name_of_subfolder*, and don't forget that Linux is case-sensitive, unlike Windows. Once you're "in" the subfolder, simply:

```
ls -la
```

... as before.

If your backup folder structure is more complex than just a single subfolder, post back with details and we'll see what we can do. The 'ls -la' won't do anything beyond telling us what the permissions are on the files. Hopefully, that will tell us why you can't delete them at the moment.

---

### Post by Geezanansa on 2011-06-30
Thank you coffeecat.  You are a :KS.




user@user-desktop:~$ cd 2007-12-07_00.51.35.550873.user-desktop.corrupt
[EMAIL="user@user-desktop:%7E/2007-12-07_00.51.35.550873.user-desktop.corrup"]user@user-desktop:~/2007-12-07_00.51.35.550873.user-desktop.corrup[/EMAIL]t$ ls -la
total 27256452
drwxr-xr-x  2 root  admin        4096 2007-12-07 01:16 .
drwx------ 60 user user       20480 2011-06-30 20:15 ..
-rw-r--r--  1 root  admin          44 2007-12-07 00:51 base
-rw-r--r--  1 root  admin         245 2007-12-07 00:51 excludes
-rw-r--r--  1 root  admin       23419 2007-12-07 00:51 excludes.list
-rw-r--r--  1 root  admin 27910356992 2007-12-07 01:16 files.tar
-rw-r--r--  1 root  admin           6 2007-12-07 00:51 format
-rw-r--r--  1 root  admin          26 2007-12-07 00:51 includes.list
-rw-r--r--  1 root  admin       40667 2007-12-07 00:51 packages
-rw-r--r--  1 root  admin       70003 2007-12-07 01:16 sbackup.2007-12-07_00.51.35.208822.log

There are 14 in all of these .user-desktop.corrupt files all dated differently.

---

### Post by Geezanansa on 2011-06-30
**The simple back up configuration and recovery launchers have gone** from the installed applications list in the applications application.

---

### Post by coffeecat on 2011-06-30
That's interesting and disturbing. Interesting that sbackup has created a folder called "2007-12-07_00.51.35.550873.user-desktop.corrupt". Disturbing that it has created a number of files in your home folder owned by root. Why disturbing? Imho, that's a most appallingly bad piece of program design. Files in one's home folder should be owned by no one but oneself - period.

Anyway - to practicalities. The easiest way of deleting these files is with a root Nautilus, but some care needs to be taken. Open a terminal with:

```
gksu nautilus ~
```

A nautilus (file browser) window will open in your home folder. It will look like an ordinary nautilus folder but it has root privileges. This means that if you accidentally browse into the system, you can delete system files easily - first caution. Take care.

Navigate into the 2007-12-07_00.51.35.550873.user-desktop.corrupt folder and delete anything that you need to. **Second caution**: don't use the delete key alone. This will have the effect of simply transferring the "deleted" files to root's trash which means that you won't free up any space. Use the key combination shift-delete. You will get a yes/no prompt but shift-delete does a proper delete. You can also delete the 2007-12-07_00.51.35.550873.user-desktop.corrupt folder when you are finished inside it.

Are there any other folders associated with sbackup? That's a most curious folder name - ending with "corrupt". It's almost as though the application expected to corrupt everything. Most odd. I wonder if there is another cache of backups elsewhere somewhere within system folders. I'll do a bit of searching and post back if I find anything.

---

### Post by Geezanansa on 2011-06-30
I love ubuntu.  Time to start learning commands..... 
sudo gobbledegook blah_blah -w -t -f aWkward/ComBinationOf/mixedCase/underscores_strokes/and.dots

---

### Post by coffeecat on 2011-06-30
> **Geezanansa said:**
> I love ubuntu.  Time to start learning commands..... 
sudo gobbledegook blah_blah -w -t -f aWkward/ComBinationOf/mixedCase/underscores_strokes/and.dots

Well - if you're referring to the 2007-12-07_00.51.35.550873.user-desktop.corrupt folder name, it sort-of makes sense, although it has a measure of daftness about it. But it makes me wonder what is special about 51 minutes, 35 and a bit seconds after midnight on 7th December 2007. I somehow doubt that was when you first or last ran sbackup, seeing as you are using Natty.

By the way, did you see my last post? You posted only seconds after me and may have missed it.

---

### Post by Geezanansa on 2011-06-30
> That's interesting and disturbing. Interesting that sbackup has created a  folder called "2007-12-07_00.51.35.550873.user-desktop.corrupt".  Disturbing that it has created a number of files in your home folder  owned by root. Why disturbing? Imho, that's a most appallingly bad piece  of program design. Files in one's home folder should be owned by no one  but oneself - period.

I have to admit coffeecat that I can not confirm that the back up program actually created these files.  I only assume that these files were created by the back up program as my hdd ran out of free space.  Possibly me changing configuration settings....
I go get Nautilus...
Thx for help.

---

### Post by Geezanansa on 2011-06-30
> **coffeecat said:**
> Well - if you're referring to the 2007-12-07_00.51.35.550873.user-desktop.corrupt folder name, it sort-of makes sense, although it has a measure of daftness about it. But it makes me wonder what is special about 51 minutes, 35 and a bit seconds after midnight on 7th December 2007. I somehow doubt that was when you first or last ran sbackup, seeing as you are using Natty.

Just to make it stranger I only started using Ubuntu maverick about February or March time (this year) and upgraded just last week to natty!  I only _**ever**_ try back up just this week!

 > By the way, did you see my last post? You posted only seconds after me and may have missed it.Yep working on getting Nautilus... I use terminal;)

:popcorn:

---

### Post by Geezanansa on 2011-06-30
>  	Quote:
 	 	 		 			 				 					Originally Posted by **Geezanansa** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10999162#post10999162") 				
 				[I]I love ubuntu.  Time to start learning commands..... 
sudo gobbledegook blah_blah -w -t -f aWkward/ComBinationOf/mixedCase/underscores_strokes/and.dots[/I]
 			 		 	 	 
I had starting to think all i had to do was either sudo and delete filenames or sudo change permissions filename.  Went looking for tutorials on command lines and easy to see i aint the first to be where i at with having my eyes opened by the huge benefits of using command but daunted by learning code.
That command line on first page of tutorial and summed it up perfect for me.:)


Well - if you're referring to the  2007-12-07_00.51.35.550873.user-desktop.corrupt folder name, it sort-of  makes sense, although it has a measure of daftness about it. But it  makes me wonder what is special about 51 minutes, 35 and a bit seconds  after midnight on 7th December 2007. I somehow doubt that was when you  first or last ran sbackup, seeing as you are using Natty.






> By the way, did you see my last post? You posted only seconds after me and may have missed it.

I posted the message you refer to seconds before your first post mentioning nautilus.  Here is alist of the sub folders 
base
excludes
excludes.list
files.tar
format
includes.list
packages
sbackup.2007-12-07_00.51.35.208822.log

sbackup confirms source but 2000 and when???

I go get nautilus and stop posting for a bit.:p

---

### Post by coffeecat on 2011-06-30
> **Geezanansa said:**
> Here is alist of the sub folders 
base
excludes
excludes.list
files.tar
format
includes.list
packages
sbackup.2007-12-07_00.51.35.208822.log

Yes, I see. Those are sub-folders within the 2007-12-07_00.51.35.550873.user-desktop.corrupt folder. Just use the gksu nautilus browser to delete everything inside each one, remembering to use shift-delete, and you should be OK.

---

### Post by Geezanansa on 2011-06-30
Thx coffeecat my hdd has now 77.5gb freespace (much healthier than 1.8gb!)

I closed nautilus file manager/browser but terminal window still open and get a process still running warning when i try to close terminal.  How do i kill gksu nautilus process from teminal?
I guessed "exit" but no worky.

---

### Post by coffeecat on 2011-06-30
> **Geezanansa said:**
> Thx coffeecat my hdd has now 77.5gb freespace (much healthier than 1.8gb!)

How do i kill gksu nautilus process from teminal?
I guessed "exit" but no worky.

Excellent.

Close the root nautilus window and the prompt should return to the terminal, after which you can close it. I suggest you also reboot. Opening a root nautilus affects the desktop (which is part of nautilus) and there is a theoretical security risk. At least until you have restarted nautilus by rebooting. Logging out and in again may be sufficient, but it takes a couple of minutes only to reboot.

Good luck!

---

### Post by Geezanansa on 2011-06-30
> Close the root nautilus window and the prompt should return to the  terminal, after which you can close it. I suggest you also reboot.

The prompt did not return to terminal after closing root nautilus.  The terminal gave a process still running warning when i tried to close terminal then tried typing "exit" in terminal but no worky... 

I have been having booting probs ie grub crashing, having to log in twice etc etc  All this can be tweaked out as everything gets configured just really enjoying learning how to...

thankyou coffeecat for your time i have now  uninstalled the back up app and have a usable hdd.  What back up app or software do you use on a desktop system? or what would you recommend for backing up system and data files?

---

### Post by coffeecat on 2011-07-01
Backing up personal files I do the old-fashioned way - simple copies to 3 generations of physically separate media. There are various GUI frontends to rsync in the repositories that you could explore - rsync allowing you to copy just the differences.

For backing up systems I use tar, but that necessitates having to be able to restore UUIDs. Many people use clonezilla which can clone whole partitions or systems.

---

### Post by Geezanansa on 2011-07-01
wow coffeecat i just check thread having breakfast and you post one minute ago!!!!!
Your time and effort really is valued and appreciated.  Now I can get on  with ironing out other probs.  Backing up is an important desktop  maintenance/administrative need and loads of info available.  Since  getting my first pc a couple of years ago I have neglected the need for  backing up...  
Just when I think of backing up this image of mountains of floppies/disks looms for some reason..
Thought since trying new os may as well spend time trying to get into good habits.
The hdd in my system is old and small.  I invest in newer and bigger hdd  as well as an external hdd using the old hdd for system back up and the  external for personal.  I just thinking out loud.   Chow for now  meeoww!!!:razz:



Fortuna favet audaci: Fortune favours the brave

:grin:

---

### Post by realzob on 2011-09-13
thanks coffecat!
 i was in the same situation with sbackup and i've learn the holly nautilus here from your post :)

:KS

---

### Post by coffeecat on 2011-09-13
@realzob, welcome to the forum. Don't hesitate to start your own thread if you need help with a problem with Ubuntu. :)

---

### Post by def_mornahan on 2012-02-02
I just wanted to say thank you, too, especially since this type of thing still seems to be a problem with Simple Backups.  Long story short, I set it up yesterday to back up a select few directories with maybe several hundred MB of data, came in this morning, read my e-mail, and shortly thereafter got a warning message that / partition (about 20 GB) was nearly full.  Knowing that it was nowhere close to that yesterday, I was using Nautilus and Disk Analyzer to try to figure out where Simple Backups was bloating up my hard drive, but no luck.

As an aside, does Disk Analyzer not gag mightily when trying to deal with separate partitiona for / and /home?  It seemed unable to comprehend the situation.

Only when I found this thread and YOU, GREAT COFFEECAT, TAUGHT ME THE AWESOME SECRET OF ROOT NAUTILUS, could I track down the 9 GB abscess in /var/backup and exorcise the demon.

FWIW, I found an article on TechRepublic that suggested fwbackups (not in Ubuntu repository) and it seems to work considerably better.  So far.  We'll see how it does with incremental backups this afternoon...

---

