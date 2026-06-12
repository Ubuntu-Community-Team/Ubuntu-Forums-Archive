---
title: "HELP: attempted rsync backup ate my harddrive space"
date: 2009-05-06
forum: General Help
---

### Post by Arcitens on 2009-05-06
Hey folks, I'm in a bind and would really, really appreciate some help.

I'm running 8.04 LTS. After a friend's laptop got stolen and another's died in the middle of writing finals, I decided I wanted to backup my data. So I found this tutorial online: [http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html)

Seemed easy enough so I went ahead and tried to use rsync to backup my data to my external HD. Here is the script I used:

```
#!/bin/bash

sudo rsync -rltDvu --modify-window=1 --progress --delete --delete-excluded --exclude-from=/home/jay/Bash/BackupExclude.txt /home/jay /media/FreeAgent Drive
```

My understanding of that was that it was supposed to copy everything in my home folder, except for directories listed in /Bash/BackupExclude.txt, to my external HD mounted at /media/FreeAgent Drive.

Now I'm guessing that the space in the external harddrive directory messed it up, because it created a new directory /home/jay/Bash/Drive and backed up everything there. My problem:

That used up all my harddrive space. My system monitor literally says I have 0 bytes free. My computer has started to behave very irregularly, I imagine from not have any write room for programs. For example, Firefox doesn't open and even Dillo shuts down after I try to navigate away from the start page so I'm now posting from the 2G Surf eee pc I never use anymore. Also, everything on my main menu has disappeared except for Places and System. The location bookmarks in Nautilus have disappeared, but the original data in my home folder is still there (I think).

Right, so I should get to the problem: Everything in the new /home/jay/Bash/Drive folder was write-protected so I used ```
chmod 777 /home/jay/Bash/Drive/*
``` and then just sent everything to Trash. It looked like almost everything deleted except for a few things, but I'm not sure. There are still files in the Trash that I cannot delete. I tried ```
sudo rm -rf $home/.Trash/*
``` and that didn't work. The thing that worries me the most though is that even though I deleted some of the files from the backup, my system monitor still tells me that I have 0 bytes free. Even after I used ```
sudo apt-get remove ___ 
``` on some programs I won't miss and my terminal said it was freeing up space, system monitor still says 0 bytes free.

I realize I am probably pretty bad at explaining this, but I would really really appreciate some help with getting my harddrive space back. Please let me know if you need any more info to be able to help me. I would really appreciate it. Thank you in advance.

EDIT: My mistake, system monitor tells me I have 207.6MiB Free but 0 bytes Available. The free space increases as I remove programs, but the available space does not.

---

