---
title: "I'm an idiot: I deleted my desktop"
date: 2006-02-21
forum: Desktop Environments
---

### Post by 90Brougham350 on 2006-02-21
I was using synaptic yesterday downloading some small programs for Gnome. I hit apply and left  the room. When I came back later, everything was done, so I used the computer for a while and shut it off. When  I turned it back on later, I quickly realized I had no GUI to work with. My biggest   problem is  that I'm  in Italy right now, and my computer  is full of pictures from a lot of people. Normally, I would just say screw it and reinstall Ubuntu, but I have neither the CD, or  the desire to delete a few thousand pictures. Is there any  way I can get the desktop back?  I can hook the laptop up to the internet, but I don't know hardly any code at all. Feel free  to laugh, I know, I kind  of screwed myself on this one! Thanks for any help  you  can provide!

Brian

---

### Post by heimo on 2006-02-21
[quote=90Brougham350] When  I turned it back on later, I quickly realized I had no GUI to work with.[/quote]

So do you have command line? Couple things I'd check - you were updating packages, so there might be something that didn't work as expected. Run this to make sure packages were configured:
```
sudo dpkg --configure -a
```

And if that gives any output, you may need to update again:
```
sudo apt-get update
sudo apt-get upgrade

```

Then try closing and opening your graphical user interface using:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```


Give us any errors/warning you get and we may be able to help you.

---

### Post by alamba on 2006-02-21
Are you able to log into the command line?

A

Edit: Too slow. The above should fix it for you.

---

### Post by 90Brougham350 on 2006-02-21
Yup, I can get to a command line and login to my normal username. I'll try the help you've provided and get back. Thanks!!!!!!!

Brian

---

### Post by rudiz on 2006-02-21
....

---

### Post by 90Brougham350 on 2006-02-21
Alright, the updates worked, but I couldn't get the code to launch the GUI to work. It didn't do anything, it just sat there at the promt.

Brian

---

### Post by suRoot on 2006-02-21
What do the X logs say?

/var/log/Xorg.*.log

---

### Post by engla on 2006-02-21
Are you sure you didn't inadvertedly remove something you really need?

Be sure to try 'sudo apt-get install ubuntu-desktop' to see if you have all components installed... If you have removed anything, even openoffice.org it should reinstall all that for you.

---

### Post by 90Brougham350 on 2006-02-21
It says the following new packages will be installed:
  gdm ubuntu-desktop                    ubuntu-sounds

then  it  asks me if i  want to continue  and  i hit Y   and  it asks for the CD which  i don't have.   I'm assuming it wants to install the desktop from what it says.

Brian

---

### Post by engla on 2006-02-21
You will have to do this to enable internet sources and disable the CD source.

I'm assuming you use Ubuntu Breezy 5.10. If you don't, DO NOT follow these instructions.

You need to edit /etc/apt/sources.list as root. Do:
$ sudo nano /etc/apt/sources.list

Remove the old contents of the file and make sure it reads like this
```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```
(Only the lines without # are important)

Now you should be able to run apt-get and install things off the internet sources.
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by dcast on 2006-02-21
would it help to remove the cd from your /etc/apt/sources.list so then it would just download whatever you need off the net?

---

### Post by kaamos on 2006-02-21
```
sudo nano /etc/apt/sources.list
```
comment out the cd with a "#". Save the file and do
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

edit: too slow ;)

---

