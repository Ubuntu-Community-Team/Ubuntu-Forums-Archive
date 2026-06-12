---
title: "Help With Fluxbox!!!!!!"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by bloodhacker2 on 2008-01-30
OK guy's i need sum help BAD...

I have already figured out how to install fluxbox on to ubutu linux and i was successful at installing it, but now i have no idea on how to add a them to fluxbox..
i have surcharge the internet all day and night to figure this out but i guess this is just way over my head.
sooo hear is what i am looking to do, i would like to know how to add this them 
[http://themes.freshmeat.net/projects/serbianfrost/](http://themes.freshmeat.net/projects/serbianfrost/)    to fluxbox. 

PLEAS GIVE ME STEP BY STEP INSTRUCTION FROM DOWNLOADING TO THE FINISH INSTALLATION BECAUSE I AM COMPLIANTLY LOST AND I WOULD LIKE TO HAVE THIS.

Thanks..

---

### Post by p_quarles on 2008-01-30
The command line way to do this:

1) Locate and go to the folder to which you downloaded the file.
2) Run this command:
```
mv serbianfrost-default-2.0.tar.gz ~/.fluxbox/styles
```
3) Go to that folder:
```
cd ~/.fluxbox/styles
```
4) Unpack the file:
```
tar -zxvf serbianfront-default-2.0.tar.gz
```
5) You're done. It will now be in your styles menu.

If you want to do this with a graphical filebrowser, I would need to know which one you are using before I can give you directions.

---

### Post by bloodhacker2 on 2008-01-30
> **p_quarles said:**
> The command line way to do this:

1) Locate and go to the folder to which you downloaded the file.
2) Run this command:
```
mv serbianfrost-default-2.0.tar.gz ~/.fluxbox/styles
```
3) Go to that folder:
```
cd ~/.fluxbox/styles
```
4) Unpack the file:
```
tar -zxvf serbianfront-default-2.0.tar.gz
```
5) You're done. It will now be in your styles menu.

If you want to do this with a graphical filebrowser, I would need to know which one you are using before I can give you directions.



ok i downloaded the folder without unzipping it yet and then i ran the first command in the terminal and it is saying No such file or directory.

And when i am in fluxbox how am i suppose to find the file. lol i am telling you man i am all new to this but i have wanted to lune so BAD how to do this lol so just bare with me lol.

---

### Post by p_quarles on 2008-01-30
Can you post the output of this command?:
```
ls -a ~/.fluxbox
```

---

### Post by bloodhacker2 on 2008-01-30
.   init       keys           menu       menu.save.1  startup
..  init.save  lastwallpaper  menu.save  slitlist     styles 


that is what it gave me.
what did that command do jw?

---

### Post by bloodhacker2 on 2008-01-30
do you think you could show sum screen shots on how to do this or maby make a movie???

---

### Post by p_quarles on 2008-01-30
Okay, so your ~/.fluxbox/styles directory is definitely there, so I'm guessing the problem is that you weren't in the same directory as the theme package. Try this:
```
mv ~/Desktop/serbianfrost-default-2.0.tar.gz ~/.fluxbox/styles
```
That should replace the first step in the sequence I gave you above. If that works, then you can run the rest of the commands I gave you. 

The "ls -a" command just provides a list of items inside of a directory.

---

### Post by bloodhacker2 on 2008-01-30
ok i see so you are basically telling it to go to the desktop and find the folder and then run the rest of the command..

---

### Post by bloodhacker2 on 2008-01-30
OK cool i finally figured it out, but i don't know how to add a background.
i found this code 

session.screen0.rootCommand: fbsetbg -f ~/backgrounds/zimdib_dark.png
but my question is,
1. do i replace the zimdib_dark.png to the name of the background i am wanting to add
2. where do i place the back ground at, do i place it on the desktop or in the background section of appearance and preferences??
3. how do i get one of tows cool side bars that have the cpu speed and ram speed and all that good stuff??
Ataraxia.jpg

---

### Post by p_quarles on 2008-01-30
You can put the background image in whatever folder you like, though having a special folder to keep them in makes it easier. For instance, I made a folder called "wallpapers" by running this:
```
mkdir wallpapers
```
Now, whenever I download a new background, I make sure it goes there.

To set the background, it would now be as simple as running this:
```
fbsetbg -f wallpapers/*name-of-image*.png
```
There are two info panels you can look at: gkrellm and conky. Both can be installed using apt-get. Using them, though, is a topic for another thread. ;)

---

### Post by bloodhacker2 on 2008-01-30
cool that works grate....

Now how do i make the terminal and the other windows transparent , when i change the focus window alpha to 0 and the unfocused windows alpha to 0 it dos int do anything??
how do i make it all transparent??

fbsetbg -f wallpapers/Serbian_Frost.jpg

---

### Post by p_quarles on 2008-01-30
The window alpha settings only change the window title bar transparency. You also have to click on "Force pseudo-transparency."

To get a transparent terminal, you need to configure the terminal itself. Which terminal program are you using?

---

### Post by bloodhacker2 on 2008-01-30
Right now i am using gnome terminal

---

### Post by p_quarles on 2008-01-31
In Gnome-terminal, click on the "Edit" menu, choose "current profile," select the "effects" tab and then set the background to transparent. You can set the transparency level with a slider.

---

### Post by rjmdomingo2003 on 2008-01-31
For some flux customizations, check out this tutorial: [http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+menu](http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+menu)

---

### Post by bloodhacker2 on 2008-01-31
ok cool.. 
i have one more question, how do i install  Beryl Emerald and where do i get it??

---

