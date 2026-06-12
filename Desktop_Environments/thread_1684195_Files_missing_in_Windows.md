---
title: "Files missing in Windows"
date: 2011-02-08
forum: Desktop Environments
---

### Post by flitbee on 2011-02-08
Recently I've started to have a problem:

When I download something on ubuntu, I sometimes copy it over to my mounted Windows drive. When I then reboot into Windows, the files aren't there. They're missing. (It used to work before - now it's strangely stopped). When I log back into Ubuntu, the files are gone again! 

Am I doing anything wrong? :confused:

---

### Post by coffeecat on 2011-02-09
Are you using Vista or windows 7? This comes up occasionally. I can't remember the precise details but this is something to do with Windows not liking writes to its own partition from outside. As a general rule, it is best not to write to a Windows C: partition. If you need to share data between Windows and Ubuntu a much better strategy is to have a separate data partition formatted NTFS.

---

### Post by P4man on 2011-02-09
Make VERY sure you are not hibernating windows. Never mount a drive that has windows on it when its hibernated.

---

### Post by flitbee on 2011-02-09
I'm using the latest update on Win XP. And I'm not writing to C:\. I can't access it since it's hibernated. I usually hibernate Windows and boot into Ubuntu (dual boot). 

And @P4man I'm not writing to the Windows OS drive - I can't since it's hibernated. But do you mean i can't write to other Windows partitions if it's on Hibernate? Is that what you mean?

---

### Post by ramitwadhwa on 2011-07-31
I have created 2 files and put them in a folder in ubuntu 11.04 64bit.  The partition is ntfs and is shared b/w ubuntu and win7. The partition  does not have win7 installed on it;  
win7 
ubuntu and swap
data partition 
are  three seprate partitions of a disk. when i logged in win7 the files and  folder newly created were missing. then i logged back in ubuntu and they  were missing from there to.

---

