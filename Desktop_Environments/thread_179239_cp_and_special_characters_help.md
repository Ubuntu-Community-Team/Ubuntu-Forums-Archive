---
title: "cp and special characters help"
date: 2006-05-19
forum: Desktop Environments
---

### Post by Subhuman2k on 2006-05-19
I would just like to say firstly, even though this is my first post I have used these forums frequently to look for help with any ubuntu/linux problems and have always found the advice to be excellent :) , so thankyou.

Onto my problem, I am copying some music over from one FAT32 partition to another, it is read only so I am using "sudo cp -r". However any filenames with special characters such as é give me the following error:

```
cp: cannot create regular file `/home/xxxx/music/Tiesto/In Search Of Sunrise 2/0 1 - Ti?sto - Tantrix.mp3': Invalid argument
```
(Where ? should be an é)

Does anyone know how to get around this without having to manually rename all of the offending files?

Thanks in advance.

---

### Post by IYY on 2006-05-19
Either way, you wouldn't have to do anything manually. You could always write a script that'll catch these errors, and automatically rename the files. However, I think it may be possible to keep the special characters as they are. 

Read these two threads:

[http://www.ubuntuforums.org/showthread.php?t=141434](http://www.ubuntuforums.org/showthread.php?t=141434)
[http://www.ubuntuforums.org/showthread.php?t=139154](http://www.ubuntuforums.org/showthread.php?t=139154)

---

