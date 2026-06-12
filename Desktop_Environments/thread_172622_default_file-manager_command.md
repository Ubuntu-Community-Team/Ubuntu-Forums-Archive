---
title: "default file-manager command?"
date: 2006-05-09
forum: Desktop Environments
---

### Post by nalmeth on 2006-05-09
[LEFT]In amsn, under advanced options, there is a dialogue box where you select which file_manager to use when opening files.
it says my_filemanager $
My question:
Is there a command that will open the default file manager for the desktop environment you're in?
I ask, because I want to have a generic desktop launcher that I can click, so that in xubuntu it opens thunar, in kde konqueror, in gnome nautilus.
Is there anything like this around?
[/LEFT]

---

### Post by louis_nichols on 2006-05-09
There in't one, but it's easily made. You just have to add to the login scripts of each desktop manager a line like

export DEFAULT_FILE_MAN=nautilus/thunar/konqueror

or whatever, and then, for launcher put in $DEFAULT_FILE_MAN

---

### Post by nalmeth on 2006-05-09
Cool, glad it's doable.
But how should I do this?
Create a new file with the line you provided? How to I make this file executable?

---

### Post by louis_nichols on 2006-05-09
well... with gnome it's easier than I previously though. Just go to System>Preferences>Sessions>Startup commands and enter 
```
export DEFAULT_FILE_MAN=nautilus
```
KDE must have a very similar option somewhere, but I don't have it installed anymore, to check.

I've used XFCE too little to know about how this could be done under it.

---

### Post by nalmeth on 2006-05-09
what does this do though? 
Gnome knows that the default file manager is nautilus for gnome, but I want to have one icon on the desktop that will launch the default file manager across any desktop environment.
The same launcher for KDE gnome and XFCE.
Currently I have a launcher that launches the command "thunar", but i don't want to use thunar in gnome or kde.
I know it's a picky thing to ask for, but I'm really into figuring out how to do this. :D
What exactly does the line you provided do? It looks like a good start on the right path.

---

### Post by ComplexNumber on 2006-05-09
[quote=louis_nichols]well... with gnome it's easier than I previously though. Just go to System>Preferences>Sessions>Startup commands and enter 
```
export DEFAULT_FILE_MAN=nautilus
``` KDE must have a very similar option somewhere, but I don't have it installed anymore, to check.

I've used XFCE too little to know about how this could be done under it.[/quote] or even easier for gnome, just select the application called 'preferred applications' from the menu and choose the default browser from there.

---

### Post by nalmeth on 2006-05-09
hmm I'm a little confused..
but I have an idea, one that may not work at all...
Can I create a file, which contains a link to a location (/home), and then set the prefered application in each DE to open this .home file?
Is this feasable?
What would the file contain?

---

### Post by louis_nichols on 2006-05-10
The commands I wrote export an environment variable containing the name of the file browser. try it in console, it'll be fun: (the first $ indicates the command line cursor)

```
$ export FILE_MAN=nautilus
$ $FILE_MAN
```

you will se it opens nautilus. So this is the principle. Unfortunatelly, I just tested it and it seems it doesn't work at the DE level (well, in gnome anyway). Now, I'm not a command shell or scripting guru, but I have another pretty simple idea.

You'll need to make 3 scripts, one for each of the DE's. I suggest you do this in a separate folder, to keep things clean. so:

```
mkdir ~/bin
```

Then, 

```
gedit ~/bin/gnome_file_man
``` and put in it the following:

```
#! /bin/bash
file_manager=nautilus
$file_manager &
```

do the same with other 2 files, called kde_file_man and xfce_file_man, replacing the correct value of the file manager. Then, make them all executable:

```
chmod +x ~/bin/*
```

Now, the thing is to put a command among the startup programs of each DE to make a symbolic link to the correct small script, but which will always have the same name. So, in gnome that will be:

```
ln -s /home/<username>/bin/gnome_file_man/file_man
```

in kde:

```
ln -s /home/<username>/bin/kde_file_man/file_man
```
and you know what to do with xfce's. :) Then, your launcher on the desktop (or any place where you are asked for the file manager) will need only include the command

/home/<username>/bin/file_man

I know it's obvious that each DE knows which is the default file browser, but I haven't found a transparent way to force it to open.

---

### Post by nalmeth on 2006-05-10
Ya, no sorry I thought you were just telling me to tell gnome to use nautilus as the default. My mistake.

I like your line of thinking though, it is making sense to me (the gears are slowing turning)

It does sound fun, and I will try it tonight.

This will be friggin cool if it ends up working. We'll have to make it a howto or something, but it's a little early to get hopes up.

I just hate having the wrong desktop launchers when I change DE's (as I frequently do), or rather, forget the chore of putting them in trash until next time I boot back. :rolleyes:

Thanks for the effort, 

I will post my results! :D

---

### Post by louis_nichols on 2006-05-10
Well, I think such a method is useful for, as you said in the beginning, apps that require you to tell them the default file browser. Otherwise, accessing the default browser in each environment is easily done in the "start" menu. I understand why you may want a shortcut on the desktop for this, though. There might be a (much) easier way than the one I posted, but I don't know it. :)

---

### Post by nalmeth on 2006-05-10
Hmm, getting mixed success here.
In xfce, I ran the sym-link manually in the terminal, and was able to execute from the terminal the correct filemanager: thunar.
I could not however find the start-up list to add the sym-link for every boot.
I'll get back to this at the end.

In KDE, I could not get kdinit to launch the file_man command, or find the start-up list.
In gnome, I was able to add the sym-link to start-up, but gnome refused to launch the command. 
From gnome terminal (I first tried it all in .bin so it would be hidden, but creating the unhidden bin folder didn't help either):
```
sdcb@vaiobuntu:~$ /home/sdcb/.bin/file_man
bash: /home/sdcb/.bin/file_man: No such file or directory
sdcb@vaiobuntu:~$ ln -s /home/sdcb/.bin/gnome_file_man/file_man
ln: creating symbolic link `./file_man' to `/home/sdcb/.bin/gnome_file_man/file_man': File exists
sdcb@vaiobuntu:~$ mkdir ~/bin
sdcb@vaiobuntu:~$ cp /home/sdcb/.bin/gnome_file_man ~/bin/gnome_file_man
sdcb@vaiobuntu:~$ ln -s /home/sdcb/bin/gnome_file_man/file_man
ln: creating symbolic link `./file_man' to `/home/sdcb/bin/gnome_file_man/file_man': File exists
sdcb@vaiobuntu:~$ ~/bin/file_man
bash: /home/sdcb/bin/file_man: No such file or directory
```

What do you think this means?

BTW:
I found that KDE has an Autostart folder:
~/.kde/Autostart
How can I add the sym-link (through CLI) to run at autostart, considering we can get the kdinit to launch the executable?
I assume xfce has a similar situation. I'll try to find it's folder.

Any ideas here?

---

