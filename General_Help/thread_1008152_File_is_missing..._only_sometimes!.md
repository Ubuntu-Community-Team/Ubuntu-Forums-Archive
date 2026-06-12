---
title: "File is missing... only sometimes!"
date: 2008-12-11
forum: General Help
---

### Post by awe on 2008-12-11
Hello,

I have typed a word processor document (Open Office) and saved it in my documents folder. Then I have dragged its icon to a sub-folder in order to store it there. I have selected the "move" option. The document has then disappeared from where it was (OK) but it has never appeared inside the folder where I intended to put it (bad).

The funny thing is that when I go to the console and I use the "locate" command, the file is listed its original location. If I try the "ls" command, then the file cannot be found. When I go there in Dolphin the file is not there. I thought that I had some corruption in the hard disk, so I did "sudo touch /forcefsck", then restarted to have the hard disk automatically checked, but that did no change anything.

Any ideas? The "half-missing" file is a long document and I would not want to retype it all.

Thanks!

---

### Post by wizard10000 on 2008-12-11
> **awe said:**
> Hello,

I have typed a word processor document (Open Office) and saved it in my documents folder. Then I have dragged its icon to a sub-folder in order to store it there. I have selected the "move" option. The document has then disappeared from where it was (OK) but it has never appeared inside the folder where I intended to put it (bad).

The funny thing is that when I go to the console and I use the "locate" command, the file is listed its original location. If I try the "ls" command, then the file cannot be found. When I go there in Dolphin the file is not there. I thought that I had some corruption in the hard disk, so I did "sudo touch /forcefsck", then restarted to have the hard disk automatically checked, but that did no change anything.

Any ideas? The "half-missing" file is a long document and I would not want to retype it all.

Hi - 

Might be good to note that 'locate' gets its database updated as a daily cron job and if the database was updated before the file moved locate's results are gonna be incorrect until the next time the database updates.

If you want to manually update locate, run

```
sudo updatedb
```

and then locate should give you the current location of the file.  The update will take from a few seconds to a couple minutes.

Good luck -

---

### Post by awe on 2008-12-11
Hello,

Wow, I did now know this particularity about the "locate" command. I am very knew to Linux, I did not know this. So...

Problem solved, thank you! I take good note about "locate" updating its database daily only.

---

