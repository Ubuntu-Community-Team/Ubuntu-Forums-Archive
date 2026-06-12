---
title: "cd confusion in terminal"
date: 2008-12-27
forum: General Help
---

### Post by ozguitarplayer on 2008-12-27
hi, I have only just started using terminal and can cd through root however when I try to cd in Home I keep getting the message...no such file or directory....is this the way it is meant to be, that I cannot cd in home?

---

### Post by theozzlives on 2008-12-27
your home or the home folder?

your home:
```
cd ~
```

home folder:
```
cd /home
```

Remember the filenames and folders ARE case sensitive. i.e. home is different than Home

---

### Post by ozguitarplayer on 2008-12-27
home folder...I didn't say it correcty, I can get cd /home however can't cd within home e.g. cd /Music

---

### Post by taurus on 2008-12-27
Do you mean the Music directory in your $HOME or the Music directory on root, /Music?

```
cd ~/Music
```

---

### Post by ozguitarplayer on 2008-12-27
In the home folder, cd ~/Music works, and for the rest of the home floder also, thanks for that.
Just to make sure of this I...cd / to move around root 
and...cd ~/ to move around home?

---

### Post by Yellow Pasque on 2008-12-27
I think you have the idea now.
cd ~
cd Music/ (not cd /Music, that's going back to the root dir)
Also, remember that you can use the Tab key to auto-complete the directory name. UNIX - made by lazy typist, for lazy typists.

---

### Post by taurus on 2008-12-27
The ~ means your $HOME, /home/your_username.  So, if you want to move to Music directory in your $HOME, you could do

```
cd ~/Music
```
or 
```
cd Musisc
```
Assuming that you are in $HOME when you run the second command.  Let's say that you have Music and Videos in your $HOME and you are currently in the Music directory, now you want to change to the Videos directory.  You could do

1.  ```
cd ../Videos
```
(It means move up on directory (the ..) and then down to Videos.)

or
2.  ```
cd ~/Videos
```
(it means start from your $HOME and change to Videos directory.)

---

### Post by ozguitarplayer on 2008-12-27
thanks again, I've been looking at LinusCommand.org and working through the very beginning bit about creating a text file for hello world and then I need to chmod 755 it however I could only get the message...no such file or directory.
Now with the cd ~/ information I can move around the Home folder, however I saved the "hello world" file in /Home/Maggie_Files/hello_world.
I can now cd to /Maggie_Files but when I cd ~/hello_world I still get the message...no such file or directory

---

### Post by Yellow Pasque on 2008-12-27
cd ~/hello_world = /home/<user-name>/hello_world directory
you want to:
cd ~/
cd Maggie_Files/
chmod 755 hello_world

---

### Post by taurus on 2008-12-27
To make sure whether the file is in the current directory or not, you can do the listing.

```
ls -l
```

---

### Post by jerome1232 on 2008-12-27
I think what your missing is this

let's say I have a file /home/user/joe/joe.sh
If I'm IN the folder /home/user/joe

then to get to joe.sh i just type
joe.sh

If I was in the folder /home/user and I wanted to get to the folder /home/user/joe I would do this

cd joe

If I was in /home and wanted to get to /home/user/joe

cd user/joe

If you put a / **before** the folder your telling bash to go all the way back to root and look there.

I hope that helps

---

### Post by ozguitarplayer on 2008-12-27
ls -l lists Maggie_Files as being in Home yet cd ~/Maggie_Files gets the no file message...

---

### Post by ozguitarplayer on 2008-12-27
thanks jerome 1232 that puts a helps, I can now navigate around with cd, this all came from me not being able to...

nigel@Master:~$ chmod 755 hello_world
chmod: cannot access `hello_world': No such file or directory
nigel@Master:~$

---

### Post by taurus on 2008-12-27
Post the output of that command.

```
ls -l
```

---

### Post by personjerry on 2008-12-27
~ is the short form of /home
is that the same as your Home?

---

### Post by taurus on 2008-12-27
> **personjerry said:**
> ~ is the short form of /home
is that the same as your Home?

Actually, ~ is the short form of your /home/your_username (not /home), aka $HOME.

---

### Post by ozguitarplayer on 2008-12-27
nigel@Master:~$ chmod 755 hello_world
chmod: cannot access `hello_world': No such file or directory
nigel@Master:~$ ls -l
total 52
drwxr-xr-x 2 nigel nigel 4096 2008-12-10 22:16 autosave
drwxr-xr-x 2 nigel nigel 4096 2008-12-23 13:04 Desktop
drwxr-xr-x 6 nigel nigel 4096 2008-12-28 08:09 Documents
drwxr-xr-x 8 nigel nigel 4096 2008-12-25 07:51 Downloads
drwxr-xr-x 3 nigel nigel 4096 2008-12-10 21:54 Music
-rw------- 1 nigel nigel    1 2008-12-27 12:35 nano.save
-rwxr-xr-x 1 nigel nigel   53 2008-12-27 11:55 nano.save.1
drwxr-xr-x 6 nigel nigel 4096 2008-12-24 18:45 Photos
drwxr-xr-x 2 nigel nigel 4096 2008-12-24 18:43 Pictures
drwxr-xr-x 2 nigel nigel 4096 2008-12-05 23:26 Public
drwxr-xr-x 2 nigel nigel 4096 2008-12-08 20:47 recordings
drwxr-xr-x 2 nigel nigel 4096 2008-12-05 23:26 Templates
drwxr-xr-x 2 nigel nigel 4096 2008-12-05 23:26 Videos
nigel@Master:~$

---

### Post by taurus on 2008-12-27
There is no Maggie_Files directory or file in your $HOME.  You can search for your file, hello_world, with

```
find . -name hello_world* -print
```

---

### Post by ozguitarplayer on 2008-12-27
nigel@Master:~$ find . -name hello_world* -print
./Documents/Maggie_Files/hello_world
nigel@Master:~$

---

### Post by taurus on 2008-12-27
So Maggie_Files is under Documents.

```
cd ~/Documents/Maggie_Files
ls -l
chmod 755 hello_world
./hello_world
```

---

### Post by ozguitarplayer on 2008-12-27
nigel@Master:~$ cd ~/Documents/Maggie_Files
nigel@Master:~/Documents/Maggie_Files$ ls -l
total 20
-rw-r--r-- 1 nigel nigel 15984 2008-12-08 20:28 Basil.odt
-rwxr-xr-x 1 nigel nigel   312 2008-12-27 11:55 hello_world
nigel@Master:~/Documents/Maggie_Files$ chmod 755 hello_world
nigel@Master:~/Documents/Maggie_Files$ ./hello_world
./hello_world: line 1: GNU: command not found
Hello World!
./hello_world: line 31: ^G: command not found
./hello_world: line 32: ^X: command not found
nigel@Master:~/Documents/Maggie_Files$

---

### Post by taurus on 2008-12-27
There is something wrong with your program hello_world.  Can you post it here?

```
cat hello_world
```

---

### Post by ozguitarplayer on 2008-12-27
was I meant to...cat hello_world...if so I got this

nigel@Master:~$ cat hello_world
cat: hello_world: No such file or directory
nigel@Master:~$

and this is a copy of the hello_world file as copied from the LinuxCommand.org instruction...
  

GNU nano 2.0.7                 New Buffer                              Modified

#!/bin/bash
# My first script

echo "Hello World!"

---

### Post by taurus on 2008-12-27
You have to be in ~/Documents/Maggie_Files.

```
cd ~/Documents/Maggie_Files
cat hello_world
```

---

### Post by ozguitarplayer on 2008-12-27
nigel@Master:~$ cd ~/Documents/Maggie_Files
nigel@Master:~/Documents/Maggie_Files$ cat hello_world
  GNU nano 2.0.7                 New Buffer                              Modified                                         

#!/bin/bash
# My first script

echo "Hello World!"
























^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCutText^T To Spell

nigel@Master:~/Documents/Maggie_Files$

---

### Post by taurus on 2008-12-27
> **ozguitarplayer said:**
> nigel@Master:~$ cd ~/Documents/Maggie_Files
nigel@Master:~/Documents/Maggie_Files$ cat hello_world
  GNU nano 2.0.7                 New Buffer                              Modified                                         

#!/bin/bash
# My first script

echo "Hello World!"























[B]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCutText^T To Spell
[/B]
nigel@Master:~/Documents/Maggie_Files$

Looks like you are using nano/pico text editor.  You need to remove the first empty line.  Then, remove everything after the last line, echo "Hello World!".

Your program should look something likes this (only four lines).

```

#!/bin/bash
# My first script

echo "Hello World!"

```

---

### Post by ozguitarplayer on 2008-12-27
ok I deleted those lines and now all's good, thanks heaps for your patience taurus...

by the way the those extra lines before and after the script were automatically placed there by nano...should I always delete them?

---

### Post by taurus on 2008-12-27
Whenever I write a script, I, personally, don't like having empty lines so I would remove them all but that's up to you.

---

### Post by ozguitarplayer on 2008-12-27
ok thanks again...

---

### Post by MaxIBoy on 2008-12-27
Probably something that will help clear things up is to read the documentation by pulling it up in a terminal window.

"Pocket reference" version: ```
man bash
```

"Thick tome" version: ```
info coreutils
```

---

### Post by ozguitarplayer on 2008-12-27
thanks MaxlBoy that helps also...there's a heap I have to learn

---

