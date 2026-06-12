---
title: "Dont know how to make so Help"
date: 2009-01-07
forum: General Help
---

### Post by Trevness on 2009-01-07
Umm will anyone make this into a run command or something where i can actually run it? when i click the .bat file it just takes me to a notepad i think...

Moparscape.org made a moparscape 3.2 download for linux/mac users and when i click that file it has .sh behind it..so someone help me please make it a .sh file so i can run it? yes i tried renaming it to .sh but it wont run..

So here you go Help me please

thank you

Umm the Play Raved.bat wont let me upload so i zipped it up and the runMoparScape 1 is the 1 where i can run it on my linux comp

Please someone help me im desperate to play with my friends... :c

---

### Post by LateNiteTV on 2009-01-07
if it the file ends in .sh, you need to run it in the terminal.

```
sh whatever.sh
```

.bat files are windows batch files. they wont run on linux.

---

### Post by Trevness on 2009-01-07
so how can i run the .bat file in a terminal or somethin..do i make the .bat file into a .sh file?

---

### Post by Trevness on 2009-01-07
i want to play the .bat file...my friends all play on that client..anyway i can play the .bat file

---

### Post by Trevness on 2009-01-07
anyone figure it out?

---

### Post by LateNiteTV on 2009-01-07
a .bat file CANNOT run on linux.

---

### Post by Trevness on 2009-01-08
im saying if i could make that .bat file into a .sh file?! could i do that?

---

### Post by jerome1232 on 2009-01-08
.bat is a Windows Batch file, won't run on linux, there is however WINE, it's a "compatibility layer" that allows *some* Windows programs to run on linux.

If you don't have wine you can install it like this:

```
sudo apt-get install wine
```

To run a .bat file I understand you can run "wineconsole" and navigate to it's directory, then type start "file.bat" and hit enter to run it.

for exampe if you wanted to run neatfile.bat and it's on your desktop you would:

```
wineconsole cmd
cd Desktop
start neatfile.bat
```

---

