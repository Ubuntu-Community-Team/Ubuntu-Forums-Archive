---
title: "Hardy Memory Question"
date: 2009-03-07
forum: General Help
---

### Post by mlnease on 2009-03-07
Hello,

I noticed recently in Network Monitor that I'm using 29 of 35.6 GB of memory.  I have no videos, and very few music and graphic files.  I'm at a loss to figure out just what is using up all this memory.  I did find a fairly large number of big backup files (for Simple Backup) in /var and deleted the older ones, which helped a bit--but there's still a huge amount of memory unaccounted for.

I believe this problem has been accumulating gradually, so I'm assuming that something is being saved somewhere that I'm unaware of.

Searching in the file system I did find a directory called 'proc' containing 17,770 items, totaling 503.4 MB.  After looking at these I still have no idea what they are or if I need them...

In my home directory I also see quite a few firefox & xulrunner +nobinonly files that appear to be successive versions that I think have appeared after I've installed updates from the 'notification' icon.  Can the older versions be deleted safely?

Can anyone suggest where I might look for the culprits?  Or how to search perhaps by file size, or any other way I might troubleshoot this?  Any advice would be much appreciated.

Thanks in advance.

mike

p.s.  I'm using Ubuntu 8.04, Gnome 2.22.3, Kernel 2.6.24-23-generic, 2800.668 MHz Intel Pentium 4 CPU 2.80GHz; Memory information:
total: 494 MiB
swap total:  1443 MiB
cached:  75 MiB
active:  349 MiB
inactive:  31 MiB

---

### Post by Skripka on 2009-03-07
> **mlnease said:**
> Hello,

I noticed recently in Network Monitor that I'm using 29 of 35.6 GB of memory.  I have no videos, and very few music and graphic files.  I'm at a loss to figure out just what is using up all this memory.  I did find a fairly large number of big backup files (for Simple Backup) in /var and deleted the older ones, which helped a bit--but there's still a huge amount of memory unaccounted for.

I believe this problem has been accumulating gradually, so I'm assuming that something is being saved somewhere that I'm unaware of.

Searching in the file system I did find a directory called 'proc' containing 17,770 items, totaling 503.4 MB.  After looking at these I still have no idea what they are or if I need them...

In my home directory I also see quite a few firefox & xulrunner +nobinonly files that appear to be successive versions that I think have appeared after I've installed updates from the 'notification' icon.  Can the older versions be deleted safely?

Can anyone suggest where I might look for the culprits?  Or how to search perhaps by file size, or any other way I might troubleshoot this?  Any advice would be much appreciated.

Thanks in advance.

mike

p.s.  I'm using Ubuntu 8.04, Gnome 2.22.3, Kernel 2.6.24-23-generic, 2800.668 MHz Intel Pentium 4 CPU 2.80GHz; Memory information:
total: 494 MiB
swap total:  1443 MiB
cached:  75 MiB
active:  349 MiB
inactive:  31 MiB

There's a handy utility in Synaptic called FileLight that graphically displays what is eating up disk space-that should be just the thing for hunting down missing space.

---

### Post by mlnease on 2009-03-07
> **Skripka said:**
> There's a handy utility in Synaptic called FileLight that graphically displays what is eating up disk space-that should be just the thing for hunting down missing space.

Thanks, Skripka--I'll have a look!

---

### Post by mlnease on 2009-03-07
> **Skripka said:**
> There's a handy utility in Synaptic called FileLight that graphically displays what is eating up disk space-that should be just the thing for hunting down missing space.

Thanks again, Skripka--here's a screenshot from Filelight.  Suggest anything to anyone?

mike

---

### Post by Skripka on 2009-03-07
> **mlnease said:**
> Thanks again, Skripka--here's a screenshot from Filelight.  Suggest anything to anyone?

mike

click on the used section of dev/sda1 for a detailed breakdown ;)

---

### Post by mlnease on 2009-03-07
Doh!  I'll get back to you--

---

### Post by dunkar70 on 2009-03-07
Are you concerned about memory or drive space? Your question seems to be about memory, but the suggested solutions are focused on drive space.

