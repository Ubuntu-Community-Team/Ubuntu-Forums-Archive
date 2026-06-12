---
title: "Ipod Read-only"
date: 2005-11-15
forum: Desktop Environments
---

### Post by Jeremiah85 on 2005-11-15
My Ipod mini seems to randomly become read only when I try to write to it, but especially when I attempt to delete from it. Sometimes it works fine and sometimes it will work for a little while then tell me it is read only. Does anybody have an idea of what's wrong and how to fix it. Thanks in advance.

---

### Post by Stambo00 on 2005-11-15
I got the same problem with my i-pod shuffle. The only way that seems to fix it for me is to format it. Unfortunately this is only a temporary fix.

---

### Post by angkor on 2005-11-16
[QUOTE=Jeremiah85]My Ipod mini seems to randomly become read only when I try to write to it, but especially when I attempt to delete from it. Sometimes it works fine and sometimes it will work for a little while then tell me it is read only. Does anybody have an idea of what's wrong and how to fix it. Thanks in advance.[/QUOTE]

Try

```
 dosfsck -a /dev/sda2
```

to check and repair a windows formatted iPod.

It works for me when I'm not able to write to my iPod. I'm thinking of reformatting my iPod with apple's filesystem because FAT seems to get corrupted a lot.

ps. specify the correct path if your iPod isn't on /dev/sda2 as it is in my case.

---

### Post by Jeremiah85 on 2005-11-16
[QUOTE=angkor]Try

```
 dosfsck -a /dev/sda2
```

to check and repair a windows formatted iPod.[/QUOTE]Thanks, This seems to be working wonderfully. 

> 
It works for me when I'm not able to write to my iPod. I'm thinking of reformatting my iPod with apple's filesystem because FAT seems to get corrupted a lot.I wish I could change the filesystem, but I need to be able to transfer files to my school's Windows computers.

---

### Post by freqhack on 2005-11-23
[QUOTE=angkor]Try

```
 dosfsck -a /dev/sda2
```

to check and repair a windows formatted iPod.[/QUOTE]

I'm trying to connect a friends iPod to my laptop with the same problem. Will running the above command on it wipe the files he already has on it, or just try to fix errors so i can mount it?

Thanks

---

### Post by Jeremiah85 on 2005-11-23
[QUOTE=freqhack]I'm trying to connect a friends iPod to my laptop with the same problem. Will running the above command on it wipe the files he already has on it, or just try to fix errors so i can mount it?

Thanks[/QUOTE]It didn't erase any of my files but I am not familiar enough with it to be sure so I would recommend backing up the Ipod first if possible.

---

