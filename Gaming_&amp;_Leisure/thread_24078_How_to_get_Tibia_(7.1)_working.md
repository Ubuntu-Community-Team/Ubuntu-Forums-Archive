---
title: "How to get Tibia (7.1) working?"
date: 2005-04-05
forum: Gaming &amp; Leisure
---

### Post by coldturkey on 2005-04-05
Hello,
I recently moved away from Windows and found Ubuntu! So far this is the best thing ever, it's fast, easy and really good looking :)
I haven't installed anything except some updates but I think it's time for me to install some games!
So, I thought of installing Tibia - An old and fun games to play with your friends - [www.tibia.com](www.tibia.com)
I downloaded the 7.1 version to accses my friends OTserver ([www.otcommunity.net](www.otcommunity.net))
I open the .tgz file and move the tibia folder to my own folder. Now here is the problem:
How do I play this game on Ubuntu/Linux?
Do I need any drivers, programs except the ones that comes with Ubuntu, if so; Which?
What more do I need to think about when playing games on Ubuntu?

As you might av noticed, am new with Linux, I installed Gentoo but it was too difficult.

So, thanks in advance!
ct

PS. There are no .exe (none that i see) files in the folder. Only .spr and so on!

---

### Post by jdodson on 2005-04-05
[QUOTE=coldturkey]Hello,
I recently moved away from Windows and found Ubuntu! So far this is the best thing ever, it's fast, easy and really good looking :)
I haven't installed anything except some updates but I think it's time for me to install some games!
So, I thought of installing Tibia - An old and fun games to play with your friends - [www.tibia.com](www.tibia.com)
I downloaded the 7.1 version to accses my friends OTserver ([www.otcommunity.net](www.otcommunity.net))
I open the .tgz file and move the tibia folder to my own folder. Now here is the problem:
How do I play this game on Ubuntu/Linux?
Do I need any drivers, programs except the ones that comes with Ubuntu, if so; Which?
What more do I need to think about when playing games on Ubuntu?

As you might av noticed, am new with Linux, I installed Gentoo but it was too difficult.

So, thanks in advance!
ct

PS. There are no .exe (none that i see) files in the folder. Only .spr and so on![/QUOTE]


use synaptic to install the tcl and tk libraries.  then go to a console go to the directory of tibia and type "./tibiawish" to run the program.

---

### Post by coldturkey on 2005-04-05
```
coldturkey@ubuntu:~$ cd /home/coldturkey/tibia
coldturkey@ubuntu:~/tibia$ ./tibiawish
./tibiawish: error while loading shared libraries: libtk8.3.so: cannot open shared object file: No such file or directory
coldturkey@ubuntu:~/tibia$
```

What am I missing? I installed every tcl and tk script i could find..

EDIT: Ok, i installed a few more updates now. I got to the part where tibiwish booted, but its only blank. A new windows open called tibiawish thats blank, nothing else :/

---

### Post by Dromio on 2005-04-06
[QUOTE=coldturkey]```
coldturkey@ubuntu:~$ cd /home/coldturkey/tibia
coldturkey@ubuntu:~/tibia$ ./tibiawish
./tibiawish: error while loading shared libraries: libtk8.3.so: cannot open shared object file: No such file or directory
coldturkey@ubuntu:~/tibia$
```

What am I missing? I installed every tcl and tk script i could find..

EDIT: Ok, i installed a few more updates now. I got to the part where tibiwish booted, but its only blank. A new windows open called tibiawish thats blank, nothing else :/[/QUOTE]

Actually, I got it to run using ./tibia , not ./tibiawish.

But I also found that the 7.4 windows client works under wine.

---

### Post by coldturkey on 2005-04-07
Atm i need 7.1, but thanks for the advice :)

./Tibia worked, but when I connected to the server it lagged and i closed it :( Didnt work.. Whats the problem?

---

### Post by Eric P. on 2005-09-19
[QUOTE=coldturkey]```
coldturkey@ubuntu:~$ cd /home/coldturkey/tibia
coldturkey@ubuntu:~/tibia$ ./tibiawish
./tibiawish: error while loading shared libraries: libtk8.3.so: cannot open shared object file: No such file or directory
coldturkey@ubuntu:~/tibia$
```

What am I missing? I installed every tcl and tk script i could find..

EDIT: Ok, i installed a few more updates now. I got to the part where tibiwish booted, but its only blank. A new windows open called tibiawish thats blank, nothing else :/[/QUOTE]
"./tibiawish: error while loading shared libraries: libtk8.3.so: cannot open shared object file: No such file or directory"
i have the same problem, help us!  :?

---

### Post by krak on 2005-09-20
you can try to download tibia client from [www.tibia.com](www.tibia.com) and run it throught wine.
did work for me :)

add this to ur /etc/apt/sources.list
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
then
apt-get update
apt-get install wine
install Tibia by wine tibia.exe adter installing go wherever u have installed tibia and do wine tibia

---

### Post by eifersucht on 2005-09-23
./tibiawish: error while loading shared libraries: libtk8.3.so: cannot open shared object file: No such file or directory


i got this with tibia75 and i had already installed Tcl/Tk pakages 

help me please
Eifersucht

---

### Post by Eric P. on 2005-09-28
acess violation when trying to run 7.5 under wine. nothing runs on it for me. just splash sceens.

---

### Post by WetWilly on 2005-10-05
tibia windowsclient run under cedega...

worthless game though =(

---

### Post by dabear on 2005-10-05
> 
./tibiawish: error while loading shared libraries: libtk8.3.so: cannot open shared object file: No such file or directory

Isn't it pretty clear what you are missing? sudo apt-get install libtk or something similar..

---

