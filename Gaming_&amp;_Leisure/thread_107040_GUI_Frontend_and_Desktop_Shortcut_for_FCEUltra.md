---
title: "GUI Frontend and Desktop Shortcut for FCEUltra"
date: 2005-12-22
forum: Gaming &amp; Leisure
---

### Post by joshuapurcell on 2005-12-22
I've been installing Ubuntu on my brother's computer, and since he has never used Linux before I've tried to make things as simple as possible for him to figure out once the computer is turned over to him. One thing I've done is make sure that every program he has been using in Windows is either working in Linux or has a replacement available, and I've put icons on the taskbar for all the most used programs.

During this process I made a shortcut for FCEUltra (NES Emulator) using Zenity and a short bash script. This shortcut doesn't just bring up fceu though.. it uses zenity to display a list of your roms in the directory specified in the bash script, and starts the rom chosen from the list in fceu. Here are the steps:

1.Install zenity and fceu:```
sudo apt-get install zenity fceu
```
2.Create the bash script that will run when clicking on the shortcut icon:```
sudo gedit /usr/bin/startfceu
```
Enter the following lines into the file. I've included an option for adding an icon to the zenity window, but it's not needed. I've also included the option for starting fceu in "fullscreen" at 800x600 resolution. Make sure to enter the correct path to your NES roms:```
#!/bin/bash
cd /path/to/nes/roms
GAME=$(zenity --title "FCEUltra - Select a Nintendo game to play" --window-icon=/icon/for/zenity/window --file-selection)
/usr/games/fceu -fs 1 -xres 800 -yres 600 $GAME
```
3.Make the new file executable:```
sudo chmod a+x /usr/bin/startfceu
```
You can test this script out now by typing **startfceu** at the command prompt. The only thing left is to create a desktop icon that points to this new script. Go to Applications -> System Tools -> Applications Menu Editor and create a new shortcut with your chosen name and icon, and make sure the command line says **startfceu**.

---

### Post by SlugO on 2006-02-13
Thanks for the guide. Since FCE Ultra doesn't seem to offer any easy way to configure keys it might be useful to do it in this script. I know it's not the most convenient way since you have to do it every time but atleast you don't need to do any hex editing this way.

Change the last line of the script to:```
/usr/games/fceu -fs 1 -xres 800 -yres 600 -inputcfg gamepad1 $GAME
```Remember to select **Start in terminal** in the menu editor when you're creating a shortcut for this one since it asks the keys in the terminal. It also seems to allow multiple keys for the same function but you can just press the same one twice when it's asking for them.

---

### Post by SlugO on 2006-02-15
Correction to my previous post: You only have to configure the keys once, then FCE Ultra remembers them. But still seems that the command line switch is the only way to configure them.

I just noticed that the graphical file selector doesn't work with files that include spaces, which is unfortunately almost all of them. Any idea how you could get the script to convert ' ' to '\ ' and '(' to '\(' so that it would work?

---

### Post by BoyOfDestiny on 2006-02-15
if you put "'"$game"'" does that work?
I tested with echo in terminal, if it returns everything in 'quotes', spaces should not be a problem...

---

### Post by SlugO on 2006-02-15
Well with the original script it gives```
Starting FCE Ultra 0.98.12...
Loading (PRG0).nes'...

Error opening "(PRG0).nes'"!
```
And with "'"$GAME"'" it just gives```
Starting FCE Ultra 0.98.12...
Loading (PRG0).nes'...

Error opening "(PRG0).nes'"!
```

The PRG0 is the last part of the file name.
Wish I knew more about shell scripting... :-k

---

### Post by joshuapurcell on 2006-03-20
Didn't know you guys were having problems with this script until now. The original script is the exact one that was working for me, but I should say that I made sure all my nes files were renamed to take out all punctuation (and to keep the nes directory easy to navigate). I'm pretty sure your problem is related to having some type of punctuation in the names of one or more of your games.

If you don't want to rename the files, you could also try enclosing **$GAME** in the last line of the bash script with single quotes instead of double quotes (double quotes will sometimes allow certain characters to be interpreted by the shell when single quotes will not). I would try this myself, but as mentioned before the computer I installed this on is with my brother on the other side of the country and my current laptop's processor is incapable of running even nes roms without getting pegged. Let me know how it works.

---

### Post by bleep on 2006-03-20
How do you get fceu to recognize an original NES gamepad connected to parallel?

---

### Post by punkrockguy318 on 2006-06-12
I have also developed a bit more extensive frontend to FCEU, check out my post here:
[http://ubuntuforums.org/showthread.php?t=195413&highlight=fceu](http://ubuntuforums.org/showthread.php?t=195413&highlight=fceu)
It supports sound, network, controller configuration, and there is more to come.

---

### Post by NMStang218 on 2006-08-10
I am getting this error messege after selecting the ROM in the GUI```
/usr/bin/startfceu: line 4: /usr/games/fceu: No such file or directory

```

What am I doing wrong? Sorry for the Newbie Q :sad:

---

### Post by punkrockguy318 on 2006-08-11
> **NMStang218 said:**
> I am getting this error messege after selecting the ROM in the GUI```
/usr/bin/startfceu: line 4: /usr/games/fceu: No such file or directory

```

What am I doing wrong? Sorry for the Newbie Q :sad:


ensure you have fceu installed:

sudo apt-get install fceu

---

