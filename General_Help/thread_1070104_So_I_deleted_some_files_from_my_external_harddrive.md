---
title: "So I deleted some files from my external harddrive and it didnt free up space..."
date: 2009-02-14
forum: General Help
---

### Post by brakattack on 2009-02-14
So I deleted some files from my external harddrive and they were sent to the recycle bin on my computer. I have tried emptying the recycle bin, it goes through the process but they are still there. Another big problem is these files are still taking up space on my external harddrive. I am a newer user to Ubuntu/Linux if anyone could walk me through removing these and remedying this problem all in very simple terms I would very grateful.

Brak

---

### Post by dcstar on 2009-02-14
> **brakattack said:**
> So I deleted some files from my external harddrive and they were sent to the recycle bin on my computer. I have tried emptying the recycle bin, it goes through the process but they are still there. Another big problem is these files are still taking up space on my external harddrive. I am a newer user to Ubuntu/Linux if anyone could walk me through removing these and remedying this problem all in very simple terms I would very grateful.

Brak

In a terminal:

```
sudo nautilus
```

Do: View-Show hidden files and then navigate to your external drive, find any .Trash folders and delete their contents.

---

### Post by brakattack on 2009-02-15
Thank you David.  You suggestions were helpful, but alas I am having another problem.  I found the .trash folder easy enough, but now when I try to delete the files, it prepares the deletion but then comes back with an error.  I have full access to the files and they are not protected when I open up the folder, but after I try to delete them the padlock appears on the file icons and will not allow me to try again.  I have tried umounting the drive and then trying again but to no avail.  The same thing happens again.  Thanks to anyone who can give me any additional help.

Brak

---

### Post by indeterminate on 2009-02-15
When you delete items from a removable drive, use Shift-Del. Holding shift while you press Delete makes it permanently delete the items; otherwise (with just hitting the delete key) it tries to move them into the .trash folder. It sounds like it's having a hard time moving the .trash folder into itself, which makes sense, I guess. Just use shift-del and you'll be fine.

---

