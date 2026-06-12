---
title: "Making a link to folter (to desktop)?"
date: 2005-09-08
forum: Desktop Environments
---

### Post by happogiri on 2005-09-08
Hello,

this might sound a really newbie question (noob that I am) but how can I make a link to folder so that I can see it in my graphical desktop?

I mounted my windows ntfs disks and one fat32 partition (for interactivity :) ) under /media/windows/... and would like to have this /media folder in my desktop. I can't do it from file browser 'ala windows' for some reasons.

---

### Post by heimo on 2005-09-08
This is untested, but you could try to run this on terminal:
 ```
ln -s /media ~/Desktop/media
```

---

### Post by frodon on 2005-09-08
If you want to create an link on your desktop in order to have an icon for your partition use these commands :  ```
cd /home/your_username/Desktop
ln -sf /media/windows/ .
```It will create a symbolic link in the directory where you are (your Desktop folder) and each folder in your Desktop repertory will appear as an icon on your desktop, if you want to delete the symbolic link use the "rm" command.
If the "ln" command return something like you don't have the permission use sudo before the command (sudo ln -sf /media/windows/ .)

---

### Post by happogiri on 2005-09-12
Thanks!

---

