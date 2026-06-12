---
title: "Where are the new programs?"
date: 2005-11-23
forum: Desktop Environments
---

### Post by Burgresso on 2005-11-23
Ola, hello. I was hoping to get advice on where i can find and use vim. I downloaded it via synaptic, and I can't find it anywhere. What do you think? Thanks!

---

### Post by tomwell on 2005-11-23
Just a guess but you might want to restart sometimes you need a restart for the programs to appear in applications.... or i think you could kill gnome and restart it...

Hope it helps but if anyone wants to back me up on that one... 

;o)

Peace 

Tom

---

### Post by Xian on 2005-11-23
[QUOTE=Burgresso]Ola, hello. I was hoping to get advice on where i can find and use vim. I downloaded it via synaptic, and I can't find it anywhere. What do you think? Thanks![/QUOTE]
Open a terminal, then just use the vim command with a text file.
For example,

```
$ sudo vim /etc/hosts
```

---

### Post by SilentCacophony on 2005-11-23
If the package doesn't support adding itself to Gnome's menu (many don't,) then chances are that you'll find the executable in /usr/bin/ and a doc folder in /usr/share/doc. You can manually add menu entries, create lauchers, or run said programs from the terminal.

If you use Synaptic, the easiest way to see the 'what and where' is to highlight the package name, select 'Properties', and check the 'Installed files' tab, after installing a package.

---

### Post by Burgresso on 2005-11-23
Xian, SilentCacophony, your responses have given me valuable insight! Thanks fellas. And tomwell, I tried restarting too, it has worked on some programs. Thanks. :)

---

### Post by tomwell on 2005-11-23
Burgresso,

Thanks for the Unnecessary credit... 

I was just trying to help out while i was waiting for a response on another post...I seem to be hooked on reading about Ubuntu and all things linux...

Am glad you managed to sort your prob out, and i learnt from it too so its a win win situation...

Peace

Tom

---

### Post by Xian on 2005-11-24
Vim is a command line program so that category of packages is not usually going to appear as a menu launcher. You can of course update your menu items with a simple instruction:

```
$ update-menus
```

---

### Post by dbmnk on 2007-06-16
but what file do I want to look for to add to the applications menu?
for example octave have installed files in all kinds of libraries

I installed alot of programs in search for something that could do what i wanted, but i carnt remember them all afterwards 
- idda be nice if there was a common list of installed applications not showing all these weird little thingies that you dont know what is or how to operate - only regular executable applications

---

### Post by dbmnk on 2007-06-16
oh - newer mind - I found a way to list all my apps by installing the debian menu like explained here:
[http://ubuntuforums.org/showthread.php?t=225390](http://ubuntuforums.org/showthread.php?t=225390)

---

### Post by Anonii on 2007-06-16
Well, vim is a terminal application without a GUI so I don't think you will have results with that link. If you want a frontend for vim, install gvim. Also, if you want to open vim in a terminal using a button created with the link you posted, the command you will use should be: **gnome-terminal -e vim**

---

### Post by mcduck on 2007-06-17
> **dbmnk said:**
> but what file do I want to look for to add to the applications menu?
for example octave have installed files in all kinds of libraries

I installed alot of programs in search for something that could do what i wanted, but i carnt remember them all afterwards 
- idda be nice if there was a common list of installed applications not showing all these weird little thingies that you dont know what is or how to operate - only regular executable applications
You can always use 'which' to find out the actual executable of a program. Just open a terminal and run 'which appname' and you get a path to the executable of that program. For example:
```
$ which firefox
/usr/bin/firefox
```
Anyway, almost always the executable file is in /usr/bin

---

