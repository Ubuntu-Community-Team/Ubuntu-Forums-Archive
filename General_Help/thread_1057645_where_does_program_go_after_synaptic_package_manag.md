---
title: "where does program go after synaptic package manager install?"
date: 2009-02-02
forum: General Help
---

### Post by bosworthy on 2009-02-02
Hi,

I know I can search through the menu system, but is there a way I can find out where ubuntu has installed my program, say under which menu, and under what directory?

Thanks,

---

### Post by iaculallad on 2009-02-02
For the directory location part, you could use the command below on your terminal:

```
which application_name
```

or 

```
locate application_name
```

---

### Post by geirha on 2009-02-02
In Synaptic, locate the package, righ-click it -> Properties -> Installed files. If there are .desktop-files installed under /usr/share/application/, that means you'll find entries for it in the menus. If it installs files under /usr/bin, but no desktop-files, then you've installed a command-line application. Lastly, some packages do not contain programs at all, some contain only documentation for instance.

You can also see the list of installed files from the terminal with:
```
dpkg -L *packagename*
```

---

### Post by pastalavista on 2009-02-02
also, during installation, choose the details or terminal view and all the files installed are listed with their full path

---

### Post by bosworthy on 2009-02-15
Thanks Geirha,

It seems tomcat is installed under /usr/share
I'm going to find a newbie intro to what these directories mean under ubuntu.



> **geirha said:**
> In Synaptic, locate the package, righ-click it -> Properties -> Installed files. If there are .desktop-files installed under /usr/share/application/, that means you'll find entries for it in the menus. If it installs files under /usr/bin, but no desktop-files, then you've installed a command-line application. Lastly, some packages do not contain programs at all, some contain only documentation for instance.

You can also see the list of installed files from the terminal with:
```
dpkg -L *packagename*
```

---

### Post by bosworthy on 2009-02-15
a few years back, I remember I need to run something to update "which" or else the database will be out of date.  Would you know what that happens to be?

man which only gave a very brief description.  I'm not sure why, but ubuntu only allows me to read 6 out of 30 pages??

"Manual page which (1) line 6/30 (END).  What happened to the other pages?  I can scroll up and down with the mouse.

Thanks.





> **iaculallad said:**
> For the directory location part, you could use the command below on your terminal:

```
which application_name
```

or 

```
locate application_name
```

---

### Post by oldos2er on 2009-02-15
"sudo updatedb" updates the database.

---

### Post by geirha on 2009-02-15
> **bosworthy said:**
> 
man which only gave a very brief description.  I'm not sure why, but ubuntu only allows me to read 6 out of 30 pages??

"Manual page which (1) line 6/30 (END).  What happened to the other pages?  I can scroll up and down with the mouse.


It's lines, not pages. There are 30 lines in total, and the line shown at the top of the screen is the sixth. The default size of a terminal window is 80 characters in the width, and 24 lines.
```
$ man which | wc -l
30

```

---

### Post by bosworthy on 2009-02-15
man updatedb says

"updatedb is usually run daily by cron(8) to update the default database."  does it does the update if I were to restart the computer?  

I'm going to have to read up on how cron works.  there's so much to learn!

> **oldos2er said:**
> "sudo updatedb" updates the database.

---

### Post by geirha on 2009-02-15
> **bosworthy said:**
> man updatedb says

"updatedb is usually run daily by cron(8) to update the default database."  does it does the update if I were to restart the computer?  

I'm going to have to read up on how cron works.  there's so much to learn!

In Ubuntu it is run by anacron daily (/etc/cron.daily/find). Anacron works a bit different than cron though. Anacron does not run as a daemon like cron does, it just gets run once a day, around 7:30 (from cron), and also during boot. When it is run, it checks if it has already been run on this date, if it has, it will just exit, if not, it runs all scripts in /etc/cron.daily.

---

