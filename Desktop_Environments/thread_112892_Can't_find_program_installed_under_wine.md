---
title: "Can't find program installed under wine"
date: 2006-01-05
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-01-05
Posted some similar post before, but this time it's a bit different:
I installed some program under wine. It's called FinaleNotePad.exe. Installation seems to be OK.
when typing in the terminal:
```
gabriel@ubuntu:~$ wine FinaleNotePad
```
or
```
gabriel@ubuntu:~$ wine FinaleNotePad.exe
```
the terminal states:
```
wine: cannot find 'FinaleNotePad'
```

Now, the program IS there, I can find it in Nautilus.

What's that?

Gabriel

---

### Post by stratotak on 2006-01-05
just go into your  .wine folder..its a hidden file in your home direcotroy..you can see if it you set option to view hiden files in nautilus  view panel..or do what i did..creat a link to wine folder  so theres a icon in your home directory pointing to your wine folder..for me it was..


ln -s  .wine/drive_c   wine               

thaat will creat a folder in home thats a link to wine

my bag..misread post...lol..thought you ment you couldnt find the windows exe...lol..

but still just go to where the exe. is in wine..right click..set it to open with wine and click it..wine should launch it..

---

