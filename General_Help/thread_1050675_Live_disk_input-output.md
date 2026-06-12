---
title: "Live disk input-output"
date: 2009-01-25
forum: General Help
---

### Post by E-Tramp on 2009-01-25
This may be an odd question, but, being a newbie to Linux, I am trying to learn some things about it, while I still don't have an installed application.  As a result I am reading a book by Richard Petersen, and he has several exercises to run through int the book.  In the last one I was working on, using the live disk application of Ubuntu 7.10, I created a simple script, altered the permissions to make it executable, and told the command line to run the new program.

When I changed the permissions on the file, I saw nothing to indicate that the permissions had been changed, and when I tried to execute it, the commandline said that the file or program didn't exist.

My question is simple.  Is this because the program on the live disk isn't capable of executing operations that involve that much of the program rescources, or am I doing something wrong.  I know the text is there, but, I can't get it to run.

I do intend to install Linux on a computer, but, the one I was going to install on has an AMD Athlon XP, and a 741GX-M V.1 ECS motherboard, which seems to be non supported by Linux Debian programming.  Even the disk won't hardly run on that computer. So, unless I want to run a dual boot system on one of my other computers, which I really don't, I have to get another motherboard and CPU.

In the meantime I would like to use the live disk, to tutor myself in the programming of Linux, if possible.

How far is it possible to run the live disk program?  Can I create and run script input-output operations with it?

Looking forward to spending a lot of time tapping your forums for information.

---

### Post by gombadi on 2009-01-25
> 
I created a simple script, altered the permissions to make it executable, and told the command line to run the new program

When I changed the permissions on the file, I saw nothing to indicate that the permissions had been changed, and when I tried to execute it, the commandline said that the file or program didn't exist.

My question is simple. Is this because the program on the live disk isn't capable of executing operations that involve that much of the program rescources, or am I doing something wrong. I know the text is there, but, I can't get it to run.



Ok so you are at the command line.

What command did you use to change permissions - chmod something filename ?

It does not normally give any output but you can see the file permissions with this

```

ls -l filename

```

It should look something like - (note the three x in the line)
```

ls -l bkup-usb.sh 
-rwxr-xr-x 1 lroger lroger 191 2008-12-19 20:04 bkup-usb.sh

```

Can you show us the script you created or at least the first line. It should look something like -
```

#!/bin/bash

```

The live CD is capable oy using all system resources - some people use a live CD as there normal desktop at times.

---

### Post by E-Tramp on 2009-01-30
OK, Thanks for your time, and I am sorry that I took so long to get back to you.  I have been down with a bug, me, not the computer.

The command that I used is $ chmod u+x greetvar, greetvar being the name of the file I want to be executable.

The file goes like this:

 
echo Please enter a greeting:
read greeting

echo"the greeting you entered was $greeting"

Is there a default location that the program looks for a script file? So far, I have just created it and saved it without picking any location in particular.  It seems to be saving it to a file in the script file program itself.  If the command line doesn't look in that location then that is probably what I am doing wrong.

As I said it is a simple execution just for practice.

Basically what I am getting is a message that the computer can't find the named file.

I am glad to know the information about the disk.  That makes the things that I can learn from it till I can get a system installed, considerable.

---

### Post by gombadi on 2009-01-30
> 
Is there a default location that the program looks for a script file? So far, I have just created it and saved it without picking any location in particular. It seems to be saving it to a file in the script file program itself. If the command line doesn't look in that location then that is probably what I am doing wrong.


If you want to be able to just enter the command name (i.e. file name of the script) then it needs to be in a directory on your path. To see what your path is enter this at a terminal

```

echo $PATH

```

and it should return a list of directories something like 

```

/home/lroger/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

If the file is not in a directory on the path then you will have to give a full location to the file to run it eg -

```

/home/username/directory/greetvar

```

But then again if it is in the current directory you can 

```

./greetvar

```

There are different ways to run the script depending on where it is and where your current directory is.
I suggest doing some research for bash path etc.

---

### Post by E-Tramp on 2009-01-31
OK, Thanks I will do that, and will try out the rest as well.  I still have a lot to learn, and my purpose is to research and learn the system. Will be back later, as soon as I have done a little more studying.

---

