---
title: "wine"
date: 2007-06-22
forum: Gaming &amp; Leisure
---

### Post by pepsie24 on 2007-06-22
i need to know a sit were i can download the wine so that i can play roller coaster tycoon 1

---

### Post by AndrewRiedi on 2007-06-22
Follow the instructions [here]("http://winehq.org/site/download-deb").

---

### Post by Motoxrdude on 2007-06-22
Go to your top right corner of the screen and go 'Applications>>Accesories>>Terminal.
Then type the command

```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```
and type in your password when it asks for it. NOTE: When you type your password nothing will show up, just type as normal.
Now paste this at the bottom
And paste
```

sudo apt-get update
sudo apt-get install wine

```
Some outputs should go flying by, this is normal.
Then when it is done, pop in your Roller Coaster Tycoon cd. Go to your CD drive and view the files. Locate the 'Setup.exe' or "Autorun.exe' and right click it and select 'Open with Other Application'. Then select 'Use Custom Command' and type 'wine' (all lower case, no parenthesis). Press OK and hopefully it will install and you will be able to play!

Let me know if you need any help.

---

### Post by cogadh on 2007-06-23
You forgot a step, after installing Wine, you need to run "winecfg" to set up your drives, sound driver and graphics options.

---

### Post by UK-Wobbie on 2007-06-23
> **pepsie24 said:**
> i need to know a sit were i can download the wine so that i can play roller coaster tycoon 1

Will Roller Coaster Tycoon 1 or 2 work on wine? And how do i get it to work #-o

---

### Post by hikaricore on 2007-06-23
You might find more info at the Wine Application Database:
[http://appdb.winehq.org/search.php?sSearchQuery=tycoon](http://appdb.winehq.org/search.php?sSearchQuery=tycoon)

---

### Post by bear54 on 2007-06-23
Hello I have been having a problem wine. I used **Automatix** to install wine than did the above directions to try get it to work. I get the following error message
"The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is to be installed
        Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
        Depends: libgcc1 (>= 1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
        Depends: libstdc++6 (>= 4.1.2) but 4.1.1-13ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
        Depends: libxslt1.1 (>= 1.1.20) but 1.1.17-2build1 is to be installed
E: Broken packages"
I am in root when I try to install. I cannot even open wine or get it to function at all. Any help with this problem would be greatly appreciated.
Eric:cool:

---

### Post by hikaricore on 2007-06-23
The general stance of Ubuntu Forums is that we do not recommend scripts such as Automatix.
Given that wine can be installed from the official repos there is no point in using 3rd party scripts.

AKA: When using scripts, exprect breakage.

---

### Post by pepsie24 on 2007-06-23
how do i get more bytes in my game folder. it says that i have zero space left in it but when i go into my file system it says that i have 4.1 bytes in there. the game wont play at all because i belive that there is no bytes left please help me.

---

### Post by hikaricore on 2007-06-23
4.1 bytes is **not** alot of space... how big is your root partition?

It's possible you made your Ubuntu partition too small or something else is taking up way too much space.

---

### Post by bear54 on 2007-06-23
Thank You for the Info. I appreciated it very much.
    Eric8)

---

### Post by pepsie24 on 2007-06-26
> **Motoxrdude said:**
> Go to your top right corner of the screen and go 'Applications>>Accesories>>Terminal.
Then type the command

```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```
and type in your password when it asks for it. NOTE: When you type your password nothing will show up, just type as normal.
Now paste this at the bottom
And paste
```

sudo apt-get update
sudo apt-get install wine

```
Some outputs should go flying by, this is normal.
Then when it is done, pop in your Roller Coaster Tycoon cd. Go to your CD drive and view the files. Locate the 'Setup.exe' or "Autorun.exe' and right click it and select 'Open with Other Application'. Then select 'Use Custom Command' and type 'wine' (all lower case, no parenthesis). Press OK and hopefully it will install and you will be able to play!

Let me know if you need any help.

thanks for all the help. i cant get the game to work for some reason but i appreciate the help thanks

---

### Post by pepsie24 on 2007-06-27
ok ty

---

### Post by nate22 on 2007-06-27
hmm i aget the same as the otehr guy


---------------------
The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.4 is to be installed
        Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
        Depends: libgphoto2-2 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed        Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

---

