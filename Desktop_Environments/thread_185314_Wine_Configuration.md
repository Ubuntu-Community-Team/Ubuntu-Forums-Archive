---
title: "Wine Configuration"
date: 2006-05-31
forum: Desktop Environments
---

### Post by utab on 2006-05-31
Dear all,

I installed wine by apt-get.

in ~/.wine I have 

dosdevices  drive_c  system.reg  userdef.reg  user.reg

I googled some time to configure but all mentioned a config file which must be under /etc or .wine under home but no use.

Can someone help me to configure that? I read the wiki but did not help.

Regards,

---

### Post by meng on 2006-05-31
Been a while since I last used wine, so things may have changed.
1. Do you have a file ~/.winerc ?
2. Have you checked out the documentation on the wine site? It recommends using winecfg
[http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index)

---

### Post by bluevoodoo1 on 2006-05-31
Is 
```
winecfg
```

what you're looking for?

---

### Post by utab on 2006-05-31
I do not have a .winerc

file

I have used winecfg and autodetect under drives tab

But when I type

wine calc.exe

I get

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system" is not accessible.
wine: cannot open (null)

So there is still a problem with the directories but I can not find the file to edit.

Regards

---

### Post by johnniecarcinogen on 2006-05-31
Doing what bluevoodoo suggested should set that up automatically. just type 'winecfg' in the terminal.

---

### Post by YokoZar on 2006-06-01
[QUOTE=utab]I do not have a .winerc

file

I have used winecfg and autodetect under drives tab

But when I type

wine calc.exe

I get

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system" is not accessible.
wine: cannot open (null)

So there is still a problem with the directories but I can not find the file to edit.

Regards[/QUOTE]This sounds like a permissions problem, which means you might have done something funny.  ~/.wine is owned by your user, right?

---

### Post by vidak on 2006-06-02
what happens if you try 
wine /windows/windows/system32/calc.exe
?
the drive_c directory in .wine is a fake windows directory, where you can install your win-based programs. When you want to start a program located on your windows partition, you have to make a 'disk' in wine using the Drives tab in winecfg. Just press the "Add" button, then set the path to the drive and the type of it.

---

### Post by utab on 2006-06-04
Vidak 

How to make the configuration for example lets say I have directory called xp which contains the C drive info inside that I have Program Files and  so on....

After I type winecfg, set path and exit from winecfg window. The problem persists but the interesting thing that is that when I again winecfg,  I get an error message that "you do not have a C: drive this is not so great"

So that s all folks for now

---

### Post by vidak on 2006-06-05
Sorry for the late answer... I think you should set more drives. For drive C: (on my computer at least) the good choice was ~/.wine/drive_c, I selected / as drive Z:, and /cdrom as drive D: - the corresponding drive types are local hard disk (C:&Z:), and CDROM (D:). ~/.wine/drive_c should be a fake windows directory in your home directory, containing a fake windows and a Program Files directory...

Tell me please if this helped or not...

---

### Post by vidak on 2006-06-05
Another idea: maybe your xp partition is not mounted when running wine, and winecfg is correct with having your windows directory as drive C:...

---

### Post by bluntu on 2006-08-24
I was following a wine tutorial somewhere on this forum and accidently removed my "drive_c".

Steps to experience this problem that the thread starter is having:

1: type 'winecfg' in terminal and enter.
2: goto 'drives' tab.

and simply remove drive_c and save/exit.

That was what I did and now I don't know how to get it back.... I am currently experiencing the same problem that the thread starter is experiencing. Any help?

---

