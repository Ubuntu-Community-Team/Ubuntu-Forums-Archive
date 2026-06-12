---
title: "after activating root"
date: 2006-01-13
forum: General Help
---

### Post by Aaron Hoy on 2006-01-13
I didn't like the idea of not having a root user and just having the first normal user have administrative access to everything, so I did like everyone said and activated root and then I removed myself from the administrator group.  However, now whenever I try to access somthing from the gnome menu that requires root, such as the users and groups, it still just asks for MY password.  My password doesn't work because I dont have access anymore, and the root password doens't work because that's not what it's looking for.  When I enter the root password anyway, it says that it was the incorrect password for root, which makes no sense because it IS the correct root password, it's just that that's not what it was expecting.  How can I get all the user privleges to normal so when I try to access these things it asks for the root password, just like in debian?

---

### Post by amohanty on 2006-01-13
I think in /etc/sudoers you will have to add the following line to the end:
> your_username ALL=(ALL) ALL

open a terminal
su
provide root password
use favorite editor (preferably vi :) ) to edit the file and add the line

HTH
AM

---

### Post by Aaron Hoy on 2006-01-13
ahh see that is the exact opposite of what I want.  
what that did was give my normal user privleges to change users and groups but still asks for my password.  this is the default in unbuntu, which makes no sense to me because it should not need your password if you are already logged on under that name.  the desired behavior is that of a normal class linux setup like debian in which you try to access such a program as a normal user and then you are prompted for the root password, not your own.  Anyone know how to fix this?

A side note: Also in unbuntu, because it is configured assuming that you have no root, if you try to sudo something you dont have permission to, instead of asking for the root password, it just does nothing, which is bad.  Also if you set up another user account the idea behind ubuntu is that that one will not have administrative privleges and only the first account will, but when you try to sudo something from the guest account it once again just does nothing instead of asking for the root password.

---

### Post by ardchoille on 2006-01-13
Congratualtions. Activating the root account just made your computer easier to break into:

