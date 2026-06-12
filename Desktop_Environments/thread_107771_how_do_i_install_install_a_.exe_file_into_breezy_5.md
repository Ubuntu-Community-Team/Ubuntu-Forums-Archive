---
title: "how do i install install a *.exe file into breezy 5.10 ?"
date: 2005-12-23
forum: Desktop Environments
---

### Post by bdd4 on 2005-12-23
My system: 1.5GHz Athlon, 1GB ram, 40GB HD.
Inew linux user - i am
Using Unbuntu Breezy 5.10.
How do I install the executable file SwCadiii.exe  ?
thx in advance 

bdd4

---

### Post by siucdude on 2005-12-23
You can't install directly into Linux.  

The only way you can is if get crossover office,  

thanks

---

### Post by fordfan753 on 2005-12-23
[QUOTE=siucdude]You can't install directly into Linux.  

The only way you can is if get crossover office,  

thanks[/QUOTE]

Actually, most exe files are installed in WINE...

Anyway, what does this exe do? I'm sure there's probably a program that does the same thing for linux.

---

### Post by userlain on 2005-12-23
I'm assuming it is a CAD program...

What you are going to need to do is get WINE, so you can run/install Windows executables under Linux.

Lucky for you the process is painless :)


Just type this in a Terminal window: "sudo apt-get install wine"

After that succeeds just change to the directory wherever SwCadiii.exe is and type: "wine SwCadiii.exe"

---

### Post by briancurtin on 2005-12-23
your best bet is to run it in windows

---

### Post by adie273 on 2005-12-24
All options stated here should work,

Running it on windows would be easiet, although it could be run on Wine easy enough. Only problem I find with Wine is that there are a number of programs that it doesn't yet support that Crossover Office does support. But Wine is free to use where as you have to buy Crossover Office. 

(Although there are no doubt most likely some "free" copies of crossover office floating about the internet if you get what I mean lol)

Adie

---

### Post by NewbieNik on 2005-12-24
[QUOTE=adie273]All options stated here should work,

Running it on windows would be easiet, although it could be run on Wine easy enough. Only problem I find with Wine is that there are a number of programs that it doesn't yet support that Crossover Office does support. But Wine is free to use where as you have to buy Crossover Office. 

(Although there are no doubt most likely some "free" copies of crossover office floating about the internet if you get what I mean lol)

Adie[/QUOTE]


NO NO NO NO NO!!!!!!! Don't do this. "free" copies as you so politely call them are taking advantage of peoples talents, time and effort in a community that thrives on peoples respect for the work these people do. If you want to be a pirate, buy a ship. If you want a well-written piece of software that helps you do what you want, spend some of your cash!!!

---

### Post by adie273 on 2005-12-24
[QUOTE=NewbieNik]NO NO NO NO NO!!!!!!! Don't do this. "free" copies as you so politely call them are taking advantage of peoples talents, time and effort in a community that thrives on peoples respect for the work these people do. If you want to be a pirate, buy a ship. If you want a well-written piece of software that helps you do what you want, spend some of your cash!!![/QUOTE]

Don't get me wrong, i'm not condoning using pirate copies, I myself use Wine for that reason. I'm just stating the fact that it does happen. The same with Windows pirate copies.

---

### Post by anil_robo on 2005-12-25
Try installing windows inside Ubuntu [(see my screenshots)]("http://www.ubuntuforums.org/showthread.php?p=600989#post600989")

---

### Post by Razman on 2005-12-31
Just curious, while poking around the Crossover website, is it not free... if they provide you the source? (please excuse my ignorance on this subject)

