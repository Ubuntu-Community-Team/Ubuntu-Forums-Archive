---
title: "Windows command line scrpit equivalent in wine??"
date: 2009-05-12
forum: General Help
---

### Post by IWilltell on 2009-05-12
I have a copy of half life 2 that i'm trying to run with wine, but in wonblows i have to run it with the command line script -game hl2. is there something equivalent to that in ubuntu 9?

---

### Post by mc4man on 2009-05-12
Well you can in a roundabout way, whether there is any use to it I'm not sure (you'd think wine would include a cmd.exe if useful

The short ex. is

Copy a version of cmd.exe to wine's windows folder (I used xp

Go to /usr/bin and copy notepad to your desktop, rename cmd (just plain cmd

Move it back to a bin folder in your path
(( I prefer a bin in home folder, just make a folder named bin in your home dir. and then add to your path ( in terminal go 

PATH=$PATH:~/bin:

export PATH

Any script or executable then placed there can be called just by name from cli

EX.
```
doug@doug-desktop:~$ cmd
CMD Version 1.0
H:\>
H:\>notepad.exe  -< notepad opened
H:\>regedit.exe  <- regedit opened
H:\>explorer.exe   <-wine explorer opened

(opens anything in the windows folder directly

H:\>C:\\Program Files\illustrate\dBpoweramp\MusicConverter.exe <- program opened
H:\>C:\\Program Files\ImgBurn\Imgburn.exe  <-program opened

```

No real use as seen here vs normal opening

Edit: as to your intent I can't try, don't have any windows script/bat files to test

---

