---
title: "Changing permissions in Oneinc 11.10"
date: 2011-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by brevardo on 2011-11-05
I have a Dell Dimension 8400 Desktop. I've just installed by third Ubuntu Operating System. The first two versions of Ubuntu I completely wiped the harddrive clean of Windows XP and installed Lucid LTS.
I'm now trying to change my Nautilus folders by adding a file called bsc-v2.py 
The reason that  want to add this to the nautilus>extensions 3.0 folder is because apparently it's a script in order to allow me to sort my MP3 files by artist name and song name. As you probably know Nautilus is set to default with basic column names such as size, type and Octal permissions. It seems that on my last version of Ubuntu as well as this new one- Oneinc that it doesn't allow me to copy ths bsc-v2.py file into ths folder because it always tells me that I don't have permissions. I'm guessing that  may have had a different user name when initially installed my first Ubuntu Operating system four years ago and this is the reason it doesn't think I'm the same owner? Can someone explain how to either change the permissions so I can copy this file or an easier way to change the list columns in Nautillus? Thanks,   Rich H

---

### Post by lncoll on 2011-11-05
May be you can change folder's owner.
Do this ONLY if the forder is inside your home, elsewhere you can get unexpected problems.
```

sudo chown -R myusername:myusername foldername

```
Of course addapt this to your user name and folder name.
This way the folder and the contents will be yours, again.

---

