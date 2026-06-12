---
title: "using custom icons"
date: 2006-04-23
forum: Desktop Environments
---

### Post by lonelypauly on 2006-04-23
i downloaded some custom gnome icons but am not able to drop them in my /usr/share/pixmaps folder...it says i do not have write permission.  they are mostly .svg files and some are .png...what do i do? 

thanks

---

### Post by Sutekh on 2006-04-23
If you have to do anything outside your home folder, then you need to use **sudo** to achieve it.

You can copy the icons using the terminal command, **cp**
```
sudo cp /<path of icons> /usr/share/pixmaps
```
If you want to use Nautilus (the file browser) to click and drag, then you need to start it as root using
```
gksudo nautilus
```

---

### Post by thunderduck3141 on 2006-04-23
use this command

sudo cp <full address of icons> /usr/share/pixmaps

for sudo make sure u type your password
you can also type 

su
<root password>
cp <full address of icons> /usr/share/pixmaps
 the latter keeps u as root

---

### Post by lonelypauly on 2006-04-23
hmm, i must be missing something here...it says no such file or directory...you mind posting the command again?

---

### Post by lonelypauly on 2006-04-23
i typed su and entered my root pw but is says "Authentication failure"

i typed in the following:

sudo cp home/me/desktop/files/icons/ /usr/share/pixmaps/  
is that correct or no?

---

### Post by Sutekh on 2006-04-23
[QUOTE=lonelypauly]i typed su and entered my root pw but is says "Authentication failure"

i typed in the following:

sudo cp home/me/desktop/files/icons/ /usr/share/pixmaps/  
is that correct or no?[/QUOTE]
No, it needs to be
```
sudo cp **/**home/me/**D**esktop/files/icons/ /usr/share/pixmaps
```
Note the bolds.  

The root filesystem is /, so all absolute paths start with that.  If they are subfolders of the current directry, they are uneeded.

The Desktop folder is usually capitalised.



Also the su method won't work unless you set a root password, which is disabled by default. 

Better to use sudo

[Ubuntu Wiki - Root and Sudo](wiki.ubuntu.com/RootSudo)

---

### Post by lonelypauly on 2006-04-23
its not working for me...i must be typing it in wrong...

sudo cp /home/paul/icons/ /user/share/pixmaps/

---

### Post by Sutekh on 2006-04-23
[QUOTE=lonelypauly]its not working for me...i must be typing it in wrong...

sudo cp /home/paul/icons/ /us**e**r/share/pixmaps/[/QUOTE]
There's no 'e'
```
sudo cp /home/paul/icons/ /usr/share/pixmaps/
```

Try copying my post, rather than typing yourself.  So long as I don't make typos, you should be fine :)

---

### Post by lonelypauly on 2006-04-23
sudo cp /home/paul/Desktop/icons/ /usr/share/pixmaps/
cp: omitting directory `/home/paul/Desktop/icons/'

still nothing...this is the last thing i entered.

---

### Post by lonelypauly on 2006-04-23
maybe my file system is not named paul...how do i check that? that is the only thing i can think of at this point.

---

### Post by Sutekh on 2006-04-23
[QUOTE=lonelypauly]sudo cp /home/paul/Desktop/icons/ /usr/share/pixmaps/
cp: omitting directory `/home/paul/Desktop/icons/'

still nothing...this is the last thing i entered.[/QUOTE]
My mistake, I left something out, depending on whether you want to copy just the contents of the icons folder or the icons folder itself.
```
sudo cp /home/paul/Desktop/icons/* /usr/share/pixmaps
```
should copy the **contents** of /home/paul/Desktop/icons/  to the /usr/share/pixmaps folder

```
sudo cp -R /home/paul/Desktop/icons/* /usr/share/pixmaps
```
will copy the **folder** /home/paul/Desktop/icons/ and subfolders/contents to /usr/share/pixmaps/**icons**

---

### Post by Sutekh on 2006-04-23
[QUOTE=lonelypauly]maybe my file system is not named paul...how do i check that? that is the only thing i can think of at this point.[/QUOTE]
You can check with this command
```
ls -l /home/
```

---

### Post by lonelypauly on 2006-04-23
cp: omitting directory `/home/paul/Desktop/icons/AquiGnome'
cp: omitting directory `/home/paul/Desktop/icons/etiquette'
cp: omitting directory `/home/paul/Desktop/icons/SnowIsh-1.0_PNG'
cp: omitting directory `/home/paul/Desktop/icons/Vista-Inspirate_1.0'

is that good?

---

### Post by lonelypauly on 2006-04-23
it copied only a few of the files...there are dozens of folders inside the icons folder...do i need to copy each folder independently??

---

### Post by Sutekh on 2006-04-23
Sorry.  I wasn't typing fast enough to keep up with you.  

I left out a crucial part of the command, whether or not there are sub-folders. I edited the post above.

---

### Post by lonelypauly on 2006-04-23
sudo cp -R /home/paul/Desktop/icons/* /usr/share/pixmaps

...that worked! thank you so much for your help. :)

---

### Post by dasyad on 2006-04-24
You can dump icons in your .icon folder in your home directory only prob is i dont think they showup when u run a GUI program using sudo

---

### Post by Ramses de Norre on 2006-04-24
Easy fix for that: ```
sudo ln -s /home/<insert your username here>/.themes /root/.themes && sudo ln -s /home/<insert your username here>/.icons /root/.icons && sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

---

