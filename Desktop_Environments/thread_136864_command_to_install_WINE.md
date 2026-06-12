---
title: "command to install WINE"
date: 2006-02-26
forum: Desktop Environments
---

### Post by markcaetano@gmail.com on 2006-02-26
hello i need the terminal command to install wine

---

### Post by bluevoodoo1 on 2006-02-26
You'll want to add....
```

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
```
to your /etc/apt/sources.list

then...

```

sudo apt-get install wine
```

---

### Post by pestilence4hr on 2006-02-26
I have found that Sidenet provides a very quick way to configure wine once you have done the above:  [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

### Post by risp on 2006-02-27
[QUOTE=bluevoodoo1]You'll want to add....
```

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
```
to your /etc/apt/sources.list

then...

```

sudo apt-get install wine
```[/QUOTE]

Between them

```
sudo apt-get update
```

Just to be exact ;)

---

### Post by handy on 2006-02-27
WineTools has it's advantages too! :) 

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by bluevoodoo1 on 2006-02-27
[QUOTE=risp]Between them

```
sudo apt-get update
```

Just to be exact ;)[/QUOTE]


Whoops, you're definitely correct!

---

### Post by mjsoccer1 on 2006-02-27
Just a heads up, lately when installing/updating wine, the sourceforge repositry is rather inconsistent, so you may have to run sudo apt-get update a few times before the package downloads completely.  Also, don't try to use winesetuptk, just do the standard install of wine:

*sudo apt-get install wine*

The two packages conflict, and winesetuptk does not install wine correctly.  Good luck

---

