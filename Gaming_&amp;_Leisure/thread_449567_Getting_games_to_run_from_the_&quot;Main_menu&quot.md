---
title: "Getting games to run from the &quot;Main menu&quot;"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by blackjackel on 2007-05-20
Hello all, I've gotten Warcraft 3: The frozen throne running using wine -opengl... The command I use to run it is the following:

first I CD to: /home/blackjackel/.wine/drive_c/Program\ Files/Warcraft\ III/

then I type: wine Warcraft_III.exe -opengl

This command runs it just fine, after cding to that directory... HOWEVER, when I do this:

wine /home/blackjackel/.wine/drive_c/Program\ Files/Warcraft\ III/Warcraft_III.exe -opengl

It runs Warcraft 3, then asks for a CD. Even though the CD is in the drive the whole time. Shouldnt running that command all at once do the exact same thing as if I cd'd into the directory then ran Warcraft_III.exe?

The reason I ask is because I'm trying to add a main menu that runs warcraft 3 so that I dont have to run it through terminal every time I want to play, but I can't do that because of this problem.

This is driving me crazy! Please help :)

---

### Post by DeadSuperHero on 2007-05-20
I think it should be like this:

wine /home/blackjackel/.wine/drive_c/Program\ Files/Warcraft\ III\Warcraft_III.exe -opengl
One of your slashes was off.

---

### Post by blackjackel on 2007-05-20
> **Mr. Psychopath said:**
> I think it should be like this:

wine /home/blackjackel/.wine/drive_c/Program\ Files/Warcraft\ III\Warcraft_III.exe -opengl
One of your slashes was off.



The way you posted gives a not found error, the way I posted runs it and asks for a CD :X

---

### Post by Jarn on 2007-05-20
Yes, your slashes are fine. I don't know why it does that, but I have that problem too with some games. Guild Wars runs fine no matter how I run it, Counter-Strike and Oblivion need to be run from inside their directory.

I think you could fix it by creating a script that cded to the directory and ran it and then having a menu item run the script, but I'm not sure.

---

### Post by blackjackel on 2007-05-20
Thats EXACTLY what I just did...

For anyone having this problem:

Create a new file, then edit the file in a text editor... Add the required commands, then set the "command" in the main menu item to run the file... "sh /path/to/the/file/yourfilename" in my case it was this:

sh /home/blackjackel/.wine/drive_c/Program\ Files/Warcraft\ III/Run\ Warcraft

It should run just dandy :)

---

### Post by edemark on 2007-05-21
you may also do the following:
you create a file in the bin directory of your home dir. (the advantage of this is the fact that /home/youruser/bin is scanned alongside /usr/share/bin and /usr/bin so you can easily start your program) 
cd bin
touch wc3
nano wc3
(insert the following: 
cd "/home/youruser/.wine/drive_c/Program Files/Warcraft III/"
wine Warcraft_III.exe -opengl
save your file with ctrl+o)
chmod +x wc3

now you can run the game with wc3 from a terminal also you can make a launcher or add it to the menu
good luck

---

