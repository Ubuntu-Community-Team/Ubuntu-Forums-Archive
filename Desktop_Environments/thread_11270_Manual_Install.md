---
title: "Manual Install"
date: 2005-01-15
forum: Desktop Environments
---

### Post by CAPTAIN RON FL on 2005-01-15
I would like to install XnView.  It is not in the rep. How would I go about a manual install of it?  I did all the upgrades that I saw in the How To's. I even did an install Of gftp [ which I feel pretty good about coming from from just using windows]  :D 

 Is it possible to do this? Will it mess up ubuntu?  Is there a reason it's not in the rep. that might be bad?

Thanks, Ron

---

### Post by DJ_Max on 2005-01-15
Have you tried adding or uncommenting the 'universal' reps in your /etc/apt/sources.list file.

If so, and it still is in there, grab the tarball source and compile it
[http://www.xnview.com/](http://www.xnview.com/)

---

### Post by CAPTAIN RON FL on 2005-01-15
I think that I have all..... universe; multiverse; marillat/ stable,unstable, and testing.

How do I grab the tarball source and compile it ? 
 I have not heard about this before.  Just apt-get and synaptic.

Thanks, Ron

---

### Post by trygvebw on 2005-01-15
[QUOTE=CAPTAIN RON FL]
How do I grab the tarball source and compile it ? 
 I have not heard about this before.  Just apt-get and synaptic.
[/QUOTE]
 Compilation Mini-Guide:

1. Download this file. [ftp://www.zoo-logique.org/xnview/download/XnView-x86-unknown-linux2.x-static.tgz](ftp://www.zoo-logique.org/xnview/download/XnView-x86-unknown-linux2.x-static.tgz)

2. Unpack it.

3. Open the resulting directory in a terminal.

4. Run ./configure. If you get any errors in this step, post the error message here.

5. Run make.

6. Run "sudo make install".

---

### Post by CAPTAIN RON FL on 2005-01-15
Do you mean extract when you say upact it?  If so I did that, but I did not see how to open the resulting directory in a terminal.
That is where I am stuck at now.

Thanks, Ron

---

### Post by DJ_Max on 2005-01-15
Whatever directory was created, you cd into. Say for example the tarball extracted a directory called foo2.
```
cd foo2
```

---

### Post by CAPTAIN RON FL on 2005-01-15
I do not know what "cd" means. I have tried to open everything and can't seem to figure out what I need to do. Heck I have no idea what a tarball is. I did down load it, First I down loaded it with "open with /bin/tar (default).  I then down loaded it   and "Save to Disk". 

I know I must be close but I am lost.  This is what I get when I click on the box  and copy :
/home/ron/XnView-x86-unknown-linux2.x-static.tgz
  

What am I not doing right.  Is there a How To" for this? Please keep in mind that I am a noob just from windows.

Thanks, Ron

---

### Post by DJ_Max on 2005-01-15
You need to learn your way around Unix systems, first is commands. cd stands for change directory. I'm gonna walk you through it.

Open up the a terminal.

Go to directory where the tarball(Tarball is a compression format, similar to zip) is.
```
cd /home/ron
``` 

Run the extraction command(s)
```
tar -xzvf  XnView-x86-unknown-linux2.x-static.tgz
``` 

Check to see what directory it makes.
```
ls
``` 

Say it creates a folder called 'XnView-1.68-x86-unknown-linux2.x-static'

```
cd XnView-1.68-x86-unknown-linux2.x-static
``` 

Configure
```
./configure
``` 

Setup Make
```
make
```

Install
```
make install
```

---

### Post by CAPTAIN RON FL on 2005-01-15
DJ_MAX,

    First let me think you for your help.

I was a little confuse at first when I did the first step because I could not see that anything had changed.  After doing the first step I thought , well maybe I should just do the second part. Well that worked. OK so far so off to the third step . No problem here. Then the forth step and here is where I am stuck. It might be because I downloaded it with "open with /bin/tar (default). I then down loaded it and "Save to Disk". So the foth step comes up with this:
Desktop       XnView-1.68-x86-unknown-linux2.x-static
My Downloads  XnView-x86-unknown-linux2.x-static.tgz
Templates
 
Do I  use everything? You mention folder and this looks like it might be two follders.

Thanks, Ron

---

### Post by DJ_Max on 2005-01-15
Ok, looks like 'XnView-1.68-x86-unknown-linux2.x-static' is the directory when you wanna be in.

So for the fourth step it should be
```
cd XnView-1.68-x86-unknown-linux2.x-static
```

---

### Post by CAPTAIN RON FL on 2005-01-15
OK did that and this what I got:

ron@ubuntu:~ $ cd XnView-1.68-x86-unknown-linux2.x-static
ron@ubuntu:~/XnView-1.68-x86-unknown-linux2.x-static $ ./configure
bash: ./configure: No such file or directory
ron@ubuntu:~/XnView-1.68-x86-unknown-linux2.x-static $ make
make: *** No targets specified and no makefile found.  Stop.
ron@ubuntu:~/XnView-1.68-x86-unknown-linux2.x-static $

Everything went well untill I got to "configure", I did not see that it did not configure and then did "make".

I was wondering that I might have down loaded it too many times and the file is corrupted?? With windows you can down load over and it just writes over or replaces it. I am not sure if linux does the same or not.


The next time should I downloaded it with "open with /bin/tar (default) or down loaded it and "Save to Disk"??

Thanks, Ron

For the nextI try to do this should I

---

### Post by CAPTAIN RON FL on 2005-01-16
Something must not be right from the down load... I think.


Should I try to delete all of the down loads I did and just start over if that is possible?


Thanks, Ron

---

### Post by CAPTAIN RON FL on 2005-01-16
I was not able to get XnView running using Tarball method. I do not know why but 

would like to know how to do it. There might be some other software out there that

 uses it.


I was able to to get it running using rpm. A big THANKS to Artificial Intelligence for

 helping me to do it.  :D 

Thanks to everybody for helping me to learn!!! :D 


Ron

---

### Post by az on 2005-01-16
The key would be for you to read what the package wants you to do.  By it's name, it is a static build, which means that it is already precompiled.  You probably just have to run it.  
I would not know.  
I have not read the README file that is sitting on your computer in the directory you created when you uncompressed the downloaded file.

---

### Post by Perfect Storm on 2005-01-16
Yep, the file precompiled with install script. But the problem lies in the script and can't be ran without modfication.

It should  be straight forward.
sudo sh install

Error appear about it have to be install as root, but Ubuntu is not build up that way.

---

### Post by DJ_Max on 2005-01-16
[QUOTE=azz]By it's name, it is a static build, which means that it is already precompiled.  You probably just have to run it.  
[/QUOTE]
Arg, how could i let that past me, you're probably right, I have yet to install it on my system, I'll try it later.

Bu just to let you know those instructions I gave you are valid for normal compiles.

---

### Post by CAPTAIN RON FL on 2005-01-16
azz:  I saw the readme file and open it. I really did not see any thing about installing it though.... or more likelyI did not understand what they meant. 

  BJ_MAX : Thanks I have started a cheat sheet for myself and I have it written down.  I also bought a book this morning on installing Mandrake. It has info on doing rpm.   

I picked Ubuntu first to try. I could not get it to download. So then I tried Mandrake for all of two days.  I could not get it to update right.  Bought a "new"old computer and got Ubuntu running so here I am.

And thanks to all who have tried to help. This has been a real learning experience for me.  I am right now one of those people that linux is good for. I am tired of the constant blue screen of death, having to down load all the patchs , watching my box slow down to a crawl, having to get rid of all the spyware and other junk. that comes along with windows.

There is nothing in windows that I really have to have or need to use. I do have quite a lot tied up in some of their software ie. photoshop from 5 to cs. However I really have not used it or really learn how to do all the things. So I can start fresh learning the different  programs in linux.  

I hope to take what I learn here and use it with BeatrIX.  The reason being I only need a couple of things. I should make it clear I am still going to use Ubuntu on my desktop. I need something smaller for my laptop.  

That way I can be rid of windows and it's problems for good!!!

AI : What can I say, but thanks again.  

Captain Ron

---

### Post by DJ_Max on 2005-01-16
No problem, we were all newbies once. Heck, I remember when I didn't know Linux was an OS.

---

### Post by cazz on 2005-08-08
hmm I try to install Xnview on Ubuntu.

When I write sudo sh install.sh
It say something about line 26 and root?

Have someone make it to works in Ubuntu?

---

### Post by Lord Illidan on 2005-08-08
are you logged in as root?
Did you install it with sudo?

Give us the exact error. Don't be vague!

---

### Post by cazz on 2005-08-08
I have try both Root Terminal and Termina whit sudo

install: line 26: syntax error near unexpected token `('
install: line 26: `     uid=*(root)*)'

---

### Post by cazz on 2005-08-08
I have fix that now so now I have xnview :D

---

