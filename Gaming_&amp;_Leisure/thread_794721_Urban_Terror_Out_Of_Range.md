---
title: "Urban Terror Out Of Range"
date: 2008-05-14
forum: Gaming &amp; Leisure
---

### Post by nathanhillinbl on 2008-05-14
I just downloaded Urban Terror (the zip file) and made the i386 file executable and when i run it, it displays out of range for my monitor, and i can't play it.

Any ideas??


Thanks,
Nate Hill

---

### Post by NightwishFan on 2008-05-14
Set your resolution to 1024x768 before you try to play, that might work.

---

### Post by Frem on 2008-05-15
It is attempting to start the game at a resolution larger than your monitor can handle. Find the value "r_mode" in your config file and set it to "4". This will start the game in 800x600.

The config file should be located some place like:
/home/YourUserNameHere/.q3a/q3ut4/q3config.cfg

---

### Post by nathanhillinbl on 2008-05-15
The r_mode was already set to 4 and I tried setting my resolution to a painful 1024*768 (my norm is 1440*900) which also didnt work.

---

### Post by NightwishFan on 2008-05-15
See if you can edit the config file to change the refresh rate in game.

---

### Post by periphery on 2008-11-20
Changing my resolution didn't work but editing the config file and telling the game to run windowed did solve the run time issues on my LCD.

i.e 
Open the file with a text editor:

/home/YourUserNameHere/.q3a/q3ut4/q3config.cfg 

Find the line:

seta r_fullscreen "1"

And change to:

seta r_fullscreen "0" 

Save changes and you should be good to go!!

---

### Post by Gen2ly on 2009-02-17
i saw this in another post that setting r_mode to -1 worked for me.

---

### Post by whistlerspa on 2009-06-06
I have the same problem and have tried all the above suggestions, alas to no avail. Does anyone know of any other things that I might try please?

---

### Post by pickarooney on 2009-09-28
I've tried all the mentioned suggestions but my monitor is still out of range. Only Alt-Enter works to play in windowed mode. This would be fine if I could increase windowed mode...

---

### Post by cocamoxb on 2009-10-06
Can you post your specs? CPU, Mem, OS, Vid card, etc?

---

