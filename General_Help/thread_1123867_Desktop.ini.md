---
title: "Desktop.ini"
date: 2009-04-12
forum: General Help
---

### Post by Beguiler on 2009-04-12
Once more, I come to where the wise gather, seeking assistance.

In several of my folders, I have a file called 'desktop.ini.' All of these folders refuse to be deleted, as does everything in them. Including the desktop.ini.

I first saw this problem when I moved some stuff that I had backed up from my windows xp days onto my Ubuntu machine. Said 'stuff' is mostly music.

Without losing the files that are with this annoyance, how can I get rid of the desktop.ini files? There was a solution offered to someone else for a similar problem, but the solution provided deletes everything in the folder. And sadly, it won't let me move the files I want out of those folders either. Permission denied, or some such. And even if I could, would that put the problem in other places?

I'd appreciate any input on this issue.

---

### Post by theozzlives on 2009-04-12
That file is used by Windows, not needed in Linux.
```
sudo chown <username> <folder> -R
```
```
sudo chmod 777 <folder> -R
```
Then you should be able to delete it.

---

### Post by Zulu-Zeffir on 2009-04-12
To delete the file:
sudo rm -f desktop.ini
To be able to modify the folders/files see manual pages for chown and chmod.

---

### Post by ad_267 on 2009-04-12
You should be able to change the permissions on the files so that they can be deleted.

It's probably easiest to do this from the terminal with:
```
sudo chown -R $USER:$USER $HOME
sudo chmod -R u+w $HOME
```

---

### Post by mb_webguy on 2009-04-12
If you dual-boot with Windows, those desktop.ini files will be recreated every time you use Windows.  These are Windows folder customization files, that tell Windows how to display a folder.  If a folder doesn't contain a desktop.ini when Windows opens one, and you change the way the folder is viewed, the file is created.

So basically, if you're dual-booting, you'll either have to continuously delete these files -- which will only have the effect of removing any preferences you've made in Windows on how folders are displayed -- or you just live with them.

---

### Post by Beguiler on 2009-04-12
First off, thanks for all the quick replies.

Sadly, none of these have fixed the issue. We'll go through one at a time...

TheOzzLives, I tried yours first. It came back with:
chown: cannot access '<filename>': No such file or directory.

Zulu-Zeffir, nothing happens when I enter that command into the terminal. It simply goes to the next line, and does not remove the file.

Ad_267, yours probably gave the most mystifying response of all. The terminal came back with: chown: cannot access '/home/<my username>/.gvfs': Permission denied.

Perhaps I can still delete it in terminal, with sudo. I'll post how it goes a little later tonight.

---

### Post by Beguiler on 2009-04-12
> **mb_webguy said:**
> If you dual-boot with Windows, those desktop.ini files will be recreated every time you use Windows.  These are Windows folder customization files, that tell Windows how to display a folder.  If a folder doesn't contain a desktop.ini when Windows opens one, and you change the way the folder is viewed, the file is created.

So basically, if you're dual-booting, you'll either have to continuously delete these files -- which will only have the effect of removing any preferences you've made in Windows on how folders are displayed -- or you just live with them.

Nope, no dual boot. Just Ubuntu. But it's good to know that it isn't something more serious.

---

### Post by ad_267 on 2009-04-12
> TheOzzLives, I tried yours first. It came back with:
chown: cannot access '<filename>': No such file or directory.

He expected you to replace <filename> with the name of the file you want to delete.

> Ad_267, yours probably gave the most mystifying response of all. The terminal came back with: chown: cannot access '/home/<my username>/.gvfs': Permission denied.

Yes, that doesn't mean it didn't work, it just means it didn't work on that one directory. You should now have write access to all files and directories in your home directory and should be able to move and delete those desktop.ini files.

---

### Post by Beguiler on 2009-04-12
Well, the first thing I found out is...

I'm an idiot.

Changing directories before inputting commands would probably have been a good idea. *slams head into wall repeatedly.* Anyway, got rid of one of the files. Not sure how many more to go, but it'll take a while.

Thanks again, for all the replies.

---

### Post by Beguiler on 2009-04-12
> **ad_267 said:**
> He expected you to replace <filename> with the name of the file you want to delete.



Yes, that doesn't mean it didn't work, it just means it didn't work on that one directory. You should now have write access to all files and directories in your home directory and should be able to move and delete those desktop.ini files.

You've saved me a lot of time typing with this one. Ad's solution works, and is by far the most time efficient. Words cannot express my appreciation.

---

