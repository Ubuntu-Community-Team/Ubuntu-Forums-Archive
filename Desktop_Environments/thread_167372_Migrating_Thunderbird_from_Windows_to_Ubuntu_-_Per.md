---
title: "Migrating Thunderbird from Windows to Ubuntu - Permissions Problem"
date: 2006-04-28
forum: Desktop Environments
---

### Post by likeatim on 2006-04-28
Hello,

I'm fairly new to Ubuntu and so far liking it. I'm a very old Windows user (over 15 years) and everything's a little different, but I like the logical structure of Linux... :D 
However, I'm trying to migrate my Thunderbird Profile (Mail and addresses) but I'm stuck with a permissions problem which might be due to a wrong approach. 
This is what I did:
[LIST=1]
[*]Windows and Ubuntu share the same hdd
[*]I opened Nautilus as root so I could access hda1, where windows is
[*]copied the thunderbird profile from hda1 to my user home dir (not the root home dir)
[*]copying the content of this profile folder to the one in ubuntu (under .mozilla-thunderbird) didn't work because owner of the files is "root" since I copied it in a root session...
[*]so I tried ```
chown -R myusername:myusername /home/myusername/ThunderbirdWinProfile
```
[*]and then ```
chmod -R 644 /home/myusername/ThunderbirdWinProfile
```
[/LIST]
However, still I can't see the relevant files and folders in a normal user session in nautilus and I can't access them with Thunderbird...
what do I do wrong? Is there an easier way?

Thanks in advance for your help,


likeatim

---

### Post by cgjones on 2006-04-28
One possible problem might be that by doing a chmod -R 644, the folders no longer have the correct permissions. I think folders need the execute permission for anyone that needs to access them.

---

### Post by louis_nichols on 2006-04-28
I think you need chmod -R 7xx for stuff to work. Instead of the x's you can put anything, as they are the permissions for other group members and other users. 700 should do just fine, I think.

---

### Post by likeatim on 2006-04-30
[QUOTE=louis_nichols]I think you need chmod -R 7xx for stuff to work. Instead of the x's you can put anything, as they are the permissions for other group members and other users. 700 should do just fine, I think.[/QUOTE]
thanks, that solved my problem!! didn't know about the right permissions.
there is no tool to convert your *settings* from thunderbird to evolution (not your mail), is there? once i have my mail now in ubuntu, i thought about trying out evolution as well....

---

### Post by louis_nichols on 2006-04-30
If there is, I haven't heard of it. Never really cared, actually. I've been using Thunderbird from the start. The only one that works good in Gbome, KDE, Windows etc. ;)

---

