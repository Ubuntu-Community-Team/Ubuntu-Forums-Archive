---
title: "FOF game dir."
date: 2008-05-19
forum: Gaming &amp; Leisure
---

### Post by element2007123 on 2008-05-19
i want to add some songs to FOF, but i don't know where the game dir. is
help?

---

### Post by ajgreeny on 2008-05-19
Don't know FOF, but the config files where such things are stored my be in ~/.FOF or ~/.fof.  Don't forget linux is case sensitive so you need to get it right.  You may also need to set nautilus to show hidden files so hit Ctrl+H to do that.

If FOF runs under wine look in the ~/.wine folder and you may find what you need there.

---

### Post by element2007123 on 2008-05-20
> **ajgreeny said:**
> Don't know FOF, but the config files where such things are stored my be in ~/.FOF or ~/.fof.  Don't forget linux is case sensitive so you need to get it right.  You may also need to set nautilus to show hidden files so hit Ctrl+H to do that.

If FOF runs under wine look in the ~/.wine folder and you may find what you need there.

:confused:
well it's fretsonfire
but i have no clue what you're talking about haha
imma linux noob

---

### Post by Phenax on 2008-05-20
In Linux, many applications have their own hidden folders inside of your home directory. These hidden folders often contain custom data and configuration files for the programs.

The applications do this so each user can easily have different configuration files and custom data for the same application.

The '~' character represents your home directory - if you type 'cd ~' in a terminal it will bring you to your home directory. ~/Desktop represents /home/yourusername/Desktop which represents your desktop, for example.

What he is saying is, go to your home directory, and enable hidden files (Ctrl+H or through the View -> Show Hidden Files menu). Then look for a folder named .FretsOnFire or .fretsonfire or .fof (Something like that)

---

### Post by Naegling23 on 2008-05-20
its /home/yourusername/.fretsonfire

you can also view hidden files in your home directory.

To add songs, you add them to .fretsonfire/data/songs (I think)

there is a chance that the songs folder will not exist, and you may need to add it.

---

### Post by element2007123 on 2008-05-20
> **Phenax said:**
> In Linux, many applications have their own hidden folders inside of your home directory. These hidden folders often contain custom data and configuration files for the programs.

The applications do this so each user can easily have different configuration files and custom data for the same application.

The '~' character represents your home directory - if you type 'cd ~' in a terminal it will bring you to your home directory. ~/Desktop represents /home/yourusername/Desktop which represents your desktop, for example.

What he is saying is, go to your home directory, and enable hidden files (Ctrl+H or through the View -> Show Hidden Files menu). Then look for a folder named .FretsOnFire or .fretsonfire or .fof (Something like that)
THANK YOU
i got it :)

---

### Post by jnuz on 2008-05-21
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST&f=11&t=20933&st=1240#entry217499](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST&f=11&t=20933&st=1240#entry217499)

head there for newest alarian mod. (2.5)

I've compiled a linux binary. runs pretty well.

---

