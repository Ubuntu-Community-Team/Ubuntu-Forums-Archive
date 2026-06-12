---
title: "root works, but sudo doesn't"
date: 2005-08-04
forum: Desktop Environments
---

### Post by tschweg on 2005-08-04
Hello,
I've come accross  strange issue with a fresh installed Ubuntu.
Whenever I access an application that requires root access, I get asked for a password. When I enter the root password, I get an authentication error. The same happens if I do ```
 sudo synaptic
``` or alike. But as soon as do ```
su
``` and enter the password, everything works fine. I got full privileges.

From my understanding, root is disabled by default and sudo is only allowed to the first created user (during installation). But on my box it seems to be exactly the opposite!

So how can I enable my user to access those root-protected applications without giving him root access to everything? And why isn't sudo allowed for my first user,  when it should be?

---

### Post by mrcbrown on 2005-08-04
[QUOTE=tschweg]Hello,
I've come accross  strange issue with a fresh installed Ubuntu.
Whenever I access an application that requires root access, I get asked for a password. When I enter the root password, I get an authentication error. The same happens if I do ```
 sudo synaptic
``` or alike. But as soon as do ```
su
``` and enter the password, everything works fine. I got full privileges.

From my understanding, root is disabled by default and sudo is only allowed to the first created user (during installation). But on my box it seems to be exactly the opposite!

So how can I enable my user to access those root-protected applications without giving him root access to everything? And why isn't sudo allowed for my first user,  when it should be?[/QUOTE]
 What is the error you get when you use sudo from console? Root's not disabled - it's more like discouraged as running  as root can end up with larger scaled "oops!" situations - even for trained linux folk - ie. 4 years ago my buddy working late tried to rm a directory and accidently put in:

rm - fR files / 

Needless to say... that space made many people on his server cry in the morning, and me and him were up till 4 that following afternoon restoring clients from backups and dealing with folks calling.... ah those were the days.

Also check /var/log/messages - see if anything in particular is coming up in there as well.

---

### Post by nemin on 2005-08-04
[QUOTE=tschweg]Hello,
I've come accross  strange issue with a fresh installed Ubuntu.
Whenever I access an application that requires root access, I get asked for a password. When I enter the root password, I get an authentication error.[/QUOTE] The only thing I can think of it that you don't enter the right password with "sudo". You should enter the *user* password and *not* the root password. 
Though, the su story still sounds really strange to me :-?

---

### Post by tschweg on 2005-08-04
[QUOTE=nemin]The only thing I can think of it that you don't enter the right password with "sudo". You should enter the *user* password and *not* the root password. 
Though, the su story still sounds really strange to me :-?[/QUOTE]

This is me after realizing that I tried for 3 days to run sudo with the root password:  ](*,) 

Thanks for your help ;)

---

