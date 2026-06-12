---
title: "help with game sources and extensions"
date: 2013-11-14
forum: Gaming &amp; Leisure
---

### Post by acodea on 2013-11-14
I would like somebody to send me in the right direction for game install files with .deb extension. If not could someone help me with installing .run extensions and other extensions (a list of preferable extensions for Ubuntu) would be appreciated.

My .sources list are as follows:

```
# /etc/apt/sources.list
```


deb [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) precise-updates main restricted universe multiverse
deb-src [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) precise main restricted universe multiverse
deb-src [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) precise-updates main restricted universe multiverse
deb [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) precise-backports main restricted universe multiverse
deb-src [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) precise-backports main restricted universe multiverse
deb [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) precise-security main restricted universe multiverse
deb-src [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) precise-security main restricted universe multiverse
deb [http://archive.ubuntugames.org](http://archive.ubuntugames.org) ubuntugames main
deb-src [http://archive.ubuntugames.org](http://archive.ubuntugames.org) ubuntugames main

---

### Post by oldrocker99 on 2013-11-14
Just open Synaptic and search for "game" and you 'll find hundreds. Seriously. If you don't have synaptic:

sudo apt-get install synaptic

Synaptic is still the best package manager out there, IMHO.

---

### Post by acodea on 2013-11-15
oldrocker99,

I agree with you. Synaptic is the best downloader/installer. I can't find the games I want. 

I don't have the sources.It would be great if Vdrift and the flight sims ever come available on the stock sources
I will be great. 

If anyone has sources for synaptic, please give me them. I am limited in Linux, only been using Ubuntu for a month

---

### Post by snafu006 on 2013-11-15
Her is your answer [http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/) 

> Use the following instructions:
 
[LIST=1]
[*]Install the repository in one of the following ways:

[LIST=1]
[*] Install the [playdeb]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb") package.

[*]Or configure the repository manually:
 Go to System-Administration-Software Sources, Third-Party Software tab, Add:
 deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb games Add the repository GPG key, open a terminal window and type:
 wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
[/LIST]
 
[*] Click the "Install this now" button below the screenshot of the desired game.

[*]**If you are using Kubuntu please check [bug 476853]("https://launchpad.net/bugs/476853").**

[*]**If the game cannot be found, run this command and try again:**
 sudo apt-get update
[*]**If you want to uninstall the PlayDeb repository run this command:**
 sudo apt-get remove playdeb
[/LIST]


---

### Post by sheridanm962 on 2013-11-15
For .run you'll need to do as follows

1. Extract the archive first whichever way you want to
2. CD command to the folder that has the .run file (Example: cd Desktop/packagehere-1.2.3)
3. [FONT=Ubuntu Mono]sudo chmod +x packagehere.run
4. sudo [/FONT][FONT=Ubuntu Mono]./packagehere.run (you can get rid of the sudo part for games I think)
5???
6. PROFIT!!!

Should work.[/FONT]

---

### Post by acodea on 2013-11-15
> **snafu006 said:**
> Her is your answer [http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)


```
[COLOR=#000000]*wget -q -O- *[/COLOR][http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key)[COLOR=#000000]* | sudo _apt-key add_ -*[/COLOR]
```

did you ever get the getdeb-archive key? wont work in apt without it.

@sheridanm962 yeah that'll work.

[http://askubuntu.com/questions/377246/how-do-i-install-this-run-file](http://askubuntu.com/questions/377246/how-do-i-install-this-run-file)

---

