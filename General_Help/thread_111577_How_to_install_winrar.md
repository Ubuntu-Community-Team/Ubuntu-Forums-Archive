---
title: "How to install winrar"
date: 2006-01-02
forum: General Help
---

### Post by antubis on 2006-01-02
Hello ubunturs,

I start using Ubuntu but I don`t know a bit. I have a rar with my documents. But when I archived it I was on Windows XP and used the latest version of WinRAR. So, Ubuntu version can`t open it. How can I install WinRAR. I downloaded the file tar.gz from rarlabs.com but ... i`m here ;) And can u tell me, or give me, a article how to install something. 

Thanks!

---

### Post by kingsidy on 2006-01-02
fire up the terminal and type in > sudo apt-get install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar the item would be in the   Applications -> Accessories -> Archive Manager menu. Or when you right click a rar archive you can extract to the desired location

---

### Post by antubis on 2006-01-02
No
The terminal returns: _E: Package rar has no installation candidate_

But I want to know how to install something from my computar if I have the file.

---

### Post by futz on 2006-01-02
[QUOTE=antubis]How can I install WinRAR. I downloaded the file tar.gz from rarlabs.com but ... i`m here ;) And can u tell me, or give me, a article how to install something.[/QUOTE]
Ok, unpack the tar.gz file with the archive manager into a directory where you can find it. It will automatically make a sub-directory called 'rar'.

Start a terminal. Cd to the rar directory. Type this:
```
make
```
and then this:
```
sudo make install
```
I'm going from memory here, but that should do it. After the install, the archive manager will know how to handle rars. Works perfect for me.

---

### Post by antubis on 2006-01-03
I unpacked the rar pack and the directory rar was created. CD the directory rar but when I type make the terminal returns:
_bash: make: command not found_

so ...?

---

### Post by mcduck on 2006-01-03
[QUOTE=antubis]No
The terminal returns: _E: Package rar has no installation candidate_

But I want to know how to install something from my computar if I have the file.[/QUOTE]
I think that rar might be in Universe or Multiverse repository, so enabling those should do the trick. Look at Ubuntu 5.10 starter guide in gnome's help to find more info about that.

And what comes to compiling things, you'll have to 'sudo apt-ge install build-essential' first to get everything needed for compiling

---

### Post by antubis on 2006-01-03
[QUOTE=mcduck]I think that rar might be in Universe or Multiverse repository, so enabling those should do the trick. Look at Ubuntu 5.10 starter guide in gnome's help to find more info about that.

And what comes to compiling things, you'll have to 'sudo apt-ge install build-essential' first to get everything needed for compiling[/QUOTE]

10x man
Universe or Multiverse give me a lots of information so I can handle the problem. I installed "non free unrar", but its fine to men.

10x again.

---

### Post by hondacodonbk on 2008-03-09
I also go to Terminal and type command : sudo apt-get install rar 
It work !

---

### Post by harold4 on 2008-03-09
if you want the GUI like windows has and ark doesn't do it for you, you can install the windows version via WINE.

NOTE: Just for informational purposes ;)

---