Ubuntu will cache information into memory assuming that you may need that information again. The cached info has a low priority, so it should not affect your system performance much unless the cache is dumped to the swap file. You can change the settings to control how much your system uses swap space to increase performance.

The following code is from a script I use to configure ubuntu servers. You can try different settings to see what works best for you. This will change the setting from 60 to 10. Since your system only have about 500MB of RAM, 10 may be too low for you:

# Change the swapiness from the default value of 60 (view current setting with cat /proc/sys/vm/swappiness).
 sudo sed -i s/'vm.swappiness=60'/'vm.swappiness=10'/ /etc/sysctl.conf
 echo '
 # Set the likeliness of the system using the swap file. Range 0-100. Default=60
 vm.swappiness=10' | sudo tee -a /etc/sysctl.conf

---

### Post by mlnease on 2009-03-08
> **dunkar70 said:**
> Are you concerned about memory or drive space? Your question seems to be about memory, but the suggested solutions are focused on drive space.

Ubuntu will cache information into memory assuming that you may need that information again. The cached info has a low priority, so it should not affect your system performance much unless the cache is dumped to the swap file. You can change the settings to control how much your system uses swap space to increase performance.

The following code is from a script I use to configure ubuntu servers. You can try different settings to see what works best for you. This will change the setting from 60 to 10. Since your system only have about 500MB of RAM, 10 may be too low for you:

# Change the swapiness from the default value of 60 (view current setting with cat /proc/sys/vm/swappiness).
 sudo sed -i s/'vm.swappiness=60'/'vm.swappiness=10'/ /etc/sysctl.conf
 echo '
 # Set the likeliness of the system using the swap file. Range 0-100. Default=60
 vm.swappiness=10' | sudo tee -a /etc/sysctl.conf

Hello Dunkar,

Thanks for this!  You are right of course, I have never clearly differentiated between drive space and memory and so have confused the two.  I still don't quite understand the difference but it's a start, eh?

