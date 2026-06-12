---
title: "How do I backup my apps"
date: 2009-04-28
forum: General Help
---

### Post by elliotn on 2009-04-28
How do I make backup for my installed software, so i can reinstall ubuntu as it is troubling me. i dont have internet so I want to backup my programs in a flash drive

---

### Post by benj1 on 2009-04-28
if you have some access to the internet, aptoncd from the repository is a good bet.
other than that /var/cache/apt/archives contains the .debs downloaded so you could copy those. but you might have issues with dependencies etc.

whats the problem, maybe that could be solved.

---

### Post by elliotn on 2009-04-28
I downloaded Aptoncd but now I cant find the parkages grrr

---

### Post by benj1 on 2009-04-28
the aptoncd menu entry is in system-->administration if thats what you mean

---

### Post by Trev2HI on 2009-04-28
You could create a list of installed apps and use said list to reinstall everything using the method described by the OP here: [http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")

---

### Post by theozzlives on 2009-04-28
try this:
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5")

---

### Post by elliotn on 2009-04-28
No no what I mean is when I open APTonCD and create it brings me to a window were it ask me to select the parkages I wish to add, destination folder:home.
Thanx

---

### Post by elliotn on 2009-04-28
I mean in var/cache/archieves, If I point it there its empty

---

### Post by tricolorpoa on 2009-04-28
I alway do it this way

```
# sudo dpkg --get-selections > installed-software.log
```this file constains all software installed in your current system.
reinstall the system and
```
# sudo dpkg --set-selections < installed-software.log
# sudo dselect
```

From this: [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

### Post by elliotn on 2009-04-28
So u mean I wont need internet. Bcoz what the above does is create a log file of installed parkages, what I wand is to backup my already installed parkages into a cd so I can reinstall them later, without internet connection.

---

### Post by elliotn on 2009-04-29
Any 1

---

### Post by todak on 2009-04-29
> **elliotn said:**
> I mean in var/cache/archieves, If I point it there its empty
The place to point is **/var/cache/apt/archives**. Notice the **apt** in the location.

---

### Post by elliotn on 2009-04-29
Oh I will check it when I get home.

Is there an option to make it an ISO and save it in a flash drive and burn it later?

---

### Post by elliotn on 2009-04-29
Yep there is nothing there either damm I realy need to do this

---

### Post by benj1 on 2009-04-30
you could perhaps look at back up software i would suspect though that they too would get installed packages from /var/cache/apt/archives.

why don't you start a post on your problem, see if it can be fixed.

the only other solution i can think of is to get the repo on DVD its advertised on distro watch for not very much money.

---

### Post by Trev2HI on 2009-04-30
If your */var/cache/apt/archives* folder is empty then you ran the **apt-get clean** command at some point which removes all of the package files.

Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=430343](http://ubuntuforums.org/showthread.php?t=430343)

A guy wrote a script to re-download all of the packages. If you can get that to work, you should be able to use aptoncd to create the ISO image of the packages.

---

### Post by tricolorpoa on 2009-04-30
> **tricolorpoa said:**
> I alway do it this way

```
# sudo dpkg --get-selections > installed-software.log
```this file constains all software installed in your current system.
reinstall the system and
```
# sudo dpkg --set-selections < installed-software.log
# sudo dselect
```From this: [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

Did you try?

---

