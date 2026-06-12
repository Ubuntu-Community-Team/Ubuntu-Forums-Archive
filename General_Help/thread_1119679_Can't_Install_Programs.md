---
title: "Can't Install Programs"
date: 2009-04-08
forum: General Help
---

### Post by al3nmikho on 2009-04-08
When I tried to install amsn from [www.amsn-project.net/](www.amsn-project.net/) I get a error


```
Could not open the file /home/kickback/Desktop/a….97.2-1.tcl84.x86.package.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
```

After trying to install a variety of programs,the same error occurred for allot of things.  Then I goggled this error and noticed it was due to Java I re-installed Java but I'm having no luck.  I need help you guys! :frown:

---

### Post by s.fox on 2009-04-08
Welcome to Ubuntu Forums,

You could just install amsn from Synaptic Package Manager.

**System-> Administration -> Synaptic Package Manager**

Do a search for "amsn" and you can install from there.

Hope this helps,

-Ash R

---

### Post by coffeecat on 2009-04-08
Just to add...

Downloading stuff from the internet and running an installer is the Windows way of doing things. More than 90% of times, what you want is already in the repositories and can be installed with a couple of mouse clicks.

The packages are listed in Synaptic by what their developers call them, which will be unfamiliar to newcomers. Also have a look in Applications > Add/Remove. Things are a bit more user-friendly in there. And no, you don't use it like Windows Add/Remove. :wink: Just select what you want, click on Apply and the system will do everything for you.

---

### Post by neu2buntu on 2009-04-08
looks like you are trying to install from source....are you trying to open the README or INSTALL if so you will want to do 
cd name_of_file
ls  (this will show all files in the directory)
gedit README (if readme exists sometimes its just "install")   but in most packages the commands are ./configure ,make and sudo make install..... this can be all a bit much if your total noob... i would do as Ash R said and install through synaptic for now and research a bit more about using the cli (terminal) to install from source

---

### Post by al3nmikho on 2009-04-08
Thanks guys! 

The problem was solved! :popcorn:

---

