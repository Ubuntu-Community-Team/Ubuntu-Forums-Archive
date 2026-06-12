---
title: "installing gui error"
date: 2006-09-29
forum: Desktop Environments
---

### Post by cooper on 2006-09-29
Hi guys

I am trying to install linux on a server.

I have a compaq proliant server and have configured a set of raid drives and installed ubuntu server

i want now to install a gui then samba so my windows network can use this as a file server/intranet

I put the command in to install the gui it runs fine

then i get a error at the end

E;unable to feach some archives, maybe run apt get update or try fix with --fix-missing?

entered 

sudo apt get update

this ran but i cant get the gui to start

i know this must be a quick fix

i have installed the server on a test machine before running it on here

thanks for advice given

cooper

---

### Post by pod25 on 2006-09-29
You need to edit your sources.list to include some hased out entries

---

### Post by cooper on 2006-09-29
could you explain this further or point me to an area that does

thanks

have also tried the command

sudo /etc/init.d/gdm start

---

### Post by pod25 on 2006-09-29
> **cooper said:**
> could you explain this further or point me to an area that does

thanks

have also tried the command

sudo /etc/init.d/gdm start

edit: sudo nano /etc/apt/sources.list
It should look like this :
```
#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://de.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
 deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by cooper on 2006-09-29
so ive opened the edit and the screen is blank apart from the top line and the bottom commands.

havnt a clue what ive got to do here.

I didnt have to do this last time i installed this

would i be easier for me to install ubuntu desktop and im gonna need a desktop to make this server work as i am a windows user and cant handle all the commands :-D

---

### Post by pod25 on 2006-09-29
> **cooper said:**
> so ive opened the edit and the screen is blank apart from the top line and the bottom commands.

havnt a clue what ive got to do here.

If it's empty then that must mean it doesn't exist ! which I know it does.
Did you copy and paste the commands in ?

But once you do find the correct sources.list after you have edited it press CTRL/O then CTRL/X

---

### Post by ajgreeny on 2006-09-29
There's a very good default sources.list file entries info at:-
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Edit your file by deleting everything in it and adding the appropriate text from the site, then run *sudo apt-get update* in a terminal.  Hopefully all will now be OK.

---

### Post by cooper on 2006-09-29
thankyou for the reply

gonna be busy for the rest of the weekend, but will be back on this monday

---

### Post by cooper on 2006-10-02
Right so i need to get the code above copied onto the server and updated.

How do i achieve this, im viewing the code on my laptop at the moment and i dont know how use the server the feach the code.

:confused:

---

### Post by ajgreeny on 2006-10-03
Can you just copy the text on your laptop as a text file (sources.txt) onto a usb flash card or something then transfer the file to your server, open it with the command *cat* and then copy it to your server sources.list file using *sudo nano /etc/apt/sources.list*.  Now save the file (Ctrl+x) and you should be good to go.

---

