---
title: "Sacred Please!!!"
date: 2004-12-11
forum: Gaming &amp; Leisure
---

### Post by puzzledm on 2004-12-11
I realy really really really really really want to get sacred running on Ubunutu ... it is the only reason I still have a windows partition running.  

Can someone who knows what they are doing just take a look at it for me ... I have cedega 4.1 and have managed to succesfully run the installer but then nothing works.

I had to run the command that told cedega to use version winxp but can't get it to do anything else ....

oh please please please please please help!

---

### Post by puzzledm on 2004-12-16
Okay so I have cancelled the issue down to a possible problem with the recognition of cedega as a program in gnome.  When I enter the command "cedega /home/matthew/.transgaming......blah_blah..../game.exe" it comes back saying cedega can't find the file.  So I try finding the file in nautilus and right clicking choosing 'open with' and enter 'cedega' it says it can't add cedega as a program to the list.  

Isn't that a bit strange? Does anyone have any ideas?

---

### Post by jdodson on 2004-12-16
[QUOTE=puzzledm]Okay so I have cancelled the issue down to a possible problem with the recognition of cedega as a program in gnome.  When I enter the command "cedega /home/matthew/.transgaming......blah_blah..../game.exe" it comes back saying cedega can't find the file.  So I try finding the file in nautilus and right clicking choosing 'open with' and enter 'cedega' it says it can't add cedega as a program to the list.  

Isn't that a bit strange? Does anyone have any ideas?[/QUOTE]

go to the directory where the file resides and try "cedega ./game.exe"  i bet you have a problem with the path.

---

### Post by gheorghe_pop on 2004-12-16
doesen't the game work with winex?

---

### Post by puzzledm on 2004-12-17
i can't actually 'cd' to the directory where the game is it comes back saying 'no directory found'  

something like:
cd /home/matthew/.transgaming/c/my programs/ascaron entertetainment/game.exe

and it says no directory found, so I put '_' underscores in to pretend spaces and that still doesn't work - works fine with every other folder.

just strange!!!

---

### Post by wulf on 2004-12-17
Shouldn't the space be escaped with a backslash? Eg. *My\ Programs*? Don't forget it's case sensitive as well - my windows drive uses quite a lot of initial capitals.

Wulf

---

### Post by jdodson on 2004-12-17
[QUOTE=wulf]Shouldn't the space be escaped with a backslash? Eg. *My\ Programs*? Don't forget it's case sensitive as well - my windows drive uses quite a lot of initial capitals.

Wulf[/QUOTE]

right, you can also hit 'tab' when you start typing in a directory to autocomplete it.  when i need to enter my fake_windows and then My Documents i tab it at My and it autocompletes the \ and everything.  makes it a bit easier.

---

