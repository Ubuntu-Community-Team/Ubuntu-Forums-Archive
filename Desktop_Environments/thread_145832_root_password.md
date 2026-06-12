---
title: "root password?"
date: 2006-03-17
forum: Desktop Environments
---

### Post by lyr on 2006-03-17
This might be silly, but I was never asked to set root password when installing ubutnu (5.10 breezy badger).. and I really need to be logged in as root to get anywhere with my configurations.. So.. what on earth is it preset as?

---

### Post by DJ Scribblinni on 2006-03-17
Your root password should be the same password you use to log in...

---

### Post by lyr on 2006-03-17
Well, it isn't.. so something is seriously messed up :)

---

### Post by Perfect Storm on 2006-03-17
Root are disbale by default instead you use sudo. eg. sudo <command> when asking for password it's the password for your default (first made) account.
sudo means superuser do

---

### Post by lyr on 2006-03-17
Oh, that worked though.. now I was able to rm that file that have been "harassing" me the past 2h.. Thanks :)

---

### Post by red_shrike on 2006-03-17
here is how-to get your root account to work. 
1. Ctrl+Alt+F1 to get in tty1
2. $ sudo passwd root
3. $ Password:  (here you type in password you use to login)
4. New UNIX administrator passwprd: (here you type in password you want ur root user to have)
5. Confirm step 4
6. logout
7. try login with root.

Note
This is not needed most of the times, but if it is what pleases you...

If you want GDM to work with root than repeat step 1
login as root and then type this: $ rm /tmp/.X0-lock (0 is null)
                                            $ startx

Thats it! Now you shold be loged in as root in the GNOME environment.

all these stuff is case sensitive, and please dont copy $.

---

### Post by d-x on 2006-03-17
I've just done exactly what you've said but when asked for Password I put in the password for the administrator account *the one you setup at the start* and it doesn't even work comes up with invalid login.


Don't worry I found the problem

before doing step 2 login first through tty1 then the rest will work like easy.

---

### Post by red_shrike on 2006-03-20
Notice, if you hit Ctrl+Alt+F7 you should find yourself in your normal user account! in general F1 -> F6 is tty with CLI, and F7 ->F12 for graphical interfaces!!!!  This means you can have multiple users loged in at the same time, on the same machine. Talk about multi-user environment! To get normal users to work you will have to select empty tty, and type this: 
$ sudo rm /tmp/.X0-lock
$ sudo startx (sometimes for this step sudo is not required, sometimes it is. Why this is so is beyond me)

---

