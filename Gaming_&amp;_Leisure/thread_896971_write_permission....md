---
title: "write permission..."
date: 2008-08-21
forum: Gaming &amp; Leisure
---

### Post by Moose187 on 2008-08-21
ok i was told to type in "sudo apt-get install 'game name and version'" and thats what i did 

 but it always says either E: cannot find 'game name' or it says do not have write permission for usr/local/games/game folder/game


i dont have internet and im updating from a disk.... do i need internet?   :mad:

---

### Post by tangibleorange on 2008-08-21
> **Moose187 said:**
> ok i was told to type in "sudo apt-get install 'game name and version'" and thats what i did 

 but it always says either E: cannot find 'game name' or it says do not have write permission for usr/local/games/game folder/game


i dont have internet and im updating from a disk.... do i need internet?   :mad:

i'm confused. what exactly are you trying to do? install a game or update a game?

---

### Post by Moose187 on 2008-08-22
no im trying to install the game but i have been updating my ubuntu from a disk.<i run ubuntu 7.10 cause i cant get 8.04.1 to run properly on my old computer>   

but when i install the game it gives me those error listings  and i tried to set admin on my name but that didnt work... also tried the sudo nautilus to install and it did install but now i cantplay it ....and now i cant uninstall it

---

### Post by tangibleorange on 2008-08-22
ah i see and the game's package is on the CD?

---

### Post by Moose187 on 2008-08-22
> **tangibleorange said:**
> ah i see and the game's package is on the CD?

no i download on to my other pc <windows> but its a linux game that is compatible with ubuntu<i know i googled> i have two dev packages and one run game.

---

### Post by tangibleorange on 2008-08-22
ah ok and you double clicked the packages and installed whilst under 'gksu nautilus' ? did the packages install correctly?

how are you trying to start the game? from an icon on the desktop? do you get any errors when launching it?

---

### Post by Moose187 on 2008-08-22
i got no errors but it wont come up i double click the icon and it  does nothing and it wont let me use the add remve theing cause 'my list is not updated' so i cant remove it ...

---

### Post by tangibleorange on 2008-08-22
> **Moose187 said:**
> i got no errors but it wont come up i double click the icon and it  does nothing and it wont let me use the add remve theing cause 'my list is not updated' so i cant remove it ...

ok. if the icon is on your desktop, could you right click it, select properties, and then in the new window, click the 'launcher' tab. where it says 'command:', what is written?

---

### Post by Moose187 on 2008-08-22
hold on lemme turn on my other comp

---

### Post by Moose187 on 2008-08-22
ok it says 'usr/local/games/quake3/tremulous/tremulous.sh'

---

### Post by tangibleorange on 2008-08-22
> **Moose187 said:**
> ok it says 'usr/local/games/quake3/tremulous/tremulous.sh'

ok lets try the following from a terminal:

```
sudo sh usr/local/games/quake3/tremulous/tremulous.sh
```

and post anything that comes up in the terminal if it doesn't work.

---

### Post by Moose187 on 2008-08-22
Its says error cannot opened usr/local/game/quake3/tremulous/tremulous.sh

that all it really says

---

### Post by tangibleorange on 2008-08-22
sorry that should be:

```
sudo sh /usr/local/games/quake3/tremulous/tremulous.sh
```

and if it still doesn't work, please post the output of:

```
cat /usr/local/games/quake3/tremulous/tremulous.sh
```

---

### Post by Moose187 on 2008-08-22
cat: /usr/local/games/quake3/tremulous/tremulous.sh there is no such file directory.


how do i re install it with admin access<ubuntu itself>

---

### Post by Moose187 on 2008-08-24
ok i tried lots of stuff to get it to work and to get it off of the computer... nothing worked... the only thing that did work is reinstall the ubuntu to get it off of my computer and its still saying that i dont have write permission... do i need to get internet to install stuff on the computer?

---

### Post by DoktorSeven on 2008-08-24
You are, I assume, trying to install Tremulous.  Go to its download page: [http://tremulous.net/files/](http://tremulous.net/files/)

Download: Linux  	tremulous-1.1.0-installer.x86.run

Save it and remember where it's been saved (for Firefox, the default is under Desktop in your home directory.

Open a terminal and use the **cd** command to go to where the file was saved (e.g. **cd ~/Desktop** if it's saved where Firefox defaults to).

Type:
```
sudo bash tremulous-1.1.0-installer.x86.run
```
and enter your password when prompted by sudo.

Hopefully that will get you pointed in the right direction...

---

### Post by Moose187 on 2008-08-25
the big problem is that the comp that has ubuntu doesnt have internet yet.... so im downloading from windows, then using usb device to transfer to desktop, then running...? is this a problem?

also im trying to get the compizconfig-settings-manager_0.7.6-3_i386.deb to work... how do i do that for this one?

---

### Post by Perfect Storm on 2008-08-25
Tremulous guide: [http://gaming.gwos.org/doku.php/guides:64bit:tremulous](http://gaming.gwos.org/doku.php/guides:64bit:tremulous) ignore the first part of installing ia32-libs (only needed if you're on 64-bit system).
No need to install it as admin, only if you're running multiply acounts on your Ubuntu system where every user(s) are playing Tremulous.

---

### Post by Moose187 on 2008-08-25
WHAT ARE THE requirements for tremulous? cause im running a compaq presario with a celeron one processor and 633 mhz and prolly a crappy gfx card....

---

### Post by Perfect Storm on 2008-08-25
Absolutly minimal;

CPU : Pentium II 233 (MHz) Processor
RAM : 64 Megabytes (MB) of RAM
Video Card : 4 Megabyte (MB) Video Card
Modem : 56 kbps Modem

---

### Post by Moose187 on 2008-08-25
so what about the compizconfic settings manager? do u know how i get that on the comp? its all the cool cube stuff!

---

### Post by Moose187 on 2008-08-25
ok it says that i cant unzip it cause its not found...
then when i do the cd command it just says that no command found
and i dont find the .games folder...so i cant do it by hand...

---

### Post by Moose187 on 2008-08-25
ok i got it installed and it gives me no errors when i click on it. but the only problem is that it doesnt come up... i think i did wrong by doing all on the 32mbit part...

---

### Post by Perfect Storm on 2008-08-26
Terminal;

```
cd ~/.Games/tremulous
./tremulous.x86
```

or

```
/home/USERNAME/.Games/tremulous/tremulous.x86
```

---

