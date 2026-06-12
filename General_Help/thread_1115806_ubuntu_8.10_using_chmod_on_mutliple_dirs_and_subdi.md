---
title: "ubuntu 8.10: using chmod on mutliple dirs and subdirs"
date: 2009-04-04
forum: General Help
---

### Post by penduleum on 2009-04-04
Hey there.

I ame trying to configure mediatomb. I could get pretty far.
The only problem i get, is that it dont read some of the mp3s i  have. From the faq on the mediatomb site, i saw that all the mp3´s need to have read only rights. Moste, if not all, have read and execute rigts, like this: -rwx---r-x.

I need them to change to 400 (-r--------).

I have tryed the following things: 

chmod 400 *.* 
on a copple of dir´s (whit more than 400 dirs its not a smart thing to do...)

sudo chmod 400 /media/music *.*
(this is the place where all my music is)
When i do this, all is read only, but only for the root....

sudo chmod `myuser` 400 /media/music/ *.*
When i do this i get the following things:

first problem:
chmod: cannot access `myuser': No such file or directory

It changes all to 400 (readonly) for root... thats not the right thing to do... :P


What can i do to change all the music (regardless if its mp3, flac aac ogg, or what ever fileformat) to read only access, so that mediatomb can process them?

Of corse, i can always start mediatomb whit root (sudo mediatomb...) but it needs to be started as ´myuser´.

thx for any input...

---

### Post by ShaunG on 2009-04-04
Try the following

```
chmod -R 400 *
```

This will recursively set the permissions on every file/sub folder to be read only.

EDIT: To be read only by super user only.
 Why would you want only super user to able to read these files?

Perhaps the following may be better:

```
chmod -R 444 * 
```

Ah sorry i didn't see the myuser bit.

Try this: 

```
sudo chmod -R 550 * 
```

This will make all files, folders readable and executable by super user and current user. But not by other users.

---

### Post by JAlexoid on 2009-04-04
If you don't want to mess up your directory access rights, you should use:
chmod -R a+r *
This will only add read by all flag to all files/directories. Without changing the execute bit on the directories. You need the execute bit to to listing of files/subdirectories in a directory.

A short manual:
a-r - will remove read flag from all users
a+x - will add execute flag to all users
a+w - will add write flag to all users
u instead of a, indicates file owner flags to be changed
o instead of a, indicates other users flags to be changes
g instead of a, indicated group users...

---

### Post by penduleum on 2009-04-04
thx for the input :)
i ame a bit closer now.

when i do:

```
sudo chmod -R 550 *
```

i get read and execute rights, to all files and subfiles.
the premissions on the dirs stay the same.

if i do:
```

chmod 400 -R *
```

whit my user, and not root, i get premission denied (after setting the premissions to 777, just to try it out.

so, still not there.

when i use:

```

sudo chmod -R 550 *
```

```
chmod -R a+r *
```

it still set the premissons to read/execute.
I realy only need read premissions to the files for mediatomb.
If it has any execution, it cant add them to the mediatomb db.
Just tryed that, and get the same error..

thx for any input..

---

### Post by lswb on 2009-04-04
I'm not familiar with the mediatomb but it seems that the problem is you need read only permissions on the files, while leaving directories as executable so they can be searched. Try first doing 

chmod -R 444 *

to make all files and subdirectories readable. If you need them wrietable also or readable only for root or owner, change the 444 accordingly.

Then you can use the command

chmod -R +X *

Note the UPPER CASE X. Using upper case X will change only directories to executable, leaving the files as-is.

---

