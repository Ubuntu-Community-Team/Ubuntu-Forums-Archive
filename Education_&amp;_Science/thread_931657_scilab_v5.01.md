---
title: "scilab v5.01"
date: 2008-09-27
forum: Education &amp; Science
---

### Post by goslings on 2008-09-27
The homepage of SCILAB say there is a new version 
why does synaptic manager not find thie rather than outdated v4?
regards

---

### Post by hubie on 2008-09-27
Apparently whomever is packaging Scilab for Debian/Ubuntu has not packed up the latest version yet.

If you want to get the latest version yourself, you can download either the source and compile it yourself, or there is a Scilab binary you can download and install.  Instructions for installing it are on the [download page]("http://www.scilab.org/download/").

---

### Post by goslings on 2008-09-27
i saw that, but I am usually used to using synaptic mgr to install items 
where does all the apps get installed on ubuntu
thanks

---

### Post by LaserJock on 2008-09-27
There are a few things to bear in mind.
[LIST=1]
[*]Scilab 5 hasn't been out for very long
[*]Debian is trying to finish a release (Lenny) and unlikely to include new upstream releases immediately
[*]Ubuntu is about to release Intrepid and is unlikely to want new upstream releases at the moment
[*]Scilab 5 includes a whole new license, which looks to be significantly more free than the previous one, and so it will take some time to get everything updated.
[/LIST]

The license change is exciting news, but will probably mean some review time. Traditionally scilab has been a bit of a tough package to get updated. Hopefully though it won't be too long before Scilab 5 makes it in.

-LaserJock

---

### Post by goslings on 2008-09-28
thanks - Ubunutu developer
In the meantime is there a detailed "how to install scilab ....'
so that it appears in apps under programming ?
many thanks 
Ian

---

### Post by Proton Soup on 2008-09-28
my scilab shows up under education, but if you right click on the menu and choose edit, it's pretty easy to figure out without instructions.  there is a help button in there, though.

---

### Post by goslings on 2008-10-03
do you have to be root to install this as the install help says nthing about this aspect ?
thanks

---

### Post by Proton Soup on 2008-10-03
is that in response to me?  i don't know about installing Scilab 5 specifically, i'm actually waiting until i can upgrade it with synaptic.  but just in general, if you can run the program from the command line, you can add a menu selection item, and put it under Education or Programming, or wherever.  you don't need any special privilege to do that.  for example, i downloaded JSymphonic to add files to my annoying Sony mp3 player.  starting it from the command line is annoying, and i forget where it is, so i added a menu shortcut for it.  i'm a linux 'tard and i thought it was pretty easy, so...

---

### Post by goslings on 2008-10-04
it was a request everyone really 
I usually install only through synaptic, but this software is only available via tar.gz download and while there are instructions nothing is mentioned about being root, which I think you must as you cann put the tar file in any "system" directory
if somoone who has install scilab 5.01 on linux could elaborate would be great 
thanks

---

### Post by goslings on 2008-10-04
> **goslings said:**
> it was a request everyone really 
I usually install only through synaptic, but this software is only available via tar.gz download and while there are instructions nothing is mentioned about being root, which I think you must as you cann put the tar file in any "system" directory
if somoone who has install scilab 5.01 on linux could elaborate would be great 
thanks

I should add that trying to extract with archive manager to a directory in say /var/ ... fails as I do not have permission, but I expected the system to ask for a root password, as it does on all other system apps 
thanks

---

### Post by Proton Soup on 2008-10-04
yeah, this kind of stuff is why i'm just waiting, but in general, i think you use the sudo command to prefix the first command, and then it gives you root access for a certain amount of time on subsequent commands.  and my scilab appears to be in /usr/lib, fwiw.

---

### Post by waspbr on 2008-10-26
I just installed it in my home directory instead and made an icon of it , no root needed there. When scilab 5 gets on the repo then I'll replace it.

---

