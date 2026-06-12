---
title: "I did chmod -R  440 /. now i cant do anything!"
date: 2008-06-01
forum: Desktop Environments
---

### Post by AnIdiot on 2008-06-01
Alright.

 First time user of ubuntu. I got linux book, and it did some chmod lessons on my ubuntu. I was just playing with my account (/home/name) but when i restarted, it said .drmc can not find, and something that /home/name does not belong to me either...chmod to 640...I did..nothing worked, I did it few more time- tried to use chmod -R 640 /. as well but that did not work either. Then it said GDM not found. Went back to windows, and looked up that I need to change dir to 700 as well, according to one eo the posts here.
I did..and i changed permission in etc/gdm to =2, and accidently wrote false for some of the value (TCP? or something about being false been default true statement in _...anyway
that did not work...so I did chmod -R a=rwx /. and i was able to now start the ubuntu...but my wifi-radar did not work, and i could not connect to the internet.
I came back here, and found that i need to something like
sudo chmod name /home/name
sudo chgrp name /home/name

So, I went back, but when i did, it said that sudoers need to be 440? for me to do it. I went there, and i checked out sudoers had root=ALL(ALL) so I added
name=ALL(ALL) 
after that I did 440 on the file
...
then, i thought that i should do an -R /. as well, because all my files were 
drwxrwxrwx....
well
after that...
i can not do a single command, it says permission denied
i rebooted, 
but then it is in
(initfram) or something mode...help gave me chmod command
everything is -r--------- only and 
chmod anythinghere /. it says read file only...

nothing work ...how do i fix it? or i think uninstall it, if in fact by some idiotic design a "root" can remove his or her access? That is just dumb. :/,,, please help.

Thank you.

---

### Post by AnIdiot on 2008-06-01
Anyone please?
:confused:

---

### Post by x1a4 on 2008-06-01
Hi,

You're screwed. 

You've messed up permissions for the the root (/) directory, and by using the -R option everything else as well.  You should not have used **[color=red]/[/color][color=green].[/color]** , instead, you should have used **[color=green].[/color][color=red]/[/color]** although changing permission to 440 on your home directory is a bad idea as well. 

All directories in / should be 755 and files 655.  /home/$USER (and subdirectories) should be 760 and files 640 or 650 if you want write permissions.  An exception is /tmp which should be 777.

I suppose that the only way to fix this is to write a script that will recursively change permissions of everything depending on whether or not a file is a directory or not, taking into account executable files like executable binaries and scripts, which, just like directories also need the executable bit set.  

You've got your work cut out for you, that's for sure.  You might want to consider a reinstall.  Good luck.

---

### Post by CameO73 on 2008-06-01
> nothing work ...how do i fix it? or i think uninstall it, if in fact by some idiotic design a "root" can remove his or her access? That is just dumb. :/,,, please help.Well, dumb... You have to realize that **root** really means: all breaks are off. As was said above, doing a chmod 440 on a folder (and its subfolders) is not a good idea, since it makes it read-only (4) for the file owner and the group users, anyone else doesn't have any permissions!

In short:

[LIST]
[*]You're screwed, since you made all files read only ... for everyone! (even root)
[*]A reinstall should fix things ... better make a backup of the files you need
[*]Next time, be cautious with the root account (or sudo)
[*]Read [this article]("http://www.freeos.com/articles/3127/") to get a better understanding of file permissions
[/LIST]
I don't get your reasoning behind:
> 
then, i thought that i should do an -R /. as well, because all my files were 
drwxrwxrwx....
Write and execute (wx) are there for a couple of reasons ... you just found out one of them.

---

