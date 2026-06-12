---
title: "Nautilus not responding."
date: 2007-08-24
forum: Desktop Environments
---

### Post by divali on 2007-08-24
Using UBUNTU FEISTY.
I have a few icons on my desktop and suddenly I find I cannot use them to open up 
their applications. When I d/click them they all dissappear and the system freezes,
so I have to control/alt backspace to reboot and the problem starts all over again,
even when I call up an app using the terminal. Strange though I can still use apps that are in the toolbar.
I removed nautilus and then reinstalled it with apt-get. But the problem remains.
Any help here would be gratefully recieved.

---

### Post by divali on 2007-08-24
Sorry here's the response from the terminal

Initializing gnome-mount extension

(nautilus:7338): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libmapping.so' (/usr/lib/gnome-vfs-2.0/modules/libmapping.so: cannot open shared object file: No such file or directory)

(nautilus:7338): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libmapping.so' (/usr/lib/gnome-vfs-2.0/modules/libmapping.so: cannot open shared object file: No such file or directory)

---

### Post by divali on 2007-08-25
Anyone ???

---

### Post by DM was on fire! on 2007-08-25
It almost sounds like something happened with the libmapping.so library file.
Only thing I can think of is to do this:

> sudo apt-get --purge remove libmapping.so 
sudo apt-get install libmapping.so

I think? o_o;;

---

### Post by divali on 2007-08-26
Thanks for responding but, as you can see, the problem continues.

divali@ubuntu:~$ sudo apt-get --purge remove libmapping.so 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmapping.so

---

### Post by Rui Pais on 2007-08-26
> **divali said:**
> Thanks for responding but, as you can see, the problem continues.

divali@ubuntu:~$ sudo apt-get --purge remove libmapping.so 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmapping.so

libmapping.so is a file of nautilus-cd-burner, check[ here]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libmapping.so&searchmode=searchfiles&case=insensitive&version=feisty&arch=i386").

you can try:```

sudo apt-get --purge remove nautilus-cd-burner
sudo apt-get install nautilus-cd-burner
```

---

### Post by divali on 2007-08-26
Hmmm. I still get..

divali@ubuntu:~$ sudo nautilus
Password:
Initializing gnome-mount extension.

and then ....  nothing

---

### Post by isaacj87 on 2007-08-26
I tried doing a "sudo nautilus" once and it screwed up my laptop big time!
Always do a "gksudo nautilus" but I think even doing that can cause problems...I'm not sure what you could do...

---

### Post by divali on 2007-08-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/134931](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/134931) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Okay I've reported this as a bug in Launchpad. So we'll have to see what happens.
If anyone has any ideas I'll be grateful if you could let me know.
Thanks for your help so far.

---

### Post by Rui Pais on 2007-08-27
> **divali said:**
> Hmmm. I still get..

divali@ubuntu:~$ sudo nautilus
Password:
Initializing gnome-mount extension.

and then ....  nothing

hi again,
you must now try to check if you have a config problem (usually user related) or if something it's broken in your system.

Try from a console (close all gnome sessions and press Ctrl+Alt+F1):
```
mkdir gnome_TEMP
mv .gconf* .gnome* .nautilus gnome_TEMP/
```
then go back (press Ctrl+Alt+F7) login and check how it's working. 
Your gnome personalizations would be missing... if nautilus is working, you can you redo them again, or move back the folders from gnome_TEMP/ one by one and try to narrow down the faulty one.

good luck.

---

### Post by divali on 2007-08-27
Thanks, but I'm still not getting nautilus to open.   I had to issue the commands via a terminal
on the desktop because ctrl/alt/f1 wouldn't work for some reason. Could this be related?

---

### Post by Rui Pais on 2007-08-27
> **divali said:**
> Thanks, but I'm still not getting nautilus to open.   I had to issue the commands via a terminal
on the desktop because ctrl/alt/f1 wouldn't work for some reason. Could this be related?

uhmm... thats weird. Do you mean that pressing Ctrl+ALT+F1 (... to  F6) don't give you a line command (kind of old DOS prompt)?

You can try another thing. Create a new temporary user and check if with that account the problem exist too. If so, then it's a system problem (and usually hard to resolve). 
If new account works, then that would be easier, and at worst you would only need to move away any configure files.

---

### Post by divali on 2007-08-27
Ok now I'm getting somewhere.   I created a new user and Nautilus
still won't start.  
So what to do.  Can I do a repair with the feisty disc? How does one go about
it? 
 In the meantime I am using Midnight Commander.
   But it would be good to get Nautilus working.  It's just frustrating.

---

### Post by Rui Pais on 2007-08-27
As long as you got a line command you can do all from there.

You can try reinstall:
sudo aptitude reinstall ubuntu-desktop

Or try to get more info about who's exactly is the culprit:
```
strace nautilus
```
should output a lot and the last lines before error happens may give some clues.

