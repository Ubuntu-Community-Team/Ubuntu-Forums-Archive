---
title: "[SOLVED] How to erase locked Files ??"
date: 2009-01-11
forum: General Help
---

### Post by sendblink23 on 2009-01-11
I'm on Ubuntu 8.10.. and really weird, I'm trying to delete some files that all the sudden they appear with a Lock icon

Like just copying files from a cd (photos & songs I had in windows) just to add them to my HD inside Ubuntu.

Well how can I erase or move them... since they are all appearing with *locks icon

I used to use:  gksudo nautilus

Before when i had 8.04   but  since...  now on 8.10  I run it..  but it doesn't show any of my User Files  (not even the Desktop ones, it appears BLANK)   when I do have files in the Desktop

Any Help with this situation ??

---

### Post by sendblink23 on 2009-01-11
anybody ?

---

### Post by taurus on 2009-01-11
When you copy files from a CD to your harddrive, those files will keep the same permissions as they appear on the CD so they end up with read/executable only.  If you want to remove them, you need to include the write in there.

```
chmod 755 filename
-or-
sudo chmod 755 filename
```

---

### Post by sendblink23 on 2009-01-11
> **taurus said:**
> When you copy files from a CD to your harddrive, those files will keep the same permissions as they appear on the CD so they end up with read/executable only.  If you want to remove them, you need to include the write in there.

```
chmod 755 filename
-or-
sudo chmod 755 filename
```

hmm are you saying I should put there the filename ?

theres a problem.. i have thrown also others in folders inside the user..

lets just say that there are Many Folders that have the lock on them

Anyway of just running a simple command.. to Overide everything so that I can normally delete them ??

That is not: gksudo nautilus   (Since it does not let me see any USER FILES when running that command *In the Pop Up Browser through Nautilus*, its extremely weird)

---

### Post by taurus on 2009-01-11
What is the name of the directory that has all those lock files & sub-directories?

---

### Post by sendblink23 on 2009-01-11
> **taurus said:**
> What is the name of the directory that has all those lock files & sub-directories?

same as my user name:   sendblink23
Its the Home Folder .. when clicked inside  *Places*
Its what shows my current Desktop, and any folder inside my User

---

### Post by taurus on 2009-01-11
You mean the directory, sendblink23, in ~/Desktop.

```
cd ~/Desktop
sudo chmod -R 755 sendblink23
ls -la
```

---

### Post by sendblink23 on 2009-01-11
> **taurus said:**
> You mean the directory, sendblink23, in ~/Desktop.

```
cd ~/Desktop
sudo chmod -R 755 sendblink23
ls -la
```

My HOME FOLDER  as in USER FOLDER


When you click ..HOME  in  Above in the Top  *PLACES*

it appears your User Name Directory (it has Desktop and all other places folders to access from my User Home Folder)

here is my Printscreen: [http://i29.photobucket.com/albums/c272/sendblink23/Screenshot-3.png](http://i29.photobucket.com/albums/c272/sendblink23/Screenshot-3.png)

---

### Post by taurus on 2009-01-11
So all those files and directories are under ~/Desktop then.

```
ls -la ~/Desktop
```

---

### Post by sendblink23 on 2009-01-11
> **taurus said:**
> So all those files and directories are under ~/Desktop then.

```
ls -la ~/Desktop
```

I said before...  not only the Desktop.. I placed files in many other folders too

isn't there a straight 1 command only  to control access to delete any files from my User Home Folder ? 

That will simply take control of me able to delete all the huge mess of locked files I have in many different folders

Somethign that would work exactly like what: gksudo nautilus DOES .. but havign access into my User Home Folder

i think its: home/sendblink23 
that is what I see in my print screen image I posted before.

---

### Post by taurus on 2009-01-11
I don't thing there is one safe command that delete some of the files or directories that you want without nuking your $HOME.  However, there is one command that would let you change the permissions so the lock on them would be removed.

```
chmod -R 755 ~/*
```

---

### Post by Carl Hamlin on 2009-01-11
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

When you use gksudo nautlius, you're going to be looking at the root user's home, not your own. Make sure you manually change your directory to /home/yourname/ and get to the Desktop directory located *there*. Your files will be there, and you'll be able to smoke them to your heart's content.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklplhQACgkQyLm4ydrABvd4xACglWl3ofaFY3+7dEXpV931YmnY
oA0AoKZizqN2nX2IF5FggSAgSkB/KGb/
=92lT
-----END PGP SIGNATURE-----

---

### Post by sendblink23 on 2009-01-11
> **taurus said:**
> I don't thing there is one safe command that delete some of the files or directories that you want without nuking your $HOME.  However, there is one command that would let you change the permissions so the lock on them would be removed.

```
chmod -R 755 ~/*
```

This is weird  i got allot of errors after applying that in Terminal ...  but it actually  let me Erase any Files of of all Directories

hehe  Well Thanx a bunch I'm going to give you   2 post *Thanx*  since you tried helping me many times.

1 on this one.. and the other one in the first post you gave

---

### Post by pizmooz on 2009-01-11
Run this command in a terminal:

```
sudo chmod -R 777 ~
```

then you can go and delete any files in your home directory using nautilus.
It will set all files and directories in your home folder to be readable, writeable and executable by all users, so if you have any specific security needs this might not be the solution you need, but it probably is :)

[http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions]("http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions")

---

### Post by sendblink23 on 2009-01-11
Sure thing, I think I will want be doing this ...

