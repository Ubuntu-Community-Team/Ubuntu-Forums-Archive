---
title: "Wierd root password problem"
date: 2005-10-17
forum: Desktop Environments
---

### Post by kooshball on 2005-10-17
I just installed 5.10 on my laptop today. When i try to run anything that requires a root password like synpatic i get an error "Wrong password".

When i try to $sudo anything
and type the password i get i also get wrong password
but if i just do $su
and type the password it works just fine.

any idea what's causing this problem? and how do i fix this?

---

### Post by KingBahamut on 2005-10-17
hmmmm.....su to root 
passwd <yourinitialusernamehere> 

enter new pass 

then reproduce the problem.

---

### Post by zenodaddy on 2005-10-17
To change the root password type in : sudo passwd root and then it will ask you  to change the password

---

### Post by KingBahamut on 2005-10-17
> [B]When i try to $sudo anything
and type the password i get i also get wrong password[/B]


The user stated that he could not do this , as sudo any command failed.

---

### Post by kooshball on 2005-10-17
[QUOTE=KingBahamut]hmmmm.....su to root 
passwd <yourinitialusernamehere> 

enter new pass 

then reproduce the problem.[/QUOTE]

i tried this still same problem

i also tried changing the rootpassword too. still same problem

---

### Post by ichigo on 2005-10-17
What about
sudo -s -H
Password: [the password you set when installing Ubuntu]
?
At least this is the only way I could find to change to the root user in 5.04...
(su - or other sudo commands didn't work with the normal password...)
I hope this solves your problem!

---

### Post by kooshball on 2005-10-17
[QUOTE=ichigo]What about
sudo -s -H
Password: [the password you set when installing Ubuntu]
?
At least this is the only way I could find to change to the root user in 5.04...
(su - or other sudo commands didn't work with the normal password...)
I hope this solves your problem![/QUOTE]

im not sure what you're refering to when you said "other sudo commands didnt work with the normal password". is there more than 1 password for root?
$sudo -s -H gave me the same error.
unlike you, i can change to root by just doing $su then password. however i can't use any of the shortcuts in the system menu thing like Synaptic. however i can do it by 
$su then /usr/sbin/synaptic manually.

is it possible somethign is wrong wiht my sudo package? can i reinstal it some how?

---

### Post by kooshball on 2005-10-17
it seems like ubuntu use sudo differently from most other distros.

according to [https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)
> 
The first user created is part of the admin group, which can use sudo. Any users created after that are not by default. It is recommended that all users of Ubuntu use sudo, as it provides clear benefits to security.

does that mean user 1000 is an admin? becuase i tried sudo and use the initial user 1000's password and it still didnt work. im so lost now.

---

### Post by eraos on 2005-10-17
[QUOTE=kooshball]I just installed 5.10 on my laptop today. When i try to run anything that requires a root password like synpatic i get an error "Wrong password".

When i try to $sudo anything
and type the password i get i also get wrong password
but if i just do $su
and type the password it works just fine.

any idea what's causing this problem? and how do i fix this?[/QUOTE]

Yeah, I have the exact same problem. su works fine, but sudo ... doesn't.



Edit: Also, when I click on the "Updates Available" icon on the top bar, the thing says the password I provide is incorrect.

---

### Post by eraos on 2005-10-17
```
nick@dhcp-373-75:~$ sudo gedit /etc/apt/sources.list
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts
nick@dhcp-373-75:~$ su
Password:
root@dhcp-373-75:/home/nick#

```

---

### Post by eraos on 2005-10-17
well, my newbie solution to this was to add myself to the sudoers... 
of course, i still need to type sudo before i do anything.. but it doesn't prompt me for a password, and everything works out fine.

---

### Post by kooshball on 2005-10-17
[QUOTE=eraos]well, my newbie solution to this was to add myself to the sudoers... 
of course, i still need to type sudo before i do anything.. but it doesn't prompt me for a password, and everything works out fine.[/QUOTE]

yea that seem to fix the problem. but i think there's got to be some explanations for this

---

### Post by hashimoto on 2005-10-18
[QUOTE=kooshball]I just installed 5.10 on my laptop today. When i try to run anything that requires a root password like synpatic i get an error "Wrong password".

When i try to $sudo anything
and type the password i get i also get wrong password
but if i just do $su
and type the password it works just fine.

any idea what's causing this problem? and how do i fix this?[/QUOTE]


If you try to run Synapric or sudo it will ask for your _username_ password, not the root password. Root password is only asked if you do su.

---

### Post by eraos on 2005-10-18
[QUOTE=hashimoto]If you try to run Synapric or sudo it will ask for your _username_ password, not the root password. Root password is only asked if you do su.[/QUOTE]

well, that sounds like good explanation

this installation was the first time i've ever used different passwords for root and for my user account

---

### Post by steve.horsley on 2005-10-19
There is a good reason why sudo asks for **your** password and not the root password: If you had to give the root password, ther would be no point in having sudo to limit what you are allowed to do. Asking for your password merely tries to establish that it is still you at the keyboard and not a passer-by while you have gone for a coffee.

---

### Post by santorini on 2005-10-23
i've got the same problem too, but after reading the above explanations, i finally see that it's asking for "your" (that's MY password) password, that solved most of my puzzle who's new to this policy

but things even more weird happened on me: 

i was puzzled by this problem and i did try to go $su then run things manually. then i changed the password to my own user account password. but synaptics etc. still don't work, but with a different situation:

it just do not load

i tried to check things up in the system monitor, but the programs hadn't even been loaded. it was as if i've never clicked anything

but my system's boot the first time from a fresh installation. the things i can do now is either $su to allow root login in through GDM and run everything without limitation or run everything needing sudo manually through shell.

anyone got an idea? how can i provide more info to make the situation clear?

EDIT:

there're new error messages

Failed to run /usr/bin/update-manager as user root:
 Child terminated with 1 status

By i'm not logging in as root.

I've got another error message before this one, but I cannot get it anymore. It says something like "the underlying mechanisms of sudo do not allow you to login ... contact your system administrator". My user account was set with "Administrator Profile". I tried setting the main user group to "root" too, but it didn't work.

---

### Post by dbarro on 2005-11-13
Did anyone find a fix for this?  I have exactly the same.  I can su without a problem, and having su'd I can then run anything required.

But sudo fails with an incorrect password, and anything from Gnome that requires the root password also fails with "Wrong password"

---

### Post by dbarro on 2005-11-14
Having re-read the above, it's time to eat humble pie.

I have to add myself to the sudo group and use visudo (sounds like a newspaper game) to add myself to the sudoers.  And then bingo.

D

---

