---
title: "Need Help creating a application shortcut on desktop"
date: 2009-03-18
forum: General Help
---

### Post by codie72 on 2009-03-18
Hello I am a bit of a newb but i have been reading pages for about 4 hours trying to work this out.
I am running Ubuntu 8.10

I have downloaded and installed the game assultcube
now I can run it from console typing "sudo sh assultcube.sh"
however I would like greatly to add this game to the /usr/games directory like all my other games that Ubuntu installed automaticly.

I have worked out how to copie files into the secure games folder by doing
"Alt-F2 and run 'gksudo nautilus"
then I copied the game into a folder called assult.

however I have been looking for ages and trying many things to create a shortcut to the game from my desktop or from my games Applications/games bar.

If anyone knows how I can simply add this link so all i have to do is click the link and run the game like the rest of em please let me know.

--------
i have gotten warnings like privileges invalid etc
-------
i have gotten warnings like canot find location
and sometimes i click the links and nothing happens
I have tried heaps 
please help

---

### Post by pmlxuser on 2009-03-18
on the desktop

right click
-> creat launcher
On command you can type the command / browse to the location of the file.

PS: i don't think running a program using sudo is nice at all

trying
```

$ sudo chown -R username:username /assualtfolder

```
this will allow you to run the comman without the sudo command

there after you can creat a link of the assaultcube.sh file  in /sbin 

after that you shall be able to run using  $ assaultcube
and thus in the link created above you could put in command assaultcube..

---

### Post by codie72 on 2009-03-18
ok i made the launcher file
then did this code

Code:

$ sudo chown -R username:username /assualtfolder

mine was 
sudo chown -R codie:codie .. /usr/games/***/assaultcube.sh
              ^user  ^username
i also tried
sudo chown -R codie:codie /usr/games/***/assaultcube.sh

however it does not do anything
---
I created a link by doing "shift ctl" and draging link into the etc folder and rebooted 
however nothing again happens 


thanks for your help and yea typing to play all the time is a pain :)

---

### Post by pmlxuser on 2009-03-18
by the way its the /sbin folder not /etc folder
the chown if for the whole folder and not the *.sh file only  so stop at 

sudo chown -R user:user **/assaultfolder/

by the way what happens when cd into the assault folder and run the .sh file without sudo?

---

### Post by codie72 on 2009-03-18
when i just write 
$sh assaultcube.sh 
it works fine from the directory

---

### Post by pmlxuser on 2009-03-18
then create a link in /sbin
ie
change into the assault folder and then
```

/****/assault/$sudo ln -s assaultcube.sh  assault

$cd /sbin
$ cp /***assault/assault   .
$chown -R user:user assault
$cd ~
$assault


```

it should run now without $sh 

then chwon it

---

