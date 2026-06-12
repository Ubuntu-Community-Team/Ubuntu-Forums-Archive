---
title: "Wine trouble"
date: 2006-01-06
forum: General Help
---

### Post by Minyaliel on 2006-01-06
Wine runs in Kubuntu too, right? I installed this app a long time ago, then couldn't find it (long story) and forgot about it. Today, I really needed it... so I went to the terminal to open it, since it wouldn't show up in the menu. This is what I got:

```
minyaliel@Fenris:~$ wine
Warning: Language 'no_NO' was not recognized, defaulting to English.
Warning: Language 'no_NO' was not recognized, defaulting to English.
Warning: Language 'no_NO' was not recognized, defaulting to English.
Wine 20050725
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
minyaliel@Fenris:~$ wine program
Warning: Language 'no_NO' was not recognized, defaulting to English.
Warning: Language 'no_NO' was not recognized, defaulting to English.
Warning: Language 'no_NO' was not recognized, defaulting to English.
wine: cannot find 'program'
minyaliel@Fenris:~$


```

I re- installed, same thing happened. What am I doing wrong?

---

### Post by LuisC-SM on 2006-01-06
I see nothing wrong.... 
now you must run wine as a normal user in a Terminal (Konsole for Kubuntu). something like this:
$wine your.aplication.to.install.exe

then you must find the "exe" file to run it in $HOME/.wine/drive_c/Program\ Files/the.folder.where.it.is.installed.the."EXE"file.to.runit
Hope this helps, while it is what I did and worked perfectly

Greetings

---

### Post by Minyaliel on 2006-01-06
Aah.... I thought there'd be a graphical interface or something... *blush* lol. Thanks for that one ;)

---

### Post by LuisC-SM on 2006-01-06
LMAO....
No no no... I've never seen a GUI from wine in K/Ubuntu... maybe it exists but have no knowledge about it. I've seen onein Linspire but I prefer the text mode method :D

If any problems should arise.. do not hesitate in posting back... 'll be glad to help a little.

Greetings

---

### Post by Minyaliel on 2006-01-06
Great, I will ;) *laughs*

---

