---
title: "so ive tried all of the WOW how to's and still cant get it working"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by storky on 2007-04-01
hi there i am very new to linux and ubuntu but really want to get WOW running on my laptop. I have a hp DV2000 with an intel graphics card. I no that the hardware will run WOW fine because it worked perfect when i was running windows XP. I have tried both the wine and crossover methods but the game crashes back to the desktop right after the second video (the one where it shows the map in the begining and then shows all the different characters.) Im pretty sure i have the latest version of wine because it came from the repository.

any help at all would be much apreciated.

---

### Post by hikaricore on 2007-04-01
post the output of:

```
glxinfo | grep rendering
```

and

```
wine --version
```

when run from a terminal.

Be aware that the Intel drivers for linux are not fully implemented in all methods of rendering when it comes to 3d applications such as WoW.  They may work perfectly in windows but Intel actually cares about the windows drivers.  Their linux counterparts have barely been updated (aside from linux community programming efforts) in about 3 years.

---

### Post by storky on 2007-04-01
the 

glxinfo | grep rendering

gives the following:

libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes


and my wine version is:

Wine 0.9.22

---

### Post by hikaricore on 2007-04-01
Alright, your 3d is working but your wine is outdated.

Yesterday's release (wine-0.9.34) can be downloaded here:

[http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb) (Edgy)
[http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.34~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.34~winehq0~ubuntu~6.06-1_i386.deb) (Dapper)

Download that file and double click on it to upate it. (you will get a box that pops up to enter your sudo password)

Once it's updated open a terminal and do:

```

cd ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft
wine WoW.exe -opengl

```

And let me know if anything changes from your orignal issue.

I know some versions of wine prior to 0.9.25 broke WoW for awhile, but I'm not sure if yours is  affected.

---

### Post by storky on 2007-04-01
im having a hard time gettin the directory changed to the WOW folder. i keep gettin directory does not exist. ill keep trying

---

### Post by hikaricore on 2007-04-01
Did you run:

```
winecfg
```

Before running the installer?

And did you install in the suggested directory or somewhere else?

My instructions assume you installed to the default directory.

---

### Post by Jarn on 2007-04-01
You typoed in your instructions. You gave him Progam instead of Program.

---

### Post by hikaricore on 2007-04-01
>.<  woops, i usually doublecheck, sorry bout that

---

### Post by storky on 2007-04-01
i can change the directory up to the  drive_c folder but i am doing something wrong from there on because if i try to change the directory to program files... what am i doing wrong, i noticed your code had wierd slashing but there not working for me.

---

### Post by Jarn on 2007-04-01
They're backslashes. You could also try using quotation marks. ```
cd ~/.wine/drive_c/"Program Files"/"World of Warcraft"
```

---

### Post by storky on 2007-04-01
alright so now that i got that typo figured out i could try and launch the game. as soon as i type the command with the -opengl command on the end like u said i small window pops up saying that 

"the hardware has changed, return to default settings?"

it doesnt matter whether i click yes or no i get the same result:

the cpu light goes solid for a few seconds and then the whole thing freezes and i have to reboot.

ALSO! i noticed right after i put the command in the terminal it gives a warning message about my 3d graphics's driver not supporting something. i cant copy and paste becasue right after that it freezes.

---

### Post by Jarn on 2007-04-01
You can have it direct the output to a log file to see the error. Then someone who knows something about WoW can help you. Just run it with this command:

```
wine WoW.exe -opengl 2>~/wow-log.txt
```

---

### Post by storky on 2007-04-01
this is the error message acording to other threads people have had simular problems but i havent seen any complete threads or solutions anywhere


libGL warning: 3D driver claims to not support visual 0x5b

---

