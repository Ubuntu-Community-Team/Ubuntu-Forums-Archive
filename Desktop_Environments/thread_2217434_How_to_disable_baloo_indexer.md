---
title: "How to disable baloo indexer"
date: 2014-04-17
forum: Desktop Environments
---

### Post by juergen-helmers on 2014-04-17
After the update to 14.04 Kubuntu I did notice an executable running constantly using up to 95% of my CPU time that I had never noticed before. The executable was **baloo_file**. Not knowing anything about it, I found out on the internets that this is the new file indexer coming with KDE 4.13 which is replacing nepomuk. First thing I disabled in older KDE installations was nepomuk. I found it not useful, a resource hog slowing down my system to a crawl, and a generator of gigabytes of index files clogging my hard drive. As clever as indexing for better and faster searches might be, I never use it anyways, so I don't want it. In KDE releases < 4.13 you could turn Nepomuk simply off in the System Settings. 

Due to the KDE developers you cannot disable baloo at all. You can suspend it (happens on low battery for laptops...), but the suspend command I found failed on my system with an error:

```
qdbus org.kde.baloo.file /indexer suspend
```

Them KDE devs recommend to add your $HOME directory to the list of directories not being indexed by baloo. I try that and added */home/* and my *$HOME *directory to the list of directories not getting indexed. Unfortunately it would not stop the darn thing. After only one day with KDE 4.13 I had accumulated 1.8 GB of index files in ~/.local/share/baloo.

So here is what I did to get rid of it: 

1. removed all contents in ~/.local/share/baloo 
```
rm -rf ~/.local/share/baloo
```
2. made the directory unwritable for anyone:
```
chmod ugo-w ~/.local/share/baloo
```

3. You can probably stop there, but might end up with crashed executables. So for good measure I created a little script in my $HOME/bin directory which I made executable and did add it to the list of scripts executed on KDE startup:

#!/bin/bash
killall -9 baloo_file_cleaner
killall -9 baloo_file
killall -9 baloo_file_extr
rm -rf ~/.local/share/baloo/*

So far no baloo services and no files in ~/.local/share/baloo.

Cheers
J

---

### Post by rex86 on 2014-04-18
You're lucky. On my PC it generated 14GB of garbage before I found out how to kill this baloo thingy.

p.s. Apparently there is less savage way to kill Baloo.

Open [FONT=courier new]$HOME/.kde4/share/config/baloofilerc [/FONT]and change the option '[FONT=courier new]Indexing-Enabled=true[/FONT]' to '[FONT=courier new]Indexing-Enabled=false[/FONT]'

This should be enough.

---

### Post by buzzingrobot on 2014-04-19
Per this ([http://vhanda.in/blog/2014/04/desktop-search-configuration/](http://vhanda.in/blog/2014/04/desktop-search-configuration/)) post by a Baloo developer, adding /home to the list of excluded directories will disable Baloo.  

Baloo only indexes a user's /home directory.

Any full-text desktop search tool (e.g., Baloo, Recoll, Spotlight in OS X) depends on indexing all files in the target directories.  It will do an initial indexing of those files that may have a temporary impact on performance and will, of course, generate data files whose size will depend on the amount and nature of the files that are indexed.

---

### Post by rowlode on 2014-04-22
Killing baloo, as juergen-helmers suggested, killed my whole KDE session.
So I went with rex86's solution, rebooted and baloo is history.

---

### Post by juergen-helmers on 2014-04-23
@rex86: Cool I will try that! Much easier... ;-)

---

### Post by juergen-helmers on 2014-04-23
> **buzzingrobot said:**
> Per this ([http://vhanda.in/blog/2014/04/desktop-search-configuration/](http://vhanda.in/blog/2014/04/desktop-search-configuration/)) post by a Baloo developer, adding /home to the list of excluded directories will disable Baloo.  

Baloo only indexes a user's /home directory.




I tried adding the $HOME dir to the list of excluded directories. Didn't work...

---

### Post by buzzingrobot on 2014-04-23
I'd guess a reboot or restarting Baloo is necessary before the new configuration is read. (Just to be sure, it would certainly want the absolute path to your home directory, e.g, /home/MyHome, not an environmental variable like $HOME.)

---

### Post by qurk on 2014-04-29
I too discovered my computer was lagging BADLY after updating my kubuntu, and top found me the program baloo_file too as a likely culprit.  I found this thread, and it solved everything, thank you.  My computer feels like it literally runs 100x faster in every way.  KDE booted in about 10 seconds compared to like 2 or 3 minutes with baloo, and my browser is running incredibly fast.  

Also, the file you need to edit is 
$HOME/.kde/share/config/baloofilerc
NOT
$HOME/.kde4/share/config/baloofilerc.  Also I did add my home dir to the systemsettings desktop search.  Logged out of KDE, came back and it was gone.

---

### Post by daniroma on 2014-05-17
I encountered same problem. 
I found baloo_file_extractor hanging and restarting over and over (KGardianSistem) causing high processor usage.
After &#8221;google&#8221; a while, I found that the problem might be indexing large files (like video files, mkv etc.)
So I configure Desktop Search not to search in my Video directory (also dev, media and mnt directory).
baloo finished to index my files and processor usage went back to normal. 

Now I can use the Search tool, very handy to find files in a messy desktop. :)

---

### Post by wd5gnr2 on 2014-05-18
I understand they are going to have a controller out for it soon but for now you might find this useful: [https://github.com/wd5gnr/balooctl](https://github.com/wd5gnr/balooctl)

---

### Post by NapalmHorn on 2015-05-08
KDE button -> System Setting -> workspace -> search -> file search (you can turn it off or exclude directories)
In general, in KDE, don't edit config files, if you can use a gui tool.

---

