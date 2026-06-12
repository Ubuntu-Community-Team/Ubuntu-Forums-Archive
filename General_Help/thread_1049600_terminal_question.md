---
title: "terminal question"
date: 2009-01-24
forum: General Help
---

### Post by sagesparrow on 2009-01-24
I'm trying to get a pesky program running (bridge game - GIB). I've been adding libraries as prompted by error messages in terminal.  Now when issuing the command to start the program, i no longer get an error message regarding not finding a needed library file.  Instead the prompt just shows "c" (without the quotation marks).  The program doesn't start, just "c" shows.  No "computername:~$".  What does this mean?
thanks

---

### Post by HermanAB on 2009-01-24
I means that it doesn't work...
;)

Try to get the source code and compile it.  Then it may actually work.

Cheers,

Herman

---

### Post by sagesparrow on 2009-01-24
thanks.  
i've tried every way including compiling manually.  no dice.

---

### Post by albinootje on 2009-01-24
> **sagesparrow said:**
> I'm trying to get a pesky program running (bridge game - GIB).

Is that GIB from here ?
[http://cirl.uoregon.edu/ginsberg/gibresearch.html](http://cirl.uoregon.edu/ginsberg/gibresearch.html)
[http://www.gibware.com/](http://www.gibware.com/)

Did you buy it from there, and do they have a Linux version ?
Or are you trying to run the Windows version ?

---

### Post by sagesparrow on 2009-01-24
That's the one.  My friend (who i convinced to try ubuntu) got  it as a gift.  On the CD they have a tarball.  I am trying to help get it going.

You are provided with the following script in a file named INSTALL:
#!/bin/sh
if test $# -eq 0
then echo "No installation directory supplied; using ."
set $1 .
fi
tar zxf gib-6.1.3.tar.gz -C $1
cd $1/gib/engine
cd ..
ln -s engine/bridge .
ln -s engine/mb.txt .
ln -s engine/eval.dat .
ln -s engine/sample .
mkdir "Saved Games"
cd ..

and a readme with the following:
To install GIB, simply run the INSTALL script.  This will install GIB in a subdirectory gib of the current directory; to install GIB in a subdirectory of an arbitrary directory, supply the parent directory as an argument to INSTALL.  To run GIB, cd to the gib subdirectory and execute "gib".  GIB requires at least a Pentium 133 with 32MB RAM for good performance.  These are minimum requirements; if GIB suddenly becomes very sluggish, check that you aren't running other memory or CPU intensive processes which might be competing with GIB for system resources.  GIB also requires Red Hat 6.0 or later, or the equivalent.  It uses recent versions of gtk, glibc and other libraries.  We will occasionally be releasing free updates to GIB.  You can check [http://www.gibware.com/updates/](http://www.gibware.com/updates/) to get the lat  
-end-


I'm not sure if this will only work on Red Hat or there is some other problem.

---

### Post by albinootje on 2009-01-24
> **sagesparrow said:**
> That's the one.  My friend (who i convinced to try ubuntu) got  it as a gift.  On the CD they have a tarball.  I am trying to help get it going.

You are provided with the following script in a file named INSTALL:
#!/bin/sh

Good.
It's possible that #!/bin/sh is to blame. Some time ago Ubuntu changed the symlink for /bin/sh to /bin/dash.
Some shell-scripts really need /bin/bash instead.

Please try the following :
```

ls -la /bin/sh
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
ls -la /bin/sh

```
and run the shell script again.

---

### Post by sagesparrow on 2009-01-24
OK, i'll give it a try.  But at some point i gave up on the script and ran through each step manually.  it's during that process that i got error messages about the libraries and finally the "c" which was the original question.  here's the terminal output (don't ask about the gibs within gibs, that's just the way it happened as i went through various contortions).  i added libraries between the errors which lead to the next error message.  but i'm going to try your suggestion now and will get back to you.

jk@ub:~$ sudo chmod +x ~/Gib/gib/gib
[sudo] password for jk: 
jk@ub:~$ ~/Gib/gib/gib
/home/jk/Gib/gib/gib: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
jk@ub:~$ sudo find / -name libgtk-1.2.so.0*
jk@ub:~$ ~/Gib/gib/gib
/home/jk/Gib/gib/gib: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
jk@ub:~$ !!
~/Gib/gib/gib
/home/jk/Gib/gib/gib: error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory
jk@ub:~$ !!
~/Gib/gib/gib
/home/jk/Gib/gib/gib: error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory
jk@ub:~$ !!
~/Gib/gib/gib
/home/jk/Gib/gib/gib: error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory
jk@ub:~$ sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2
[sudo] password for jk: 
jk@ub:~$ ~/Gib/gib/gib
/home/jk/Gib/gib/gib: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory
jk@ub:~$ sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
jk@ub:~$  ~/Gib/gib/gib
c

---

### Post by sagesparrow on 2009-01-24
I'm somewhat reluctant to remove /bin/sh.  It's linked to something.  Could you explain what these instructions are doing and why i'm not going to screw up something.

---

### Post by albinootje on 2009-01-24
> **sagesparrow said:**
> I'm somewhat reluctant to remove /bin/sh.  It's linked to something.  Could you explain what these instructions are doing and why i'm not going to screw up something.

I included the "ls -la /bin/sh" before and after the commands so you can see the difference.

/bin/sh is a symbolic link, if you do "ls -la /bin/sh" then you can see that it is linked to /bin/dash

The next command removes /bin/sh and then the symbolic link is created again, but now pointing to /bin/bash instead.

---

### Post by albinootje on 2009-01-24
> **sagesparrow said:**
> 
jk@ub:~$ ~/Gib/gib/gib
/home/jk/Gib/gib/gib: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


This is the older libgtk, install it with :
```

sudo apt-get install libgtk1.2

```
and try again to see whether the error is gone.

---

### Post by sagesparrow on 2009-01-24
Ok
Trying to start cleanly again, I deleted the gib directory that was created by manually compiling the tar.gz file.  Now I have directory called Gib with the tar.gz file and a shell script file using the INSTALL script.  After trying to run the script here is the terminal:

jk@ub:~$ ls -la /bin/sh
lrwxrwxrwx 1 root root 4 2009-01-19 18:56 /bin/sh -> dash
jk@ub:~$ sudo rm /bin/sh
[sudo] password for jk: 
jk@ub:~$ sudo ln -s /bin/bash /bin/sh
jk@ub:~$ ls -la /bin/sh
lrwxrwxrwx 1 root root 9 2009-01-24 18:39 /bin/sh -> /bin/bash
jk@ub:~$ sudo ~/Gib/gibscript.sh
No installation directory supplied; using .
tar: gib-6.1.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/jk/Gib/gibscript.sh: line 7: cd: ./gib/engine: No such file or directory
jk@ub:~$ 

Repeatedly getting this is what led me to follow the script manually.

---

### Post by sagesparrow on 2009-01-24
re: libgtk1.2

i had loaded that from synaptic and got rid of the error message.  As you can see from that terminal readout, the process moved on to the next error message.  The other two libraries, I created a symbolic link to the newer version of that library which was already installed.  That strategy seemed to allow the process to continue past the error messages.

---

### Post by albinootje on 2009-01-24
> **sagesparrow said:**
> 
jk@ub:~$ sudo ~/Gib/gibscript.sh
No installation directory supplied; using .
tar: gib-6.1.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Can you please try again, but without sudo ?

---

### Post by albinootje on 2009-01-24
And this could be even better :
```

cd ~/Gib
chmod +x ./gibscript.sh
./gibscript.sh

```

---

### Post by sagesparrow on 2009-01-24
jk@ub:~$ ~/Gib/gibscript.sh
No installation directory supplied; using .
tar: gib-6.1.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/jk/Gib/gibscript.sh: line 7: cd: ./gib/engine: No such file or directory
ln: creating symbolic link `./bridge': Permission denied
ln: creating symbolic link `./mb.txt': Permission denied
ln: creating symbolic link `./eval.dat': Permission denied
ln: creating symbolic link `./sample': Permission denied
mkdir: cannot create directory `Saved Games': Permission denied
jk@ub:~$

---

### Post by sagesparrow on 2009-01-24
jk@ub:~$ cd ~/Gib
jk@ub:~/Gib$ chmod +x ./gibscript.sh
jk@ub:~/Gib$ ./gibscript
bash: ./gibscript: No such file or directory
jk@ub:~/Gib$ ./gibscript.sh
No installation directory supplied; using .
jk@ub:~/Gib$

---

### Post by sagesparrow on 2009-01-24
alternately:

jk@ub:~/Gib$ cd ~/
jk@ub:~$ chmod +x ~/Gib/gibscript.sh
jk@ub:~$ ~/Gib/gibscript.sh
No installation directory supplied; using .
tar: gib-6.1.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/jk/Gib/gibscript.sh: line 7: cd: ./gib/engine: No such file or directory
ln: creating symbolic link `./bridge': Permission denied
ln: creating symbolic link `./mb.txt': Permission denied
ln: creating symbolic link `./eval.dat': Permission denied
ln: creating symbolic link `./sample': Permission denied
mkdir: cannot create directory `Saved Games': Permission denied
jk@ub:~$

---

### Post by albinootje on 2009-01-24
> **sagesparrow said:**
> 
jk@ub:~/Gib$ cd ~/
jk@ub:~$ chmod +x ~/Gib/gibscript.sh
jk@ub:~$ ~/Gib/gibscript.sh
No installation directory supplied; using .
tar: gib-6.1.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
You're missing that file gib-6.1.3.tar.gz

Are there specific installation instructions on the cdrom for Linux ?
If so, please post them.

---

### Post by albinootje on 2009-01-24
Can you also do a :
```

sudo chown -R jk:jk /home/jk/Gib/

```
to make your user the owner (and group owner) of your files.

After using sudo on that script it's quite possible that some of those files are owned by root, which can explain the "permission denied" errors.

---

### Post by sagesparrow on 2009-01-24
You're missing that file gib-6.1.3.tar.gz

Are there specific installation instructions on the cdrom for Linux ?
If so, please post them.

I know that's what it says, but i do have the tar.gz file and in fact am able to extract it using Archive Manager.  The furthest I got was extracting and then creating the symbolic links as listed in the shell script.  Perhaps there is something wrong or missing in some part of that tar.gz.  

In doing this manually, what more would I need to do except extract the tar.gz and create the links?  Perhaps you could just list the steps in long form in case I am missing something or not doing it properly.

I don't have the disk.  My friend does.  They even called GIB for some help, but GIB could not offer any support for linux beyond the script and that readme file.

Taking ownership did not remove the "permission denied" error messages.
jk@ub:~$ sudo chown -R jk:jk /home/jk/Gib/
[sudo] password for jk: 
jk@ub:~$ ~/Gib/gibscript.sh
No installation directory supplied; using .
tar: gib-6.1.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
/home/jk/Gib/gibscript.sh: line 7: cd: ./gib/engine: No such file or directory
ln: creating symbolic link `./bridge': Permission denied
ln: creating symbolic link `./mb.txt': Permission denied
ln: creating symbolic link `./eval.dat': Permission denied
ln: creating symbolic link `./sample': Permission denied
mkdir: cannot create directory `Saved Games': Permission denied

thanks for all the time

---

### Post by albinootje on 2009-01-24
> **sagesparrow said:**
> 
I know that's what it says, but i do have the tar.gz file 
--- cut ---
They even called GIB for some help, but GIB could not offer any support for linux beyond the script and that readme file.

Okay, can you copy the gib-6.1.3.tar.gz inside the ~/Gib/ directory, and try again ?

And also post the output of your extracted directory ? I assume it's ~/Gib, so :
```

ls -laR ~/Gib/

```

---

### Post by sagesparrow on 2009-01-24
> **albinootje said:**
> Okay, can you copy the gib-6.1.3.tar.gz inside the ~/Gib/ directory, and try again ?

And also post the output of your extracted directory ? I assume it's ~/Gib, so :
```

ls -laR ~/Gib/

```

By copy the tar.gz, I presume you mean extract to that directory. Once that is done, a directory named "gib" is created in Gib.  Inside gib is the following files and directories:
jk@ub:~$ ls -l ~/Gib/gib
total 3264
drwxr-xr-x  3 jk jk    4096 2009-01-24 20:36 demos
drwxr-xr-x  3 jk jk    4096 2009-01-24 20:37 engine
-rwxr-xr-x  1 jk jk 3309038 2003-01-08 15:03 gib
drwxr-xr-x  4 jk jk    4096 2000-05-05 12:20 images
-rw-r--r--  1 jk jk     265 2003-01-08 15:10 INSTALL
drwxr-xr-x 24 jk jk    4096 2009-01-24 20:36 locale
drwxr-xr-x  3 jk jk    4096 2002-08-08 09:07 Saved Deals
drwxr-xr-x  2 jk jk    4096 2002-12-17 16:09 Systems

INSTALL contains the script.  gib should be the executable to start the program.  The others are directories.  Trying to start as before:
jk@ub:~$ ~/Gib/gib/gib
c

(that "c" that started this thread.)

---

### Post by sagesparrow on 2009-01-24
good news.  it's working.
i got rid of all the directories previously installed.  Then i untarred the tar.gz using tar -zxvf command.  that coupled with the added libraries and the symbolic links.  then double clicking on the gib executable in the gib directory starts it right up.  it will not start as a terminal command for some reason.

i walked my friend through the steps and got hers working now.

in short here's what worked:

untar the tar.gz in a directory such as ~/Gib

add the following libraries from synaptic (if not already installed):
   libgtk1.2 
   libpng3
   libtiff4

create symbolic links:
   sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2
   sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

(FROM GIB SCRIPT) do the following in terminal:

cd ~/Gib/gib/engine (assuming you extracted the tar.gz in ~/Gib)
cd ..
ln -s engine/bridge .
ln -s engine/mb.txt .
ln -s engine/eval.dat .
ln -s engine/sample .
mkdir "Saved Games"
cd ..

double click gib executable in ~/Gib/gib

that should do it.

thanks for your help.

---

### Post by mecanopsis on 2009-09-11
As a relative newbie, I've tried to follow [sagesparrow]("http://ubuntuforums.org/member.php?u=240054")'s advice, but it didn't work for me. I got the right files in the right places (apparently) but the gib executable had no file to make it operate. I was wondering whether other folks have had success with this system and (if so) any clues as to where I might be going wrong ?
Thanks.......

---

