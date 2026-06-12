---
title: "IE4Linux not working correctly"
date: 2009-04-29
forum: General Help
---

### Post by dmcdaniel on 2009-04-29
The Problem:

There is a website we have to use IE for. We just recently switched over to Ubuntu so I installed IEs 4 Linux. 

I can get it to open the first time but the problem I am having is it then locks up the process and you can not re-open the program without killing the process. I created a script that runs and kills the process for me but sometimes the people forget to run the script. Also, I want it to display a message once the script is run. Something like: "Agent: This was completed successfully" or something to that nature. 

Any ideas?

---

### Post by kpkeerthi on 2009-04-29
```

zenity --info --text "Agent: This was completed successfully"

```

You could put something like that in your bash script to display a graphical message box on the desktop.

See man page for more options: [http://linux.die.net/man/1/zenity]("http://linux.die.net/man/1/zenity")

---

### Post by dmcdaniel on 2009-04-29
Thanks :) I tested it and that seemed to do the trick. My script looks like this (In case you may have a better way of doing it)

#! /bin/sh

pkill wineserver
pkill IEXPLORE.EXE
pkill explorer.exe

zenity --info --text "Agent: This was completed successfully"

---

