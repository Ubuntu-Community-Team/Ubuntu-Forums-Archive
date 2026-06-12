---
title: "Have I installed R correctly?"
date: 2008-02-20
forum: Education &amp; Science
---

### Post by MatMan on 2008-02-20
I am running 64 bit Gutsy 7.10.

I have (hopefully) installed R 2.5.1-1 using synaptic manger (I am only 2 weeks into being a Linux person, and am not a programmer at all).

I have tried to run it from Terminal as follows:

mat@mat-desktop:~$ r
The program 'r' is currently not installed.  You can install it by typing:
sudo apt-get install littler
bash: r: command not found

so I ran:

mat@mat-desktop:~$ sudo apt-get install r
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package r

so i treid to reinstall r using synaptic and it claims to be successful... but this particular moron (me) can't seem to get into the program. I have no idea where synaptic even downloaded my files to...

sorry to be a pain in the noob. I mean neck.

---

### Post by ad_267 on 2008-02-20
I think the package you want to stall is r-base: [http://packages.ubuntu.com/r-base](http://packages.ubuntu.com/r-base)

If you use the synaptic package manager (system -> administration -> Synaptic package manager) it makes things a lot easier

---

### Post by lsmobrian on 2008-02-20
Also its case sensitive, try R at the command line instead of r

---

### Post by vanadium on 2008-02-20
You might want to subscribe to the repositories of the R project itself, not to the Ubuntu maintained version. This way, you will be using the latest stable version at any time.

To "subscribe" to the R repositories, you can take a look at the official documentation here: [http://lib.stat.cmu.edu/R/CRAN/](http://lib.stat.cmu.edu/R/CRAN/)

I will elaborate on these explanations in a "newbie friendly" way, although you will see there is not a lot more to add.

> 
To obtain the latest R packages, add an entry like

   deb [http://my.favorite.cran.mirror/bin/linux/ubuntu](http://my.favorite.cran.mirror/bin/linux/ubuntu) gutsy/

or

   deb [http://my.favorite.cran.mirror/bin/linux/ubuntu](http://my.favorite.cran.mirror/bin/linux/ubuntu) feisty/

or

   deb [http://my.favorite.cran.mirror/bin/linux/ubuntu](http://my.favorite.cran.mirror/bin/linux/ubuntu) dapper/

in your /etc/apt/sources.list file. See [http://cran.r-project.org/mirrors.html](http://cran.r-project.org/mirrors.html) for the list of CRAN mirrors. 

What this means is: load the text file /etc/apt/sources.list in your editor. You must have root privileges, though because it is a system file. 

* First open a terminal (Applications - Accessories - terminal).

* Then open /etc/apt/sources.list with root privileges: type in the terminal

gksudo gedit /etc/apt/sources.list

You will need to give your user password (this assumes you are a user with root privileges) and then the file will load in the editor "gedit".

At the end of the file, add a line that looks like:

```

deb http://www.freestatistics.org/cran/bin/linux/ubuntu gutsy/

```

Replace the "http:///... " part by the url of a cran mirror near to you (see [http://cran.r-project.org/mirrors.html](http://cran.r-project.org/mirrors.html) for the possible mirrors). If you use an earlier version f Ubuntu, you will need to adjust the gutsy/ part as well: feisty/ for version 7.4 and  edgy/ for version 6.10.

Save the file and exit gedit.

[/quote]To install the complete R system, use

   sudo apt-get update
   sudo apt-get install r-base

Users who need to compile packages should also install the r-base-dev package:

   sudo apt-get install r-base-dev

The R packages for Ubuntu should otherwise behave like the Debian ones. For more information, see the README file in [http://cran.R-project.org/bin/linux/debian/](http://cran.R-project.org/bin/linux/debian/)
[/quote]

Just type the commands as given now. Now, R will be installed. You might not need the third command except if you want to develop.

You will have warnings that the packages can not be verified. To eliminate that warning, you need also to get the key. How to do that is also explained on the page linked above. I had to use the "alternate" approach to get it to work.

After that, you start R from the terminal by typing (capital! Linux is case sensitive!)

R

Now, the terminal prompt changes into the R prompt >. If you now type

 demo(graphics)

and the graphics demo runs as expected, you are pretty much sure that your installation is OK.

After this procedure, your R installation will eventually be updated automatically through Ubuntu's update manager.

---

### Post by akniss on 2008-02-20
Unless you have a good reason to have the very latest version of R (which i suspect from your initial post that you do not) ignore the extremely long post above this one.  There is absolutely no need for you to do all of that.  If you have installed R though synaptic then it probably installed correctly. The only thing you need to change is type a capital R instead of a lowercase r.

---

### Post by wwood on 2008-04-26
> Unless you have a good reason to have the very latest version of R (which i suspect from your initial post that you do not) ignore the extremely long post above this one.

Well I for one thank you. Managed to solve the problem of not knowing the public key for that repo and so apt-get update has stopped complaining.

---

### Post by bryncoles on 2008-06-06
hello! just resurrecting an old thread... i want to add the r-cran repos to my heron box (im doing a psychology PhD, and need to access some extra packages above and beyond whats in ubuntu's own repos). 

i followed the above post, but when i get to reloading my repo indexes in synaptic, it tells me:

```
Failed to fetch http://cran.uk.r-project.org/bin/linux/ubuntu/hardy/Packages.gz  301 Moved Permanently [IP: 148.88.0.10 8080]
Some index files failed to download, they have been ignored, or old ones used instead.
```

the repo i have put in is

```
 deb http://cran.uk.r-project.org/bin/linux/ubuntu 
```.

and i have firestarter firewall (just in case thats causing problems). 

can anyone help me see what ive done wrong?

---

### Post by NikoC on 2008-06-08
> **bryncoles said:**
> hello! just resurrecting an old thread... i want to add the r-cran repos to my heron box (im doing a psychology PhD, and need to access some extra packages above and beyond whats in ubuntu's own repos). 

i followed the above post, but when i get to reloading my repo indexes in synaptic, it tells me:

```
Failed to fetch http://cran.uk.r-project.org/bin/linux/ubuntu/hardy/Packages.gz  301 Moved Permanently [IP: 148.88.0.10 8080]
Some index files failed to download, they have been ignored, or old ones used instead.
```

the repo i have put in is

```
 deb http://cran.uk.r-project.org/bin/linux/ubuntu 
```.

and i have firestarter firewall (just in case thats causing problems). 

can anyone help me see what ive done wrong?

I think the repository does no longer work... you might want to download the package manually and save it for example on your desktop (for packages: see R website). You can install the packages in terminal by typing:
cd ~/Desktop
sudo R CMD INSTALL package_name

Cheers

---

### Post by machoo02 on 2008-06-08
Or...you could simply pick a different repository.  What about one of the European ones close to the UK?

---

### Post by bryncoles on 2008-06-11
hi machoo02. ive managed to add the belgium repo for R, as well as installing the psych package via the methid recommended (described?) by nickoC. so im happy now! thanks for everyones input though!

---

### Post by Greeney on 2008-08-05
Hi,
Thank you for your very detailed instructions. I am really, really beginner with Ubuntu, but i wanted to learn how to use R. I had installed R via synaptic package manager, but I was unable to download package (ISwR= introductory statistics with R) so that I could work through examples and also I wanted to use Java as editor but I was not able to enable the Java support in R. Therefore I wanted to reinstall R with these instructions. I was able to get this far with the instructions (with loads of time and tears):

> You will have warnings that the packages can not be verified. To eliminate that warning, you need also to get the key. How to do that is also explained on the page linked above. I had to use the "alternate" approach to get it to work.

I think I have the correct key and i have it as txt file at my desktop. But as i tried to feed the key to apt-key with

   <sudo apt-key add key.txt>

It gave me this:
> gpg: no valid OpenPGP data found
What can I do? And does someone have some other suggestions, what could be wrong with my R and what could be done. Is there something else that I should know when I install? And please, remember I have no basic knowledge of ubuntu, or even windows, so do not asume anything :mrgreen:

 Thank you already!
 -G

---

### Post by tomthumb99 on 2010-04-24
Folks kindly advise, I have R and Cran installed on Ubuntu 9.10, still do not see any relevant apps under my Gnome applicatrions menu.  Am I missing some thing, do I need to start things from the command line only?  I have  many apps ( MySQL, Drupal, Open-office) installed alrady.  Trying to keep installed apps  to a min for simplicity under ubuntu.

I am using synapic to install and check packages.

---

### Post by Tart on 2010-04-24
You won't see anything.
Open terminal and type "R" if you see something like this

```
R version 2.10.1 (2009-12-14)
Copyright (C) 2009 The R Foundation for Statistical Computing
ISBN 3-900051-07-0

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

```

It means you installed it correctly. 
Install Rkward - this is realy really nice IDE, it will show up in your applications, and I prefer to use it when working with R

Best

---

### Post by tomthumb99 on 2010-04-25
Tart,

Thanks for the response. I do successfully get the R command line environment.  But, I was looking for a GUI off of X-Win. Sounds like Win and Mac has a GUI interface, not too sure on Linux side 

I did install both 'r-cran-rattle' and 'r-cran-rcmdr' packages without errors.  Best I can tell these look to be GUI interfaces to the tool/language. Still do not see any X-Win entires.  Sorry for the basic question, was looking to get started on sw.  Thanks in advance.

Note: Multiple cran packages listed under synaptic, sure could be painful if you over install this application/sw, so looking for a min approach.

---

### Post by earlycj5 on 2010-04-25
> **tomthumb99 said:**
> Tart,

Thanks for the response. I do successfully get the R command line environment.  But, I was looking for a GUI off of X-Win. Sounds like Win and Mac has a GUI interface, not too sure on Linux side 

I did install both 'r-cran-rattle' and 'r-cran-rcmdr' packages without errors.  Best I can tell these look to be GUI interfaces to the tool/language. Still do not see any X-Win entires.  Sorry for the basic question, was looking to get started on sw.  Thanks in advance.

Note: Multiple cran packages listed under synaptic, sure could be painful if you over install this application/sw, so looking for a min approach.

R-Commander is a GUI.

I know we discussed the missing entry in menus here in this forum in the past.

I don't use it so I'm not much help other than that.  You might search for R-Commander to see what you find?

---

### Post by Spike the Dingo on 2010-04-25
For what it's worth -

You should be able to install R-Commander using the new "Software Center" in the next Lucid 10.04 LTS release. When you use this method, it will appear in your GNOME panel menu.
But if you have R-commander installed and want to launch it from the terminal:
1)In a terminal start R simply by typing: ```
R
```
2)type:
```
library(Rcmdr)
```

If you want something simpler and closer to the CLI:
As I'm sure you know, Gedit (the default Ubuntu text editor) has basic support for syntax highlighting in R. If you have R running in a terminal and the Gedit open, you can drag-n-drop text back-and-forth between the two windows if you'd like. This is a fairly simple and robust way to work with R.

This may be a bit off topic, but...
If you'd like to write actual R scripts you can write all the commands you'd like to make and save it in a file with an .R extension... then go to that directory in your terminal and run
```
R CMD BATCH filename.R
```
and it will run leaving you with a nice, hidden .Rhistory file that shows all the input and output from the R script.

---

### Post by tomthumb99 on 2010-05-01
Thanks ..Thanks...Got the GUI working, the command prompt commands strictly activate/run the GUI.  

Somebody should tell Robert Gentleman, that it is 2010 and that iPhones & GUI are rulling the world.  Working off a command prompt is like watching black and white TV, why do it.

---

### Post by hubie on 2010-05-03
For what its worth, I hate running something like R from a GUI.  It really slows me down.  If I'm exploring data and I'm doing quick plots and trying out this and that, it is so much easier for me to type in the quick command, or better still hit the up-arrow to repeat commands.

There are lots of things I would much rather do from a command line, such as word processing.  I know some people really like it, but I'd rather pull out my fingernails than do anything more than building simple equations in LaTeX using a GUI (oh how I dreaded using the MS equation editor).  All those mouse clicks to choose menus and submenus, etc. just to put in a simple symbol drove me crazy.  Filling in forms and spreadsheets using only a mouse drives me crazy as well.  My rant can go on and on, but I think you get the idea.

I know it is 2010, and I know we've covered this various times in this forum, but I'm on the other side where I usually wonder why anyone would want to run R from a GUI (unless, I suppose, they only know Windows and are used to having to do everything from a GUI).

---

### Post by earlycj5 on 2010-05-03
> **hubie said:**
> If I'm exploring data and I'm doing quick plots and trying out this and that, it is so much easier for me to type in the quick command, or better still hit the up-arrow to repeat commands.


From that perspective that's *exactly* why I use RKward.  Script files in the top pane, CLI in the bottom.

I'd hesitate to call it a "GUI", more of an interface to the CLI that accesses other things like help files in an integrated way.  

Quicker for me to explore this way than the CLI since I can just run a line or a selection of a script file and change this or that along the way.

YMMV.

---

### Post by hubie on 2010-05-03
> **earlycj5 said:**
> I'd hesitate to call it a "GUI", more of an interface to the CLI that accesses other things like help files in an integrated way.  

That doesn't sound like it fits tomthumb99's definition of 2010.  Maybe 2005... ;)

By the way, if I have easy access to the CLI and it is not made a hindrance to work that way, then I wouldn't consider it a GUI either.  Just like if I run GVim, I know there are all these drop-down menus, but I almost never use them (and when I do, it is to remind myself what the appropriate command is that I have forgotten).

---

### Post by earlycj5 on 2010-05-03
> **hubie said:**
> That doesn't sound like it fits tomthumb99's definition of 2010.  Maybe 2005... ;)

By the way, if I have easy access to the CLI and it is not made a hindrance to work that way, then I wouldn't consider it a GUI either.  Just like if I run GVim, I know there are all these drop-down menus, but I almost never use them (and when I do, it is to remind myself what the appropriate command is that I have forgotten).

Then it's like GVim I guess. 
Run Analysis Plots Distributions <- just a few menu entries.

So, I guess I don't know what the full definition of a GUI would be for R, but if you can select from a drop-down menu to do analysis I'd call that a GUI since you can point and click.  ;)

But they (menus) don't get in my way either, I tend to forget they're there the way I use it.

It's a GUI that doesn't get in the way of getting stuff done, for those of us who know how to use R.

FWIW, I do believe the developer calls it a transparent front end for R.

---

### Post by gunksta on 2010-05-04
Another option that at least one person likes here is the combination of JGR and Deducer.

[JGR Website]("http://jgr.markushelbig.org/JGR.html")

[Deducer Website]("http://www.rforge.net/Deducer/")

JGR is very similar to Rkward, but it's written in Java, rather than C++/QT. Deducer is (I believe) a plugin for JGR that provides a more extensive set of menu entries than JGR provides by default. It is also written in Java (surprised?). 

I did install JGR on my system years ago. As I recall, it's a bit of a pain to install, but it's a nice application once you get it working. Note - You MUST follow the directions on the JGR website EXACTLY as written. Don't skip something just because it sounds a little weird and then wonder why it doesn't work. 

. . . . Not that I would have ever done that or anything. :D

I have never used Deducer, so if it sucks, well . . .

---

### Post by silvioskk on 2010-05-20
Hi        gunksta,
I installed JGR and everything works but I noticed that one of my CPUs is completely used by a process called "java" (which is JGR, I suppose..) even if I am doing nothing..
In the JGRError.log it continues to add the same lines, see the file attached herewith.
This is very annoying because my notebook became an electric fire, and so JGR is unusable..

As GUI I tried also RCommander (but I find it uncomfortable) and RKWard (which is really nice!), but I can't solve a problem at  startup: "The 'rkward' R-library either could not be loaded at all.."

So I need help to solve one of these problems. I only need a GUI that works..

---

### Post by gunksta on 2010-05-20
Hmmmmm. One thing that always helps - what version of Ubuntu are you running? And, are you on Ubuntu or Kubuntu?

I haven't used JGR in years. There does appear to be a bug tracker and a general mailing list:

[http://jgr.markushelbig.org/FAQ.html](http://jgr.markushelbig.org/FAQ.html)

I did take a minute and poke around their bugs and I found this from 2007:
[URL="https://www.rforge.net/bugzilla/show_bug.cgi?id=15"]
https://www.rforge.net/bugzilla/show_bug.cgi?id=15[/URL]

Unfortunately, this looks very similar to what you have described and the error output looks similar to (although I just glanced at it all).

There is a work-around. They discuss opening the About Dialog and closing it, which appears to return CPU usage to 0 when JGR is idle. From what I can read on the bug reports, this appears to be an effective work around, but the fact that it has persisted since 2007 is not a good sign. As a Java program, the devs may focus more on the Mac/Win side of their program. I don't know. I do know that most of the JGR screenshots I have seen are on Macs. It might help to drop the devs a message on the mailing list to see if you can persuade someone to do something about it.

Assuming the splash screen theory is correct - I would look to see if there is an option in the GUI to disable the splash screen. If it's the culprit - disabling it would be a better fix than having to use the About dialog every time you start the program.

Regarding the rkward error - you didn't give very many details. Are you getting this error in a dialog box, from R, from bash, etc?

---

### Post by Iurie on 2011-04-04
[How to install R, JGR and Deducer in Ubuntu 10.04]("http://realshared.com/2011/how-to-install-r-jgr-and-deducer-in-ubuntu-10-04.htm")

---

### Post by RumilSH on 2011-12-22
Hi,

First of all I'm from Spain and maybe I'll say something that sound strange. If you don't know what I mean in some sentence, please tell me to repeat (yes, I want to learn about Ubuntu and improve my english also :P, be patient please xD)

After this short presentation I'll tell my problem. I installed R successfully to use (I'm a biology studient), but our teacher uses lots of packages like BiodiversityR, Rcmdr, ade4TkGUI, etc. I installed all of them with:
```
install.packages()
``` 
and I thought I installed them correctly, but every time I need to use them I have to reinstall, or they doesn't work.

Do you know what happens?

Thank you

---

### Post by Iurie on 2011-12-23
Every time you need one of these packages you must to run from R:
```
library(packagename)
```
and than use them.

---

