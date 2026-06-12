---
title: "Quake 2 Install"
date: 2007-10-12
forum: Gaming &amp; Leisure
---

### Post by whistlerspa on 2007-10-12
Now that I've found CNR to be a lame duck how can i install Quake 2? 

I have an old Windows full version of it and there is Quake2-data that i can install from the reposotory in 7.04 but i haven't got a clue as to how to use this.

---

### Post by rajeev1204 on 2007-10-13
Install the quake 2 packages from synaptic .Check where the package is installed .Its probably in /usr/local/games/quake2 folder

Then copy the pak files from the windows cd to this folder (or if there is a quake2base folder inside the quake2 folder.)

Steps are same for all id games :)

---

### Post by reset3x on 2007-10-13
> **whistlerspa said:**
> Now that I've found CNR to be a lame duck how can i install Quake 2? 

I have an old Windows full version of it and there is Quake2-data that i can install from the reposotory in 7.04 but i haven't got a clue as to how to use this.

Install quake2 and quake2-data via Synaptic or apt-get ....

Copy the PAK files from your Windows install CD to /usr/lib/games/quake2/baseq2

Type quake2 in a terminal to start the game...

---

### Post by whistlerspa on 2007-10-13
Thanks for that guys.. Now I have another problem. When I put the Quake CD in . Serpentine opens up. I'm unable to browse the folder for anything much less find and copy the pak files. Can't seem to do anything about this.

---

### Post by reset3x on 2007-10-13
> **whistlerspa said:**
> Thanks for that guys.. Now I have another problem. When I put the Quake CD in . Serpentine opens up. I'm unable to browse the folder for anything much less find and copy the pak files. Can't seem to do anything about this.

Try ```
sudo cp /media/cdrom0/Install/Data/baseq2/*.pak /usr/lib/games/quake2/baseq2
```

---

### Post by whistlerspa on 2007-10-13
> **reset3x said:**
> Try ```
sudo cp /media/cdrom0/Install/Data/baseq2/*.pak /usr/lib/games/quake2/baseq2
```

Thanks was aware of terminal command but hate using it (legacy of years of Windows and MAc use i guess). I prefer to logon as root and click and paste. Solved it by altering system > preferences> removable drives and media option.

I've got the three Quake 2 mission packs as well. But adding the first and renaming it from pak0pak to pak1pak caused a crash. is there any way to load these in and select whjch one to run?

---

### Post by reset3x on 2007-10-13
> **whistlerspa said:**
> Thanks was aware of terminal command but hate using it (legacy of years of Windows and MAc use i guess). I prefer to logon as root and click and paste. Solved it by altering system > preferences> removable drives and media option.

I've got the three Quake 2 mission packs as well. But adding the first and renaming it from pak0pak to pak1pak caused a crash. is there any way to load these in and select whjch one to run?

