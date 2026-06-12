---
title: "Boot Log location?"
date: 2005-09-22
forum: Desktop Environments
---

### Post by kris kincaid on 2005-09-22
Where can I find a copy of the boot log? Just to be clear, I want to see a copy of everything that flashes by the screen as Ubuntu is booting up, and also (important) when Ubuntu shuts down.

When I am booting, it gets to a point where it says there is a duplicate file (start.*something* ) and it very VERY quickly opens Vim so I can edit this mystery file. I have to do a :qa! command to exit and it continues booting. Now I notice there is no longer any sound. When I shutdown, I see something about "/etc/ALSA.*something*  " not having permission for something??


My assumption is I can look at a log and see these errors. I tried writing them down as they flash by, but that all happens very quickly.

Thanks!!

---

### Post by Xian on 2005-09-22
[QUOTE=kris kincaid]Where can I find a copy of the boot log?[/QUOTE]
It does not exist in Ubuntu.

---

### Post by bsussman on 2005-09-22
Look at the early stuff by typing (in a terminal window):

 ```
 dmesg | less
``` 

or by:

 ```
 dmesg > filename
``` 

and examine using your favorite text editor

then the logs in /var/log take over.

examine them using your favorite text editor.

---

### Post by mlomker on 2005-09-22
> 
 ```
 dmesg > filename
``` 


FYI, dmesg is almost the same thing as **cat /var/log/kern.log**.  There's really no point in dumping dmesg to a file because you can just open the kern.log instead.

---

### Post by dbott67 on 2005-09-22
[QUOTE=mlomker]FYI, dmesg is almost the same thing as **cat /var/log/kern.log**.  There's really no point in dumping dmesg to a file because you can just open the kern.log instead.[/QUOTE]

FWIW, on my computer I tried mlomker's suggestion (I had only used dmesg in the past) and it provided a lot more information than dmesg ever did.

Thanks!
-Dave

---

### Post by bsussman on 2005-09-23
Cool -  kern.log is actually more valuable...

Lessee - store new trick, throw out old trick...:smile:

---

### Post by kris kincaid on 2005-09-26
Awesome info, but it doesn't seem to have the exact info I need. Looks like I'm on to plan B.

---

### Post by Zwack on 2005-09-27
[QUOTE=bsussman]Cool -  kern.log is actually more valuable...

Lessee - store new trick, throw out old trick...:smile:[/QUOTE]

Don't throw out the old trick if you want to remain portable... On real Unix systems dmesg is important and /var/log/kern.log doesn't exist.

On my system the difference between dmesg (218 lines) and the last 218 lines of /var/log/kern.log is the syslog header stuck on the front of the line (and some minor printing differences on three lines that are to do with whether control characters were interpreted or not).

A good way to view these logs is by using the System Log viewer under Applications -> System Tools -> System Log.

Z.

---

### Post by mlomker on 2005-09-27
[QUOTE=Zwack]Don't throw out the old trick if you want to remain portable... On real Unix systems dmesg is important and /var/log/kern.log doesn't exist.
[/QUOTE]

It's portable if you add one line to your /etc/syslog.conf file.  I guess it just depends on whether or not you own the box.

---

### Post by Zwack on 2005-09-28
[QUOTE=mlomker]It's portable if you add one line to your /etc/syslog.conf file.  I guess it just depends on whether or not you own the box.[/QUOTE]

Only if you've already made that change to syslog (and created directories as needed)...

dmesg still has a place (as does errpt...) and given that the differences between the two are dmesg has a shorter memory and no date stamps I don't see a big need for   one over the other.

Z.

---

