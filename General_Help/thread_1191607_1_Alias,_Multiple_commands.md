---
title: "1 Alias, Multiple commands"
date: 2009-06-19
forum: General Help
---

### Post by Tobywuk on 2009-06-19
Hello,

I have an alias names 'backup' which uses rsync to backup my home directory to an external hard drive.  I also want the same command to back up my /etc directory.  

```
alias backup="sudo rsync -avhW --delete /home/user /media/linuxbackup"
```

Is there any way I can make a single alias do multiple commands?

Perhaps this situation would be best suited using a script? I am not that familiar with bash, so If someone could let me know how I would write it with an example I would be great full :)

Thanks

---

### Post by kaibob on 2009-06-19
> **Tobywuk said:**
> Is there any way I can make a single alias do multiple commands?
I'm not familiar with rsync, but you can make an alias execute multiple commands by separating them with a semi-colon. For example,

```
alias example='(echo bob ; echo jane)'
```

You can use two ampersands if you want command 2 to execute only if command 1 completed without error. 

```
alias example='(echo bob && echo jane)'
```

---

### Post by Tobywuk on 2009-06-19
Thanks.

I havent tried it yet, but that should do the job :)

---

