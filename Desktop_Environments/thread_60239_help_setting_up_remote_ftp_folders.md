---
title: "help setting up remote ftp folders"
date: 2005-08-27
forum: Desktop Environments
---

### Post by Statik on 2005-08-27
Hi all,

As a nub I'm having trouble figuring out how to do this. So far, I've managed to use the places->connect to server thing to mount a remote FTP server. What I want to do is create a folder in my home directory so that I can use bluefish to browse to that folder, then to the remote server, for web development. I keep seeing reference to gnome-vfs which tells me that I'm supposed to be able to use it, especially with konquerer. Konquerer isn't on my menus anywhere . . . unless that's what file browser actually is. even so, I cannot seem to create the remote folders in any way other than the Places menu which puts them on the desktop.

I tried following the mount instructions in the ubuntu quickstart guide, and it gave an error when trying to connect to the server. I think it's because the server is a domain name instead of an IP.

Another problem is that some of the ftp servers I access require the username to be in the form of [email]user@domain.com[/email], and others only user. The later work, the former give an error (%40) becuase of the double @. Any ideas here?

Statik

---

### Post by amohanty on 2005-08-27
AFAIK you cannot do that via the fstab file (I could be off on this, but I have never seen one that could). If you can mount the drive from the cli try putting it in the .login in your home dir. if you dont have one, create one.

konquerer is the KDE file browser. Gnome uses Nautilus.

HTH
AM

---

### Post by Statik on 2005-08-27
Well, I know that if I create them using the places menu they end up on my desktop and stay there . . . is there a way to make them appear elsewhere?

---

### Post by Statik on 2005-08-30
So, I've discovered that I can't move the mount displays anywhere . . . feature request?

There hasn't been any definitive word on the username@emailaddress problem tho. IS there a solution, or are we all just pitching in the dark here?

Statik

---

