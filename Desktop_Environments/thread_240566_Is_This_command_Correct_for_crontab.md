---
title: "Is This command Correct for crontab???"
date: 2006-08-21
forum: Desktop Environments
---

### Post by true_friend on 2006-08-21
15 * * * * /usr/bin/home/ss/wallpaper/.wallpaper 
this is a command i gave in crontab tasks to run a wallpaper changer script. my problem is it works some time some time not. e.g. it worked after 1 day today morining and now it is quit. i can not understand how would it work after every 15 minutes.
 i saved it in folder ~/.cronfiles/cronfile and this file is added in startup.
"/usr/bin" i found in tutorail at wiki.ubuntu.org/Crontab in some examples.
plz suggest me the correct command.
Regards
True_Friend

---

### Post by Chris Tucker on 2006-08-21
the best way to edit crontab stuff is with ```
crontab -e
```You have the time part right, but your command is kind of ... way off... unless you have created a very strange path to a program youve written.

brief bit of information on script writing... Lets assume your username is "ss", and you have a folder called "wallpaper" in your home folder, and a script inside that folder called "wallpaper" ... also assuming that you have written your script properly.
To test your script once you've written it, you would have done this: ```
cd ~/wallpaper
chmod +x wallpaper
./wallpaper
```
the chmod line you would only ever have to do once, unless you've un-done it.
now to the program part of it, the script is called "wallpaper" , if you typed ```
wallpaper
```, it would not work, because if you dont tell the shell where the program your trying to run is, it assumes a few places, it doesnt search the drive for it, and it does not assume the current directory. so you prefix the program with ```
./
``` that tells the system "current directory"
in your attempt to create the scheduled job you should put ```
 15 * * * * /path/to/program
```
so ```
15 * * * * /home/ss/wallpaper/wallpaper
``` or the like, wherever it is.
the way you had it written the shell looked in /usr/bin/home/ss/wallpaper/ for a *hidden* program called wallpaper (any file prefixed with "." is hidden

hope this helps

---