I have experimented with swappiness before (thanks to Tom Adelstein at [http://www.linuxjournal.com/article/8308?page=1](http://www.linuxjournal.com/article/8308?page=1) ).   I think I have it pretty well optimized but may tinker with it a little more.

Meanwhile:  Does it make sense that I'm using 28.9 GB of 35.6GB total drivespace?  (I have no other OS or anything else on this hard drive except Hardy).  Is it something I should be looking at or nothing to worry about?  My main concern is that, as my drivespace usage seems to be on the increase (I think), I might eventually use it all up, then...?

Thanks again for the very helpful advice.

mike

---

### Post by dunkar70 on 2009-03-08
Here's an analogy that might help:
[LIST]
[*]**Hard drive**: Think about a set of file cabinets in your office. You have files in there that are available when needed, but not immediately accessible unless you go to them and get them. 
[*]**Memory**: Think about your desk where you have already retrieved the files and are actively using them.
[*]**Swap space/file**: Think of a drawer or file rack at your desk to store some files if you pull too many to fit on your desk. You are working on more than one file at a time, but your desk is not big enough to show them all at once. You move some files out of the way, but you don't put them back into the file cabinet.
[/LIST]
Does this help?

The amount of hard drive space really depends on what you do. My wife is a photographer, so I store over 300GB of pictures on my computer. If you store music files, the space can get used up quickly as well.

There are a number of things you can do to release space on your system partition. You can add a second hard drive to your system and move your data to the hard drive. I have a second hard drive that is mounted at /home so all of my data is separate from my operating system.

---

### Post by mlnease on 2009-03-08
> **dunkar70 said:**
> Here's an analogy that might help:
[LIST]
[*]**Hard drive**: Think about a set of file cabinets in your office. You have files in there that are available when needed, but not immediately accessible unless you go to them and get them. 
[*]**Memory**: Think about your desk where you have already retrieved the files and are actively using them.
[*]**Swap space/file**: Think of a drawer or file rack at your desk to store some files if you pull too many to fit on your desk. You are working on more than one file at a time, but your desk is not big enough to show them all at once. You move some files out of the way, but you don't put them back into the file cabinet.
[/LIST]
Does this help?

The amount of hard drive space really depends on what you do. My wife is a photographer, so I store over 300GB of pictures on my computer. If you store music files, the space can get used up quickly as well.

There are a number of things you can do to release space on your system partition. You can add a second hard drive to your system and move your data to the hard drive. I have a second hard drive that is mounted at /home so all of my data is separate from my operating system.

Thanks Again, Dunkar,

Yes, this is helpful.  I'll consider your analogy at greater length.  Meanwhile, is there an analogue for drivespace that would fit into this, or is drivespace synonymous with one of its elements?

I do realize that these are fairly elementary questions--I've been using Ubuntu exclusively for nearly three years now but retain much of the mentality of the MSOS user--that is, there's still much behind the GUI that's a mystery to me.  Thanks again for your time and patience.  

mike

---

### Post by CrucifiedEgo on 2009-03-08
i'd say drive space would be the amount of filing cabinets you have.  Whereas the used space is filled with files and folders (get it?) the unused space is empty.  And yeah, if you could pull off a screenshot that would be uber helpful.  Or if you're comfortable at a terminal(or willing to try for us), the output of this would provide a lot of insight as well:
```
du --max-depth=3 | sort -n | tail
```

the 'du' command lists the sizes of every folder in your system up to 3 levels deep, sort... sorts by the file size, and tail only gives us the biggest folders.  You could then copy/paste the output over here.

---

### Post by mlnease on 2009-03-08
> **CrucifiedEgo said:**
> i'd say drive space would be the amount of filing cabinets you have.  Whereas the used space is filled with files and folders (get it?) the unused space is empty.  And yeah, if you could pull off a screenshot that would be uber helpful.  Or if you're comfortable at a terminal(or willing to try for us), the output of this would provide a lot of insight as well:
```
du --max-depth=3 | sort -n | tail
```

the 'du' command lists the sizes of every folder in your system up to 3 levels deep, sort... sorts by the file size, and tail only gives us the biggest folders.  You could then copy/paste the output over here.

Thanks, Cru,

Also for the handy code--I'll hang onto it.  A screenshot of what would be useful?

OK, I think I get it that the drive space is the physical portion of the hard drive where the files, directories and subdirectories reside.  I notice that Sysinfo shows 'cached', 'active' and 'inactive'.  Are these designations pertinent to my problem--assuming I have one?

Here's the terminal output:
mn@mn-desktop:~$ du --max-depth=3 | sort -n | tail
du: cannot read directory `./.dbus': Permission denied
296460	./xulrunner-1.9-1.9.0.7+nobinonly/mozilla
296464	./xulrunner-1.9-1.9.0.7+nobinonly
311016	./linux-2.6.24.2
319832	./midbrowser-0.3.0rc1a
406104	./.wine/drive_c
407576	./.wine
511828	./.mozilla-thunderbird/svvkur1h.default/Mail
519800	./.mozilla-thunderbird/svvkur1h.default
519808	./.mozilla-thunderbird
6202668	.
mn@mn-desktop:~$ 

Thanks again for your time and trouble.

mike

---

### Post by dunkar70 on 2009-03-08
mlnease,

Drive space is the same as the hard drive. You can have used drive space and free drive space. The command CrucifiedEgo provided will help you determine which folders are taking up the most space (used drive space), but you need to run it from the root. The listing you provided looks like you ran it from the default location, which is your home drive. Try this...

> user@computer:~$ cd /
user@computer:/$ sudo du --max-depth=3 | sort -n | tail

---

### Post by mlnease on 2009-03-09
> **dunkar70 said:**
> mlnease,

Drive space is the same as the hard drive. You can have used drive space and free drive space. The command CrucifiedEgo provided will help you determine which folders are taking up the most space (used drive space), but you need to run it from the root. The listing you provided looks like you ran it from the default location, which is your home drive. Try this...

Hi Dunkar,

Thanks, tried it again (via sudo) with this output:
mn@mn-desktop:~$ cd /
mn@mn-desktop:/$ sudo du --max-depth=3 | sort -n | tail
[sudo] password for mn: 
du: cannot access `./home/mn/.gvfs': Permission denied
du: cannot access `./proc/11656/task/11656/fd/3': No such file or directory
du: cannot access `./proc/11656/task/11656/fdinfo/3': No such file or directory
du: cannot access `./proc/11656/fd/3': No such file or directory
du: cannot access `./proc/11656/fdinfo/3': No such file or directory
2353548	./var/backup/2009-03-04_00.00.04.243003.mn-desktop.ful
2353552	./var/backup
2839484	./var
2858568	./usr
6202360	./home/mn
6225512	./home
17392580	./root/.local/share
17392584	./root/.local
17401468	./root
30166212	.

Still doesn't look right, eh?  I tried to change permission for `./home/mn/.gvfs' but couldn't find the file.  Any suggestions?

Thanks again for your time.

mike

p.s.  Thanks for the explanation:  Drive space = hard drive.  Does partition size make any difference to performance?

---

### Post by dunkar70 on 2009-03-09
The last line of output confirms that you are using about 30GB of hard drive space. Your root account has over 17GB in the .local/share folder. I would start there and see why that folder is so large. 

Considering the 2.3GB backup file, I suspect you have a scheduled backup using CRON or ANACRON that has a rotating backup file. CRON may be deleting old backup files as root and storing them in the /root/.local/share/Trash folder, which would not normally be purged when you empty your trash.

---

### Post by mlnease on 2009-03-09
> **dunkar70 said:**
> The last line of output confirms that you are using about 30GB of hard drive space. Your root account has over 17GB in the .local/share folder. I would start there and see why that folder is so large. 

Considering the 2.3GB backup file, I suspect you have a scheduled backup using CRON or ANACRON that has a rotating backup file. CRON may be deleting old backup files as root and storing them in the /root/.local/share/Trash folder, which would not normally be purged when you empty your trash.

Hello Again Dunkar,

Your conclusion should've been obvious to me (doh!).  I'll have a look--if I find anything interesting I'll follow up.

Thanks Again (and a Million) for your time and advice.

mike

---

### Post by mlnease on 2009-03-09
> **dunkar70 said:**
> The last line of output confirms that you are using about 30GB of hard drive space. Your root account has over 17GB in the .local/share folder. I would start there and see why that folder is so large. 

Considering the 2.3GB backup file, I suspect you have a scheduled backup using CRON or ANACRON that has a rotating backup file. CRON may be deleting old backup files as root and storing them in the /root/.local/share/Trash folder, which would not normally be purged when you empty your trash.

Dunkar, Yer a Prince,

16GB of trash in .local/share.  I'd never have known that there was a trash subdirectory there without your help.  This certainly explains why my used memory seems to keep perpetually expanding.  And yes, my Simple Backup does rotate and leave obsolete backup files behind--but I thought only in /var--

THANK YOU.

---

### Post by mlnease on 2009-03-09
> **dunkar70 said:**
> The last line of output confirms that you are using about 30GB of hard drive space. Your root account has over 17GB in the .local/share folder. I would start there and see why that folder is so large. 

Considering the 2.3GB backup file, I suspect you have a scheduled backup using CRON or ANACRON that has a rotating backup file. CRON may be deleting old backup files as root and storing them in the /root/.local/share/Trash folder, which would not normally be purged when you empty your trash.

Almost There,

I've opened gksudo naultilus and tried to delete the trash files--no go.  They vanish for a second then come back with new lock files to replace the just deleted lock files.  How can I get rid of trash in the .local/share folder?

mike

p.s.  I've changed the permissions from admin to root, folder access: create and delete files.  No luck!
p.p.s.  I've tried 'rm -rf ~/.local/share/.Trash/*'(as root)--still no luck.

---

### Post by dunkar70 on 2009-03-10
Glad I could help. Here's a link to a thread on deleting the root trash... 

[http://ubuntuforums.org/showthread.php?t=970708](http://ubuntuforums.org/showthread.php?t=970708)

---

### Post by mlnease on 2009-03-10
> **dunkar70 said:**
> Glad I could help. Here's a link to a thread on deleting the root trash... 

[http://ubuntuforums.org/showthread.php?t=970708](http://ubuntuforums.org/showthread.php?t=970708)
Skripka, Dunkar and CrucifiedEgo,

Done and done.  My used memory's down to 36% (from over 90% originally) and I think my confuser's much happier.  Many, many thanks to the great Ubuntu community.

mike

---

