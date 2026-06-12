---
title: "Can't remove folder from desktop"
date: 2011-01-31
forum: Desktop Environments
---

### Post by vinnypew on 2011-01-31
Hello, I am trying to move a folder from my desktop to Trash and I keep getting an Error
"Permission denied";)

---

### Post by mattman85 on 2011-01-31
```
gksudo nautilus /home/<yourname>/.Trash
```

then empty your trash :-)

---

### Post by coffeecat on 2011-01-31
> **vinnypew said:**
> Hello, I am trying to move a folder from my desktop to Trash and I keep getting an Error
"Permission denied";)

We need to check the ownership and permissions of the folder you are having trouble with. Open a terminal (Applications > Accessories) and post the output of this command:

```
ls -l Desktop/
```Also which folder is refusing to move? It will be listed in the output.

---

### Post by coffeecat on 2011-01-31
> **mattman85 said:**
> ```
gksudo nautilus /home/<yourname>/.Trash
```then empty your trash :-)

I'm sorry to have to tell you that that's not a good idea for three reasons:

1 - There is no /home/<username>/.Trash. The Trash folder is somewhere among the hidden folders in home, but I'm not going to tell you where. :wink:

2 - It doesn't help with the OP's problem.

3 - If you do manage to navigate to where the files in trash are kept with a root nautilus and delete them, (I presume that is what you are suggesting the OP does) all that happens is that they are moved to root's trash and use up hard drive space. There are too many threads appearing already asking for help because of forgotten stuff in root's trash consuming too much hard drive space.

---

### Post by garvinrick4 on 2011-01-31
+1 with coffeecat find out why you do not have permissions. Aren't you curious to why?

---

### Post by Forlong on 2011-01-31
You are only allowed to delete files you own. There may even be a a little lock icon on the folder indicating that this is not the case.
A graphical alternative to coffeecat's command is right-clicking that folder and having a look at the Permissions tab under Properties.

---

### Post by weedeater64 on 2011-01-31
> **vinnypew said:**
> Hello, I am trying to move a folder from my desktop to Trash and I keep getting an Error
"Permission denied";)

I don't know why we have trash folders :frown:
Or sudo.

#rm file.file

works every time.

---

### Post by vinnypew on 2011-02-01
> **Forlong said:**
> You are only allowed to delete files you own. There may even be a a little lock icon on the folder indicating that this is not the case.
A graphical alternative to coffeecat's command is right-clicking that folder and having a look at the Permissions tab under Properties.

I was trying to install software for my Seagate HD Media Player (using WINE loader). I copied the CD to the Desktop and I still could get it to load. Now there is a Seagate folder on my desktop with a locked padlock on it. I tried the properties tab and didn't work  BUT just thought of something.............Went back into Properties and changed folder access for owner, group and others to "Create and delete files" and it worked Thanks;)

I good thread could be closed

---

### Post by leonardyuri on 2011-02-01
If that's the case then I suspect that your file or folder is already corrupted or it may come from other resource that's why whenever you tried to delete it you always encounter the message not permitted or you do not have permission.

---

