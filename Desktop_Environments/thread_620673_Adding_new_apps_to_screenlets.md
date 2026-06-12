---
title: "Adding new apps to screenlets?"
date: 2007-11-22
forum: Desktop Environments
---

### Post by -RYknow on 2007-11-22
Ok, so i've installed screenlets, and I have it working. I checked out gnome-look and found a few nice "desklets" that i wanted to try out. I downloaded them, and haven't figured out how to install them. 

They are .tar.bz2 extension files. If I double click on the file, it opens the Archive manager. When I choose where I want it to go (usr/local/share/screenlets) I get the following error message. 

> tar: CPU_Meter: Cannot mkdir: Permission denied
tar: CPU_Meter/CPU_MeterScreenlet.py: Cannot open: No such file or directory
tar: CPU_Meter/menu.xml: Cannot open: No such file or directory
tar: CPU_Meter/Screenlet.package: Cannot open: No such file or directory
tar: CPU_Meter/themes: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/silver: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/white: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/blackwhite: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/orange: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/violet: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/neon: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/blue: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/x360: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/default: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/dark: Cannot mkdir: No such file or directory
tar: CPU_Meter/themes/silver/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/silver/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/silver/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/silver/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/white/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/white/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/white/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/white/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/blackwhite/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/blackwhite/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/blackwhite/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/blackwhite/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/orange/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/orange/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/orange/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/orange/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/violet/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/violet/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/violet/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/violet/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/neon/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/neon/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/neon/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/neon/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/blue/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/blue/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/blue/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/blue/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/x360/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/x360/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/x360/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/x360/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/default/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/default/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/default/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/default/dial2.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/dark/back.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/dark/dialdot.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/dark/dial.png: Cannot open: No such file or directory
tar: CPU_Meter/themes/dark/dial2.png: Cannot open: No such file or directory
tar: Error exit delayed from previous errors

I also tried to make a directory using (mkdir /usr/local/share/screenlets/CPU_Meter) All with no luck. 

Any suggestions would be great!
Thanks!
-RYknow

---

### Post by taurus on 2007-11-22
You don't have permission to write to /usr/local/share/screenlets.  So you have two options:

1.  Unpack the file that you downloaded to your own $HOME/.screenlets

Applications -> Accessories -> Terminal
```
mv **filename.tar.bz2** ~/.screenlets
cd ~/.screentlets
tar xvjf **filename.tar.bz2**
```

or

2.  ```
sudo cp **filename.tar.bz2** /usr/local/share/screenlets
cd /usr/local/share/screenlets
sudo tar xvjf **filename.tar.bz2**
```

---

### Post by -RYknow on 2007-11-22
First off, thanks for the fast reply! I love this forum for that! =]

Ok, the file that I'm dealing with calls " 64599-CPU_Meter.tar.bz2 ".

So I typed: mv 64599-CPU_Meter.tar.bz2 -/.screenlets
I got an output of: mv: cannot stat `64599-CPU_Meter.tar.bz2': No such file or directory

Then when I typed " sudo cp 64599-CPU_Meter.tar.bz2 /usr/local/share/screenlets " I get an output of: cp: cannot stat `64599-CPU_Meter.tar.bz2': No such file or directory

No idea what I'm doing wrong here. =\

-RYknow

---

### Post by taurus on 2007-11-22
First of, you are in the wrong directory since I believed you saved it to ~/Desktop.  So, you need to be in that directory first.  Second, it should be ~/.screenlets, not -/.screenlets.

```
cd ~/desktop
mv 64599-CPU_Meter.tar.bz2 **[COLOR="Blue"]~[/COLOR]**/.screenlets
cd ~/.screenlets
tar xvjf 64599-CPU_Meter.tar.bz2
```

---

### Post by -RYknow on 2007-11-22
Ok, I did as you suggested. The directory for where the files are is actually /home/username/Saved Downloads. I followed your instructions, but I'm not finding the file, and it doesn't show up in Screenlets. 

I'm really sorry about this. I'm sure this is very basic stuff. I'm still pretty new to linux. so please forgive me.:( 

