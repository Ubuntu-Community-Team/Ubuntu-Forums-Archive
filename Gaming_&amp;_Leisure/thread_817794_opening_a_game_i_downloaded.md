---
title: "opening a game i downloaded"
date: 2008-06-03
forum: Gaming &amp; Leisure
---

### Post by Auntoldstory on 2008-06-03
[FONT="Comic Sans MS"]I just downloaded americas army and im new to ubuntu..I have xubuntu and i was trying to open the game and it kept opening mousepad? how do i install this game?[/FONT]

---

### Post by Sef on 2008-06-03
Moved to Gaming and Leisure.

---

### Post by Prospero2006 on 2008-06-04
You have to drive down to your local recruiting office, raise your right hand, sign a few documents, and pow. You're right in the middle of the action.

---

### Post by 4th guy on 2008-06-04
What is the name of the file you downloaded?

---

### Post by Auntoldstory on 2008-06-04
[FONT="Comic Sans MS"]armyops250linux.run   ....It says its a shell script...And by the way i already did join..lol[/FONT]

---

### Post by Sockerdrickan on 2008-06-04
:lol:

---

### Post by Auntoldstory on 2008-06-04
[FONT="Comic Sans MS"]Okay so i got it to open and run it but i ran into a problem..Its supposed to be put in a file/directory? named usr/local/armyops/ but when i hit "ok" it tells me something about no permission to write or some crap..[/FONT]

---

### Post by 4th guy on 2008-06-04
You have to run the program with administration privileges. I'll give you the easy way:

copy your file (armyops250linux.run) to your home directory. (/home/<yourusername>)
open the terminal (applications > accessories > terminal)
write (without quotes) "sudo ./armyops250linux.run" and press enter
enter password and press enter (don't be alarmed if no stars appear while writing your password, it's a security feature)
if you entered the password correctly, the program will let you install

Don't hesitate to come ask questions if you run into problems. After you have verified that it has installed correctly, you can delete the installer (armyops250linux.run) from your system.

PS: The America's Army Linux client is outdated, the developers stopped supporting it a while ago.

---

### Post by Auntoldstory on 2008-06-04
[FONT="Comic Sans MS"]Okay I did as you instructed and I hit a wall...Should my terminal say christopher@christopher-desktop:~$  ? Because when i did the sudo. /armyopslinux250.run thing it told me directory does not exist...I do know its unsupported but AA stopped producing updates/newer versions for linux..Im running V2.8.1 on my windows computer.. [/FONT]

---

### Post by Auntoldstory on 2008-06-04
[FONT="Comic Sans MS"]Im now getting "command not found"..I hope im not troubling you guys with this..[/FONT]

---

### Post by 4th guy on 2008-06-04
Yes, the terminal should say that.
Try typing

chmod o+w armyopslinux250.run

or

chmod o+w ./armyopslinux250.run

(not sure which one)

before doing sudo ./armyops250linux.run

---

### Post by Auntoldstory on 2008-06-04
"command not found" does it matter if im running xubuntu?

---

### Post by Auntoldstory on 2008-06-04
[FONT="Comic Sans MS"]Okay so I got some progress..I right clicked the download, Hit "execute"..Then when I got to the screen where it asks for a location to install to I typed  /Home/Christopher/Armyops/   ...Now im at a screen that says "Installing..." "Installing Base Install..." And the meter goes to a hundred and starts over again and its done it tons of times but at different speeds each time...[/FONT]

---

### Post by RadarBat on 2008-06-04
You misplaced the dot (.) in the command. It should be before the / not after the sudo

---

