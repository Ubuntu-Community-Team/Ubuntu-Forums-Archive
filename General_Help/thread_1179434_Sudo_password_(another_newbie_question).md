---
title: "Sudo password (another newbie question)"
date: 2009-06-05
forum: General Help
---

### Post by iiyohnewb on 2009-06-05
ok so the terminal, when someone says copy the code and put it in the terminal i do, but it always asks for a dang sudo password...

ive tried to type in my own password and nothing happens and then it just says WRONG PASSWORD then after 3 times it gives up, if anyone can help or point me in the right direction that would be greatly appreciated

and sorry for asking all the newb questions

---

### Post by marshall.robert on 2009-06-05
Can you give us an example of the commands you are given?

---

### Post by solidsnake204 on 2009-06-05
It should be your own password, make sure you are typing it correctly and in the correct case (lower or UPPER).

---

### Post by iiyohnewb on 2009-06-05
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

its commands for installing flash packages, and firefox stuff, someone referred me to that thread but the terminal is giving me problems and, when i type my password nothing happens it stays blank, im using 
(9.04 jaunty by the way)

and yeah ive tried my current password and my first password i had when i fist installed ubuntu

---

### Post by marshall.robert on 2009-06-05
Well, the sudo command gives you temporary root like privilages allowing you to do things like install software.

When you are presented with a request to type in your password after using a sudo command you should type your normal user password. When typing there will be no characters appearing on the screen, this is normal. You then press enter and continue.

If this is what you are doing then make sure you are using the correct password, which is the same one you use to log in given you dont use automatic login. Remember; passwords are case sensitive.

---

### Post by rsmseys on 2009-06-05
Try changing the password (both your password and the root account password) to the same thing.

System -> Administration -> Users and Groups

Change your user password, unlock it using that password, then change the root password to the same thing.

---

### Post by marshall.robert on 2009-06-05
> **rsmseys said:**
> Try changing the password (both your password and the root account password) to the same thing.

System -> Administration -> Users and Groups

Change your user password, unlock it using that password, then change the root password to the same thing.

I don't suppose you really thought about this answer? It requires that you know your password, the same way as you would with sudo, which is what the problem is...

---

### Post by iiyohnewb on 2009-06-05
ok thank you ill try that

---

### Post by jrox717 on 2009-06-05
Are you the only user on your machine? If you are not then it's possible that you don't have root priviledges. Try performing a root command from another user and if that works then you can change the priviledges for your own username by going to System > Administration > Users and Groups.

---

### Post by Word Life on 2009-06-05
> **iiyohnewb said:**
> ok so the terminal, when someone says copy the code and put it in the terminal i do, but it always asks for a dang sudo password...

ive tried to type in my own password and nothing happens and then it just says WRONG PASSWORD then after 3 times it gives up, if anyone can help or point me in the right direction that would be greatly appreciated

and sorry for asking all the newb questions

sudo password, or [sudo] Password: is when you put the password to your administrative account on your computer. So lets say you log in with the user of "abcdefg". Type in the password you used to log in to the account when you get that message.

---

### Post by iiyohnewb on 2009-06-05
man i figured it out, i didnt unlock and authenticate my account like someone said =P, i just didnt expect that to be it...i thought i had the privileges since im the only user, well thank you for the help

---

