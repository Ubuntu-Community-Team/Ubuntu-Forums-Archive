---
title: "in dosbox, how to mount a folder listed in extra drive, or home"
date: 2017-09-03
forum: Emulators
---

### Post by seekertom on 2017-09-03
In windows, I have a folder c:\qa containing another folder game, which contains my dos program called ace.exe. This would be c:\qa\game\ace.exe. In dosbox I enter the following: 

mount c c:\qa
c:                    ( this gets me into c:\qa )
cd   game        ( this gets me into c:\qa\game )
ace                  ( this runs the program ace.exe from c:\qa\game )

How to I structure my windows commands shown above, to do the same thing in ubie?
I think my first issue is where to put the folder qa, since I don't really have a drive c: ? 
Next issue would be what to type to mount it.
then....?
sheesh...:mad:

hope you can help!

st
Yup! Y'alls help did help, so thanks!
this is what I entered...

mount c /home/tom
c:
cd qa
ace

st

---

### Post by deadflowr on 2017-09-03
*Thread moved to **Emulators***


You can put the qa folder in your home folder somewhere, perhaps create a new Games folder.
then to mount, it's basically the same structure as Windows
```
mount C /some/folder/location
or
mount C /home/your-username-here/Games
```

To create a Games folder either open Files and right click in the main window area and select "create/new folder" then locate the new folder marked as unknown folder and right click and select rename to rename it Games,
or
open a terminal and run
```
mkdir Games
```
both by default will create a new folder in your main home folder, the same area as your Documents Pictures, Videos folders are located.

---

### Post by Perfect Storm on 2017-09-03
Wouldn't it just be

**mount c c:\ **instead of **mount c c:\qa**

By the way youo should check out: DOSBox Game Launcher it's way easier and you can set games up with a click: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)

---

### Post by Dennis N on 2017-09-03
You don't have to manually mount the application's folder in dosbox. All you need is a path to the executable, and dosbox will mount the folder and start the program automatically.

Example from this computer. I created a folder dosgames, then a separate subfolder for each game:

```
dosbox /home/dmn/dosgames/brain/BRAIN.EXE
```

---

### Post by seekertom on 2017-09-03
In win, dosbox complains about trying to mount the root directory. Besides, I have many other folders in \qa that I go to, and all have the same executable. keeping each program in the qa folder keeps them together, and in separate folders
to make it easier for me to keep track of. Thanks for the help!
st

---