[http://www.ubuntuforums.org/showthread.php?t=116564](http://www.ubuntuforums.org/showthread.php?t=116564)

---

### Post by Aaron Hoy on 2006-01-13
the post you linked suggests that someone actually log in as root.
this is bad, my intention is only to use su to become root temporarily for just along enough to perform administrative tasks.  This is the normal way of doing things in linux an it is actually more secure (if you are actually worried about that sort of thing, although I wouldn't be) than the default ubuntu method.  The way ubuntu sets things up, the first user has administrative privleges, this IS pretty much like logging in as root as the post describes.  By activating he root user and chaning your account back to a normal one you are making sure you will only change something important when you really want to, and no program run by your user can screw up anything important either.  I however dont really worry about security because i'm not paraniod enough to think that anything like that is going to happen.  I just prefer the classic way of using su.

---

### Post by amohanty on 2006-01-13
> Congratualtions. Activating the root account just made your computer easier to break into:

[http://www.ubuntuforums.org/showthread.php?t=116564](http://www.ubuntuforums.org/showthread.php?t=116564)


I am sorry but thats not necessarily true. Sometimes some apps dont work under sudo because of env settings not being transferred. And if sudo is setup the same way as it is in a default ubuntu install, you or a cracker can do just as much damage as root by cracking just your password. One thing to keep in mind regarding security (and I have said this previously somewhere around here) is that if someone is determined enogh and skilled enough, they _will_ get in. The best you can hope for is to know about it in a short enough time period so that you can respond appropriately. Enabling root does not make it any easier or harder to break into a box. I believe  (and please corret me if I am wrong here) the motivation behind ubuntu's default sudo is to prevent you from screwing up more easily. 

AM

---

### Post by amohanty on 2006-01-13
> ahh see that is the exact opposite of what I want.
what that did was give my normal user privleges to change users and groups but still asks for my password. this is the default in unbuntu, which makes no sense to me because it should not need your password if you are already logged on under that name. the desired behavior is that of a normal class linux setup like debian in which you try to access such a program as a normal user and then you are prompted for the root password, not your own. Anyone know how to fix this?

I think what you want then is what you already have :)
To tighten it up you could customize the sudoers file and allow only relevant stuff to be run by your user eg update-manager etc. Read the manual for more details:
[http://www.courtesan.com/sudo/man/sudoers.html](http://www.courtesan.com/sudo/man/sudoers.html)

HTH
AM

---

### Post by Aaron Hoy on 2006-01-13
i agree that ubuntu deactivated root for the good reason of keeping people from screwing up their computers.  however, they should have just made it so you cant log in as root in X, but you can still su in.  Then do away with the first user having administrative privleges sortof but only sortof and having to enter your own password again to do certain things.  I definately agree that noone should just login as root, but that doesn't mean the acount should be disabled.  On the subject of security, what the hell do you people have on your computers that you think someone wants to get to it so bad they are going to hack into your machine?  If someone has the ability to somehow brute force your password for your normal account or get into it by some other method (which would be pretty difficult seeing how there is a maximum rate of password tries), they could have just as easily done the same thing to root.  I cant imagine how anyone would just into my machine unless they sent me something that I willingly executed as root or something rediculous like that, and I also cant think of any reason anyone would WANT to get into the machine.

---

### Post by Aaron Hoy on 2006-01-13
[QUOTE=amohanty]I think what you want then is what you already have :)[/QUOTE]

Right will I am one step towards it.  The problem is, ubuntu is recognizing that something should only be run by an administrator, but since they are assuming you have things set up the default way, it just says to enter YOUR password.  And then it is actually expecting YOUR password, if you enter the root password or any other password it says it is wong, and if you enter yours it just waits a little while and then does absolutely nothing.  the problem is that the system is expecting the normal user to have the administrative privleges that ubuntu set them up with.  It currently expects the users password, it needs to expect the root password when performing administrative tasks.

---

### Post by aysiu on 2006-01-13
[QUOTE=Aaron Hoy]This is the normal way of doing things in linux an it is actually more secure (if you are actually worried about that sort of thing, although I wouldn't be) than the default ubuntu method.  The way ubuntu sets things up, the first user has administrative privleges, this IS pretty much like logging in as root as the post describes.[/QUOTE] Actually, this isn't true. You use your own password to temporarily gain root privileges with the *sudo* command, but you do not normally operate as root just because you're the first user. In fact, you're far less likely to do stuff accidentally, as you have to preface *every* root command with the word *sudo*, whereas with the traditional model, you can forget you're in *su* and do whatever.

I'm not saying *sudo* is necessarily a better security model--I just think you're misrepresenting it. To read more about the pros and cons of root and sudo, look at this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

I don't see what the big deal is. In the traditional model, this is what you'd do to install Thunderbird: ```
su
password:
apt-get update
apt-get install mozilla-thunderbird
exit
exit
``` In the Ubuntu model, this is what you'd do to install Thunderbird ```
sudo apt-get update
password:
sudo apt-get install mozilla-thunderbird
exit
```

---

### Post by Aaron Hoy on 2006-01-13
your right i t's not really a huge deal, it's just a matter of preference.
i'll admin it's true that it's easy to forget to exit from su, but that's not something i'm really worried about.
sometimes I will do alot of things in su at a time and I would rather not type sudo before each one.  also as someone commented in the post that was linked, some things just dont work at all when things are set up this way.  for example, on another machine that I have ubuntu on I was using a graphical printer configuration tool as a last resort and it prompted me for a username and password. root didn't work because there wasn't one, and he current user didn't work because the program was hardcoded I guess to only accept root.

---

### Post by amohanty on 2006-01-13
> On the subject of security, what the hell do you people have on your computers that you think someone wants to get to it so bad they are going to hack into your machine?

This is a very big misconception a lot of people have. Its not your data, but your internet connected box that crackers might want to control. It could then be used as a jumping point for more dangeous and/or criminla activity. So securing your box os not only good for you but for everybody else too.

AM

---

### Post by Aaron Hoy on 2006-01-13
I'll agree that if someone gained access to your root acount they could use it as a proxy or something similar and cause problems for everyone, but like I said before, what is someone going to do, brute force your password? there is a maximum try rate among other brute force countermeasures to make it so the average case brute force success takes like a million years or something.  Now if someone is physically at your computer thats another story, but over a network there's pretty much no way to get in without having a password ot getting the user to exeute something like a trojan themselves.   If you have a secure password and you dont go around executing just any old file you find, it should be completely safe.

---

### Post by amohanty on 2006-01-13
I suggest you take a look at the following books:
1. Linux and OpenBsd Firewalls
2. Hacking Linux exposed

They are a bit old, but it will give you some insight as to the methods available to a skilled cracker to get into your box.

HTH
AM

---

### Post by Aaron Hoy on 2006-01-13
I have a pretty good idea of what's possible, but a modern version of linux is not suceptable to buffer overflow attacks and the like because if was more carefully coded.  Anyway as nice as it has been to hear what everyone has to say about security, lets get back to the main topic.
whether you think it is a security risk or not, does anyone know how to get ubuntu to expect the root password and not the user's password when trying to do administrative tasks.  All the answers I have gotten so far told me how to do the opposite.  Even if you do things the ubuntu way and dont activate the root user, the problem still arises if you create a second user.  That user cannot successfully sudo or anything of the sort either because of the assumptions ubuntu makes about the way you are managing the computer.  Can anyone help?

---

### Post by Corvillus on 2006-01-13
You'd actually probably have to go through all of the menu items that do "gksudo command" and replace it with "gksu command", or something to that effect, because Ubuntu is set up to use gksudo instead of gksu by default for everything. As for the whole security model thing, su vs sudo doesn't really offer much difference in terms of security...both of them are only as secure as your password. And they both offer the ability for user restricted authentication (su has the "wheel" or "root" group which can be enabled by editing /etc/pam.d/su, and if you do this, only users in that group can su to root, and sudo by default in ubuntu restricts privileges to users in the "admin" group). However, sudo does offer a couple of advantages, in the ability to log each command you do, and in multiuser environments the ability to restrict the commands a given user can do, so with sudo, you can give people root privileges for some commands but not others (for example, you might give a webmaster the ability to run apache as root and only apache as root so he can restart the server...etc). Also, you can make sudo use the target user (typically root), or the root password instead of the invoking user password for authentication, if you want to do that, add either runaspw or rootpw respectively to the end of the Defaults list in /etc/sudoers. For example, to make it use the root password, you can change this line
```
Defaults	!lecture,tty_tickets,!fqdn
```
to
```
Defaults	!lecture,tty_tickets,!fqdn,rootpw
```
gksudo will still say it wants your password, but it will only authenticate with root's after doing this modification...same goes for sudo at the command line

---

