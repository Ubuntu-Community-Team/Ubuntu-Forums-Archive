---
title: "Installing software"
date: 2005-12-11
forum: General Help
---

### Post by leupi on 2005-12-11
Hi all,

This is my first post here and I am brand new to Ubuntu so please be patient...  :)

I am trying to install Skype and am having a few issues. When I go into Synaptic and do a search for 'skype' I get no results. Am I supposed to add repositories to it after installing Ubuntu?

When I go to the command line and type:
```
apt-get install skype
```
I get:
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```
I also went to Skype's website and downloaded the file:
skype_1.2.0.18_i386.deb
But when I try to open it I get:
```
Could not open "skype_1.2.0.18-1_i386.deb"

Archive type not supported.
```
If someone could point me in the right direction I would certainly appreciate it. Thank you.

Todd

---

### Post by Rackerz on 2005-12-11
To install that .deb file open up the terminal (console/command line).

Type;

cd /path/to/file
sudo dpkg -i skype_1.2.0.18-1_i386.deb

It will ask for your password just type it in and it should all run fine. I'll just find a page which explains about adding the repositories, then i'll add it.

Here is two pages that should help. 
Extra repositories - [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
Installing software - [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Credits go to aysiu for the links.

---

### Post by taurus on 2005-12-11
If you want to run "apt-get" from the command line, you need to close down synaptic!!!  You can't have synaptic open and run apt-get at the same time.

Since you downloaded skype_1.2.0.18-1_i386.deb, you can install it with

sudo dpkg -i skype_1.2.0.18-1_i386.deb

---

### Post by Qrk on 2005-12-11
Skype is not included in the repositories. 

But you need to do three things to get what you want to work.

The first is easy, when you run apt-get... you must add sudo before the command to get root permissions.

```
sudo apt-get install X
```

next you should enable the other repositories.

Run 

```
sudo gedit /etc/sources.list
```

and remove the # before the lines with addresses. Also, add a # before the line with the cd in it.

Lastly, the way to install a .deb, such as the skype you downloaded is first to change to the directory you saved skype to.

```
cp /path/to/directory
```

Then to run the command

```
sudo dpkg -i skype_1.2.0.18_i386.deb
```

---

