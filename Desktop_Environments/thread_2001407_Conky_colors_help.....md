---
title: "Conky colors help...."
date: 2012-06-10
forum: Desktop Environments
---

### Post by SilverSS/SC on 2012-06-10
Hello,

I have searched google and the forums, but cannot get conky and conky colors to work properly at all.

I am attempting to use conky colors currently.  I am using Ubuntu 12.04.  Here is my entry:


cer3alk1ll3r@Lappy2009:~$ cd conky_colors
cer3alk1ll3r@Lappy2009:~/conky_colors$ make
make: Nothing to be done for `all'.
cer3alk1ll3r@Lappy2009:~/conky_colors$ /.conky-colors --lang=en --theme=blue --ubuntu --cpu=2 --cputemp --swap --battery --battery-value=battery --updates --proc=10 --clock=digital --calendarm --nvidia --hd=default --rhythmbox=glassy --pidgin --limit=5 --network --weather=61614 --side=right
bash: /.conky-colors: No such file or directory
cer3alk1ll3r@Lappy2009:~/conky_colors$ make install
mkdir -p /usr/share
mkdir -p /usr/share/fonts/TTF/conky
mkdir -p /usr/share/fonts/OTF/conky
mkdir -p /usr/bin
cp -v conky-colors /usr/bin
`conky-colors' -> `/usr/bin/conky-colors'
cp: cannot create regular file `/usr/bin/conky-colors': Permission denied
make: *** [install] Error 1
cer3alk1ll3r@Lappy2009:~/conky_colors$ 


Thanks for the help!

---

### Post by zombifier25 on 2012-06-10
```
sudo make install
```
Instead of just
```
make install
```

---

### Post by SilverSS/SC on 2012-06-10
> **zombifier25 said:**
> ```
sudo make install
```
Instead of just
```
make install
```

tried that, gave me the same error. and conky still only looks like the basic conky when I type conky in terminal.

---

### Post by zombifier25 on 2012-06-11
After done installing, does typing JUST
```
conky-colors
```
give you anything

---

### Post by SilverSS/SC on 2012-06-11
It gives me the help menu for conky colors.  If I type conky colors (without the dash) it draws the standard black and grey, boring conky.

---

### Post by zombifier25 on 2012-06-11
You MUST configure conky-colors first. Read the help menu it provides and configure it to your need. For example (on your post)
```
conky-colors --lang=en --theme=blue --ubuntu --cpu=2 --cputemp --swap --battery --battery-value=battery --updates --proc=10 --clock=digital --calendarm --nvidia --hd=default --rhythmbox=glassy --pidgin --limit=5 --network --weather=61614 --side=right
```
Note that your system may be different than the example, so take a good look and choose the parameters carefully.
After that, if you want conky-colors, run this in order to have conky use conky-colors' config.
```
conky -c ~/.conkycolors/conkyrc
```

---

### Post by SilverSS/SC on 2012-06-16
Thanks for the help, but I still can't get it to work.

I think conky hates me.

---

### Post by MalditohoN on 2012-06-20
Have you tried uninstalling conky and removing all its related files. 

Then apt-get autoremove, to uninstall unused or unnecessary files.

Then install conky then the conky-colors.

---

### Post by stinkeye on 2012-06-20
I just tested this and it worked.
Followed the directions here ---> [**_[COLOR="DarkRed"]http://helmuthdu.deviantart.com/art/CONKY-COLORS-244793180?[/COLOR]_**]("http://helmuthdu.deviantart.com/art/CONKY-COLORS-244793180?")

Check you have the tools for compiling...
```
sudo apt-get install build-essential checkinstall
```

Make sure your opening a terminal in the correct path.
eg: I extracted the **conky_colors** folder to my **~/conky** folder so the command for me was...
```
cd /home/glen/conky/conky_colors
``` 

After compiling I chose to run one of the options shown in the deviantart link.
It then gave me a conky command to run.

PS: Note that the conky_colors just sets up various configs to be used by conky.
It's not necessary to compile to use conky.
Helmuthdu has just tried to make it easier to get conky up and running without having to know a lot.
You can download configs and get help to set up conky from this thread.
[**_[COLOR="DarkRed"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2008")

---

