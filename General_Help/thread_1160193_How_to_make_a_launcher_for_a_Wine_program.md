---
title: "How to make a launcher for a Wine program??"
date: 2009-05-15
forum: General Help
---

### Post by Sergio7676 on 2009-05-15
Hi all!


I am trying to set up a launcher for my Oxford dictionary which works with wine. After looking in the forums and having a look to Wine's documentation I typed this on the command line of the launcher 

'/home/sergio/.wine/dosdevices/c:/Program Files/Common Files/Diccionario/OxfordPortable/coed11.exe' 


Someone suggested my to type

wine '/home/sergio/.wine/dosdevices/c:/Program Files/Common Files/Diccionario/OxfordPortable/coed11.exe' 


Using one command line or the other I got this error message window:

Failed to open COED11 dictionary file

If I try to open the exe file with wine the dictionary works fine. The problem is that I use it a lot and I would really need a launcher.

My Wine version is 1.0.1, O.S Ubuntu 9.04

Thanks in advance!

---

### Post by mc4man on 2009-05-15
Maybe try 1 or 2 different ways for launch command (use 'windows' syntax 

```
wine "C:\Program Files\Common Files\Diccionario\OxfordPortable\coed11.exe"
```

```
env WINEPREFIX="/home/sergio/.wine" wine "C:\Program Files\Common Files\Diccionario\OxfordPortable\coed11.exe"
```


If coed11.exe can 'standalone' (work without being in OxfordPortable folder ) you could move or place a copy of  it in the windows folder and then use a 'wine wrapper script' named coed11 placed in a bin dir. in your path.

Then the command to start would just be coed11 (the same as 'notepad' and 'regedit' work


A short description of how to use wine wrapper script is here ( for something else, idea is the same, may work, may not

[http://ubuntuforums.org/showthread.php?p=7262865#post7262865](http://ubuntuforums.org/showthread.php?p=7262865#post7262865)

---

### Post by Sergio7676 on 2009-05-15
Thank you for your answer mc4man. Unfortunately, none of your code lines worked, I get the same error. Besides the exe file cand stand on his "own".
I guess, It's going to be very difficult to find a solution...

Cheers

Sergio

---

### Post by mc4man on 2009-05-15
Unfortunately can't test (assume it was installed from a cd(s)

Did you try browsing  to  drive_c.....ect, and right clicking on coed11.exe -> make link. Then drag the link to your desktop? and see if it works

( noting that in the right click ->  properties -> open with of any .exe it should be set to "Wine Windows Program Loader" as the default

---

### Post by Sergio7676 on 2009-05-15
I have just tried, when I double click the link no response all. I do not even get an error message.... I downloaded the dictionary and unziped it in common files (Wine).

Cheers

Sergio

---

### Post by soro2005 on 2009-05-15
Try
```
Exec=env WINEPREFIX="/home/YOUR-USERNAME/.wine" wine "C:\\Program Files\\Common Files\\Diccionario\\OxfordPortable\\coed11.exe"
```

---

### Post by Sergio7676 on 2009-05-15
Hi soro2005, thank you for your response, after using you command line
I got this error message:

There was an error launching the application.

Details: Failed to execute child process "Exec=env" (No such file or directory)

Cheers

Sergio

---

### Post by soro2005 on 2009-05-15
Oh, I thought you were editing the .desktop file directly. Try without Exec= at the beginning. Sorry.

---

### Post by Sergio7676 on 2009-05-15
No problem!. I've tried again but not even an error message!

Cheers

Sergio

PS; I am just posting your lines in the command launcher menu

---

### Post by soro2005 on 2009-05-15
Try it in a terminal. There might be more output.
```
env WINEPREFIX="/home/sergio/.wine" wine "C:\\Program Files\\Common Files\\Diccionario\\OxfordPortable\\coed11.exe"
```

---

### Post by Sergio7676 on 2009-05-15
I have tried in the terminal, I got the error I had at the begining...

Failed to open COED11 dictionary file

I guess this cannot be done, I will go to the folder and execute the dictionary from there

Thank you very much for your help!

---

### Post by soro2005 on 2009-05-15
Ah, okay. So the .exe starts, but fails to locate some data file it seems.

You can always write a little script, and then launch the script. For instance, something like:
```

#!bin/bash
cd /home/sergio/.wine/drive_c/Program\ Files/Common\ Files/Diccionario/OxfordPortable
wine coed11.exe
```
Save it something.sh, and make it executable with
```
chmod +x something.sh
```
test it in a terminal with
```
./something.sh
```
If it works, make a launcher that points to something.sh.

---

### Post by mc4man on 2009-05-15
If the script doesn't work (and I've had a couple of occasions where a valid command only worked properly when executed from a script) could you describe this (overall I'm curious anyway

> If I try to open the exe file with wine the dictionary works fine

How is it that you open the .exe?  You go to the folder and...?

---

### Post by Sergio7676 on 2009-05-15
mc4man I just open it with the option "Wine Windows program loader".

On the other had, I have tried to make the script but I am just a beginner...
I write the script with Ubuntu's default text editor and then I save it with the sh extension. But where should I save it?. After trying to execute it from terminal I got this error message:

bash: ./oxford.sh: bin/bash: bad interpreter: No such file or directory

I apologize for my ignorance :(

---

### Post by mc4man on 2009-05-15
2 things
> I just open it with the option "Wine Windows program loader

Did you right click -> **properties** -> **open with** -> set "Wine Windows program loader" as the default before? (click little radio button

Then a double left click becomes the same as what you're presently doing and the right click -> make link, ect. should work


..........................................................................

For the script save it in your home folder (places -> home
(you really don't need the .sh but leave it

then run (assuming you named it oxford.sh
```
chmod +x  oxford.sh
```

After that try in terminal again
./oxford.sh
If it works ok then,....

For launcher command just browse to it (the script) and mark 'Type" as "application in terminal"

---

### Post by alwayshere on 2009-05-15
command =  winefile

command =  winecfg

right click on desktop and click "create launcher"

use one of above commands eg winefile and name it what ever ya want 
make two launchers one for each command.

---

### Post by barraclou on 2009-05-15
Have you simply tried to go in your wine applications menu, then right-click on the application you want? It worked just fine for me.

---

### Post by soro2005 on 2009-05-15
> **Sergio7676 said:**
> 

bash: ./oxford.sh: bin/bash: bad interpreter: No such file or directory

I apologize for my ignorance :(

try /bin/sh instead of /bin/bash in the first line of the script. You can probably skip the first line entirely and leave it to the shell to pick the right interpreter. (Looks like you don't have bash installed)

But I have to agree: If you have it in the Wine menu and can start it from there, then you can find the correct Exec line by simply opening a text editor, such as gedit, and dragging and dropping the menu entry onto the text editor. That will open the menu entry in the editor, and you can just copy the Exec line...

---

### Post by mc4man on 2009-05-16
to quote the OP
> .. I downloaded the dictionary and unziped it in common files (Wine).


I don't believe it was 'installed' per se, so probably no menu entry.

If a r. click "open with" " Wine Windows program loader" works then creating a file association for .exe of - "Wine Windows program loader" should make a d. left click work and then by extension a link should work

---

### Post by CatKiller on 2009-05-16
> **Sergio7676 said:**
> wine '/home/sergio/.wine/dosdevices/c:/Program Files/Common Files/Diccionario/OxfordPortable/coed11.exe' 


Using one command line or the other I got this error message window:

Failed to open COED11 dictionary file

Launchers are .desktop files. They are quite straightforward. The easiest way is probably to create the launcher on your Desktop first, so that it's easy to edit.

Having created the launcher for the above command on your Desktop, you can open a Terminal and run ```
gedit Desktop/*.desktop
``` to edit the file that you've made. It's probably as simple as adding in a line that says ```
Path=/home/sergio/.wine/dosdevices/c:/Program\ Files/Common\ Files/Diccionario/OxfordPortable
``` You might also find that you need to take out the quotes and "escape" the spaces in your command line so that it reads ```
wine /home/sergio/.wine/dosdevices/c:/Program\ Files/Common\ Files/Diccionario/OxfordPortable/coed11.exe
```

---

### Post by Sergio7676 on 2009-05-17
Sorry, I was not able to post before. I want thank all of you for your help. I did not manage to solve the problem, but in a few weeks I will be able to get an original cd copy of the dictionary.That is gonna solve my issue cos I will be able to make a launcher from the Wine's application Menu.

Thanks again, This community rules!


:D

---

