---
title: "deskbar only showing files and folders in /home"
date: 2007-01-09
forum: Desktop Environments
---

### Post by munkar on 2007-01-09
i just discovered the deskbar-applet, which is potentially very useful. but somehow when it comes to files and folders, it can only find items that are in my /home/username/ folder -- it doesn't even find things in subdirectories!

so, if there's a /home/me/mystuff/pics/ on my system, it will find "mystuff", but it won't find "pics".

how do i make it index subdirectories of /home/username/ (i don't necessarily need it to search the entire filesystem)?

another thing is that it would be cool if it could run my scripts....

---

### Post by nihalz on 2007-01-12
yeah man...i am having the same problem...it dosent displat any of the files in the subdirectories of the home folder....does anyone know what could be the solution to this problem??

---

### Post by munkar on 2007-02-08
in spite of knowing anything about python, i figured out how to hack the deskbar files & folders handlers to make it automatically find the files that i specify.

i have a special folder in which i keep all of the links that i want deskbar to be able to find immediately (the advantage of having them as links is that i can change the names and give them "aliases"). i use a nautilus script that lets me right-click on files or folders and "tag" them as "bookmarks" for deskbar. my code is probably ugly because i'm a beginner, but it works! i'll post a full solution if anyone wants it.

---

### Post by Ronnie.vd.c on 2007-03-25
Sure, i have the same problem.

---

### Post by mgmiller on 2007-03-25
I use deskbar a lot.  It's one of my favorite Ubuntu features, and I feel it should be enabled by default.  I find it has no trouble finding files buried several layers deep in my home directory, for example:  /home/marty/TV-Shows/farscape-peacekeeper_m480.mov  It even finds pictures buried further layers deep in my pictures folder that have spaces in the filenames.  It launches applications for me and sends e-mail.  I have stopped organizing my Firefox bookmarks, because it's easier to just deskbar them.  

Have you right clicked on the deskbar applet and checked off the features you want it to have?  :confused:

The only other thing I can think of is I had previously installed gnome-launch-box before deskbar existed, and I never bothered to uninstall it.  It had similar functionality, but somehow, I didn't like or use it as much.

```
sudo apt-get install gnome-launch-box
```

---

### Post by ComplexNumber on 2007-03-25
guys, what you need to do is to include other folders in the search path. deskbar uses beagle for its search facility.  go to the beagle GUI in the accessories menu. it will be listed as 'search'. in beagle, open up the preferences and select the indexing tab. if you don't have beagle, then you will need to install the GUI which is called simply 'beagle'. the backend which actually does the searching is called  libbeagle.

alternatively, you can go to the gnome control centre(called gnome-control-center. note the american speliling of "center"), the indexing  is listed as 'search and indexing'. i'm really not too sure if that feature is installed with libbeagle(the search backend) or the beagle GUI (ie beagle).

the search and indexing GUI looks like this where you can add your own search paths in addition to your home directory. for example, you can see that i've added "/usr" to my searchpath. **NOTE**: be aware that when you add large directories such as /usr, the resultant indexing database will be very large. the .beagle directory which holds all the config files and indexing database related to beagle in my own home directory is 496MB, so make sure home directory is large enough to accomodate it. i know that this isn't an issue on most computers, but i just wanted to make you aware of it.
**NOTE 2**:you need to give beagle a few days or so to build up the database of where everything is.

---

### Post by mgmiller on 2007-03-25
I have to disagree with complex number.  I do not have beagle installed and never did.  It works fine without it.

---

### Post by ComplexNumber on 2007-03-25
> **mgmiller said:**
> I have to disagree with complex number.  I do not have beagle installed and never did.  It works fine without it.
you dont appear to have understood fully what i've said. i'm referring to searching though directoriers other than the home directory. beagle is merely the frontend. the backend, libbeagle, is installed with nautilus and is a dependency of it. for example, when you click on search in the nautilus menubar, thats using libbeagle, not beagle. the deskbar applet is too.

---

### Post by mgmiller on 2007-03-25
> you dont appear to have understood fully what i've said. i'm referring to searching though directoriers other than the home directory.

You're right, I didn't imply that from your response.

The original poster only wanted to be able to search subfolders in his home directory, not his whole file system.  If I use deskbar to search for "pixmaps", for example, since, it's default is my home directory, it won't find anything, but you can click the "Look in" drop down and change it to file system and it finds it instantly in /usr/share.  I have resisted installing the Beagle front end because of all the problems I read about it.  Using deskbar without the beagle front end works great.  The big question for the original poster is why it won't search deeper within his home directory, and my question is why it works fine in my system.

---

### Post by mgmiller on 2007-03-25
> alternatively, you can go to the gnome control centre(called gnome-control-center. note the american speliling of "center"), the indexing is listed as 'search and indexing'. i'm really not too sure if that feature is installed with libbeagle(the search backend) or the beagle GUI (ie beagle).


I just looked in gnome-control-center and "search and indexing" is not there.  As you say, it's probably installed with the beagle front end.

---

### Post by ComplexNumber on 2007-03-25
>  The original poster only wanted to be able to search subfolders in his home directory,i've given the answer to that here:
> **NOTE 2**:you need to give beagle a few days or so to build up the database of where everything is.actually, its probably anything up to a week or more.

the bits about directories other than the home directory is a "just in case", because its inevitable that people are going to want to find other stuff on their filesystem.

---

### Post by mgmiller on 2007-03-25
> Quote:
The original poster only wanted to be able to search subfolders in his home directory,
i've given the answer to that here:
Quote:
NOTE 2:you need to give beagle a few days or so to build up the database of where everything is.


You are still implying that to do what the poster wants, he has to install the Beagle front end and change the search path.  This does not explain why it works fine for me without ever having installed the Beagle front end.  There must be a config file somewhere that controls this.  That is why I mentioned the gnome-launch-box I had installed long ago.  Is it possible that this app changed the default search path?  I do not have to wait for anything.  Any files placed anywhere, no matter how deep in my home directory are instantly available to deskbar.  I love this app and would not want to risk "gumming it up" with the Beagle front end.

---

### Post by ComplexNumber on 2007-03-25
no, he just has to wait several weeks. i would also check to see if the beagle daemon is running at boot up. when i first installed the beagle front end, it asked me to start the daemon.
one thing to also note is that libbeagle doesn't produce the right result when the beagle daemon is running. try testing the search facility in nautilus  BEFORE and AFTER the beagle daemon is started.

---

### Post by mgmiller on 2007-03-25
> no, he just has to wait several weeks.

:lolflag: 

Exactly!!!  With Beagle, you wait several weeks,  without it, it's instantaneous.

---

