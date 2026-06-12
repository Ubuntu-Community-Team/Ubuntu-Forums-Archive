---
title: "Problem moving files"
date: 2008-12-22
forum: General Help
---

### Post by zurn on 2008-12-22
Hi everyone, I have a script to backup 2 logs files. When I type each line on a command prompt without using the script, the files are moved with the correct filename. But when I move the files using the script, the filenames have ? at the end of it.

Here's the script

I launch the script with sh gin_logbackup.sh

mv /home/vadmin/gin/unlagged/gin.log /home/vadmin/gin/unlagged/logs/`date +%m%d%y`.gin.log
mv /home/vadmin/gin/unlagged/chat.log /home/vadmin/gin/unlagged/logs/`date +%m%d%y`.chat.log

Here are the files once moved

-rw-r--r-- 1 root   root     341310 Dec 21 23:01 122208.chat.log?
-rw-r--r-- 1 root   root    2900178 Dec 21 23:08 122208.gin.log?

Any idea why its adding a "?" at the end

---

### Post by unutbu on 2008-12-22
I'm guessing the problem has to do with DOS-style end of line characters.

To remove the DOS ^M characters, type this:

```
sed -i 's/^M$//g' gin_logbackup.sh
```

Note you have to type Ctrl-v Ctrl-m in place of the ^M.

---

### Post by zurn on 2008-12-22
> **unutbu said:**
> I'm guessing the problem has to do with DOS-style end of line characters.

To remove the DOS ^M characters, type this:

```
sed -i 's/^M$//g' gin_logbackup.sh
```

Note you have to type Ctrl-v Ctrl-m in place of the ^M.

Thanks a lot, that did the trick. It there another way to move files withough having to do this? I mean, is my code wrong?

---

### Post by unutbu on 2008-12-22
Your code looks fine to me.
If the script was written on a Windows machine however, I believe it will save the file with \r\n (carriage return/line feed) at the end of each line, while on a unix machine, the end of line is marked by \n (line feed). 

The problem only occurs when transferring dos files to unix, or vice versa. If you don't want to have to remember that sed command,
there is also a package in the official repos called tofrodos.
The "fromdos" command will convert DOS files to unix format.

---

### Post by zurn on 2008-12-22
> **unutbu said:**
> Your code looks fine to me.
If the script was written on a Windows machine however, I believe it will save the file with \r\n (carriage return/line feed) at the end of each line, while on a unix machine, the end of line is marked by \n (line feed). 

The problem only occurs when transferring dos files to unix, or vice versa. If you don't want to have to remember that sed command,
there is also a package in the official repos called tofrodos.
The "fromdos" command will convert DOS files to unix format.

Well the script was made in linux but I might of copy/pasted the line from a windows box notepad into putty. I'll try to type everything directly from linux next time.

Thanks for the help.

---

