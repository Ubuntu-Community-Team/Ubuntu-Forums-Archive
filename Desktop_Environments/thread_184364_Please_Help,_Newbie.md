---
title: "Please Help, Newbie"
date: 2006-05-29
forum: Desktop Environments
---

### Post by CDundee on 2006-05-29
I just installed Ubuntu 5.10 and am at a terminal.  How do I get a GUI? ](*,) I am completely new to Linux and am eager to learn.  Any and all help is greatly appreciated.

---

### Post by rado_london on 2006-05-29
So you dont have any gnome loaded. No graphical stuff only black DOS-like thing. If so try this command:
```
startx
```

if it doesnt work try this:
```
sudo apt-get install ubuntu-desktop
```

And then startx again.

---

### Post by Sef on 2006-05-29
when you installed 5.10, did you type server or not?

---

### Post by CDundee on 2006-05-29
When I typed in startx nothing happened, and when I typed in sudo apt-get install ubuntu-desktop, I got the following error code

E: dpkg was interrupted, you must manually run ' dpkg --configure -a' to correct the problem.

and when I type in dpkg --configure -a, I get

dpkg: requested operation requires superuser privilidge

so I assume that the root account is the superuser account that the error code is speaking of so what is the default password for the root account?

As to what I did on install, I did not type in server, I just pressed Enter.

Thanks again for all the help!

---

### Post by rado_london on 2006-05-29
there is no rot by default. There is sudo. Your account can be used as riit. SImply add sudo in front of every line. then it will ask for password and enter you user password.

---

### Post by CDundee on 2006-05-29
Ok so what exactly does that error code mean?  Also do I have to have the install CD in the drive when  I type in the sudo apt-get install ubuntu-desktop command?

---

### Post by decaturcomp on 2006-05-29
so you want to type:
sudo dpkg --configure -a

mmmkay?

---

### Post by CDundee on 2006-05-29
Ok thanks

---

### Post by rado_london on 2006-05-29
And remember to post if it works. You also have to have the CD or internet connecton to get the packages.

---

### Post by CDundee on 2006-05-29
Ok I figured out what was wrong, the hard drive I used wasn't big enough.
I will just go out and purchase another one in a couple of weeks and try again.  Thanks for all of your help!

---

### Post by rado_london on 2006-05-29
Good for you that you found the problem. Good luck with getting a nice HDD.

---

