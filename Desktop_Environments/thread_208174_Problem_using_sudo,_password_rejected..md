---
title: "Problem using sudo, password rejected."
date: 2006-07-03
forum: Desktop Environments
---

### Post by koumdros on 2006-07-03
I 'm having a sever problem after i installed k5.10.

initially i ttied to install it in a very simple manner bassicaly following the installer instructions. I eneded up with a workign system but after the second reboot i had a problemQ whenever i tried using someprogram that needed "root" access i would get the dialogasking for the password..i would input it hit enter ..and nothing happened, i was back in the previous screen.

Anyway i decided to reinstall everything from scratch , as i wasnt satisfied with the initial partioning scheme. This time i chose to do an "advanced install" and during that i was asked whether i wanted to set a seperate "rrot" password. I accepted.

Now i boot normally i go into the GUUI and whenever i try to use any program that needs "root" acess i use the password i provided during install ( and yes i am 100% that it is right.. especially as i found out my system had the well known bug where everything during installation was recoreded in a plaintext file in "/var/log/installer/cdebconf/questions.dat". So my password i sthere and i try to input the exact sdsame thing as i see there ( talkign about a bug being usefull:p)

i read on these forums that I could try to "hack" the grub loader and slightly modify the entries so i 'll get within a root enabled cl.

i tried that but it says it deosnt recognise passwd as a comand :p

any other hints? somebody wrote soemthing about changing the sudoers folder..or a file in there but i cant find the psot again :(

any pointers?

---

### Post by TwistesdTexan on 2006-07-03
Unless you login useing the root you still would use the login password of the user you loged in under. To login under root type in root in the login screen, and then the root password. If you login using a user password use the sudo comand to act as the root but also use the user password not the root password.

---

### Post by koumdros on 2006-07-03
[QUOTE=TwistesdTexan]Unless you login useing the root you still would use the login password of the user you loged in under. To login under root type in root in the login screen, and then the root password. If you login using a user password use the sudo comand to act as the root but also use the user password not the root password.[/QUOTE]

i may not have been as clear as i thought i was..

on second reading it appears as if some of the text i typed is misiing from my post ( about waht error messages i was getting etc..)
the ssytem does not accept the root password AT ANY POINT, neither the  "user " password at SUDO.

if i use the user paassword it says "password incorect" if i use the root password i get a different error message somethign like "'Conversation with su failed?'"

---

### Post by koumdros on 2006-07-03
ok..i booted from recovery console..there edited /etc/sudoers to include my user name and now everything seems to work as it is suposed to. :)

---

