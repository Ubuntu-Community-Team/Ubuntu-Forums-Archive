---
title: "Cannot launch a game"
date: 2009-06-10
forum: General Help
---

### Post by jordanae on 2009-06-10
I downloaded a game and went to launch it. I did the chmod a+x to get permission to execute it, and after that I put ./NameOfGame to launch it. But instead of launching the game I got "exec: 22: ./NameOfGame.bin: Permission denied" in the terminal.
I noticed that it said .bin after the filename although the game doesn't have a file extension. I looked in the folder and it turns out there is another file by the same name that is a .bin file. 
To make sure the terminal knew which file I meant I slightly changed the .bin to NameOfGame1.bin and reran ./NameOfGame. But it now it just says "exec: 22: ./NameOfGame.bin: not found"
Then I tried double clicking on the file to see if it would launch that was. A box came up asking how I wanted to open it. When I opened in terminal a window popped up for a second and closed immediately. Also, nothing happens if I just click "Run".

So, any help?

---

### Post by jonobr on 2009-06-10
In the words of Abba

"whats the name of the game"

Could you do an ls -l on the name of the game in where you have installed it

---

### Post by jordanae on 2009-06-10
Well the game is World of Goo, and the output for ls -l is

```
-rw-r--r--  1 jordan jordan    8776 2009-02-10 16:35 eula.txt
-rw-r--r--  1 jordan jordan   52841 2009-02-10 16:37 icon.png
drwxr-xr-x  2 jordan jordan    4096 2009-02-15 18:11 icons
drwxr-xr-x  2 jordan jordan    4096 2009-02-15 18:12 libs
-rw-r--r--  1 jordan jordan   11247 2009-02-10 16:37 linux-issues.txt
-rw-r--r--  1 jordan jordan   10892 2009-02-10 16:37 linux-issues.txt~
drwxr-xr-x  2 jordan jordan    4096 2009-02-15 18:11 properties
-rw-r--r--  1 jordan jordan   15804 2009-02-10 16:35 readme.html
drwxr-xr-x 12 jordan jordan    4096 2009-02-15 18:12 res
-rwxr-xr-x  1 jordan jordan     536 2009-02-10 16:37 WorldOfGoo
-rw-r--r--  1 jordan jordan 4013816 2009-02-10 16:37 WorldOfGoo.bin

```

---

### Post by Cheesemill on 2009-06-10
There's no need for you to use the .bin file for World of Goo, just download the .deb instead to automatically install it and add it to your Applications menu.

Cheesemill

---

### Post by jordanae on 2009-06-10
Well I found the solution as embarrassing as it is. I ran ./WorldOfGoo.bin O.o

---

### Post by jonobr on 2009-06-11
When running this from a terminal, you need to be in the same directory as the executable to execute the file.

I e if your game is in /home/myhome/desktop/games/fps
and you are in your home directory
(/home/myhome)

doing the dot slash will not execute the game unless the game is in your path.

If it cant find this in the dir you are in, it will look in your path and if not there issue an error.

your path can be seen be doing 

```
echo $PATH
```

So , to run the game you can cd to your location where the executable is,
you could run it using an abolute directory

eg,
/home/myhome/desktop/games/fps/shootemup.bin
or you could put it in your search path.
Not wise if you are familiar with changing enviroment variables

---