btw, can you give a little more details?
What exactly happens? any error message? 
Did this happen with sudo only or with normal user powers too?
Did this happen with gksudo nautilus? 
If you start a console on root mode (something like sudo -s -H) did nautilus starts if you type it from there?

Can you sudo other graphical apps?

---

### Post by Gremlinzzz on 2007-08-27
try this command
killall nautilus

---

### Post by Gremlinzzz on 2007-08-27
killall nautilus
is a command that refreshes nautilus and nautilus should open up when you do that command .

---

### Post by divali on 2007-08-28
[I]As long as you got a line command you can do all from there.

You can try reinstall:
sudo aptitude reinstall ubuntu-desktop[/I]

# This told me that it was already installed

[I]Or try to get more info about who's exactly is the culprit:
```
strace nautilus
```
should output a lot and the last lines before error happens may give some clue[/I]s.

#This gave me:

unlink("/tmp/orbit-divali/linc-207d-0-3259f81d2de55") = 0
close(12)                               = 0
exit_group(0)                           = ?
Process 8317 detached
divali@ubuntu:~$ 


[I]btw, can you give a little more details?
What exactly happens? any error message? 
Did this happen with sudo only or with normal user powers too?
Did this happen with gksudo nautilus? [/I]

#gksudo strace nautilus.
gives me........
write(20, "===== BEGIN MILESTONES =====\n0x8"..., 4096) = 4096
write(20, " to signal 11\n0x81868f8 2007/08/"..., 4096) = 4096
write(20, "x81868f8 2007/08/28 20:52:39.464"..., 4096) = 4096
write(20, "8/28 20:52:43.1807 (USER): debug"..., 4096) = 4096
write(20, "745 (USER): debug log dumped due"..., 4096) = 4096
write(20, "ug log dumped due to signal 11\n="..., 4096) = 4096
write(20, "bug log dumped due to signal 11\n"..., 4096) = 4096
write(20, "due to signal 11\n0x81868f8 2007/"..., 4096) = 4096
write(20, "1\n0x81868f8 2007/08/28 20:52:43."..., 4096) = 4096
write(20, "7/08/28 20:52:47.9281 (USER): de"..., 4096) = 4096
write(20, "2.5100 (USER): debug log dumped "..., 484) = 484
close(20)                               = 0
munmap(0xb6681000, 4096)                = 0
sigreturn()                             = ? (mask now [])
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
gettimeofday({1188330773, 130577}, NULL) = 0
open("/root/nautilus-debug-log.txt", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 20
fstat64(20, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6681000

#sudo strace nautilus.    Gives me the same message.



[I]If you start a console on root mode (something like sudo -s -H) did nautilus starts if you type it from there?
[/I]
#divali@ubuntu:~$ sudo -s -H nautilus
Password:
/usr/bin/nautilus: /usr/bin/nautilus: cannot execute binary file

[I]Can you sudo other graphical apps?
[/I]
#Yes, no problem except with Nautilus.

---

### Post by divali on 2007-08-28
> **Gremlinzzz said:**
> killall nautilus
is a command that refreshes nautilus and nautilus should open up when you do that command .

Thanks, but -killall nautilus- had no effect.

---

### Post by divali on 2007-08-29
Just a bit more info:

#divali@ubuntu:~$ gksudo nautilus
(nautilus:5669): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension


And then ......   nothing.

---

### Post by Rui Pais on 2007-08-29
Hi,
sorry the late answer. 

Well problems like that are not easy to solve... you must try google with the symptoms to see if you get clues on whats going on. 

Mean while, here a thread related to your last post output error. Maybe it helps:
[http://ubuntuforums.org/showthread.php?t=376536](http://ubuntuforums.org/showthread.php?t=376536)

A correction on a previous command. The 'sudo -s -H nautilus' is not correct. You should do:
```
sudo -s -H 
```
and after that (you will be in a console logged as root):
```
nautilus
```

Anyway, if your system works normally and you just can't open nautilus, you can try to do your administrative tasks from a terminal (safer) or try another file manager for that purpose, like thunar,pacmanfm that are very similar, or rox, a little different but fast and powerful...

---

### Post by divali on 2007-09-02
Yes.    I'm gonna leave it for now. 
I've installed Claw4, which will suffice and good old
 Midnight Commander Is always there when the going get tough.
Thanks for the help everyone. If anything comes up I'll post it here.

---

### Post by divali on 2007-10-02
Still no solution.

---

### Post by divali on 2007-10-12
At last after weeks of installing and uninstalling Nautilus and searching I solved the problem by following the advice on this Post.  Thanks guys

[https://answers.launchpad.net/ubuntu/+question/4838](https://answers.launchpad.net/ubuntu/+question/4838)

---

### Post by remza on 2008-01-03
I now have the same problem but can't see how you solved it using that lanchpad post.... please help me divali =)

---

