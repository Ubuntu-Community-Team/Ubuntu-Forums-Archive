---
title: "Useradd without login"
date: 2009-06-17
forum: General Help
---

### Post by Mack1 on 2009-06-17
Hi all,

I am trying to setup my own mailserver. I've done this in the past on windows but i am trying my bestest to get away from it.

At this time i was successfull to get a combination of fetchmail, postfix and dovecot running. And i use cli and webmin both.

Why everyone always says that setting up a mailserver on ubuntu is a breeze is beyond me, i had to read like 100+ howtos and through trial and error, i got it running.

My question is this:
I have added a few users to get fetchmail to retrieve e-mails for those users from our isp via pop3.

These users however show up in the login screen of ubuntu, which i do not want.

Can someone explain what i do wrong (or don't do) when i add a user through:

sudo useradd -d /home/a9999 -m a9999 -g users -s /bin/bash

As said the user gets added and the mailserver works ok but i do not want the user to be able to login in the login screen.

I am very grateful for any help, thanks! :D

---

### Post by madverb on 2009-06-17
Are you using Ubuntu desktop for a server?
Anyway, to stop them from showing up you can change it via System > Administration > Login Window > Users

---

### Post by Ocxic on 2009-06-17
go to System->Administration->Login Window Preferences, then to the users tab. you will be able to exclude users from the login screen from there.

---

### Post by Mack1 on 2009-06-17
Thanks for your replies!

I am using a seperate computer as a file/print/mail/etc server, it's running windows xp atm and it's fine for my homeneeds (so no win2003 server etc. needed)

Atm i am busy getting ubuntu server running on it. Ubuntu server is installed and i am fiddling with setting up a mailserver on my other computer which runs ubuntu desktop version.

When this works ok i will set things up on my ubuntu server box.

That is the reason why i want to know how to know how to get those users not to show up in the login screen (although no-one will login to the server i know...).

I cannot go to system > Administration > Login Window > Users on my ubuntu desktop as it once was a Kubuntu desktop on which i installed ubuntu desktop and i've been using ubuntu ever since.
It says something like GDM is not active..

Living life the hard way ey :-)

So....you cannot help me with a non-graphical way of getting them not to show up in the login screen? :(

---

### Post by Chris Musampa on 2009-06-17
You could make GDM your default with:

sudo dpkg-reconfigure gdm

---

### Post by Mack1 on 2009-06-18
Hi Chris,

Worked like a charm thank you!
I've learned another thing about linux/ubuntu.

I know it was a bit weird to ask about this because a server normally doesn't have a desktop and users do not log on to it through the desktop but i just had to find out how to do it.

The fact that i once installed through kubuntu and now using ubuntu on my desktop was the thing that messed up my test.

Thanks again!

---

### Post by Chris Musampa on 2009-06-18
Glad it worked for you Mack :D

---

