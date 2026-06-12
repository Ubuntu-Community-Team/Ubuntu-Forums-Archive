---
title: "Install Gaussian 09 on Ubuntu 10.04"
date: 2010-08-12
forum: Education &amp; Science
---

### Post by rajan on 2010-08-12
Dear Sci/Eng community, I've been trying to install a program to build molecules with the ability to convert to various file types. After trying to avoid it, I decided to install Gaussian and GaussView ('09) and this is my attempt to A) get some help doing so, B) put out some information on how to go about this task. 

Before I get into any specifics, I should also point out there is a very nice thread on this subject on a different linux forum:

[http://www.linuxquestions.org/questions/linux-software-2/need-help-installing-gaussian-on-suse-10-a-467329/](http://www.linuxquestions.org/questions/linux-software-2/need-help-installing-gaussian-on-suse-10-a-467329/)

and some very skeletal instructions from Gaussian:

[www.gaussian.com/g_tech/install/g09bin.pdf](www.gaussian.com/g_tech/install/g09bin.pdf)

Ok, first, here is the platform I'm starting out with:

```

rajan@saraswati:~$ uname -a
Linux saraswati 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

```

I received a disk with the following contents:

```

rajan@saraswati:/media/Gaussian 09 + G$ ls
AMD64_Linux  GaussView_x86_64 Linux  Intel_EM64T_Linux   Source
CD.md5       IBM_Power5_Power6       Linda_for_Gaussian

```

From this website:
[www.gaussian.com/g09_plat.htm](www.gaussian.com/g09_plat.htm)

It doesn't look like there is anything else that I need (I have already made sure that the gfortran-4.4 and gcc-4.4 are up-to-date), but there's not much information on my particular system. It looks like most of those systems listed are relevant only to MPI installations. 

After entering the "C" shell (by typing /bin/csh), I set the mntpnt to be where I had copied the files from the CD into, after which I set the g09root to be a directory where I will be able to find Gaussian:

```

saraswati:~/Work/Comp/Gaussian09+G> setenv mntpnt "/home/rajan/Work/Comp/Gaussian09+G"
saraswati:~/Work/Comp/Gaussian09+G> setenv g09root "/home/rajan/Work/Comp/Gaussian"

```

I then tried to cd into the directory, but since I had not created it, I got the predictable error, and the easy fix:

```

saraswati:~/Work/Comp/Gaussian09+G> cd $g09root 
/home/rajan/Work/Comp/Gaussian: No such file or directory.
saraswati:~/Work/Comp/Gaussian09+G> mkdir /home/rajan/Work/Comp/Gaussian
saraswati:~/Work/Comp/Gaussian09+G> cd $g09root

```


The one thing that I found that the instructions had incorrect was that the directory for the source code to be untarred in the line:

```

gunzip -c $mntpnt/tar/*.tgz | tar xvf -

```

was actually in the directory that would be accessed with the following command (notice the /Source inserted):

```

gunzip -c $mntpnt/Source/tar/*.tgz | tar xvf -

```

then

```

saraswati:~/Work/Comp/Gaussian> chgrp -R rajan g09
saraswati:~/Work/Comp/Gaussian> cd g09
saraswati:~/Work/Comp/Gaussian/g09> ./bsd/install 

```

This is the point I'm at now. I'm not sure if I'm missing something, but I simply cannot execute the code. In fact, I don't think the ./bsd/install script actually did anything (read it yourself and let me know if I'm wrong). I don't think there is an executable that came out of the install process. 

If anyone has any ideas, I'm listening. Otherwise, hopefully I'll figure out what these makefiles do, or how to get them to "make" gaussian.

---

### Post by rajan on 2010-09-11
I quit trying to install this and instead just am using the install that is there on the local supercomputing cluster. 

This has been done on Ubuntu 10.04, but I'm just not willing to put the effort into getting it to work when there's a low-hanging fruit in the area. 

Feel free to post your tips about how this can work for someone else if you have been successful.

---

### Post by Wistful on 2010-09-11
If you bought this program then I think you are eligible for support: [http://gaussian.com/g_tech/1.htm](http://gaussian.com/g_tech/1.htm) and [http://gaussian.com/g_orders/contact.htm](http://gaussian.com/g_orders/contact.htm) (always when you buy something, contact the manufacturer)

Libre software comes with no warranty and support must be bought from companies that offer such support or if you don't need such support, there is the so called -community- (i.e. ordinary people/users who use the program or the developers of that program that are willing to help), proprietary software on the other hand is _supported by the vendor who made it_, so **you should directly contact _"that vendor"_**.

---

### Post by jdwhitfield on 2012-08-14
This is what I had to do to get things to compile.  I'm running on
 
```
3.2.0-29-generic #46-Ubuntu x86_64 x86_64 x86_64 GNU/Linux
```

I tried to follow the Gaussian instructions but they are mostly useless.  Here's the steps I had to go through to install Gaussian 09 on Ubuntu 12.10.

[LIST=1]
[*]Prepare the machine
[*]Copy the file
[*]Setup bash variables
[*]Correct faulty scripts
[*]Compile
[/LIST]


**1) Prepare the machine**

I had to install the following packages: 
```
sudo apt-get install build-essential libc6-dev-i386 gfortran csh
```

You will need a fortran complier.  For this I installed Portland Group Fortran (10.5).  This installation went much smoother but if you are also using version 10.5 on Ubuntu you will need the patch ([http://www.pgroup.com/userforum/viewtopic.php?t=1914&postdays=0&postorder=asc&start=5](http://www.pgroup.com/userforum/viewtopic.php?t=1914&postdays=0&postorder=asc&start=5)). If your university or company doesn't have the portland complier, you can use the ifort from Intel or gfortran from GNU.  I used PGF and if you use something else please give instructions in a follow up post.

**2) Copy the files**
Exporting env variables globally at too hard for me so I changed ownership of thefolder /usr/local/g09 to myself with
```
sudo mkdir /usr/local/g09 
sudo chown -R myUserName /usr/local/g09
``` 
Then I copied the (untar'd) files from YourFolderSomeWhere/Gaussian09/TAR/g09 to /usr/local/g09 using Nautilus.

**3) Set up bashrc**

I added the following to my .bashrc
```

 # for Gaussian 09
 export g09root=/usr/local
 export GAUSS_SRCDIR=/tmp
```
Note that g09root is '/usr/local' not '/usr/local/'.  You should execute the same commands on the commandline to set the variables within the current session.

**4) Correct scripts so that they run**

Most of the scripts fail because the commands are not 'not found.'  Use the following command in the folder /usr/local/g09/bsd/ correct this
```

  sed -i 's/`gau-machine/`.\/gau-machine/' *
  sed -i 's/`set-mflags/`.\/set-mflags/' bldg09
  sed -i 's/`bsd\/set-mflags/`.\/bsd\/set-mflags/' bldg09
  sed -i 's/`gau-hname/`.\/gau-hname/' set-mflags 
  sed -i 's/`cachesize/`.\/cachesize/' set-mflags 
  cp gau-unlimit ..
  cp cachesize ..
  cp set-mflags ..
  cp ../gau-machine .
```
The gau-unlimit and gau-machine files are used in folders g09 and g09/bsd and is easier to copy it than sort out their scripts.

The file fsplit.c didn't work out the box but I google'd an easy solution: ([http://root.cern.ch/phpBB3/viewtopic.php?t=11913&p=51654](http://root.cern.ch/phpBB3/viewtopic.php?t=11913&p=51654))
```
sed -i 's/getline/get_line/' fsplit.c
```

**5) Compliation**
Now things should run.
Go to g09 folder
```
cd /usr/local/g09
./bsd/bldg09 2>&1 | tee make.log
```
The '2>&1 | tee make.log' outputs the stdout and stderr to make.log and to the commandline. I found this useful to see if there are any errors. If you trust everything will go smoothly just use
 ```
$ ./bsd/bldg09 >&make.log 
```
and check the make.log file if it ends too quickly.

**6) See if it worked** 
Check the end of make.log for successful completion, and confirm that the executables have been built:

   ```
 ls $g09root/g09/*.exe
```

There should be 78 files.

---

### Post by overdrank on 2012-08-14
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

