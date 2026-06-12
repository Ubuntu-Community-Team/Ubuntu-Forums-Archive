---
title: "Make something appear in Games folder"
date: 2008-02-22
forum: Desktop Environments
---

### Post by psychofish25 on 2008-02-22
I recently downloaded Phun, yet like many other Linux apps, it doesn't install the game, yet it just has a folder containing the program and some files. I was wondering how I could make a Desktop icon for this (not a shortcut) and then have Phun appear in my games folder, and also open when i type phun in terminal. How can I do these?

---

### Post by avdzm on 2008-02-22
What exacly do u mean by "game folder"?
If u mean in the Applications menu,
you can do this using the menu editor.

Go to, System->Preferences->Main Menu.

about the desktop I'm sorry i don't know with out creating a shortcut(at the moment).

---

### Post by chipants on 2008-02-22
that's not nearly enough information to help you out.

1) did you downlaod a binary package from a website? was it a source package that needs to be compiled? did you get it from an apt repository? you say you 'downloaded' but it didn't 'install'.

2) once again, you say you downloaded and it didn't install. when you download something, you generally need to install it first before anything shows up in the 'Games' menu. did you try to install through apt-get and just don't see an launcher in the menu and assume it isn't installed?

---

### Post by psychofish25 on 2008-02-22
> **chipants said:**
> that's not nearly enough information to help you out.

1) did you downlaod a binary package from a website? was it a source package that needs to be compiled? did you get it from an apt repository? you say you 'downloaded' but it didn't 'install'.

2) once again, you say you downloaded and it didn't install. when you download something, you generally need to install it first before anything shows up in the 'Games' menu. did you try to install through apt-get and just don't see an launcher in the menu and assume it isn't installed?
It wasnt source code or anything, it was simply a tar.bz2 file and when I extracted it, it was simply a bunch of files. There was no option to install anything. I couldnt find it on synaptic.

---

### Post by chipants on 2008-02-22
> **psychofish25 said:**
> It wasnt source code or anything, it was simply a tar.bz2 file and when I extracted it, it was simply a bunch of files. There was no option to install anything. I couldnt find it on synaptic.

are you sure it wasn't source? where did you get the file? if i knew what you were looking at, it would be much easier to help you install correctly.

---

### Post by avdzm on 2008-02-22
> **psychofish25 said:**
> It wasnt source code or anything, it was simply a tar.bz2 file and when I extracted it, it was simply a bunch of files. There was no option to install anything. I couldnt find it on synaptic.

extract the files into a folder
open the terminal go to the folder.

If you see a "configure" file, type
```

./configure
make
sudo make install

```

or if u see a *.sh file, type
```

sh *.sh

```

Usually the sites you download from tell you how to install and run.

---

### Post by chipants on 2008-02-22
i think you can safely ingnore avdzm's instructions. i think i found the file you downloaded from the developer's website. it looks like the tar.bz2 archive contains the executable file. from the terminal, navigate to the folder with all the game files and type:

./phun

that should start the game.

if it doesn't work, then check out the README.txt file in the folder. i glanced through it and it lists some dependencies that may not be met. meaning, you may need to install other software to get it to work, assuming your hardware meets it's requirements.

---

### Post by avdzm on 2008-02-22
I just download phun,

the files are already compiled, 
so you just have to dbl click on the file called "phun" or
type ./phun in terminal.

---

### Post by milesje on 2008-02-22
if you want to just be able to type phun in the terminal and have it run you will need to set up an alias to do so. put the alias in the .bashrc file that is in your home directory. you can do a man on alias to see how to create an alias if you do not know. All a desktop icon is, is a shortcut so I do not know what you mean by "how I could make a Desktop icon for this (not a shortcut)". You can add it to the Games menu in the Applications menu by go to System->Preferences->Main Menu and then adding a entry there that has the full path to launch the game just as if you where going to start it in a bash shell (terminal). You may have to restart your xserver to get the memu to show up, just logout and log back in and it should be there.

---

### Post by psychofish25 on 2008-02-22
I realize I can simply click on the Phun executable, now I want to add it under Applications->Games, yet you can only place a "launcher" in there, which I do not know how to use. I guess I'll look around.

Great answers,
Jordan

---

### Post by chipants on 2008-02-22
> **psychofish25 said:**
> I realize I can simply click on the Phun executable, now I want to add it under Applications->Games, yet you can only place a "launcher" in there, which I do not know how to use. I guess I'll look around.

Great answers,
Jordan

actually, just like milesje said, go to System->Preferences->Main Menu. all you have to do is create a new entry under the games menu and then add the path to the executable file, wherever you decided to put it. that is THE way to do it. it's very easy.

---

