---
title: "warzone 2100"
date: 2012-01-02
forum: Gaming &amp; Leisure
---

### Post by Silas1989 on 2012-01-02
Hello everyone,

I just installed the game warzone 2100 on my ubuntu 11.10 installation. A problem however is that is doesn't work. every time i try to start the game ubuntu simply logs out... It has worked only once, right after installing the game, but it doesn't anymore now.

Does anyone know what is wrong??

Thanks in advance

---

### Post by Silas1989 on 2012-01-03
bump

---

### Post by oldos2er on 2012-01-03
Moved to Gaming & Leisure

---

### Post by DangerOnTheRanger on 2012-01-03
I haven't noticed this problem with Warzone 2100, though I have noticed this problem with a few other games - it looks like a possible Ubuntu bug. Anyone else have this problem?

---

### Post by donkyhotay on 2012-01-05
Try running the game from CLI (terminal) and post the crash dump here.

---

### Post by Silas1989 on 2012-01-05
i can't, since it logs out it also closes the terminal and then the next time i open the terminal it is empty again.

---

### Post by Arthur_D on 2012-01-06
Try piping the output to a file, like 'warzone2100 > ~/warzone_crash.txt'

Maybe you can get something useful out of it, maybe not. Worth a try though. :)

---

### Post by donkyhotay on 2012-01-06
> **Silas1989 said:**
> i can't, since it logs out it also closes the terminal and then the next time i open the terminal it is empty again.

Are you choosing 'run in terminal' from the menu system or actually opening the terminal? It doesn't make sense that if you go to applications, click on terminal, at the prompt type in the command to launch warzone2100 (can't remember it off-hand) that the entire terminal window closes. If it does then you'll need to try piping it like arthur_d recommended.

---

### Post by Silas1989 on 2012-01-07
okay, so i tried this by piping the output, but.... it's kinda empty XD.

The problem is also quite direct, the user logs out DIRECTLY after the input of the "warzone2100" command line (if i add the command > ~/warzone.txt it waits just a short while and then still logs out)

any other suggestions??

---

### Post by donkyhotay on 2012-01-07
> **Silas1989 said:**
> okay, so i tried this by piping the output, but.... it's kinda empty XD.

The problem is also quite direct, the user logs out DIRECTLY after the input of the "warzone2100" command line (if i add the command > ~/warzone.txt it waits just a short while and then still logs out)

any other suggestions??

Without an error prompt that will involve some guesswork. I'm assuming no other games do anything like this. How many other games have you tried (especially 3D games)? What type of video card and drivers do you have? Since it worked once you might try deleting the .warzone2100 folder (it's hidden in your home folder) but thats just a shot in the dark.

---

### Post by Silas1989 on 2012-01-09
deleting the folder didn't work, but i noticed that i might be piping the prompt wrong, since i tried it on another program that did work and the file also came out empty, are you sure that the suggested code above works??

---

