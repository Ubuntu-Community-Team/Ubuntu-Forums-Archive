---
title: "Setting current directory when making desktop launcher"
date: 2009-07-01
forum: Desktop Environments
---

### Post by Darvenkry on 2009-07-01
I want to make a desktop launcher for Alien Arena. From the terminal I need to go:

cd /home/garry/Alien_Arena
./crx

How do i set current directory in desktop launchers coz using a direct path like   /home/garry/Alien_Arena/crx   does not work. Thx

---

### Post by PureLoneWolf on 2009-07-02
Hi

I had this issue with some games, so I now create a text file that contains the commands I would normally run in the terminal - Make the text file executable and then change the icon to the game icon.

Works well for me :)

Hope that helps

---

### Post by ronaldprettyman on 2009-07-02
Wow read that three times. My closest guess is your trying to add a directory to your path. Like /usr/bin.
look at your path with
```
echo $PATH
```
add to your path with
```
PATH=$PATH:/new/dir/you/want/to/add
```
and add export code to your .profile file
```
vi ~/.profile
```
add to end of file
```
export PATH=$PATH:/new/dir
```

variable in bash, one thats kinda kewl
```
PS1="variable$ "
```
don't export that last one in your profile though

---

### Post by airtonix on 2009-07-02
Ronald,

you should suggest people use gedit to edit text files. 

most of the time the are presented with vi or nano they have no idea how to do the basic things.

original poster also doesn't need to do any of the things you listed.

all thats required is to make a shell script (an executable text file) that lives in the games folder.
But purelonewolf already mentioned this.

---

### Post by Darvenkry on 2009-07-03
PureLoneWolf, bloody useful trick u have, thanks alot, works a treat

---

### Post by RandyN on 2013-03-28
@ Purelonewolf - Thank you! Thank you! This was the easiest way I found to make a shortcut to launch the game.

---

### Post by wildmanne39 on 2013-03-28
Thread closed. Please do not post in old threads.

---

