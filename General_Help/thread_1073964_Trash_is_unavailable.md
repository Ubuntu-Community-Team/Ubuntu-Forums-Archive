---
title: "Trash is unavailable"
date: 2009-02-18
forum: General Help
---

### Post by barraymian on 2009-02-18
Hi All,

Newbie here. Whenever i try to delete a file i get an msg "Trash is unavailable. Could not move "filename.txt" to the trash" and I am given two options, Cancel and Delete

I am wondering why that is? and how to resolve it.

btw, this is not from the command line. I just selected a file in gui, right click and used the "Move to Trash" options from the menu 

thanks

---

### Post by drs305 on 2009-02-18
In hardy and intrepid, your user trash bin should be located at /home/*[COLOR="DarkRed"]username[/COLOR]*/.local/share/Trash  
Inside should be two folders, *files* and *info*

Do these folders exist? Try opening nautilus and see if it locates them:
```
nautilus ~/.local/share/Trash
```
If that doesn't work, try:
```
gksudo nautilus ~/.local/share/Trash
```

The trash bins should be owned by you and not root, so run this:
```

sudo chown -R *[COLOR="DarkRed"]yourusername[/COLOR]:* /home/*[COLOR="DarkRed"]yourusername[/COLOR]*/.local/Share/Trash

```

These trash folders should be created if they don't exist as soon as you try to delete something. I suspect some type of permission problem but have to admit I haven't seen this problem before.

---

### Post by barraymian on 2009-02-19
thank you for your reply

I realized why it was giving me that msg, but i still don't know the solution

I get that message when i try to delete a file from my other hard drive. I've two drives in my computer and whenever i try to move anything to the trash from the other drive, thats when i get this msg. It works fine if i try to move anything to trash from my main drive where Ubuntu is installed.

any ideas how i can resolve that?

---

### Post by drs305 on 2009-02-21
Look on your second drive and see if you have a .Trash-1000 folder (your user id if it is not 1000). If you have one, check the permissions and make sure you own the folder and subfolders. Root's trash on the second drive may be shown as .Trash-0

---

### Post by barraymian on 2009-02-21
the other drive is an ntfs drive that i used to use when i had windows, and it doesn't have that folder that you mentioned. 

so created a folder called .Trash-myuserid and if i go in the permissions for that folder, its owned by root for some reason even though i am not logged in as root.

I am assuming that my username should be the owner of this folder. Now how do i access this drive from command prompt so i can try the command you mentioned in ur earlier post to gain the ownership of the the folder? The drive is called "New Volume"

thank you

---

### Post by barraymian on 2009-02-23
bump

---

