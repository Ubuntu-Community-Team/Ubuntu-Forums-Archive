---
title: "Empty Deleted Items button greyed out despite there being items in there"
date: 2008-08-28
forum: Desktop Environments
---

### Post by thomashauk on 2008-08-28
The empty deleted items button in the deleted items folder/wastebasket/trash is greyed out and unclickable.
The menu option is also greyed out and unclickable.

Selecting and deleting the items however works.

Any ideas as to why this might be and how I can fix it?

---

### Post by MyR on 2008-08-29
command line is very powerful; try this:
```
sudo su
cd ~/.local/share/Trash/files
rm example*
```

sudo su swithes to root user.
cd changes the directory to the trash folder.
rm removes the files (with root permission; be *very* careful removing stuff as root)

peace

---

### Post by thomashauk on 2008-08-29
It seems to have fixed itself anyway. I know how the command line works and the only reason it was example* was to just be sure that nothing personal was in there.

---

### Post by sensory on 2009-10-16
I feel bad for reviving this thread, but I've been having the exact same problem. The first time it happened I thought nothing of it and just rebooted. 

Now that it's happened again I thought I'd post and see if any one has any help to give...

Jaunty, by the way.

Thanks in advance for any help!

---

### Post by MyR on 2009-10-17
One way is to use the terminal (applications > accessories > terminal)

Switch to root with this command:
sudo su

Change the working directory to the trash folder with this:
cd ~/.local/share/Trash/files

Delete everything in the folder with this:
rm *

if you have folders in your trash you will need to use
rm -r *


peace

---

### Post by sensory on 2009-10-17
Thanks for the reply but perhaps I should have been more clear. I don't want to empty the recycle bin through the terminal because the button is greyed out. I want to know why the button is greyed out and how I can fix it and stop it from happening again.

For now, I can restart Nautilus and it will fix it, which is fine. It's still a bit weird, though.

Thanks again and sorry for not being more clear.

---

### Post by MyR on 2009-10-17
> **sensory said:**
> Thanks for the reply but perhaps I should have been more clear. I don't want to empty the recycle bin through the terminal because the button is greyed out. I want to know why the button is greyed out and how I can fix it and stop it from happening again.

For now, I can restart Nautilus and it will fix it, which is fine. It's still a bit weird, though.

Thanks again and sorry for not being more clear.

Probably has something to do with what you have in there.

---

