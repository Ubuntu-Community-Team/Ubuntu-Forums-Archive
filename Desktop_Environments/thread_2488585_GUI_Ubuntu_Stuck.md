---
title: "GUI Ubuntu Stuck"
date: 2023-07-10
forum: Desktop Environments
---

### Post by maiia on 2023-07-10
My images to this post:
[https://drive.google.com/file/d/1kK-HS5sgD6Z02xAtHoSQHAdLEY06WYk3/view?usp=sharing](https://drive.google.com/file/d/1kK-HS5sgD6Z02xAtHoSQHAdLEY06WYk3/view?usp=sharing)

I deployed several years ago open free software “Dspace 6 repository” ([https://dspace.lyrasis.org/download/](https://dspace.lyrasis.org/download/), [https://wiki.lyrasis.org/display/DSDOC6x/DSpace+6.x+Documentation](https://wiki.lyrasis.org/display/DSDOC6x/DSpace+6.x+Documentation), [https://en.wikipedia.org/wiki/DSpace](https://en.wikipedia.org/wiki/DSpace) ) on Ubuntu 18.04.5 LTS desktop. 
I deployed Dspace repository on http, not on https. I didn't have time to fix https. Now I have problem with my Ubuntu. Maybe It is virus which penetrated through Dspace http or through lack of latest security updates of Ubuntu 18.04 desktop. 
The problem is that GUI Ubuntu stuck (Gnome Ubuntu stuck).
See gnome.jpg
 
Also I can press ctrl+C and see the following text:
See terminal1.jpg, terminal2.jpg

And I can press Alt+F2 and run tty2 where I can see error string “I have no name!@repository”:
See tty2.jpg
 
I read everything in the Internet conserning this problem and I could not resolve this problem. Would you have such possibility to help me? I lack for knowledge to solve my problem. 
I need to avoid the situation when I need to reinstall Ubuntu, because 1.5 years have passed since the last backup of my repository postgres database was made. I can lose lots of users data. And now I can not to make backup because I have the following error: “[archiver (db)] connection to database “dspace” failed: local user with ID 122 does not exists”.
See backup_dspace.jpg
 
 I made screenshots of my journalctl:See journalctl1.jpg - journalctl12.jpg  


And screenshots of /var/log/syslog:
See syslog.jpg


Maybe can you propose me more comfortable decision without Ubuntu reinstallation based on the above screenshots?


I did not lose my home directory. I have access to it. My hard disk is Ok. 
I have test web server with Ubuntu 18.04 Desktop LTS. My problem is not in postgres. In my opinion, my problem is in Ubuntu, which was corrupted by a virus that entered either through the http of my Dspace repository or due to the fact that the latest Ubuntu updates were not installed.

---

### Post by DuckHook on 2023-07-12
Please do not double post. Duplicate of: [https://ubuntuforums.org/showthread.php?t=2488677](https://ubuntuforums.org/showthread.php?t=2488677)

**Thread *closed*.**

---

