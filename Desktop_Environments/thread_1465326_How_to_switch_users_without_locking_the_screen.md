---
title: "How to switch users without locking the screen?"
date: 2010-04-29
forum: Desktop Environments
---

### Post by vmalep on 2010-04-29
Hi everybody,

Does someone knows how to disable the screen lock when switching users. We are sharing the computer my girlfriend and I and it is annoying to have to enter the password every time one of us want to return to his own environment.

I noted that if I switch directly doing Alt+F7 or Alt+F8, the environment I am coming from is not locked if I come came. I guess the lock is thus activated when pushing on the "Switch user..." short cut.

Thanks for your contribution!
Pierre

---

### Post by rnerwein on 2010-04-29
hi
i you talk about the command "su - your_gierlfriends_name" then what do you think about this solution.
append the last line in the file /etc/sudoers by adding the following line ( !!! remember it must be the end of that file !! )

your_username ALL=NOPASSWD: /bin/su

save the file ( the best is to open a root shell before in another window - just for the reason you made a mistake when you edit the file - /etc/sudoers is very sensitive ! )

then create a shell script (call it how you like it ) e.g. your_girlfriends_name with following command.
/usr/bin/sudo /bin/su - your_girlfriends_name

make this script executable.
in the terminal you have only to type: your_girlfriends_name  ( ~/any_where/your_girlfriends_name )
this will switch to your girlfriends account without asking you for a password.

have fun with both  :-)
ciao

---

### Post by alfplayer on 2010-04-29
Try running the command gdmflexiserver. After that you can switch desktops pressing Ctrl+Alt+F7 and Ctrl+Alt+F8. Be aware this runs another X server and another desktop environment, so the memory usage will increase and might be inappropriate for your hardware.

---

### Post by BlackShift on 2010-05-14
You can switch without locking when you disable locking the screen completely by using gconf-editor to set /desktop/gnome/lockdown/disable_lock_screen to True.

[http://ubuntuforums.org/showpost.php?p=9297314&postcount=25](http://ubuntuforums.org/showpost.php?p=9297314&postcount=25)

---

