---
title: "Can't install themes"
date: 2005-06-04
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-04
I'm trying to get some icon themes from the gnome site, but when I go to install them, it tells me "installation failed". I've tried installing the archive, the folder in the archive, the theme file etc. (I think I've been told that it's the archive itself you run the install on, but i've tried files in it as well.) Why is my installation failing? What do I need to do? Thanks!

---

### Post by GrumpySimon on 2005-06-04
How are you installing them? This works for me:

1) System -> Preferences -> Theme
2) Click "Theme Details"
3) Choose "Icons" Tab
4) Drag .tar.gz file onto the Icon list.

If that doesn't work, then check if the file is ok (and not corrupted), or try another icon archive to see if that works.

--Simon

---

### Post by Curlydave on 2005-06-04
Naww, tried that too, same error. (just tried it again and it still errors.) I'm downloadign them from Gnome Art, and all of the icon themes do this. I havn't tried the app themes yet. Something's screwey.

---

### Post by GrumpySimon on 2005-06-04
[QUOTE=Curlydave]Naww, tried that too, same error. (just tried it again and it still errors.) I'm downloadign them from Gnome Art, and all of the icon themes do this. I havn't tried the app themes yet. Something's screwey.[/QUOTE]
 Does the directory  ~/.icons exist? What permissions does it have?

--Simon

---

### Post by Curlydave on 2005-06-04
If I click "go to theme folder" under icons, it takes me to a folder called .icons with two subfolders. If I go up from there, there is no folder, and a search reveals nothing. Basically it's as is it's not there, but suddenly appears when I click "go to theme folder." Without being able to view the folder from a window, I can't see the permissions. Also, where exactly is it? It appears to be in /home/david, I think. What does the "~" indicate?

---

### Post by GrumpySimon on 2005-06-04
[QUOTE=Curlydave]If I click "go to theme folder" under icons, it takes me to a folder called .icons with two subfolders. If I go up from there, there is no folder, and a search reveals nothing. Basically it's as is it's not there, but suddenly appears when I click "go to theme folder." Without being able to view the folder from a window, I can't see the permissions. Also, where exactly is it? It appears to be in /home/david, I think. What does the "~" indicate?[/QUOTE]
 Sorry ~ is linux shorthand for your home directory. In your case it's /home/david.

Can you open a terminal, and do this:
```

ls -la ~/.icons

```

You should see something like:
```

simon@lurch:~/.icons$ ls -la
total 12
drwxr-xr-x   3 simon simon 4096 2005-06-04 21:44 .
drwxr-xr-x  47 simon simon 4096 2005-06-05 09:20 ..
drwxr-xr-x   4 simon simon 4096 2005-06-04 21:44 Kreski-Lines

```

What we're interested in is the first bit of info on each line, which show the permissions. Can you post it here?

--Simon

---

### Post by Curlydave on 2005-06-05
Found the problem: Some of the files on the Gnome Art site are bugged up, eg the most popular one. Others work though. Messed up!

---

### Post by poptones on 2005-06-20
I dont believe the problem is mucked up packages. I just installed hoary on a system that was running warty recently and hoary before that, and the icons will not display properly. 

I'm tempted to say it's an SVG problem but I am not sure. Copying my icons folder from my old working desktop to this one does not work. The permissions and ownership are set to 755 in my username. Not only do the existing folders not work (the menu names appear in the selection box but selecting any of them results in broken default icons) I also cannot install any of the packages that installed just fine before. Ximian south, blankon, edge, clearlooks, iris, flat - none of them will display.

---

### Post by syn4k on 2008-04-06
sudo gnome-appearance-properties
or
sudo gnome-appearance-properties --ignore-theme-index
Then try :)

---

### Post by syn4k on 2008-04-07
I just discovered something interesting.
Untar the theme file. Does the folder name contain spaces like "GANT theme"? If so, this seems to be the culprit. Rename the folder to "GANT_theme" and then compress the folder again. This fixes the issue for me.

---