[http://www.codeweavers.com/products/source/](http://www.codeweavers.com/products/source/)

Is the website I am talking about.

---

### Post by Rhizome21 on 2005-12-31
[QUOTE=anil_robo]Try installing windows inside Ubuntu [(see my screenshots)]("http://www.ubuntuforums.org/showthread.php?p=600989#post600989")[/QUOTE]

how do you do that? :o

---

### Post by briancurtin on 2005-12-31
[QUOTE=NewbieNik]NO NO NO NO NO!!!!!!! Don't do this. "free" copies as you so politely call them are taking advantage of peoples talents, time and effort in a community that thrives on peoples respect for the work these people do. If you want to be a pirate, buy a ship. If you want a well-written piece of software that helps you do what you want, spend some of your cash!!![/QUOTE]
that made no sense. dont use free as in beer software because it takes advantage of peoples talents? im pretty sure no one would work on the wine project if they thought the application was being used to take advantage of them. they are not slaves. welcome to gnu/linux by the way.

---

### Post by briancurtin on 2005-12-31
[QUOTE=Razman]Just curious, while poking around the Crossover website, is it not free... if they provide you the source? (please excuse my ignorance on this subject)

[http://www.codeweavers.com/products/source/](http://www.codeweavers.com/products/source/)

Is the website I am talking about.[/QUOTE]
ive never messed with or looked at crossover, but there are two types of meanings to the word free in reference to software

1. free as in freedom: you are free to access the source code, and do whatever you want with it
2. free as in beer: you receive the software free of charge

1 and 2 do not have to happen in the same application though. you can have a free as in beer program (no cost) that is not free as in freedom (no source provided).

---

### Post by Galoot on 2006-01-01
[QUOTE=briancurtin]that made no sense. dont use free as in beer software because it takes advantage of peoples talents? im pretty sure no one would work on the wine project if they thought the application was being used to take advantage of them. they are not slaves. welcome to gnu/linux by the way.[/QUOTE]Made sense to me. CrossOver Office is a commercial product.

---

### Post by briancurtin on 2006-01-01
[QUOTE=Galoot]Made sense to me. CrossOver Office is a commercial product.[/QUOTE]
alright yeah i missed part of that quoted text, therefore my statements are off. apologies for that

---

### Post by Iandefor on 2006-01-01
[quote=briancurtin]ive never messed with or looked at crossover, but there are two types of meanings to the word free in reference to software

1. free as in freedom: you are free to access the source code, and do whatever you want with it
2. free as in beer: you receive the software free of charge

1 and 2 do not have to happen in the same application though. you can have a free as in beer program (no cost) that is not free as in freedom (no source provided).[/quote] You can also have a free (speech) program that is not free (beer). Codeweavers can technically charge you for the software, in compiled form, even if it's released under the GPL. However, they are obligated under the terms of the GPL to release the source. The thing is, someone who has a bit of GPL'ed code can make any kind of changes to the software that s/he likes, release their new version, or even redistribute the original version freely. Therefore, you can download and compile the source to Crossover Office without reprimand. Heck, you can even redistribute it and they won't do anything. Crossover makes it's money by providing the software in a prepackaged format, which the end user doesn't have to compile, as well as official support and documentation.

Also: Google shows that Switcher CAD III is an ECAD application. My suggestion is to try running it under WINE, and if that doesn't work, you might possibly give Crossover a go. Failing the above two, you could work out how to make your computer dual-boot Windows and Ubuntu :-D.

---

### Post by briancurtin on 2006-01-01
[QUOTE=Iandefor]You can also have a free (speech) program that is not free (beer).[/QUOTE]
yeah i left combo out to keep the free, speech, and beer usage to a minimum and avoid too much confusion haha.

---

### Post by sunny_nwho on 2006-01-01
I have crossover office pro 5 if anyone needs it i can share after all linux is free ;)

---

### Post by bdd4 on 2006-01-02
hi,
sorry for my belated thanks for your reply.
i did this and wine says it can't find swcadii.exe which
downloaded to desktop. i also copied it into my /home
same problem. 
what next ?

---

### Post by mcduck on 2006-01-02
[QUOTE=bdd4]hi,
sorry for my belated thanks for your reply.
i did this and wine says it can't find swcadii.exe which
downloaded to desktop. i also copied it into my /home
same problem. 
what next ?[/QUOTE]
you'll have to change directory to desktop first. do 'cd ~/Desktop' ;) Also, linux is case sensitive, so make sure you type the file's name right. After typing some letters you can push Tab to autocomplete the name.

---

### Post by GrumpyBob on 2006-01-02
[QUOTE=Rhizome21]how do you do that? :o[/QUOTE]


Having tried Wine on a few occasions, I would suggest the following:

1.  Try installing Windows in the qemu emulator.  Qemu is available from the repos, but there is a more up to date version from the qemu website ([http://fabrice.bellard.free.fr/qemu/)](http://fabrice.bellard.free.fr/qemu/)).  I downloaded the binary distribution.  USB support is still rudimentary.

edit: there's a very long thread about qemu on these forums if you take a look.

2.  Win4lin Pro is a commercial version of qemu, or something like that.  Win4Lin9x is for Win95, 98, Me.  I use the predecessor, Win4lin 5.1.  This is proprietary, costs money, and unlike qemu and Win4Lin Pro requires a pateched kernel, which is a bit of a pain.

3.  Crossover Office - a commercial implementation of Wine.  Not too expensive, and there is a trial you can download.  In my experience, it's easier than wine.

Robert

---

### Post by bdd4 on 2006-01-02
thx
wine complained:

bp@bphostname:~$ cd winapps
bp@bphostname:~/winapps$ ls -l
total 5596
-rwxrwxrwx  1 bp bp 5718016 2005-12-22 09:40 swcadiii.exe
bp@bphostname:~/winapps$ wine switchercadiii.exe
wine: cannot find 'switchercadiii.exe'
bp@bphostname:~/winapps$ ls -l

some wine binary files failed to download. maybe thisis my problem ?

bdd4

---

### Post by varunus on 2006-01-02
```

bp@bphostname:~/winapps$ ls -l
total 5596
-rwxrwxrwx 1 bp bp 5718016 2005-12-22 09:40 swcadiii.exe
bp@bphostname:~/winapps$ wine switchercadiii.exe
wine: cannot find 'switchercadiii.exe'
```

Umm...shouldn't you have ran "wine swcadiii.exe" instead of switchercadiii.exe?

---

### Post by hericus on 2006-01-02
Well first things first you have several options. I'd advise you to either use qemu or vmware so as to run windows on *nix. Wine isn't generally compatible with all files. You'd also be better off making a partition and running windows on that. Depending on your HD space. You're best bet, would be making a partition however, qemu & VMware takes up a slight bit of RAM.

---

### Post by bdd4 on 2006-01-02
hi,
thank you for your reply. you are in nigeria ? i'm in usa.
is that your picture by your post ?

bye for now 
bdd4

---

