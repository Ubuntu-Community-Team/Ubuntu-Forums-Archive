---
title: "When loading app in Ubuntu it just disappears!  Worked before."
date: 2007-03-01
forum: Desktop Environments
---

### Post by techguy0012 on 2007-03-01
Hi, 

I appreciate any and all help concerning this situation.  I'm familiar with linux and have been using it off and on for a few years now. 

My problem is this: 

After a fresh install, I of course I apply the latest updates then begin configuring the system.  At first everything works perfectly.  Of course with clicking things like "user and groups" and various other admin tasks it asks for my root password.

Problem is that now, when I click something it begins to load up like but then after a few moments it just disappears from the screen.  It doesn't even get to the point where it asks me for my root pw.

Please help, this is a very annoying problem.

Thanks a Bunch!

---

### Post by invalid on 2007-03-01
Try running these applications from a terminal to see the output (if any).
```
gksudo <app>
```

---

### Post by techguy0012 on 2007-03-01
Here is the errors I get when I applied the following command: gksudo adduser/useradd

dialt0ne@LIN-E38R4I3JKF:~$ gksudo smb
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
dialt0ne@LIN-E38R4I3JKF:~$ smb
bash: smb: command not found
dialt0ne@LIN-E38R4I3JKF:~$ gksudo useradd
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
dialt0ne@LIN-E38R4I3JKF:~$ adduser
adduser: Only root may add a user or group to the system.
dialt0ne@LIN-E38R4I3JKF:~$ gksudo adduser
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
dialt0ne@LIN-E38R4I3JKF:~$ sudo adduser
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0

Not sure why it's doing this at all.  I didn't change anything in the system.  Only thing I did was  update it and thats about it.

Also here is what happened when I tried to correct the error in /etc/sudoers

dialt0ne@LIN-E38R4I3JKF:/etc$ sudo gedit sudoers
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
dialt0ne@LIN-E38R4I3JKF:/etc$

---

### Post by invalid on 2007-03-01
Well to edit the sudoers file, you need to use ```
sudo visudo
```but I fear this won't work either.

I'm not sure what those errors relate to, hopefully someone else will be a little more help.

---

### Post by ComplexNumber on 2007-03-01
[B]techguy0012
[/B]i would suggest that you reboot and choose failsafe at the boot menu. then type in the following to correct the problem:
visudo



it seems like there is something(maybe a typo) in your sudoers file that is rendering the whole file to be incorrect.

---

### Post by techguy0012 on 2007-03-01
THANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOUTHANK YOU THANK YOU THANK YOU THANK YOU

Once I logged out and booted into failsafe then did what "ComplexNumber" stated which is to visudo.

I deleted the first few paragraphs because first (they didn't seem like they belonged there) and 2nd (they didn't belong there).

Once I did this then logged bake into my terminal, it worked perfectly.

THANKS A BUNCH PEOPLE!!!! UBUNTU FORUMS ROCK!

---

