---
title: "compiling quake 3 arena"
date: 2006-06-25
forum: Gaming &amp; Leisure
---

### Post by Rosenrot on 2006-06-25
i just downloaded quake 3 arena source

and i looked at the readme file and it told me to compile using this command


[..]/code$ ./unix/cons -- gcc=gcc-2.95 g++=g++-2.95


i tried just copieing and pasting but i got a command not found error

I don't know what directories to add to the command to make it work

I also have all the necessary packages installed

any ideas?

---

### Post by rpgcyco on 2006-06-25
You've got a much better chance using something like [icculus.org/quake3](http://www.icculus.org/quake3/).

- Rpg Cyco

---

### Post by Rosenrot on 2006-06-26
ive tried installing the package from icculu.org/quake3 many times and i can't open quake or run any mods through it

and i think im doing something wrong but im not sure

i have it installed in /home/b/ioquake3

this is what i get when i try to run from terminal

b@b-desktop:~$ /home/b/ioquake3/ioquake3
./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

i know im either missing a library or its reading the wrong directory 

and im not shure if "shared object file:No suck file or directory" is my attempt to install the mod 'Urban Terror' v.3.7 by going by the readme instructions and extracting pacages3.0-3.7 to the quake 3 directory

---

### Post by crane on 2006-06-26
Your urban terror should have created a folder like ut3 or q3ut3 or something like that in your quake3 folder. it shlould not have cause the error.
I am not familiar with this install method, but just glanceing at it. Did you run the game data installer? It said even if you have already installed the files from the cd you still need to run the game data installer after running th .run file to install.
 I guess you need the pako.pk3 file from the cdrom plus an updated one the installed adds.

You could search for the lib file it is looking for then link to it or change the script I guess.

---

### Post by rpgcyco on 2006-06-26
[QUOTE=Rosenrot]ive tried installing the package from icculu.org/quake3 many times and i can't open quake or run any mods through it

and i think im doing something wrong but im not sure

i have it installed in /home/b/ioquake3

this is what i get when i try to run from terminal

b@b-desktop:~$ /home/b/ioquake3/ioquake3
./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

i know im either missing a library or its reading the wrong directory 

and im not shure if "shared object file:No suck file or directory" is my attempt to install the mod 'Urban Terror' v.3.7 by going by the readme instructions and extracting pacages3.0-3.7 to the quake 3 directory[/QUOTE]

If you haven't installed OpenAL, then that's the problem. OpenAL functionality was recently (within the last few months) added to ioquake3.

```
sudo apt-get install libopenal0a
```

That package is in the universe repo.

- Rpg Cyco

---

### Post by Rosenrot on 2006-06-27
[QUOTE=crane]Your urban terror should have created a folder like ut3 or q3ut3 or something like that in your quake3 folder. it shlould not have cause the error.
I am not familiar with this install method, but just glanceing at it. Did you run the game data installer? It said even if you have already installed the files from the cd you still need to run the game data installer after running th .run file to install.
 I guess you need the pako.pk3 file from the cdrom plus an updated one the installed adds.

You could search for the lib file it is looking for then link to it or change the script I guess.[/QUOTE]

im installing from source and i don't have the pako.pk3 file and i searched for the file and i didn't have it

so I installed OpenAL and now i get this error

b@b-desktop:~$ /home/b/ioquake3/ioquake3
ioQ3 1.34-rc1 linux-i386 Jun  5 2006
----- FS_Startup -----
Current search path:
/home/b/.q3a/baseq3
/home/b/ioquake3/baseq3

----------------------
0 files in pk3 files
Sys_Error: Couldn't find pak0.pk3. Check that your Q3
executable is in the correct place and that every file
in the baseq3 directory is present and readable.




so i can't run the game unless i have the pak0.pk3.


but how would i run urban terror? i don't have any file to run off of

i have a q3ut.ico
but thats an icon

ill try getting a different install of urban terror and see if i can get it to work

and if not i guess it would just be easier to go out and find a linux version of quake 3? lol


O and i checked google about my error and all i got was these sites that were ALL in some odd foriegn language : /

---

### Post by Rosenrot on 2006-06-27
i tried installing urban terror again and in the readme it tells me

Extract 3.0 to your Quake III Arena folder. Extract 3.1, 3.2, 3.3, 3.4, 3.5 3.6 and 3.7 to your Q3UT3 folder.

I extraced 3.0 to my Q3 folder
but then no Q3UT3 folder is made
is there something extra i have to do?or do i just create a folder and call it Q3UT3?

but then i can't start Q3 to go to mods and play urban terror....

---

### Post by crane on 2006-06-28
You will have to have the pak0.pk3 file to play quake3 or urban terror.
If you start Quake3. You will see a menu item labeled Mods. select that, the select Urban Terror from the list to play urban terror.
I believe you can also add this to you start command.
+set fs_gametype q3ut3.

So I believe your command would be:
/home/b/ioquake3/ioquake3 +set fs_gametype q3ut3.

But as I said, you have to have the ppk3 file to run quake3.

---

### Post by FredB on 2006-06-28
Speaking of Icculus version, it is available on Synaptic (after activing universe and / or multiverse) directory.

->[]

---

### Post by jonifen on 2006-06-28
I personally downloaded the Quake 3 1.32b binary from [http://www.fileshack.com/file.x?fid=1289](http://www.fileshack.com/file.x?fid=1289)

All I needed to do then was copy the PAK0.PK3 file from my Quake 3 arena cd into /usr/games/quake3/baseq3 and then load it up - worked fine. Only problem I had was getting punkbuster to update, but after getting PBSetup from Evenbalance.com and running that, it updated no problems and I'm back to playing Threewave CTF just like I used to on Windows :)

---

### Post by Rosenrot on 2006-06-29
ahh i see

i don't have a quake 3 arena cd
ill try to go out and get it but that may be awhile(weekend most likely)
thanks for the help everyone

---

### Post by jonifen on 2006-06-29
You should be able to pick Q3 up for a few pounds/dollars these days - its pretty old and Q4 has recently been released too. Well worth buying though, as you need the CD Key to play online these days too because of Punkbuster (anti-cheat).

---

### Post by crane on 2006-06-29
Pretty old indeed, I believe it is about 7 years old! I have not seen it for sale in stores around here in a couple of years. Around here being Southeast U.S.

---

### Post by dominik on 2006-07-01
hey, i tried the icculus-version and get this error, any ideas?

```
Sys_Error: recursive error after: User Interface is version 3, expected 6 
```

---