-RYknow

**EDIT**: Ok, hopefully this will make things a bit easier. I just moved the Saved Downloads folder right to the desktop.

---

### Post by taurus on 2007-11-22
What's the output of this command from a terminal?

```
ls -la ~/"Saved Downloads"
```

If a directory (or file) has an empty space between two words, you need to use " " or \.  For instance, "Save Downloads" is the same as Save\ Downloads.

---

### Post by -RYknow on 2007-11-22
Here is the output of that command: " ls: /home/username/Saved Downloads: No such file or directory "

-RYknow

---

### Post by taurus on 2007-11-22
Dude, why do you keep moving stuff around?  Then, my previous commands won't work.

```
ls -la ~/Desktop/"Saved Downloads"
```

---

### Post by -RYknow on 2007-11-23
Sorry I moved things. I just figured it would be easier to work off the desktop. 

Anyway, the output of your last command is as follows:
> drwxr-xr-x 2 ryknow ryknow   4096 2007-11-22 23:13 .
drwxr-xr-x 7 ryknow ryknow   4096 2007-11-22 23:13 ..
-rw-r--r-- 1 ryknow ryknow 300653 2007-11-21 15:30 64599-CPU_Meter.tar.bz2
-rw-r--r-- 1 ryknow ryknow 762496 2007-11-21 15:30 64806-Screenlets1.tar.gz
-rw-r--r-- 1 ryknow ryknow 767637 2007-11-21 15:31 66609-ClearWeather03.tar.bz2
-rw-r--r-- 1 ryknow ryknow 763868 2007-11-21 15:29 69229-Screenlets2.tar.gz
-rw-r--r-- 1 ryknow ryknow  55096 2007-11-21 15:34 69966-reflective-black.tar.gz

-RYknow

---

### Post by taurus on 2007-11-23
```
mv ~/Desktop/"Saved Downloads"/64599-CPU_Meter.tar.bz2 ~/.screenlets
cd ~/.screenlets
tar xvjf 64599-CPU_Meter.tar.bz2
```

---

### Post by -RYknow on 2007-11-23
Ok, I was able to use the first command. The second one gave me an error. Here is the output:

> ryknow@jason-desktop:~$ mv ~/Desktop/"Saved Downloads"/64599-CPU_Meter.tar.bz2 ~/.screenlets
ryknow@jason-desktop:~$ cd ~/.screenlets
bash: cd: /home/ryknow/.screenlets: Not a directory


-RYknow

**EDIT:** I haven't changed, or moved anything.

---

### Post by taurus on 2007-11-23
Looks like you don't have a ~/.screenlets directory.   Try

```
mv .screenlets 64599-CPU_Meter.tar.bz2
mkdir .screenlets
mv 64599-CPU_Meter.tar.bz2 .screenlets
cd .screenlets
tar xvjf 64599-CPU_Meter.tar.bz2
```

---

### Post by -RYknow on 2007-11-23
Hey alright!! That worked! Thank you for the help! Now, before I leave you alone about this issue, how would I go about adding more?

I assume it would just be: 
> mv filename.tar.bz2 .screenlets
cd .screenlets
tar xvjf filename.tar.bz2 

Thanks for your help! 

-RYknow

---

### Post by taurus on 2007-11-23
You need to be in the directory where those files are; otherwise, you have to include the whole path to them.

```
cd ~/Desktop/"Saved Downloads"
mv **filename.tar**.bz2 ~/.screenlets
cd ~/.screenlets
tar xvjf **filename**.tar.bz2
```

---

### Post by -RYknow on 2007-11-23
Hey, one more thing. I have a file with a .tar.gz extension. When I go to extract it from terminal, this is the output I get. 

> ryknow@jason-desktop:~/.screenlets$ tar xvjf 69645-Calc.tar.gz
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

I assume it has something to do with the xvjf command? Could you tell me what I'm doing wrong?

Thanks, 
-RYknow

---

### Post by -RYknow on 2007-11-23
ok, a little hunting showed it's zxvf. 

Sorry, 
-RYknow

---

