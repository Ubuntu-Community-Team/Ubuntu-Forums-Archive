---
title: "wine doesn't work..."
date: 2006-01-24
forum: Desktop Environments
---

### Post by lucaflea on 2006-01-24
hi. i finally landed (again to ubuntu). and now i'm happy....

i have a problem: i've installed wine through synaptic but it doesn't work. if i do "ctrl+f2" and then "wine" nothing happens... xwine works, i can load the .exe program file i need (finale) but it doesn't start...maybe because wine doesn't work...
how can i make it work? from my windows partition (ntfs) i only need finale 2006 (or 2005)...

thanx luca

ps: maybe because the programs are in a ntfs partition??

---

### Post by Havoc on 2006-01-24
Well, the Wine version in the repository is *old*.

Try [THIS](http://wine.sourceforge.net/apt/breezy/) repo for the newest version.Either download wine from the web, or add 

```
deb http://wine.sourceforge.net/apt/ binary/
```

to your */etc/apt/sources.list*.

That can be done using the command:

```
sudo gedit /etc/apt/sources.list
```

This will open a gedit window with the contents of /etc/apt/sources.list.
Navigate to the end and in a new line append the code I gave ya!

The second one is a good long-term solution.The update manager will inform you of new versions, when available.

Try that, and see if it works.

---

### Post by Havoc on 2006-01-24
Oh, and write support from Linux to NTFS is not *that* good.Try copying the things you want on your computer. ;)

---

### Post by mostwanted on 2006-01-24
WINE probably doesn't support that program.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Don't expect everything to work in WINE, creating APIs for 3 generations of DOS/Windows apps based on a closed proprietary spec isn't exactly easy.

---

### Post by lucaflea on 2006-01-24
with debian finale 2004 and 2005 worked....

i first tried with the repo i found in winehq but it didn't work....i'll try again later...

thanx for now.luca

---

### Post by Pep864 on 2006-01-24
[QUOTE=Havoc]Well, the Wine version in the repository is *old*.

Try [THIS](http://wine.sourceforge.net/apt/breezy/) repo for the newest version.Either download wine from the web, or add 

```
deb http://wine.sourceforge.net/apt/ binary/
```

to your */etc/apt/sources.list*.

That can be done using the command:

```
sudo gedit /etc/apt/sources.list
```

This will open a gedit window with the contents of /etc/apt/sources.list.
Navigate to the end and in a new line append the code I gave ya!

The second one is a good long-term solution.The update manager will inform you of new versions, when available.

Try that, and see if it works.[/QUOTE]

I too am having problems with wine.  I am new to linux and I have tried following the instructions above to get wine to run but to no avail.  When I open my terminal and type wine, this is what I get

wine client error:19: version mismatch 218/221.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

According to automatix, I have the latest version of wine installed.  
Any help will be greatly appreciated.

Thank you,
Pep

---

### Post by dcstar on 2006-01-24
[QUOTE=Pep864]I too am having problems with wine.  I am new to linux and I have tried following the instructions above to get wine to run but to no avail.  When I open my terminal and type wine, this is what I get

wine client error:19: version mismatch 218/221.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

According to automatix, I have the latest version of wine installed.  
Any help will be greatly appreciated.

Thank you,
Pep[/QUOTE]
Kill any Wine processes using the System Monitor, and try again.

---

