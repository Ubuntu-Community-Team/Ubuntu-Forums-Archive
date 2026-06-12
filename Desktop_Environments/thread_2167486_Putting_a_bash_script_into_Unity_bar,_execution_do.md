---
title: "Putting a bash script into Unity bar, execution does not work"
date: 2013-08-13
forum: Desktop Environments
---

### Post by linux_dream on 2013-08-13
Hi guys,
I'm using Ubuntu 12.04 (64 bits version), I was using Ubuntu 12.04 (32 bits version) but formatted my disk and installed the 64 bits version. So I'm trying to get back all I had.
Some proceedures that used to work don't seem to work anymore.
I need help to put a bash script into Unity bar. I already have the bash script written and it executes fine when I double click on the file and execute it from the terminal.
Here is the proceedure I've followed:
----------------------------------------------------
1)Open a terminal and type 
```
gksudo gedit /usr/share/applications/goban.desktop
```
So this opens gedit. In this file I type:
```
[Desktop Entry]
Name=goban
Comment=kgs go server
Exec=sh /home/isaac/Games/goban/goban.sh
Icon=/usr/local/bin/kgs.png
Terminal=true
Type=Application
StartupNotify=true
```
2)Go to  /usr/share/applications and move the .desktop file into unity bar.
---------------------------------------------------
This always worked with all kind of bash scripts I have done. (3 for chess programs, 1 for kgs go server and 1 for a simple program I worte myself).
I can see the desktop entry in /usr/share/applications with the icon I chose in /usr/local/bin/, I can even move it into Unity bar. The problem is when I click on the icon in the Unity bar.
For example the above code does nothing. The computer seems to think for a few seconds but nothing appear. It should start a java interface that would let me enter in kgs go server. 

The bash script itself is very simple:
```
#!/bin/bash
java -jar cgoban.jar 

``` and as I said, it executes fine when I double click on it and select "execute from a terminal".

I have other errors for bash scripts of chess engines, they were working 2 days ago prior to the formatting of my disk. But hopefully by fixing this one I'll be able to handle the other errors.
Thanks for any help!

---

### Post by linux_dream on 2013-08-20
Hey guys, I still haven't fixed the problem. Any idea? 
It must be that the .desktop file is wrong somehow, despite working in Ubuntu 12.04 (32 bits). I don't know what to modify in order for it to work for Ubuntu 12.04 (64 bits).
Thanks for any help.

---

### Post by Petro Dawg on 2013-08-20
Is your program supposed to open in terminal or in GUI?

---

### Post by linux_dream on 2013-08-20
This one in particular, a GUI. However it also works if I open it in the terminal.

---

### Post by Petro Dawg on 2013-08-20
[FONT=verdana]The reason I asked is because I saw your .desktop file differed from what I typically do for GUI apps.

First I set:
[COLOR=#000000][FONT=arial]Terminal=**false**[/FONT]

[SIZE=2]Yes even for bash scripts which run in terminal before executing the GUI program.
[/SIZE]
also:
[FONT=arial]StartupNotify=**false**[/FONT]

Also I will typically save my .desktop files in ~/.local/share/applications  and then just search for my app in the unity dash and drag to my launcher.

Not sure if any of that will make a difference, but it's what I do and it seems to work for me.[/COLOR][/FONT]

---

### Post by linux_dream on 2013-08-20
> **Petro Dawg said:**
> [FONT=verdana]The reason I asked is because I saw your .desktop file differed from what I typically do for GUI apps.

First I set:
[COLOR=#000000][FONT=arial]Terminal=**false**[/FONT]

[SIZE=2]Yes even for bash scripts which run in terminal before executing the GUI program.
[/SIZE]
also:
[FONT=arial]StartupNotify=**false**[/FONT]

Also I will typically save my .desktop files in ~/.local/share/applications  and then just search for my app in the unity dash and drag to my launcher.

Not sure if any of that will make a difference, but it's what I do and it seems to work for me.[/COLOR][/FONT]
Here is what I just tried: 
```
[Desktop Entry]
Name=goban
Comment=kgs go server
Exec=sh /home/isaac/Games/goban/goban.sh
Icon=/usr/local/bin/kgs.png
Terminal=false
Type=Application
StartupNotify=false
```
Then I go to /usr/share/applications, I see the "goban" icon and I drag it into Unity bar. Then I click on it (in Unity bar), nothing happens as usual. It looks like the computer thinks for a few seconds but nothing pops up.

---

### Post by stinkeye on 2013-08-20
Instead of execing a script to run a java command try just using the java command as the **Exec=** ...
```
Exec=/usr/bin/java -jar cgoban.jar
```


**PS**: I usually create custom launchers in **~/.local/share/applications**
Don't need root to edit...
Makes them only available to the user who created them and are saved
when you back up your home folder.

You can also copy .desktop files from **/usr/share/applications** to **~/.local/share/applications** and customize.

A .desktop file in ~/.local/share/applications will override a .desktop file in /usr/share/applications of the same name.

---

### Post by linux_dream on 2013-08-20
> **stinkeye said:**
> Instead of execing a script to run a java command try just using the java command as the **Exec=** ...
```
Exec=/usr/bin/java -jar cgoban.jar
```

I just tried this, it does exactly the same as before. Computer seems to "think" for a bit and then nothing happens. 
Thanks so far guys.

---

### Post by linux_dream on 2013-08-20
GUYS I FIXED THE PROBLEM!!!
The problem was in my bash script, ```
#!/bin/bash
java -jar cgoban.jar
``` doesn't work (althought it used to work for Ubuntu 12.04 32 bits version.) 
I had to change it to 
```
#!/bin/bash
java -jar /home/isaac/Games/goban/cgoban.jar
```
Thanks for all. Problem solved.

---

