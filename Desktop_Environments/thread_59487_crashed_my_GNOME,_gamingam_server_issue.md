---
title: "crashed my GNOME, gamin/gam_server issue"
date: 2005-08-24
forum: Desktop Environments
---

### Post by Magicdead on 2005-08-24
Well yeah, I kinda fucked up this computer (I'm in here using XFCE 4.2 atm)

What I did was mainly that I have this shellscript I coded. What it does is delete all files containing log or mail from a given path, replacing them with empty ones.
I did this script to empty my /var/log/ folder when the logs get to big an logrotate still needs some time.
Well any ways, after I didn't use it some time, I'd forgotten the syntax (scriptname path)
and just used the comand without a path.
Well when I saw that it's deleting some stuff from my homefolder, I immediatly pressed CTRL+C to interrupt it, but it had already deleted quite some files.
So yeah the computer worked another 2 days untill I had to reboot and then the errors showed up.

```
scheduling while atomic: gam_server 0xffffffff/9227
schedule +1239/1298 schedule 0x30d/0x512
Aiee, killing interrupt handler
``` 

first I reinstalled gamin and libgamin, which didn't help.
Then, as GNOME freezed when I logged in always giving above errors on tty7, i reinstalled all packages containing gnome in their name (just to be sure) and then I backed up the gnome configuration folders in my /home/user/ and deleted them, so that GNOME generates new ones.
Now I can login, but as soon as I start nautilus, gam_server crashes the kernel again.
XFCE4.2 is working, but as soon as I start xchat, it crashes with the gam_server error, too.

Unfortunately, my script had deleted the log files, too, and well yeah, I don't really know what files were deleted. (ok lucky me, the script couldn't delete any folders, so that saved many files)

ah, and I corrected that script so that not even me with this stupidity can use it in a wrong way again...
it's now like outputting "you idiot, do you wanna run into all those troubles again? USE a frickin path when you launch me". that should help :)

so anyways, anyone got an idea how to fix this?

(I think it has soemthign to too with missing authentification files for gamin used by the different programs, but I'm not entirely sure)


greetings, Magic

---

