---
title: "root/sudo privileges and &quot;authorize&quot; button"
date: 2008-08-08
forum: Desktop Environments
---

### Post by wally80 on 2008-08-08
Hi all!

I am a slackware user recently jumped into xubuntu.
I would have a question regarding the root account and the sudo management.
I've read (and understood) the document help.ubuntu.com/community/RootSudo regarding the fact that a user can administer the system without requiring to know the root password.
Now I have a problem:
I share a user with my girlfriend. I don't want to create different users for other reasons, but I would like that when I "administrate" the system it asks me for the root password and not for the user password.
I accomplished it by putting the option "rootpw" into etc/sudoerc.
Everytime I type a sudo, it asks me for the root password.
This works also with gksudo (synaptics for examples asks for the root password too).
Now it comes my problem:
In KDE/gnome/xfce some windows require that I press the button "authorize" to activate some administrative options. When I do it, it still asks me for the user password.
Is there a way to tell the system that also in that case I want to be asked for the root password?

What I want is basically this:
A user, who is not capable of doing ANYTHING administrative unless he/she types the root password.

(I tried to remove the administrative privilege to the user, but this prevents the user from issuing a sudo...)

Many thanks,
Danilo

---

### Post by tamoneya on 2008-08-08
remove the user from the admin group.  Then the authorize button wont work at all.  You can then login as root to change things.  Are you really worried about your girlfriend messing up networking.  Tell her if it prompts for a password that she should not mess with it.

---

### Post by wally80 on 2008-08-08
> **tamoneya said:**
> remove the user from the admin group.  Then the authorize button wont work at all.  You can then login as root to change things.  Are you really worried about your girlfriend messing up networking.  Tell her if it prompts for a password that she should not mess with it.

I discarded the solution you propose because I would not like to login as root everytime I need to change something.
I just wanted to change the way authorize works.
But what's the sense of authorize, if you cant change the password that it asks?
A user authorizes himself to do something? :-)
Is there maybe something to change in /etc/policykit.conf?

thanks,
Danilo

---

### Post by woaibbhemm on 2008-08-12
hello~
  nice    to   meet   you .   
 thank  you   for   your   sharing    and   welcome    to  our   website .  a  big   funny    game   just   waiting     for   you !


     





Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[url=http://www.usfine

---

