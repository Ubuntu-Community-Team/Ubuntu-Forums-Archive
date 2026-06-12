---
title: "Cannot delete files"
date: 2010-01-23
forum: Desktop Environments
---

### Post by AmpersUK on 2010-01-23
I am trying to delete a folder with mp3 files in called Opera.

I get the following error message:

[INDENT][INDENT]**Error while deleting.**

Files in the folder "Opera" cannot be handled because you do not have permissions to see them.
[/INDENT][/INDENT]I am using Karmic 9.10 (64-bit version) which was loaded onto a brand new 64-bit computer yesterday.

I have clicked on "show hidden files" but that doesn't do anything.

The folder is on a REV drive.

Failing anything here, I will have to go to a Windows machine and format the drive.

Ampers.

---

### Post by jflaker on 2010-01-23
Open the terminal (APPLICATIONS>ACCESSORIES>TERMINAL) type 
sudo nautilus

Be careful, you can also delete system files as a super user.

---

### Post by ianto` on 2010-01-23
The best option would be to use sudo to delete the files by the looks of your problem.  If you know where the files are stored,  simple do: ```
sudo rm -Rf /media/rev-drive/music/Opera
``` This should fix the issue for you.  You can change the */media/rev-drive/music/Opera* to the correct path to your music directory.  If you need help finding this I'll try my best to explain otherwise I hope this will help you.

---

### Post by howefield on 2010-01-23
> **jflaker said:**
> Open the terminal (APPLICATIONS>ACCESSORIES>TERMINAL) type 
sudo nautilus

Be careful, you can also delete system files as a super user.

Wouldn't you prefer to use gksudo when gaining elevated rights with a graphical application ?

---

### Post by ianto` on 2010-01-23
> **jflaker said:**
> Open the terminal (APPLICATIONS>ACCESSORIES>TERMINAL) type 
sudo nautilus

Be careful, you can also delete system files as a super user.

I highly recommend against opening nautilus in root-mode,  however if you do please type the following:
```
gksudo nautilus
```
sudo nautilus isn't recommended please use gksudo if you are going to do this method.

---

### Post by andrea000 on 2010-01-23
Some way you have the wrong permissions on that folder
open a terminal
Application->accessories->terminal

copy and past this into terminal
> gksu nautilus
Then when ask type your password then find the folder
you want to delete.Do not delete this folder right click
it and go to the bottom were it says properties click
that and then go to the permissions tab and change it to
your user name then after exiting all of that go and delete
the folder

---

