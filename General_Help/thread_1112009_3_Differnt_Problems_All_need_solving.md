---
title: "3 Differnt Problems All need solving"
date: 2009-03-31
forum: General Help
---

### Post by kehon on 2009-03-31
i am running ubuntu 8.10 kernel .10 whatever its the most up to date one
on my compaq presario c700

problem 1:
When i log in it says user .dmrc is not owned by user permission need to be 644 or something like that i've looked all the threads and i cant get any to work or fix it and when i look at permissions everytime it says its owned by root even though i tried chmod *myusername* nothing works

edit: i moved home too but $HOME registers as /media/userfiles/home

problem 2: the sound (headphone speaksers whatever) has/is when trying to play a sound even startup just plays static again looked up but nothing works the computer has conexant speakers from intel and they were working but i installed some stuff like vuze (which i hate and will be uinstalling) ktorrent, eclipse was the longest, ubuntu tweak, and someothers now it was working till after i installed this stuff oh and i installed wine (next problem)

i know speakers work because they work on windows so its not speakers its ubuntu

problem 3: recently installed wine now i havent even used it but i installed all that stuff after then when i went to try wine wont load up or do anything its like i didnt even press it to launch wont let me configure through gui cant run notepad, cant run exes

any help would be greatfully appreciated so i can get all the kinks worked out and if it matters i'm on ubuntu 8.10 kernel thingy like i said before 10 and on amd64 (intrepid)

---

### Post by sisco311 on 2009-03-31
> **kehon said:**
> 

problem 1:
When i log in it says user .dmrc is not owned by user permission need to be 644 or something like that i've looked all the threads and i cant get any to work or fix it and when i look at permissions everytime it says its owned by root even though i tried chmod *myusername* nothing works


[thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

---

### Post by kehon on 2009-03-31
chmod 644 /media/userfiles/home/.dmrc
chmod: changing permissions of `/media/userfiles/home/.dmrc': Operation not permitted

forgot to mention i moved home so that it would be in another partition but $HOME registers as /media/userfiles/home which is where i want it

edit: even used sudo chmod and it acted like it worked but it didnt i still get the error message

---

### Post by sisco311 on 2009-03-31
> **kehon said:**
> chmod 644 /media/userfiles/home/.dmrc
chmod: changing permissions of `/media/userfiles/home/.dmrc': Operation not permitted

forgot to mention i moved home so that it would be in another partition but $HOME registers as /media/userfiles/home which is where i want it

edit: even used sudo chmod and it acted like it worked but it didnt i still get the error message

How did you change the location of your home directory?

Is the correct location listed in the /etc/passwd file?

```
cat /etc/passwd
```
> ...
[noparse]username:x:1000:1000:real_name:,,,:[/noparse]**media/userfiles/home**:/bin/bash
...


Did you copy your files to the new home directory?

Did you run first the *sudo chown ...* command?

---

### Post by kehon on 2009-03-31
i used usermod to change it along with ubuntu tweak for other folders

```
kurt:x:1000:1000:kurt,,,:/media/userfiles/home:/bin/bash
```

its listed correctly and i did sudo chown it didnt say anything so i guessed it worked but i still get that error when logging in

and yes files were copied

---

### Post by sisco311 on 2009-03-31
strange. please post the output of:
```
ls -al /media/userfiles/
```
and
```
ls -al /media/userfiles/home/.dmrc
```

---

### Post by kpatz on 2009-03-31
You'll probably find that .dmrc is owned by root.

```

sudo chown username:username /media/userfiles/home/.dmrc
chmod 644 /media/userfiles/home/.dmrc

```

If you find all your files are owned by root, and they should be owned by you, you can change them all with:

```

sudo chown -R username:username /media/userfiles/home

```

---

### Post by kehon on 2009-03-31
sorry for the long time no internet had to go home and charge up
```
ls -al /media/userfiles/
kurt@kurt-laptop:~$ ls -al /media/userfiles/
total 3030128
drwxrwx--- 1 root plugdev       8192 2009-03-30 18:58 .
drwxr-xr-x 4 root root          4096 2009-03-31 09:43 ..
drwxrwx--- 1 root plugdev       4096 2009-03-30 23:29 $AVG8.VAULT$
drwxrwx--- 1 root plugdev       4096 2009-03-30 14:08 Backups
drwxrwx--- 1 root plugdev      40960 2009-03-28 13:22 Contacts
drwxrwx--- 1 root plugdev          0 2009-03-30 07:42 Database
drwxrwx--- 1 root plugdev       8192 2009-03-29 22:33 Desktop
drwxrwx--- 1 root plugdev       4096 2009-03-29 14:42 Documents
drwxrwx--- 1 root plugdev       8192 2009-03-30 15:27 Downloads
drwxrwx--- 1 root plugdev       4096 2009-03-30 08:03 E-Books
drwxrwx--- 1 root plugdev       4096 2009-03-30 12:53 Encrypt
drwxrwx--- 1 root plugdev       4096 2009-03-28 12:49 Favorites
drwxrwx--- 1 root plugdev          0 2009-03-28 14:48 Games
drwxrwx--- 1 root plugdev       8192 2009-03-31 10:39 home
drwxrwx--- 1 root plugdev       4096 2009-03-28 12:49 Links
drwxrwx--- 1 root plugdev     163840 2009-03-28 14:34 Music
drwxrwx--- 1 root plugdev       4096 2009-03-28 14:45 Pictures
-rwxrwx--- 2 root plugdev 3102564508 2009-03-28 21:56 PSPSDK Offline.nrg
drwxrwx--- 1 root plugdev          0 2009-03-29 14:36 Public
drwxrwx--- 1 root plugdev          0 2009-03-28 12:39 $RECYCLE.BIN
drwxrwx--- 1 root plugdev          0 2009-03-23 12:09 Saved Games
drwxrwx--- 1 root plugdev       4096 2009-03-28 12:49 Searches
drwxrwx--- 1 root plugdev          0 2009-03-28 12:39 System Volume Information
drwxrwx--- 1 root plugdev          0 2009-03-29 14:37 Templates
drwxrwx--- 1 root plugdev       4096 2009-03-28 14:46 Videos


```
and
```
ls -al /media/userfiles/home/.dmrc
kurt@kurt-laptop:~$ ls -al /media/userfiles/home/.dmrc
-rwxrwx--- 2 root plugdev 2 2009-03-29 14:29 /media/userfiles/home/.dmrc

```

this partion is where i keep all of my files both windows and ubuntu but the home folder is just for ubuntu only i dont mess with in windows unless i need too

---

### Post by kehon on 2009-03-31
why is everything owned by root and what is plugdev new to linux and ubuntu

---

### Post by sisco311 on 2009-03-31
FAT and NTFS don't support Unix/Linux permissions/ownership.

You can not use FAT/NTFS filesystem for the home directory or partition.

---

### Post by kehon on 2009-03-31
oh ok well i just want all of my documents,downloads, etc folders to stay like they are as default save and download locations  so what is the correct way to change my home folder back

also what would you say is the best format to keep all of my files ntfs, FAT, or what when i have over 100,000 files + that i know of and i'm using linux and windows and want to be able to acess both

and thanks so much for your help

---

### Post by sisco311 on 2009-03-31
Just change back your home dir to /home/kurt. You can use Users and Groups or the terminal:
```
sudo usermod -md /home/kurt kurt
```

the contents of the current home directory("/media/userfiles/home/") will be moved to the new home directory(/home/kurt), which is created if it does not already exist.

Then set the correct permissions:
```
sudo chown -R kurt\: /home/kurt
chmod 755 /home/kurt
chmod 644 /home/kurt/.dmrc
```


You can mount the FAT or NTFS in your home dir (/home/kurt/data or something) or you can create symbolic links in your home dir to the Download, Music, Games etc. directories:
```
ln -s /media/userfiles/Backups /home/kurt/Backups 
ln -s /media/userfiles/Downloads /home/kurt/Downloads
...
```

---

### Post by kehon on 2009-03-31
cool thanks do you think this will fix wine and my sound

---

### Post by kehon on 2009-03-31
what if i just move the home directory and leave the other directoires where they are because ubuntu tweak changed those for me

---

### Post by kehon on 2009-04-01
thanks moving the home folder solved the wine problem and i set the permissions and that fixed that error message still got my desktop and other folders on other partition though thanks for your help 

sound still does not work though

---

