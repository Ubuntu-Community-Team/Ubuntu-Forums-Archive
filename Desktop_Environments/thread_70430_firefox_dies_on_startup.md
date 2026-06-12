---
title: "firefox dies on startup"
date: 2005-09-29
forum: Desktop Environments
---

### Post by nighttime on 2005-09-29
Firefox suddenly started closing on startup... it starts to open and then it's gone,  just like that. I tried installing Mozilla and the exact same thing happens. I tried running firefox from the terminal, all I get is:

oscarmier@nexus:~$ firefox
*** loading the extensions datasource
Segmentation fault

so I tried 

sudo firefox -H

wich worked fine... but I don't wanna have to do this every time I want to surf the web. I tried re-installing it also w no results.

I have firefox 1.0.7

---

### Post by codejunkie on 2005-09-29
[QUOTE=nighttime]Firefox suddenly started closing on startup... it starts to open and then it's gone,  just like that. I tried installing Mozilla and the exact same thing happens. I tried running firefox from the terminal, all I get is:

oscarmier@nexus:~$ firefox
*** loading the extensions datasource
Segmentation fault

so I tried 

sudo firefox -H

wich worked fine... but I don't wanna have to do this every time I want to surf the web. I tried re-installing it also w no results.

I have firefox 1.0.7[/QUOTE]
you could delete or rename the /home/youusername/.mozilla directory that will reset firefox to default settings but you'll loose your bookmarks extensions etc, so you might want to save your bookmarks first.

---

### Post by jrib on 2005-09-29
you can try running firefox in safe mode:
```
$firefox -safe-mode
```
If it works fine then some extension you installed probably messed up your profile.  Go to tools->extensions and remove any extensions you think may have caused the problem.  Then try starting firefox again.

If that fails you can try running firefox with a new profile:
```
$firefox -profilemanager
```
Of course you won't have any of your settings or bookmarks so you would have to transfer those over.  A little googling will let you find your bookmarks file in your old profile and copy it over.

I hope that helps, that's all I could think of.

---

### Post by nighttime on 2005-09-29
> 
you could delete or rename the /home/youusername/.mozilla directory that will reset firefox to default settings but you'll loose your bookmarks extensions etc, so you might want to save your bookmarks first.
Didn't work...

---

### Post by nighttime on 2005-09-29
[QUOTE=_jason]you can try running firefox in safe mode:
```
$firefox -safe-mode
```
If it works fine then some extension you installed probably messed up your profile.  Go to tools->extensions and remove any extensions you think may have caused the problem.  Then try starting firefox again.

If that fails you can try running firefox with a new profile:
```
$firefox -profilemanager
```
Of course you won't have any of your settings or bookmarks so you would have to transfer those over.  A little googling will let you find your bookmarks file in your old profile and copy it over.

I hope that helps, that's all I could think of.[/QUOTE]

There are no extensions installed, I re-installed the whole thing using the synaptic package manager. And firefox -profilemanager opens nothing... :(  There are some threads on this "Segmentation fault" though... I just can't find any concrete solution in them.

---

### Post by jrib on 2005-09-29
did you just upgrade to 1.07?  Has 1.07 ever started or did this just start after you upgraded?

---

### Post by nighttime on 2005-09-29
Well... today I saw the little red button on the corner of the screen and clicked on it to install the updates, I have done this a few times before. I don't know what version I had before today's intallation. I know I started with firefox 1.0.2 but I don't know what version it upgraded to after the first update (wich was about a month ago)

 It may not have been that, cause the problem had not started untill a while after the updates were installed (I opened a few firefox windows right after today's updates installation with no problem...)

---

### Post by jrib on 2005-09-29
The firefox 1.07 update caused a lot of problems for a lot of people.  It messed up my install too.  If you search the forums you will get a lot of information on it.  
If it was the update then we can fix it.  If not, then I don't know.  But let's try to fix it assuming it was the update.  Here is what I did:
```
$killall firefox-bin
```
try running firefox again after this.  If your prolem is update related, then firefox should start up.

To be on the safe side, I went into synaptic and removed the four firefox packages (firefox, mozilla-firefox, and two corresponding gnome support for firefox packages).  Then I went ahead and installed mozilla-firefox (which will tell you you need gnome support too, ok).  1.07 worry free!  (I hope).

---

### Post by tronda on 2005-09-30
I tried the following:
```

mv .mozilla/firefox tmp/.
firefox
```

I got up a dialog asking if I would like to import my bookmarks from anywhere. I said NO to this. After a while firefox just died with the following error message in the console:
```

(Gecko:13378): libgnomevfs-WARNING **: Cannot create pipe for GnomeVFSProcess initialization: Too many open files
```

The problem started after updating to 1.07.

---

