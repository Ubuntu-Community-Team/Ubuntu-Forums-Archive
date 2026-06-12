---
title: "Customizing Gnome Right Click Menu?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by aPello on 2006-09-24
I want to add a right click option to any file either on the desktop or in nautilus, thats like "Upload to Upit.be", and then when some one clicks this, it calls a cmd line php script i have written and passes the file path as an arg to it.

Could any one point me in the right direction of achieving this?

---

### Post by SavageBeginner on 2006-09-24
Check out the 'nautilus-actions' package. 

To install:
```
sudo apt-get install nautilus-actions
```
To configure:
```
nautilus-actions-config
```

---

### Post by aPello on 2006-09-24
Hmm, thats exactly what i need, but how do i get it to open a terminal first? (e.g, execute the script in the terminal).

---

### Post by SavageBeginner on 2006-09-24
I think you want something like this:
```
gnome-terminal -x <script to execute>
```

---

### Post by aPello on 2006-09-24
Yes again thats what i needed :P i should have done man gnome-terminal lol. 

But another question, how do i keep the terminal open after the script is executed? (So i can see its output).

For a hack i made the PHP script pause for 2 minutes, but im sure there is a better way.

---

### Post by dtmilano on 2006-09-29
In gnome-terminal Edit->Profiles...-><your profile>->Title and Command select the option "When command exits: Hold the terminal open"

---

### Post by L a r r y on 2008-06-27
> **SavageBeginner said:**
> Check out the 'nautilus-actions' package. 

To install:
```
sudo apt-get install nautilus-actions
```
To configure:
```
nautilus-actions-config
```

Thank you, SavageBeginner!  This code let me add new content to my 
right-click menus on my file icons.

What I'm looking for, and began a thread on the topic, is to add new 
menus to the vertical scrollbar arrows.  See:

[http://ubuntuforums.org/showthread.php?p=5275535#post5275535](http://ubuntuforums.org/showthread.php?p=5275535#post5275535)

Thanks again.

---

