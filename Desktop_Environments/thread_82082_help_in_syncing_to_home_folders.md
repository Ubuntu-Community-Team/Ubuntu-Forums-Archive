---
title: "help in syncing to home folders"
date: 2005-10-25
forum: Desktop Environments
---

### Post by shooterae5 on 2005-10-25
I have Ubuntu running on my laptop and my desktop at work. I'd like to keep the home folders for my user in sync with each other. So I can work on ether machine and run a script at the beginning and end of the day and have all changed files from both machines copied to the other. 

I've set up the desktop to be a nfs server sharing /home/dale and the laptop to mount this share to /net. 

Could someone get me started on a script to sync my /home/dale on the laptop to the mount at /net on the laptop?

Thanks Shooter

---

### Post by SickTwist on 2005-10-25
I'm not 100% positive but it might get messy to try to "sync" both home directories because various programs store preferences and other user data there. For example if you use thunderbird and there is a e-mail that you downloaded on your home computer stored in the thunderbird directory but that same e-mail is not  on your work computer, should the script delete or keep the e-mail-- see what I mean? There are other areas it might get tricky as well (program settings that are specific to hardware that could vary between both locations such as cd burners and the like)

It may be better to create a specific directory in both home folders that is synchronized (e.g. /home/shooter/documents). It would be easier to write a script that only synchronizes that specific directory.

---

### Post by shooterae5 on 2005-10-26
I had thoughts along this line as well. 

Isn't there a way to exclude the .* folders and doc's that program information is stored in?

---

### Post by SickTwist on 2005-10-26
Sure, that would be another solution that basically accomplishes the same thing. The hidden dot files are where the trouble would be. If you avoid synchronizing those that would make things less problematic.

Other ideas:
[LIST]
[*]Store the shared files on a USB drive. That way the files are always in the current state (no need to synchronize) and it could easily be backed up.
[*]Host the common files somewhere on the internet if both home and work have internet access.
[*]Keep the files on your home computer and ssh/sftp into the home machine from work.
[/LIST]

---

### Post by shooterae5 on 2005-10-27
[QUOTE=SickTwist]Sure, that would be another solution that basically accomplishes the same thing. The hidden dot files are where the trouble would be. If you avoid synchronizing those that would make things less problematic.

Other ideas:
[LIST]
[*]Store the shared files on a USB drive. That way the files are always in the current state (no need to synchronize) and it could easily be backed up.
[*]Host the common files somewhere on the internet if both home and work have internet access.
[*]Keep the files on your home computer and ssh/sftp into the home machine from work.
[/LIST][/QUOTE]


These ideas have been considered and discarded for various reasons. 

The desktop machine at work is not on the net. my hole network is the desktop an my laptop. I simply wont a shell script that I can run twice a day that will:

1# exclude all .*** files and folders
2# compare mollification date and copy the newest version to the proper machine 
	(this needs to happen bidirectionally)
3# remove old files that have been deleted
4# copy new file that have been created

The desktop is an nfs server, sharing, /home/dale
The laptop mounts this share to /net.

Is what I'm asking here really that hard to do with a bash script?

---

### Post by shooterae5 on 2005-10-27
I've found a program call "unison" that sounds like it should do what I'm lookin for. I'll post later after having time to test it.


10/28/05
unison works great. installed the unison app and the gtkkinterface and it works great. Read the manual it have some nice features.


Shooter

---

### Post by SickTwist on 2005-10-28
[Unison]("http://www.cis.upenn.edu/~bcpierce/unison/") looks interesting. Thanks for the tip! :)

---