Drill to the bottom of this page: [http://webpages.onvoy.com/bobz/howto/Quake-HOWTO-3.html](http://webpages.onvoy.com/bobz/howto/Quake-HOWTO-3.html)

---

### Post by whistlerspa on 2007-10-14
> **reset3x said:**
> Drill to the bottom of this page: [http://webpages.onvoy.com/bobz/howto/Quake-HOWTO-3.html](http://webpages.onvoy.com/bobz/howto/Quake-HOWTO-3.html)

Tried this but the mission packs don't load  - only the default Quake 2. 

I had to modify the command to 

./quake2.real +set game xatrix [or rogue]  

to get anything to happen but to no avail  - any idea as to why this is happening please?

---

### Post by PrimoTurbo on 2007-10-14
Just use wine for Quake2 it runs very very well under wine, the default engine from repo sucks and there are many problems with Quake2 on linux from my experience.

---

### Post by FredB on 2007-10-14
> **PrimoTurbo said:**
> Just use wine for Quake2 it runs very very well under wine, the default engine from repo sucks and there are many problems with Quake2 on linux from my experience.

Well, it is not a great idea after all.

Why using Wine when with synaptic you can have a better version of Quake 2 engine ?

---

### Post by PrimoTurbo on 2007-10-14
Because.....

[http://ubuntuforums.org/showthread.php?t=517752](http://ubuntuforums.org/showthread.php?t=517752)

> **PrimoTurbo said:**
> I spent a good part of today trying to get Quake2 up and running, I have tried the repos, manual installation, and loki's installer, and bunch of other ports.

Most if not all (at least I haven't found 1), suffer from a number of problems.
Quake2 is not version 3.20 under linux, repos have some odd version, linux version is 3.21..
Mods like Action Quake2 don't work! Only part of the game data works correctly the rest doesn't load on +set game
Default gl based rendering engines kinda suck
Sound, sound and more sound problems and even when you finally get OSS to work with some parameters the sound slows the hell out of the game and you get like 20 fps.
Stuck in window mode for certain gl modes, mouse stuttering problems also.

With Wine and my Quake2 folder, I can run everything pretty well maxing out at 100+ fps. I'm not sure there might be slight mouse delay but it's very hard to really notice, I just feel a little odd but I'm getting used to it.

Just my 0.02, if you have had any other experiences with getting Quake2 to work please post. Also if you search the forum you will see people complaining about the same problems.

---

### Post by averagebeatboy on 2007-10-29
[SIZE=1]A Stupid question from a newbie ... do you have to have any version of Windoze installed to run Wine?[/SIZE]

---

### Post by zakeen on 2007-10-31
No, think of wine like a version of windows, thats very very lean and all it does is run windows apps.

---

### Post by Xcursion666 on 2010-11-26
can u use a disk image to install the game my cd drive broke so i had a friend make a disk image of my copy 
i used the data installer and i got this error

robert@laptop:~$ sudo dpkg-reconfigure quake2-data
Installing data from CD-ROM
find: `x-nautilus-desktop:///1.volume/players': No such file or directory
xargs: Warning: a NUL character occurred in the input.  It cannot be passed through in the argument list.  Did you mean to use the --null option?
robert@laptop:~$ 



can anyone help:confused:

---

### Post by Xcursion666 on 2010-11-27
> **Xcursion666 said:**
> can u use a disk image to install the game my cd drive broke so i had a friend make a disk image of my copy 
i used the data installer and i got this error

robert@laptop:~$ sudo dpkg-reconfigure quake2-data
Installing data from CD-ROM
find: `x-nautilus-desktop:///1.volume/players': No such file or directory
xargs: Warning: a NUL character occurred in the input.  It cannot be passed through in the argument list.  Did you mean to use the --null option?
robert@laptop:~$ 



can anyone help:confused:

i forgot to mention that the image is a .bin file with a cue file and i have it mounted with acetone i know its a good image because i tested it on a windows pc and it installed fine 
i also tried to install it with wine  and i did the full install so i wouldn't need to mount the image every time i wanted to play the game but it still tells me i need the the quake2 cd-rom even when the image is mounted. i also have software to convert the file to an iso would that help in any way i figured that it might be a format issue.
any help would be welcomed

:mad::confused:](*,)

---

### Post by rajeev1204 on 2010-11-28
> **Xcursion666 said:**
> i forgot to mention that the image is a .bin file with a cue file and i have it mounted with acetone i know its a good image because i tested it on a windows pc and it installed fine 
i also tried to install it with wine  and i did the full install so i wouldn't need to mount the image every time i wanted to play the game but it still tells me i need the the quake2 cd-rom even when the image is mounted. i also have software to convert the file to an iso would that help in any way i figured that it might be a format issue.
any help would be welcomed

:mad::confused:](*,)

Hi

Try some no cd patch from the internet .Should be enough .Or one more step :

[http://goinggnu.wordpress.com/2007/05/08/howto-mount-bincue-files-in-linux/](http://goinggnu.wordpress.com/2007/05/08/howto-mount-bincue-files-in-linux/)

---

### Post by Xcursion666 on 2010-11-28
> **rajeev1204 said:**
> Hi

Try some no cd patch from the internet .Should be enough .Or one more step :

[http://goinggnu.wordpress.com/2007/05/08/howto-mount-bincue-files-in-linux/](http://goinggnu.wordpress.com/2007/05/08/howto-mount-bincue-files-in-linux/)

i already downloaded a no cd patch but it tells me that is already patched when i try 
to use it

---

### Post by CowzRule on 2010-11-28
Have a look at the thread titled "[Looking for modern QUAKE 2 client]("http://art.ubuntuforums.org/showthread.php?t=1566423")"
The last couple of posts talks about "Yamagi Quake II". I'm using it on Lucid 32bit and it runs Great.

---

