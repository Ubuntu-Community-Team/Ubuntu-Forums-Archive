---
title: "undeletable icons"
date: 2006-08-06
forum: Desktop Environments
---

### Post by n_hall on 2006-08-06
i have three icons i can't delete from trying to get cedega on my sytem. i'm preatty new to linux, so please try to be as clear as possiable. thank you.

---

### Post by Sutekh on 2006-08-06
What are the filenames, and purpose of the icons if you know and where are the icons located on your filesystem?

If you can determine the location, say from the the file browser, for example /home/user/.cedega, then could you open a Terminal window (Applications -> Accessories menu) and then use this command to list the files in the location?  This is of course /home/user/.cedega is where the icons are located.  Sing out if that needs to be clearer.
```
ls -la /home/user/.cedega
```
Paste the results back here.  There could be a permissions problem.

Hope that's clear.

---

### Post by n_hall on 2006-08-07
here's the error i get, i'm preatty sure it's a permission error.

Cannot move "/home/nick/Desktop/bin" to the trash because you do not have permissions to change it or its parent folder.

---

### Post by Sutekh on 2006-08-07
Right on. Before anyone tells you how to remove it, is there anything inside the folder that's important, or do you want to scrap it all?

A permission problem can be easily solved by using **sudo**, which allows you to run a command as the user root (who has total access).

If you are sure that there is nothing in the folder, other than the stuff you want gone, you can use this command to remove the folder. Open a Terminal window (Applications -> Accessories menu) and use the command
```
sudo rm -rf /home/nick/Desktop/bin
``` Then enter your user's password when prompted. The rm command will remove the files, the -r flag will make it recursive (delete all files/folders underneath) and the -f flag will ignore warnings about removing directories that are not empty.

You can also use the rm command to remove the files individaully if you'd prefer, so say
```
sudo rm /home/nick/Desktop/bin/somefile
``` And if you'd rather stay away from the command line, you can run Nautilus, the file browser as root using the following command, entering your password when asked.
```
gksudo nautilus
``` A word of warning, close Nautilus as soon as you are done with the deleting. As Nautilus was opened as root, you will have total access over the filesystem, so to avoid any accidental deletions/mistakes, don't leave it open.

---

### Post by n_hall on 2006-08-07
thank you very much Sutekh, it worked perfectly.

---

### Post by Sutekh on 2006-08-07
Sure no problem!  

Just be careful using the rm -rf command, and running Nautilus as root.

---

