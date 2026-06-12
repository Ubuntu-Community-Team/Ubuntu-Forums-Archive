---
title: "conky wont load"
date: 2010-04-23
forum: Desktop Environments
---

### Post by andru183 on 2010-04-23
when i try to run conky

Conky: can't open '/sys/class/hwmon/hwmon2/temp1_input': No such file or directory
please check your device or remove this var from Conky

is all i get and i dont know how to remove this var from conky,
this all happened because i tried to install a conky file i found in gnome eyecandy site

---

### Post by stinkeye on 2010-04-23
Look in your home folder for a file named .conkyrc (control + h to show hidden files)
If you run conky in the terminal it will load this file.

If you have no .conkyrc file, running conky in terminal will open
/etc/conky/conky.conf  (sample config included with conky)

To test different conky configs you download, just place them all in a folder named conky in your home directory.Name them anything you like.(eg conky1, conky2 etc)
To run a specific config, in the terminal, enter
```
conky -c ~/conky/[COLOR="DarkRed"]name of your config[/COLOR]
```

Thread for conky configs  [_**[COLOR="#8b0000"]http://ubuntuforums.org/showthread.php?t=281865[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=281865")

[_**[COLOR="#8b0000"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]**_]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

