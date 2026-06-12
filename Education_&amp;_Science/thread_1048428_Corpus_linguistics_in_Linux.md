---
title: "Corpus linguistics in Linux"
date: 2009-01-23
forum: Education &amp; Science
---

### Post by educamero on 2009-01-23
Hi there, does anybody, by any chance, know an open-source tool to analyze texts under corpus-linguistics with support for arabic? (actually I'm an ecologist but a friend of mine who is a windows user is having problems with that).

 Thanks on advance.

---

### Post by hubie on 2009-01-23
> **educamero said:**
> (actually I'm an ecologist but a friend of mine who is a windows user is having problems with that)

Damn those ecologist-hating Windows users! :)

I can't claim any corpus linguistics expertise, but you might find the links on [this page]("http://www.linguistics.ucsb.edu/faculty/stgries/other/links.html") useful.  It lists various software by free/non-free as well as by OS.

---

### Post by educamero on 2009-02-02
Thanks a lot. 


> **hubie said:**
> Damn those ecologist-hating Windows users! :)

I can't claim any corpus linguistics expertise, but you might find the links on [this page]("http://www.linguistics.ucsb.edu/faculty/stgries/other/links.html") useful.  It lists various software by free/non-free as well as by OS.

---

### Post by Scott T on 2009-02-04
As a new arrival to Ubuntu, and as a corpus linguist, I need to be able to install corpus/concordancing software, such as WordsmithTools - which doesn't seem to have a Linux-friendly version. (See: [http://www.lexically.net/wordsmith/](http://www.lexically.net/wordsmith/))

