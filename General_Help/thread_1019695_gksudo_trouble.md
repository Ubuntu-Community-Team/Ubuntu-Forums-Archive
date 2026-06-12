---
title: "gksudo trouble"
date: 2008-12-23
forum: General Help
---

### Post by Gregz on 2008-12-23
I have a problem with gksudo. I try and modify a file, try and run gksudo /ect/php5/apache2/php.ini, it will wait about 7 seconds and just go to next line.  What am I doing wrong here?????  I tried nano it just brings up a blank screen, and I can't find file in myphpadmin. I need to edit this file by root............................

---

### Post by decoherence on 2008-12-23
you've given gksudo a filename rather than a command.

instead try

```
gksudo gedit /etc/php5/apache2/php.ini
```

gksudo only grants root permissions to a command.... it is not a text editor itself -- you still need to specify that (gedit, in this case)

---

### Post by taurus on 2008-12-23
Aren't you supposed to include an editor in there if you want to edit a file?

```
gksudo **gedit** /etc/php5/apache2/php.ini
```

---

### Post by Idefix82 on 2008-12-23
To edit the file, you need to type
```
sudo nano /etc/php5/apache2/php.ini
```
or, if you want to edit it with gedit say, then
```
gksudo gedit /etc/php5/apache2/php.ini
```

If you then get a blank file then either this file really is blank or does not exist. in your case, you typed 'ect' instead of 'etc' so the file name you typed did not exist.
You can hit tab after typing the first few characters of a folder or file name and the terminal will automatically complete the name if it is uniquely identifiable. If it isn't, then hitting tab again will show you all the options. This reduces the risk of typing errors and greatly increases typing speed.

---

### Post by Gregz on 2008-12-23
oooohhhhh ddduuuhhh 

Sorry guys my mistake you are right. To much christmas cheer lastnight lol Thank You

---

### Post by decoherence on 2008-12-23
> **Gregz said:**
> oooohhhhh ddduuuhhh 

Sorry guys my mistake you are right. To much christmas cheer lastnight lol Thank You

lol I always find I'm going "apt-get xeyes" and such... whaddya mean I gotta tell it to INSTALL??

:lolflag:

---

