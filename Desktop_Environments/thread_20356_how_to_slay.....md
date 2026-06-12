---
title: "how to slay...."
date: 2005-03-16
forum: Desktop Environments
---

### Post by redneckr1 on 2005-03-16
This may seem like a strange thread, 

right being an idiot ive broken synaptic, hard drive space is a premium and i dont need half of the application software bundled with ubuntu (handy as it may look i have no use for an offline mac server ;) ) sooo

how do i uninstall python etc... without synaptic?
 
also how can i get synaptic to work again, when i go into preferences all of the display boxes (like name, etc...) are unchecked and will not "enable".

please go gently as im extremely new to linux.


Thanks for your time

Red

---

### Post by wylfing on 2005-03-16
Synaptic is what is called a "front end" program. In other words, it's just a pretty face doing command-line work for you behind the scenes. (FYI, a lot of Linux software is like this.) The actual commands are called 'apt-get' and 'apt-cache', which are in turn fronts for dpkg, but that's beside the point.

So if you can open a terminal, you should be able to type

sudo apt-get remove gtoaster

to uninstall the program 'gtoaster'. The 'sudo' bit just gives you administrator priveleges for the purpose of running the 'apt-get' command.

The main problem with this is that you have to know the package names beforehand. That's where 'apt-cache' comes in. If you type

sudo apt-cache search gtoaster

it will show you all the package names that include 'gtoaster'. That way, you can find the name of the package you need for the 'apt-get' command. Make sense?

---

### Post by Xian on 2005-03-16
[QUOTE=redneckr1]how can i get synaptic to work again, when i go into preferences all of the display boxes (like name, etc...) are unchecked and will not "enable".[/QUOTE]
Let's just reinstall that application. Open a terminal and then:

$ sudo apt-get install --reinstall synaptic

---

### Post by canglan on 2005-03-16
[QUOTE=redneckr1]This may seem like a strange thread, 

right being an idiot ive broken synaptic, hard drive space is a premium and i dont need half of the application software bundled with ubuntu (handy as it may look i have no use for an offline mac server ;) ) sooo

how do i uninstall python etc... without synaptic?
 
also how can i get synaptic to work again, when i go into preferences all of the display boxes (like name, etc...) are unchecked and will not "enable".

please go gently as im extremely new to linux.


Thanks for your time

Red[/QUOTE]
 Swith / open up the console / terminal, try 'sudo apt-get remove appname' or 'sudo dkpg --remove appname', without the quotes, where appname is the name of the package you wish to remove.

If you want to completely remove a package, which means all the configuration files belong to the specific package will be deleted as well, try 'purge' instead of 'remove'.

---

### Post by lorap on 2005-03-16
nice explanation,one of the bests i've ever seen.
pavel

---

### Post by canglan on 2005-03-16
Here is a quick reference for you:
[http://intrepid.perlmonk.org/apt-dpkg-brief-ref.html](http://intrepid.perlmonk.org/apt-dpkg-brief-ref.html)

Hope it helps.

---

### Post by frijolito-ts on 2005-03-16
Hi redneck,

To remove packages from the system, you have other options besides synaptic.

If you know the precise name of the package to remove, run the following command in a gnome-terminal (it's in the main menu: Applications -- System Tools -- Terminal):

```
sudo apt-get remove name_of_package
```


Alternatively, you can run from the same gnome-terminal the dselect application, which will give you a (kind of) user-friendly interface for managing (installing, updating, removing, etc.) packages:

```
sudo dselect
```


However, if you prefer to use synaptic, then probably updating your packages might help. First, ensure you have a working internet connection. Then from a terminal run:

```
sudo apt-get update
sudo apt-get install synaptic

```

If you want to update your entire system (instead of just the "synaptic" package), after running "apt-get update" run:

```
sudo apt-get upgrade
```

---

### Post by fdoving on 2005-03-16
[QUOTE=redneckr1]This may seem like a strange thread, 

right being an idiot ive broken synaptic, hard drive space is a premium and i dont need half of the application software bundled with ubuntu (handy as it may look i have no use for an offline mac server ;) ) sooo

how do i uninstall python etc... without synaptic?
 
also how can i get synaptic to work again, when i go into preferences all of the display boxes (like name, etc...) are unchecked and will not "enable".

please go gently as im extremely new to linux.


Thanks for your time

Red[/QUOTE]
 two nice applications used for removing stuff you never use.. and unneccessary packages:

sudo apt-cache show deborphan
sudo apt-cache show debfoster

If one or both of them looks like something you could use, do sudo apt-get install <package names separated by spaces>.

with deborphan i use this command to automagically remove unused libraries: sudo apt-get --purge remove `deborphan` (make sure you get the right ` it's not the ')

to use debfoster, just start debfoster as root: sudo debfoster

good luck.

---

### Post by redneckr1 on 2005-03-17
thanks very much, youve all been super kind.


ill let you know how i get along :)

---

