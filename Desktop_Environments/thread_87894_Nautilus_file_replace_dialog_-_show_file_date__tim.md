---
title: "Nautilus file replace dialog - show file date / time?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by megamania on 2005-11-09
Is there a way to have Nautilus show the date/time of the files in the "file replace" dialog?

I often have to copy files from my pendrive to the computer, and it is tiresome (and dangerous) to have to manually check which files are newer (i.e. have to be copied) and which ones are older (i.e. copying them would overwrite a newer file!) *before* starting the copy process.

Do you have any suggestions? I have been trying to find a solution (google and ubuntuforums), but I'm still stuck...

---

### Post by Skrewdriver on 2005-11-09
I do the same thing when I am copying from USBkey or CD-ROM.
The best way is with the command line and the cp -u command (check the man page for details)
```
cp -Ru /media/cdrom ~/mp3
```
[LIST]
[*]The R option is for recursive copy
[*]The u option is for update
[/LIST]
This command will copy any files in any directory on the cd without overwriting any newer files at the destination. It is also a lot quicker than Nautilus.

Your pendrive should be located somewhere in the /media directory.

---

### Post by megamania on 2005-11-09
thanks for the advice. 

I'll try using it, but it's a workaround because I don't usually copy all of the files in a directory: I usually select 10 or 15 files with the mouse and then do a drag & drop to the destination directory (the structure and location of the files on the pendrive is different from the structure of my /home).

In my opinion it's really weird that Nautilus lacks such an "easy" to implement feature as displaying time and date of a file...

---

