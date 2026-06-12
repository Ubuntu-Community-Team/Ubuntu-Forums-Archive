---
title: "[SOLVED] where and how to get GW on ubuntu 7.04?"
date: 2007-08-28
forum: Gaming &amp; Leisure
---

### Post by RuB3N on 2007-08-28
I just switched over to ubuntu 7.04 and im not really sure how to do anything.

I love to game guild wars and im not sure where to get the download for it and how to get it to run? or what program to run it under?

thank you for your time.

---

### Post by edemark on 2007-08-28
Hi 

this page might help you: [http://ubuntuforums.org/showthread.php?t=283122](http://ubuntuforums.org/showthread.php?t=283122)
Actually it was on the very next page on the forum you wrote your question
get GW --> I have no idea where and how as I do not know the game
get wine --> [www.winehq.org](www.winehq.org) see the get wine menu and follow instructions 
get hte game running --> follow the thread linked abowe 

hope it helps
pd if you check if your question has allready been replied will save you time (you do not have to wait idle for the replies to your question) and save space (i guess on the server running this forum)

---

### Post by cogadh on 2007-08-28
Since you are new to Linux and are probably not very familiar with Wine or how to use it to run Windows games on Linux, you might want to check the "Stuff I've learned about Wine" link in my sig. It contains a ton of basic info on how to properly use Wine.

---

### Post by dorath on 2007-08-28
Hi RuB3N,

You can download the Guild Wars installer [here]("http://www.guildwars.com/support/downloadclient/").

---

### Post by Polygon on 2007-08-29
and then to run the program

```

WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed

```

if that doesnt, work, stick a -dx8 in the command and try again.

---

### Post by RuB3N on 2007-08-29
when i put that in the terminal i get this...


ruben@ruben-desktop:~$ WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed
wine: creating configuration directory '/home/ruben/.wine'...
wine: '/home/ruben/.wine' created successfully.
wine: cannot find 'C:\Program Files\Guild Wars\Gw.exe'


still wont run..

---

### Post by cogadh on 2007-08-29
You have to install the game as if you were installing it in Windows first. Based on the output you posted, that was the first time you ran Wine (the "creating configuration directory..." is a dead giveaway), so you haven't actually run the game's install yet. Run the install like this:
```
wine /path/to/setup.exe
```
Obviously, change the "/path/to/" to the actual path to the install executable.

---

### Post by RuB3N on 2007-08-29
i think you have lost me... sorry...  but if the Guild wars file= gwsetup.zip and that file is in....

places -> computer -> file system -> tmp

how would i get to install it?

what would i put in the terminal or how would i do that?:confused:

---

### Post by Polygon on 2007-08-29
extract the zip file and you should get a file called Gw.exe

just run that file and it should just download the entire game for you

---

### Post by RuB3N on 2007-08-29
when i try to load the exe. it shows this..

Cannot open /home/ruben/GwSetup.exe: No application suitable for automatic installation is available for handling this kind of file.

---

### Post by RuB3N on 2007-08-29
Alright i finally got it!!

Thank you all for all your help!!!:)

---

### Post by koer on 2007-08-30
WOW!!!!! thx a lot !!!! it works !!!! cheers man , long live happy feet!

---

### Post by Polygon on 2007-08-31
> **koer said:**
> WOW!!!!! thx a lot !!!! it works !!!! cheers man , long live happy feet!

lol.... your welcome :D

---

