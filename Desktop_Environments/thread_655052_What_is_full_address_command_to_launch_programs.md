---
title: "What is full address command to launch programs"
date: 2007-12-31
forum: Desktop Environments
---

### Post by heatpumpcontrol on 2007-12-31
setting up btnx launch config file and I want to program buttons to launch ie: rhythmbox terminal comix and so on......

what is the correct address to use? 

I've tried dragging and dropping the icon in /usr/share/applications/ name of app into terminal to try it but it won't work that way. It will work if I click on the icon but not if I drag and drop the icon. Oh and even if I edit the ' ' quotations or even if I use sudo to launch from terminal after I drag and drop.

suggestions?

also how about to launch nautilus at a specific folder.... ie: /media/Documents?

---

### Post by p_quarles on 2007-12-31
Executable files are in your "path," so you only need to enter the name of the command. For Rhythmbox, it's simply:
```
rhythmbox
```That said, most of those files are located in /usr/bin ... so, if you wanted to enter the path manually, it would be:
```
/usr/bin/rhythmbox
```
EDIT: Also, the icons in /usr/share are just that: icons. ;)

---

### Post by heatpumpcontrol on 2007-12-31
cool I got the commands down by using the /usr/bin/rhythmbox and so on... I see that this is where the "executables" are located... now how about opening a specific folder using a command for nautilus....? like /usr/bin/nautilus /media/Documents

EDIT:

I see that this command opens up the app as root user and not under my preferences or my account. This shows up when I went to Rhythmbox and noticed it didn't have my settings of my music folders so when I went to 'import a folder' is shows 'root' as the user's account and when I click on rhythmbox from my applications menu, It loads my settings and it shows my name when selecting to import a folder.

---

### Post by p_quarles on 2007-12-31
That's where *most* executables are located. Basic system utilities are located in /bin, programs that you've compiled from source are located in /usr/local/bin, and many but not all games are located in /usr/games. A select few other programs are located in /sbin and /usr/sbin.

To open a folder with Nautilus:
```
nautilus /path/to/folder
```

---

### Post by heatpumpcontrol on 2007-12-31
Excellent... thanks. I was close. And as for the other locations.. I'll keep this thread.. thanks.

It still shows everything as being commanded by 'root' though. Do you how to set up the argument to have it open under my user account?

Thanks man and Happy New Year!!

---

### Post by p_quarles on 2007-12-31
Not sure I understand the question -- executables are all owned by root, but the vast majority of them can be run by other users. That's how it's supposed to work. If you want to give me an example, I can probably answer your question better. 

And happy 2008 to you as well. ;)

---

### Post by heatpumpcontrol on 2007-12-31
Ok.. I just entered

me@pc:~$ nautilus /media/Documents

it opens as I would expect it..

However, when I enter the command line 

nautilus /media/Documents  in the btnx command line it opens up the 'Documents' folder but under root which is the same that is occurring with other apps.

---

### Post by p_quarles on 2007-12-31
I'm not familiar with the btnx application, so maybe I'm missing something. Are you running btnx as root? If nothing else, a screenshot might help me, umm, get the picture. ;)

---

### Post by heatpumpcontrol on 2007-12-31
Well I guess that is why...

I have to enter into root to edit the btnx-config file.. I would attach a picture but that is another issue I haven't resolved.... webdav... oh boy.. I don't want to get started on that... I had forgotten it..lol

---

### Post by heatpumpcontrol on 2007-12-31
thanks p_quarles I really have used your help...


Hey have a happy one. 2 more hours for me...

---