So ...  how should I do this...  should I first run the *gksudo nautilus*  command .. and while having that Open ...  Manually Pass the folders inside that Pop Up Window .. ??

Because after I run that command, I do not see any Home folder, i only see ROOT

here is a Printscreen after Running that command: [http://i29.photobucket.com/albums/c272/sendblink23/Screenshot-4.png](http://i29.photobucket.com/albums/c272/sendblink23/Screenshot-4.png)

here is the printscreen when I haven't run that command *Home Folder: [http://i29.photobucket.com/albums/c272/sendblink23/Screenshot-3.png](http://i29.photobucket.com/albums/c272/sendblink23/Screenshot-3.png)
 


> **Carl Hamlin said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

When you use gksudo nautlius, you're going to be looking at the root user's home, not your own. Make sure you manually change your directory to /home/yourname/ and get to the Desktop directory located *there*. Your files will be there, and you'll be able to smoke them to your heart's content.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklplhQACgkQyLm4ydrABvd4xACglWl3ofaFY3+7dEXpV931YmnY
oA0AoKZizqN2nX2IF5FggSAgSkB/KGb/
=92lT
-----END PGP SIGNATURE-----

---

### Post by sendblink23 on 2009-01-11
You guys are killing me

giving me many commands.... 

I'm no Linux Expert

Simple just LOOK AT MY PRINTSCREENs

on my above last Post

can you help me from there by looking at it ...

All I want now is for the simple command: gksudo nautilus

I want i to work, like it used to as normally in Ubuntu 8.04, in which there i just imputed that command, and i could erase anything i wanted.. since I could see every file of my computer

BUT now on Ubuntu 8.10  .. No you do not see any folder or Files of your HOME USER..   after applying that command ...

So  LOOKING at my Printscreens   how can you help me...  make that COMMAND   and be able to see my HOME USER FOLDER FILES in there?

as simple as that

---

### Post by taurus on 2009-01-11
Just click Up, then Home, then sendblink23.  Now, you are in your $HOME directory.

---

### Post by sendblink23 on 2009-01-11
> **taurus said:**
> Just click Up, then Home, then sendblink23.  Now, you are in your $HOME directory.
Haha  yeah that worked

---

### Post by sendblink23 on 2009-01-11
So would you suggest ..  that now.. everytime  ...  I put in a CD.. that i wanna drag files out of it...

I should run the  nautilus  command...   and inside there..  open the files from inside the CD/DVD to pass them around where i want them..  so that they don't appear Locked?

that is just a random question

---

### Post by taurus on 2009-01-11
If you look at the files on the CD, you will see they have only read and executable so if you want to modify them or delete them after you copy them to your $HOME, you need to change the permissions of those files first.

You can do that as a regular user from a terminal.  No need to use root privilege (sudo/gksudo) unless root owns those files in your $HOME.

---

### Post by sendblink23 on 2009-01-11
> **taurus said:**
> If you look at the files on the CD, you will see they have only read and executable so if you want to modify them or delete them after you copy them to your $HOME, you need to change the permissions of those files first.

You can do that as a regular user from a terminal.  No need to use root privilege (sudo/gksudo) unless root owns those files in your $HOME.



so yeah i think the case would be to manually change the permission of the files..  copied

so in other words.. i should  *Copy them   to the Desktop ...  and what command should I run there.. to change the permission if its on the Desktop. I think it should be changed its permission to 777 so it can be altered as any way I want...

so what would be the command for a file or directory in the Desktop

here would be an examples both on the Desktop
Directory named:  cowattack
File named:   bubble.mp3

Give me both examples of commands to change permissions, please if you can, so that I could understand it

---

### Post by foo_bar on 2009-01-11
> **sendblink23 said:**
> here would be an examples both on the Desktop
Directory named:  cowattack
File named:   bubble.mp3

For a directory type: chmod 777 -R cowattack (the -R stands for recursive, in other words it will change the permissions on all of the files inside the directory).

For a single file type: chmod 777 bubble.mp3

When you rip a cd create a directory "folder" then drop the tracks into that directory. Then chmod "change the permissions" on the whole directory as in the example I gave above. You can use the GUI to create the directory or you can use "mkdir cowattack" to create a directory in the terminal.

---

### Post by sendblink23 on 2009-01-11
> **foo_bar said:**
> For a directory type: chmod 755 -R cowattack (the -R stands for recursive, in other words it will change the permissions on all of the files inside the directory).

For a single file type: chmod 755 bubble.mp3


When you rip a cd create a directory "folder" then drop the tracks into that directory. Then chmod "change the permissions" on the whole directory as in the example I gave above. You can use the GUI to create the directory or you can use "mkdir cowattack" to create a directory in the terminal.

Can i use 777  instead of 755   on those commands you gave me?

---

### Post by foo_bar on 2009-01-11
yea.. you beat me to it. I just change my answer above. 777 is fine.

---

### Post by sendblink23 on 2009-01-11
> **foo_bar said:**
> For a directory type: chmod 777 -R cowattack (the -R stands for recursive, in other words it will change the permissions on all of the files inside the directory).

For a single file type: chmod 777 bubble.mp3

When you rip a cd create a directory "folder" then drop the tracks into that directory. Then chmod "change the permissions" on the whole directory as in the example I gave above. You can use the GUI to create the directory or you can use "mkdir cowattack" to create a directory in the terminal.

hehehe   okay .. yup  yup noticed you changed it.. Thanx ;)

---

