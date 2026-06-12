---
title: "Folder Permissions and ability to install applications"
date: 2006-01-11
forum: Desktop Environments
---

### Post by DigitalDuality on 2006-01-11
I've installed Ubuntu on a Mac Mini of mine, a Dell, and a PII 400mhz PC and it worked beautifully.

I took the big step and made my main PC Celeron 1.8ghz, 2GB mem (HP Pavilion 513n.. i didn't have a choice in this machine.. it was purchased for me)..into an Ubuntu machine. 

I can't seem to install any application what so ever. Stuff that should be really easy to install (like adobe reader).  Then i noticed i dont have file permissions anywhere except my Home folder and subfolders of the home folder.

Maybe related, but when i go to the nice little Add Applications feature, i get this message 
"The application cannot be found in your archive.  This usually means it's not available for your hardware platform."

Huh?  Why the hell not?    Any help would be greatly appreciated. :)

I've spent close to 30 hours backing up a 2nd 400 Gb (300 used) NTFS hard-drive just so i can re-format it to FAT so it can be read and written to by Ubuntu.. i hope this isn't going to be some problem that plagues me on this machine in particular.

---

### Post by DoorGunner on 2006-01-11
Did you set up your regular user account??

---

### Post by DigitalDuality on 2006-01-11
During the install right? If so, then yeah.  It's the only acct on the machine

---

### Post by DoorGunner on 2006-01-11
sorry for all the questions .....it helps me to rule things out....

Are you following the ubuntu guide?
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by DigitalDuality on 2006-01-11
no i didn't.  I think the install itself is pretty simple, straight forward and to the point. Having installed it one two other machines.. i didn't think there would be a need to.

---

### Post by DoorGunner on 2006-01-11
Right now it sounds like the your user was not set up........I would go back to the ubuntu guide and retry the administration section. that may help

but are you logging in as your normal user??
can you access root from termial?

---

### Post by DigitalDuality on 2006-01-11
i just tried to re-install the OS and the user that came up by default was a random user in the network i'm on.  Odd.  Would active directory on a Win 2003 box automatically shoot down a user to it?  I'm just gonna re-install from stratch while not online and see how it goes.

---

### Post by shanghaipi on 2006-01-11
To access and change files and folders that you don't have permissions to, you have to enable the Root Privileges. That means you have to type this into the terminal:



```
sudo su
``` 
(You'll have to enter your password to get Root privaleges.)

```
sudo nautilus
``` 

(This will open up your file browser with Root privileges so you don't have to do everything with the terminal. Another thing, don't close the terminal while you are playing around with nautilus because it will exit nautilus.)

---

### Post by DigitalDuality on 2006-01-11
any idea why this happened upon install, while i've never come across this in two other installs?

---

### Post by DoorGunner on 2006-01-11
> sudo su or just su

I dont believe he had set up his user account yet. That was my driving point. Once he is set up then you dont need root privileges to edit your home folders since your home folders would be part of you user profile. 

Actually i think we are saying the same thing but from different perspectives shanghaipi. 

Maybe what he needed to do was to go back to basics and use the guide to get up and running properly. He will have to anyways now given he is reinstalling.

**edit

sorry Digital Duality......i was speaking to shanghaipi. The installation only gives you interm user priviledges.....you have to go in and set the rest up.....I have 4 os's on my machine and the best advice i can give you is to go back to basics and follow the official guide .... you cant go wrong......if you havent done the install yet go back and follow the guide.....it doesnt hurt and you might find some things you missed. no offence intended

---

### Post by aysiu on 2006-01-11
[QUOTE=shanghaipi]
```
sudo nautilus
``` 

(This will open up your file browser with Root privileges so you don't have to do everything with the terminal. Another thing, don't close the terminal while you are playing around with nautilus because it will exit nautilus.)[/QUOTE] If you use Alt-F2 ```
gksudo nautilus
``` you don't have to worry about closing (or opening) the terminal, and it does the same thing.

---

### Post by jerrykenny on 2006-01-11
It all sounds OK really, you're not supposed to have permission to read / write on folders rather than you're own home folder.

Are you actually using the Synaptic package manager to install programmes?   ie System > Administration > Synaptic ?

It sounds like you're using the Gnome facility instead ?

You may have to add repositories to your apt.sources list, look at the ubuntu starters guide for this.

Dont try to manually insert binary files for Adobe, or stuff like that, you'll compromise your system. . .

---

### Post by DigitalDuality on 2006-01-11
i haven't started too yet.. lol i'm at work.. i'm taking this sucker home and see what i can do.  More than likely i'll be re-installing though.

---

### Post by DigitalDuality on 2006-01-11
[QUOTE=DoorGunner]
sorry Digital Duality......i was speaking to shanghaipi. The installation only gives you interm user priviledges.....you have to go in and set the rest up.....I have 4 os's on my machine and the best advice i can give you is to go back to basics and follow the official guide .... you cant go wrong......if you havent done the install yet go back and follow the guide.....it doesnt hurt and you might find some things you missed. no offence intended[/QUOTE]

No offense taken, you've been quite helpful :)

---

### Post by shanghaipi on 2006-01-11
I was just giving a quick fix, but you are right Doorgunner. 

I forgot about the alt-F2 shortcut and didn't know about the gksudo command...learn something new everyday.  Thanks aysiu.

---

### Post by DigitalDuality on 2006-01-11
[QUOTE=shanghaipi]To access and change files and folders that you don't have permissions to, you have to enable the Root Privileges. That means you have to type this into the terminal:



```
sudo su
``` 
(You'll have to enter your password to get Root privaleges.)

```
sudo nautilus
``` 

(This will open up your file browser with Root privileges so you don't have to do everything with the terminal. Another thing, don't close the terminal while you are playing around with nautilus because it will exit nautilus.)[/QUOTE]

and when i do that i get this: 

```
(nautilus:8101): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

But i have folder permissions like you said.

---

### Post by shanghaipi on 2006-01-11
I get that to, with a different number in parentheses.  Follow aysiu's instructions.  They are much easier, and you don't have to keep the terminal open.

---

