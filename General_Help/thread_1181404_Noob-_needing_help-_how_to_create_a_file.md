---
title: "Noob- needing help- how to create a file"
date: 2009-06-07
forum: General Help
---

### Post by redgs95 on 2009-06-07
I need help! i need to know how to create this file so bitpim will work and see my phone.  /etc/udev/rules.d/60-cell.rules
 I have been searching the forums (here and elsewhere) and can't find the instructions on how to create files. I am running the Ubuntu 9.04 version. I am trying to get away from xp  unless i want to play warcraft.

---

### Post by michy99 on 2009-06-07
To create a file in /etc you will have to have root permissions so you need to open a text editor with gksudo```
gksudo gedit /etc/udev/rules.d/60-cell.rules
```Put whatever you need to in the file and save it.

As to what goes in the file you will have to ask someone who knows about that program.

---

### Post by redgs95 on 2009-06-08
thank you for the information. i find the things i needed to put in it and saved it. ):P

---

### Post by bzm3r on 2009-06-08
Why gksudo in this case, instead of just plain old sudo? Sudo seems to handle graphical stuff fine as well...(btw, I'm a linux noob too)

---

### Post by _Purple_ on 2009-06-08
> **bzm3r said:**
> Why gksudo in this case, instead of just plain old sudo?

sudo is for CLI applications where as gksudo is for GUI applications. Please see this link for details:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dnairb on 2009-06-08
> **bzm3r said:**
> Why gksudo in this case, instead of just plain old sudo? Sudo seems to handle graphical stuff fine as well...

It is better (safer?) to use **gk**sudo for graphical apps, such as gedit, nautilus, etc and plain-old sudo for terminal commands.

IIRC if you become root on Debian using **su -** rather than **gksu -** you cannot then run gedit.

---

### Post by Cheesemill on 2009-06-08
You shouldn't really use sudo at all for graphical apps, it will work OK 99% of the time but the other 1% it can screw up your files.

See here for more info.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Cheesemill

---

### Post by bzm3r on 2009-06-08
@_Purple_: Ahhh...thank you for that good link. I'll keep that in mind next time I sudo something.

---

### Post by redgs95 on 2009-06-08
I was needing to set up a file so that bitpim will see my cellphone. So which way do i create the file? I have already created one using gksudo should i delete it and create it using plain sudo?

---

### Post by michy99 on 2009-06-08
> **redgs95 said:**
> I was needing to set up a file so that bitpim will see my cellphone. So which way do i create the file? I have already created one using gksudo should i delete it and create it using plain sudo?

No. sudo and gksudo just allow you to run a command as root. The difference is that gksudo is for graphical programs (like gedit) and sudo is for command line programs (like nano). Once you have created and saved your file it doesn't matter which method you used to do it.

---

### Post by redgs95 on 2009-06-08
Well I created the file and entered in the information like it said to. I started bitpim and tried to get the filesystem and nothing it still doesn't see my phone. I am stuck! I have used windows to long. I will not give up I just need to read more about the way linux is set up. Are there any good reading out there to teach an old dog some new tricks?

---

### Post by michy99 on 2009-06-08
I don't have any experience using linux with phones, but I would suggest you start a new topic with a title like "Trying to get my ____ phone to work with Ubuntu" (fill in the blank). That way someone who knows about this might see it and help. Good luck.

---

### Post by redgs95 on 2009-06-08
ok that sounds like a good thing to do.

---

