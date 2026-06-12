---
title: "How to delete file in this hidden folder?"
date: 2012-10-17
forum: Desktop Environments
---

### Post by mirchichamu on 2012-10-17
Recently I was told by my software update center to update my  Linux to the latest version 12.o4..This took me a long time to update..very painful and I am not happy with this version... previously I was running ultimate edition based on Ubuntu...now everything gone...
But my question at this time is that I am having a hidden folder in my storage partition which is shared with windows which is labelled as .trash...I can open the files inside but I cannot delete anything...It has taken a lot of space...19 GB...when I right click the files, everything like move  or move to trash are grayed out...how can I solve this problem?

---

### Post by cherva on 2012-10-17
Open a terminal and try ```
sudo rm -rf /path/to/folder 
```
You will be asked for your password (as you type it it won't be visable)

---

### Post by PowerBarry43 on 2012-10-17
can you not just empty the trash or does that not work for you?

Barry

---

### Post by mirchichamu on 2012-10-17
> **PowerBarry43 said:**
> can you not just empty the trash or does that not work for you?

Barry

Thanks for your reply...I can open the trash as usual and empty it..this is another hidden folder  among the folders in my Storage partition..

---

### Post by Trumusiate on 2012-10-17
Hello,

could you post an **ls -la ** output just to check file and directory details and permissions?

---

### Post by mirchichamu on 2012-10-17
> **cherva said:**
> Open a terminal and try ```
sudo rm -rf /path/to/folder 
```
You will be asked for your password (as you type it it won't be visable)

Thanks for being with me...I wrote the above in terminal but nothing happened..Can you explain in detail? Thanks

---

### Post by cherva on 2012-10-17
> **mirchichamu said:**
> Thanks for being with me...I wrote the above in terminal but nothing happened..Can you explain in detail? Thanks

Did you used /path/to/folder or your path to the right foler mate :)
sudo <- execute command as root (not exactly but for you it will do ok)
rm -rf <- remove a directory and anything in it 
/path/to/folder <- you will have to substitute this with the path to the folder you want to delete. For example if you want to delete /media/storage/.trash .... you use the command
sudo rm -rf /media/storage/.trash 
:)

---

### Post by mirchichamu on 2012-10-17
OK brothers, I found it...It was actually a window folder, that's why I couldn't delete it..when I went through windows, I opted to show the hidden files and folders..I found it and able to delete the files inside..
Thanks once again for being with me.

---