However, AntConc ([http://www.antlab.sci.waseda.ac.jp/software.html](http://www.antlab.sci.waseda.ac.jp/software.html)) does have a Linux option, but the instructions baffle me - see
[http://www.antlab.sci.waseda.ac.jp/software/Installing_AntConc_on_Linux.pdf](http://www.antlab.sci.waseda.ac.jp/software/Installing_AntConc_on_Linux.pdf)

Do I have to do all this if I have Ubuntu?  Or what else could I install to make the installation of AntConc easier?
Or, does anyone know of any other corpus software that is easily installable on Ubuntu? 
I don't suspect there are many corpus linguists out there - but on the off-chance....
:neutral:
Scott T

---

### Post by hubie on 2009-02-05
The AntConc program does not appear to be in the repositories, so the Ubuntu/Debian way of installing won't work.  However, the install directions you linked to are pretty standard unix-like steps.  The one advantage here for you is that the program that you download is the compiled binary, so you don't need to go through the usual compile and install routine.  All you need to run the program is to know where you downloaded it and to run the command that runs it.

I've written a little install script you can try.  Put the script in the same directory you downloaded the antconc file.  When the script is run, it will change the file permissions and copy it to a new directory named antconc off of your home directory.  It will also automatically run it for you the first time.  To run the script, if you use a command line you just type ./antconc_install.sh

You can also run the script by double-clicking on it from the file browser and choose the "Run in terminal" option.

After running the install script, any other time you want to run the AntConc program, you can either type "antconc" from a command line, or you can double-click the antconc icon from the folder.  If it is a program that you would run a lot, it is very easy to add an icon on the top of your screen that you would just need to click to run it.  I would be happy to let you know the several steps you'd need to do to do that. I'm mostly a command-line guy and I was going to script those steps to add a quick launcher to your desktop, but I'm not that savvy.

If my script doesn't run for you, it is still easy to run the antconc program.  All my script does is move the program to its own folder and change the permissions.  You can do the same manually.  After you download the code and put it in its own directory, use your file browser and right-click the icon for the program, select Properties, and make sure the Access choices are "Read and Write", and that the "Allow executing file as program" is checked.  Then you can just double-click it to run.

As for WordSmith, I did a little Googling around and I've seen some posts that say that it will run under Wine, which is a program you use to run Windows-based programs on Linux.  Another alternative I came across is [Corsis]("http://sourceforge.net/projects/corsis/"), which advertises itself as a WordSmith alternative.  If you need help running either of those I would be glad to try and help.

---

### Post by Scott T on 2009-02-05
Thanks Hubie, that's incredibly helpful. Let me play around a bit, and if I have any problems I'll post them here. I'm really very impressed with this suppport facility. :-)

---

### Post by Scott T on 2009-02-07
OK, I managed to now open the program manually as you advised, but I'm curious about the following operations which I figure I should be able to do, but don't know how! 
1. "put the script in the same directory...." how do i found the directory? is this the same as a folder? If not, how do I "put something into a directory"? (I created a folder called Antconc and put the little install command you wrote into the same folder, but suspect this is not what I was meant to do)
2. "when the script is run" - how do you "run a script"? (I tried double-clicking but couldn't find any option called "Run in terminal"
3. "type XYZ from a command line" - hmm, what's that? I did find an Open With dialogue window which had the option to "use a custom command", but when I typed in ./antconc_install.sh I got the message "could not find application" - presumably because it was not in the appropriate directory? 

The program is running (for which I'm eternally grateful) - so you don't need to answer these questions but maybe point me in the right direction.

As for the Corsis program, I downloaded it, but don't know where to find it to open it.  In Windows I'm used to being asked where i want to save a downloadable application, and then I click on the -exe file there. I'm obviously unaware of some basic downloading and filing procedure in Ubuntu (I also was unable to get Filezilla working, maybe for the same reason).
Please indulge the ignorance of a newbie!
Scott

Here's the latest on installing Corsis (aka Tenka). I read further down the installation page and found out I have to something called Mono 2.0 installed; I found this in the Synaptic list and activated it. Fine. Then tried to download Tenka again. As before, it appears in the Archive Manager window. This is where I'm not sure what to do. I sent it to my desktop, and there I "extracted" its folders. They are now sitting on the desktop too.  But I'm still no nearer knowing how to run this software. Where did I go wrong?

---

### Post by srt4play on 2009-02-07
Filezilla is available in the repositories. Install it from Synaptic (System->Administration->Synaptic package manager).

---

### Post by Scott T on 2009-02-08
Wow, thanks, it worked!

---

### Post by hubie on 2009-02-10
Hi Scott,

Were all your questions answered?  I'll answer a few of the ones you specifically mentioned:

1.)  I routinely interchange "folder" with "directory."  I'm an old VAX and unix guy, so I'm used to talking about directories.  Apple and Microsoft slapped folder icons onto directories in their file browsers and now people call them folders.  I usually use directories mainly because I try to work from the command line where one does not see any folders.  On occasion I use both in the same sentence. :)

2.)  Unfortunately I am not on my linux box right now, but if you weren't presented the option to run the script in the terminal, the script needs to be turned into an executable.  To do that, you right-click on it and go to properties, and from there you check the box for "Allow executing file as program."  Then you should be able to run in terminal.

3.)  I think you are correct that you weren't in the same directory as the file you were trying to run.

Did you get Corsis to run?  If not, I'll be glad to help you if I can.

---

### Post by Scott T on 2009-02-10
Thanks so much, Hubie, for your tips. I really appreciate the time you're putting in. :)

I've got AntConc up and running (by using the manua method you suggested, i.e. "make sure the Access choices are "Read and Write", and that the "Allow executing file as program" is checked), but haven't been so lucky with Corsis. This is what I posted into a previous message, but you might have missed: 

"Here's the latest on installing Corsis (aka Tenka). I read further down the installation page and found out I have to something called Mono 2.0 installed; I found this in the Synaptic list and activated it. Fine. Then tried to download Tenka again. As before, it appears in the Archive Manager window. This is where I'm not sure what to do. I sent it to my desktop, and there I "extracted" its folders. They are now sitting on the desktop too. But I'm still no nearer knowing how to run this software. Where did I go wrong?"

:confused:
Scott

---

### Post by hubie on 2009-02-12
I've looked into Corsis on Ubuntu and so far it is not very promising, at least on my machine.  The issue seems to be that the Corsis (nee Tenka Text) that you download from Sourceforge requires Mono version 2.2, while the default version installed on Ubuntu 8.10 is 1.9.something.  When I try to run it on my machine, it blows up with a bunch of errors.

I've perused this site as well as Googling around and I get the impression that there are all kind of issues with version 2.2, which is why the people who make the packages for Debian (and therefore Ubuntu) have not made a package.  Normally when you run into this issue, it is pretty easy to just go and grab the source code yourself and compile it on your machine.  Unfortunately Mono is a very large group of software and it isn't quite that easy (which is why the Debian guys don't just compile it up and package it).

I don't use Mono so I can't really speculate what the issue is on my machine.  I am running a 64-bit kernel, which sometimes adds some subtle problems with this kind of thing, so you might have better/different experience trying to run it.

If you want to try, it is pretty easy to do.  You should have Mono installed by default, and you said you have Tenka Text on your desktop.  As per the instructions on the Sourceforge site, you just need to open a terminal, change to the directory that has the program, and run the command to run the program.  To do this:
[INDENT]On your desktop to go *Applications -> Accessories -> Terminal*[/INDENT]
This will put you on a command line in your home folder.  You change to your Desktop folder/directory by
```
cd Desktop
```
You can then change to your Tenka Text directory by
```
cd TENKA-TEXT-0.1.3.4
```
or you can do the above two in one step with the command
```
cd Desktop/TENKA-TEXT-0.1.3.4
```
From here all you are supposed to need to do is type
```
mono Tenka.Text.WindowsInterface.exe
```
and it should run.  This is where I get a whole slew of errors and it doesn't run.

If it does run, let me know and I can show you how to make this a click-an-icon type of thing to get it to run so you don't have to go through the above steps every time you want to run it.  This is also true with the Antconc program, by the way.

If this doesn't work for you, there are a few other potential options, but they are much more involved (such as running a virtual machine that boots up a version of linux or Windows that does have Mono 2.2 support).  Otherwise, you might have to wait for a Debian/Ubuntu Mono 2.2 package to be put together.

(By the way, this goes to something you posted earlier regarding where things download, but by default Firefox downloads things to your desktop.  This is convenient, but can really clutter things up after a while.  You can have Firefox ask you where to download things by going to Edit->Preferences->Main and checking the box "Always ask me where to save files"  I usually make myself a downloads folder in my home directory and I end up putting all my downloads there.)

---

### Post by Scott T on 2009-02-14
THANKS once again, Hubie. I tried your advice but I too got the "whole slew" of errors (nice word, slew). Essentially the message was that there was a "segmentation fault".  I think I might forget Corsis/Tenka, and go back to trying WordSmith within Wine. Apropos, is it Wine 1.0.1 that I should install?
Thanks, Scott

---

### Post by cetinsert on 2009-03-17
I'm the developer of the (now very much inactive) project Corsis and could provide you a self-contained version of mono 2.2 or even mono 2.4 for your Ubuntu machine. Please inform me whether you are using 32 or 64-bit Ubuntu.

---

### Post by Emmerkar on 2009-04-04
> **cetinsert said:**
> I'm the developer of the (now very much inactive) project Corsis and could provide you a self-contained version of mono 2.2 or even mono 2.4 for your Ubuntu machine. Please inform me whether you are using 32 or 64-bit Ubuntu.


Since i have the same problem could you please send me the same mono?? Ubuntu version is now 2.0.14 that is evidently not the good one to run Corsis (or Tenka) I use a 32bit Ubuntu

Thank You

---

### Post by cetinsert on 2009-04-06
> **Emmerkar said:**
> Since i have the same problem could you please send me the same mono?? Ubuntu version is now 2.0.14 that is evidently not the good one to run Corsis (or Tenka) I use a 32bit Ubuntu

Thank You

Sorry for my late reply. Please take either step 1 or 2 and then step 3. I suggest trying the package I built for you.

-------------------------
1) WANT TO BUILD MYSELF
-------------------------

Here is how you can download and make and install Mono 2.4 - in case any step fails install the missing dependencies (like bison) and retry the failed command:

(Any minor mistakes (typos etc.) in the build instructions are to be forgiven.)

-------------------------

```
mkdir ~/mono24build
cd ~/mono24build
wget http://ftp.novell.com/pub/mono/sources/libgdiplus/libgdiplus-2.4.tar.bz2
wget http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.tar.bz2
tar xvf libgdiplus-2.4.tar.bz2
tar xvf mono-2.4.tar.bz2

cd libgdi-plus-2.4.tar.bz2
./configure --prefix=/opt/mono
make
make install

cd ~/mono24build
cd mono-2.4
sudo apt-get install bison
./configure --prefix=/opt/mono
make
make install
```

-------------------------
2) WANT TO TRY YOUR BUILD
-------------------------

