---
title: "help using wine"
date: 2006-12-14
forum: Gaming &amp; Leisure
---

### Post by Refined Power on 2006-12-14
Hi I am complete newbie to wine and was wondering how to get started. I have installed Wine using automatix2 so I have it on my system and supposedly setup. But I am not sure how to go about getting games working on it. Are there any good tutorials out there(I tried Wine's web site but it was very difficult to understand) I want to install Blake stone, which is basically wolfenstien, a Dos program.  I tried using disbox but could not figure it out. any advice would be appreciated.
thanks


I found this little tutorial and got to the mounting part but i could not get it to mount,


1. Create a folder called "dosbox" in your home directory.
/home/username/dosbox where username is your username.

2. Download 1wolf14.zip from [http://www.wolf3d.co.uk/downloads/](http://www.wolf3d.co.uk/downloads/). Extract in /home/username/dosbox

3. download and install dosbox: sudo apt-get install dosbox

4. start dosbox: dosbox

5. mount the dosbox folder as your c drive: mount c /home/username/dosbox

6. Run install.bat

7. run wolf3d.exe

---

### Post by Shatrat on 2006-12-14
Well, in general to use wine you just use the command ```
wine <some windows program here>
```.
Wine has it's own windows style file tree in .wine in your home directory with Program Files and so forth in it and if you run an install program, the program gets installed there.  Then you just run ```
wine .wine/drive_c/Program\ Files/Program/executable.exe
``` or you can make a nice little bash script to launch the program or put all that into a button on your gnome panel or whatever.

As for running DOS games, I havent tried that.  I know you can get a dos prompt in wine by typing ```
wine cmd
``` But I think thats more like the dos prompt in windows XP and might not work with the game youre trying to run.

---

### Post by Refined Power on 2006-12-14
> **Shatrat said:**
> Well,

As for running DOS games, I havent tried that.  I know you can get a dos prompt in wine by typing ```
wine cmd
``` But I think thats more like the dos prompt in windows XP and might not work with the game youre trying to run.

So you think I should try running the game in DOSbox instead of Wine? Inline with that does anyone know how to mount the file? I have the exe file in mansfield/dosbox, but when i try to put in the command <mount c/home/mansfield/dosbox> it gives me some error that it was not able to mount the file.

---

### Post by unarmedninja on 2006-12-18
dosbox does work well with dosgames. i think you may have mounted it wrong. after you start dosbox you should be in the Z: drive, then you need to create a C: drive.
```
mount c /home/username/directory
```
(theres a space after the c that you didnt have above). this will mount your folder to a fake C: drive. you then need to switch to that drive ```
c:
```
then you can use dos commands to execute your program or view the folder with DIR.

good luck.

---

### Post by Sammi on 2006-12-18
Just a very very obvious reminder...

In this line:
mount c /home/username/directory
You need to remember to insert your own personal username that you use on your computer, with the word "username" ;):p

---

