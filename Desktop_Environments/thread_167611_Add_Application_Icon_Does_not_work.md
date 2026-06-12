---
title: "Add Application Icon Does not work"
date: 2006-04-28
forum: Desktop Environments
---

### Post by JL_COG on 2006-04-28
When i click on application; Add Application an error window opens:

error
Cannot Launch Entry
Failed to execute child process "/home/jlcog/desktop/setup-en.exe"
No such file or directory

Did my installation become corrupted somehow? Can i correct this easily.
All i know about Linux would fit here: ()

Using Breezy Badger

Thanks from a total newb :)

---

### Post by sYs^ on 2006-04-30
Well, linux won't run .exe files that easily, you will have to install an emulator, for example wine:
```
sudo apt-get update
sudo apt-get install wine
```

This will be your command: *wine /home/jlcog/desktop/setup-en.exe*
But probably the file's location is wrong because it even can't find it.

so try ths:
```
sudo updatedb
locate setup-en.exe
```

It'll give you the corrent location of the file.

I hope it'll help.

---

