---
title: "Backing-Up To USB HDD Won't Work"
date: 2006-03-22
forum: Desktop Environments
---

### Post by Admiral Valdemar on 2006-03-22
I've been fiddling around with trying to back-up my whole Ubuntu installation as per the How To on this board, but I run into a problem when trying to cd to the directory. Even as root, I get the usual bash message saying no such file or directory exists. Yet, the USB HDD is mounted (it's FAT32 and I can move data to and from it via Nautilus easily), so it's not as if Ubuntu doesn't acknowledge the drive is there, only as console, I cannot change to that drive to initiate a back-up. 

Ordinarily, I'd just back-up on my main disk, but since there's not enough room to do that, I'm SOL.

Any help would be appreciated, though I suspect it's something glaringly obvious I overlooked.

---

### Post by Mustard on 2006-03-22
The most obvious answer is that what you are typing in is not the correct syntax.  Perhaps you could show what command you are typing in.

---

### Post by Admiral Valdemar on 2006-03-22
Well, I'm copying the location from the location bar in Nautilus (CTRL+L), even tried it with a folder I made on the drive manually, but still no luck. It will cd to any other directory or folder on my main drive though.

---

### Post by Mustard on 2006-03-22
[QUOTE=Admiral Valdemar]Well, I'm copying the location from the location bar in Nautilus (CTRL+L), even tried it with a folder I made on the drive manually, but still no luck. It will cd to any other directory or folder on my main drive though.[/QUOTE]

What is the command you are entering though, the literal command....

---

### Post by Admiral Valdemar on 2006-03-22
[QUOTE=Mustard]What is the command you are entering though, the literal command....[/QUOTE]

```
nick@ubuntu:~$ su
Password:
root@ubuntu:/home/nick# cd /media/USB HDD
bash: cd: /media/USB: No such file or directory
root@ubuntu:/home/nick#

```

Syntax and spelling is correct, but no recognition of switching to that drive. Does the exact same thing if I try to get to /media/USB HDD/Backup, a folder I just created.

---

### Post by Mustard on 2006-03-22
[QUOTE=Admiral Valdemar]```
nick@ubuntu:~$ su
Password:
root@ubuntu:/home/nick# cd /media/USB HDD
bash: cd: /media/USB: No such file or directory
root@ubuntu:/home/nick#

```

Syntax and spelling is correct, but no recognition of switching to that drive. Does the exact same thing if I try to get to /media/USB HDD/Backup, a folder I just created.[/QUOTE]

Ah ok, I was suspecting this was the case.  You have a space in the middle.

Try this...
```
cd /media/USB\ HDD/
```

To get to the folder Backup try this..

```
cd /media/USB\ HDD/Backup/
```

If you want to avoid this awkwardness in command line path names, avoid putting spaces in your folder names.

---

### Post by Ramses de Norre on 2006-03-22
The shell can't handle a space that way, I think you need to type cd /media/USB\ HDD, the easiest way is to just type cd /media/U [tab] and it will complete the name correct automaticaly.

---

### Post by Admiral Valdemar on 2006-03-22
Gah! I knew there was something insanely simple I was overlooking. Thanks, I may as well change the name to USB-HDD instead or something to avoid this in future. I thought I'd been using the wrong spelling at first.

---

### Post by Mustard on 2006-03-22
[QUOTE=Admiral Valdemar]Gah! I knew there was something insanely simple I was overlooking. Thanks, I may as well change the name to USB-HDD instead or something to avoid this in future. I thought I'd been using the wrong spelling at first.[/QUOTE]

I've been in the same place with this issue. :)  I was mucking around trying to cd to a directory in my .wine folder in the 'Programs Files' folder.  It had me scratching my head for a looong time. :D

Autocompletion with the TAB key saved the day for me, as suggested above.  Just type the first few letters in and then hit the TAB key.

---

### Post by Admiral Valdemar on 2006-03-22
Guess I can live with the TAB idea instead. I forget how to rename an external drive anyway. :p

---