Or you can download something I built on a 32-bit machine running Ubuntu 8.10:

(The package is 46 MB large and downloads from kirchhof.ath.cx are pretty slow (66 KB/s max.). Please bear with this. Might take 15 mins or more to finish.)

-------------------------

```
cd /opt
sudo wget http://kirchhof.ath.cx/stuff/mono-2.4_ubuntu_x86.tar.gz
sudo tar xvf mono-2.4_ubuntu_x86.tar.gz
```

-------------------------
3) NOW TRY TO RUN CORSIS
-------------------------

Follow Hubbie's instructions on the second page of this thread changing only the last line to read:

-----------------------

```
/opt/mono/bin/mono Tenka.Text.WindowsInterface.exe
```


Let me know if this helped you.

Regards,
Cetin Sert

---

### Post by lad.kocb on 2009-04-14
**Could a programming toy by a physicist be useful for linguists?**
This is a link to my little toy, which perhaps could be useful even for some serious work. It is a toy called Concordle, 
[COLOR="Blue"][http://folk.uib.no/nfylk/concordle/]("http://folk.uib.no/nfylk/concordle/")[/COLOR] (also: [COLOR="Blue"][http://concordle.blogspot.com/]("http://concordle.blogspot.com/")[/COLOR] - [http://www.wordle.net/]("http://www.wordle.net/"))
which I wrote during some free time in October 2008, as a reaction to my meeting with the rather famous [COLOR="Blue"][Wordle]("http://www.wordle.net/")[/COLOR] . Concordle is a very simple concordancer, written by a complete amateur in both concordancers and JavaScript (myself, a physicist, old-time FORTRAN programmer).

The absolute advantage of Concordle is that it is completely inside the browser (it even runs on Nokia N-800 internet tablet), and you can do anything with the program, it is read into your browser. It is all very simple, no libraries, no installations.

One of my points was to demonstrate (mainly to myself) how one could do sort of serious work using the pure JavaScript (you might know that JavaScript is an important part of AJAX, the basis of the new web. In my toy I just use the pure JavaScript, no A or AX added)

Since that time I have not done anything with it. In principle one needs only quite limited knowledge of programming to improve - or simply change the functionality of the code. 

As mentioned, this is mainly a toy, but I used it to compare some real world texts - looking for how the author(s) - or myself - use some words. I would be interested in reactions of real linguists - the thing can be modified in some moments (or hours).

If you will try the toy, simply remember that everything is clicable and nothing is left when you leave the browser. You must yourself find the ways how to save the "results" (this because I did not want to go beyond the simplest JavaScript). In most cases "copy and paste" should do that. And use of "seamonkey" ( [http://www.seamonkey-project.org/]("http://www.seamonkey-project.org/") ) which contains embeded HTML-editor.

Perhaps some of you linguists would be interested in some collaboration on making the [concordle]("http://folk.uib.no/nfylk/concordle_dev/") toy more serious.

The link [http://folk.uib.no/nfylk/concordle_dev/]("http://folk.uib.no/nfylk/concordle_dev/") shows the history of the developement - and several versions.

---

### Post by elitzurd on 2010-08-09
Hi, 

I've tried all this, but still run into problems. My system is a 32, Ubuntu 10.04. 
Can you please help?

Thanks!

(here's the problem...)

```
** (Tenka.Text.WindowsInterface.exe:6623): WARNING **: The following assembly referenced from /home/elitzur/mono24build/TENKA-TEXT-0.1.3.4/Tenka.Text.WindowsInterface.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=2)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/elitzur/mono24build/TENKA-TEXT-0.1.3.4/).


** (Tenka.Text.WindowsInterface.exe:6623): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (Tenka.Text.WindowsInterface.exe:6623): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (Tenka.Text.WindowsInterface.exe:6623): WARNING **: Missing method EnableVisualStyles in assembly /home/elitzur/mono24build/TENKA-TEXT-0.1.3.4/Tenka.Text.WindowsInterface.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'

```> **cetinsert said:**
> Sorry for my late reply. Please take either step 1 or 2 and then step 3. I suggest trying the package I built for you.

-------------------------
1) WANT TO BUILD MYSELF
-------------------------

Here is how you can download and make and install Mono 2.4 - in case any step fails install the missing dependencies (like bison) and retry the failed command:

(Any minor mistakes (typos etc.) in the build instructions are to be forgiven.)

-------------------------

```
mkdir ~/mono24build
cd ~/mono24build
wget http://ftp.novell.com/pub/mono/sources/libgdiplus/libgdiplus-2.4.tar.bz2
wget http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.tar.bz2
tar xvf libgdiplus-2.4.tar.bz2
tar xvf mono-2.4.tar.bz2

cd libgdi-plus-2.4.tar.bz2
./configure --prefix=/opt/mono
make
make install

cd ~/mono24build
cd mono-2.4
sudo apt-get install bison
./configure --prefix=/opt/mono
make
make install
```-------------------------
2) WANT TO TRY YOUR BUILD
-------------------------

Or you can download something I built on a 32-bit machine running Ubuntu 8.10:

(The package is 46 MB large and downloads from kirchhof.ath.cx are pretty slow (66 KB/s max.). Please bear with this. Might take 15 mins or more to finish.)

-------------------------

```
cd /opt
sudo wget http://kirchhof.ath.cx/stuff/mono-2.4_ubuntu_x86.tar.gz
sudo tar xvf mono-2.4_ubuntu_x86.tar.gz
```-------------------------
3) NOW TRY TO RUN CORSIS
-------------------------

Follow Hubbie's instructions on the second page of this thread changing only the last line to read:

-----------------------

```
/opt/mono/bin/mono Tenka.Text.WindowsInterface.exe
```Let me know if this helped you.

Regards,
Cetin Sert

---

### Post by Sigma1 on 2010-10-05
Hello,
This thread is a bit old, but I hope the question might interest some people. Wordsmith Tools is a popular piece of linguistics software, running under Windows. A functional demo version is available for download here: [http://www.lexically.net/wordsmith/version5/index.html](http://www.lexically.net/wordsmith/version5/index.html) It's supposed to run correctly under Linux (see earlier post here), but, although it installs fine, when I run it, using wine or crossover, I cannot choose my texts, which appear crossed out, cf. screenshot below.

[IMG]http://straw.blog.free.fr/public/Capture-wsmith.png[/IMG]

I've tried installing Wordsmith 5 and 4 with wine or crossover, running it as sudo (though I think this might ultimately be the source of the problem), or changing character encoding of text files, with no success. Any help would be much appreciated!

P.S. Have had no luck with Corsis either: the link above is no longer functional.

---

### Post by Habermas on 2013-01-13
Hey guys! I've been using AntConc for quite some time now and it runs great and I absolutely love it. But unfortunately every time I start up the program I have to set up my preferences (like fontsize, font style, colors, etc), they are not being saved. Any ideas on what I could do or what keywords should I use to look up a solution?

---

### Post by overdrank on 2013-01-13
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

