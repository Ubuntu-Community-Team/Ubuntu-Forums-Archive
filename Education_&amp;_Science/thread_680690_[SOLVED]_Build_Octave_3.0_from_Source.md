---
title: "[SOLVED] Build Octave 3.0 from Source?"
date: 2008-01-28
forum: Education &amp; Science
---

### Post by Telescope_Nerd on 2008-01-28
Hey
Has anybody out there successfully built Octave 3.0 from source?
I am having problems. I tried ./configure and got the error message that gnu readline was required. I got gnu readline 5.1 and tried ./configure again. Same error message??!!

Is there another dependacy that I might not have that could cause the same error message?

If you have performed a successful build  please post and let me know how!

Cheers
T

---

### Post by thisismalhotra on 2008-01-28
Yes I have sucessfully built Octave from source.

Do following.

sudo apt-get build-dep octave

(This will build all the dependencies)

Open Synaptic and Install libqhull

Now the usual

./configure
make 
make install.

Instead of make install if you do 

sudo checkinstall

it will give you a deb package which is better for future install and any subsequest reinstalls or uninstalls.(you will nee to install package 'checkinstall' from synaptic)

I hope you know that you will need to install Gnuplot anf build-essential as well as gfortran before you do ./configure.

Read this it might help.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

P.S; I have the deb package if you need. Send me your e-mail ID I will send the package to you.

TC :popcorn:

---

### Post by Telescope_Nerd on 2008-01-28
Hey thanks for the info!
I have already done 

sudo apt-get build-dep octave 

but I have not installed libqhull. I will give that a try later on and let you know if it works out. I will also follow your checkinstall tip as it would be good to have the .deb

Yeah I have Gnuplot and compilers for just about everything, all the c's, java, f77 perl etc 

If all else fails I'll be in touch for that .deb

Thanks again!
T

---

### Post by thisismalhotra on 2008-01-28
Hey,

No Problem, I am not sure f77 works in this case (I think I remember my self getting the same issue) use gfortran and you will build it like a dream.

FYI, Octave 3.0 has lot of additons you will really like it...:guitar:

---

### Post by Telescope_Nerd on 2008-01-28
Just finished the build and install. octave 3.0 is up and running sweet!...
Great tips thanks

---

### Post by thisismalhotra on 2008-01-28
Do me a favor, if you build it using a checkinstall and have a .deb package. Upload it to a website (I don't know of any) and post a link for other users to use.

I always want to do it but don't know how .. it will really be appreciated. Also, if you can let me know any useful websites I can post Octave 3.0 + Qtoctave(which is a gui frontend for octave) + EasyPlot (Alternate plot package instead of Gnuplot) all up there. I have deb packages for them??

Thnks and happy number crunching

---

### Post by Tantor on 2008-02-06
Why is it that Octave 3 is not offered in Synaptics and we have to compile it ourselves?? (my Synaptics only offers me Octave 2.9). Is it just because the list hasn't been updated yet or because Ubuntu developers recommend installing 2.9??

---

### Post by UbuWu on 2008-02-07
> **Tantor said:**
> Why is it that Octave 3 is not offered in Synaptics and we have to compile it ourselves?? (my Synaptics only offers me Octave 2.9). Is it just because the list hasn't been updated yet or because Ubuntu developers recommend installing 2.9??

Octave 3.0 will be in ubuntu 8.04 (hardy).

---

### Post by Telescope_Nerd on 2008-02-07
I thinks it is already in the repositories for hardy, does anyone know if it's possible to add a hardy repository to gutsy? Or is this just unwise?
Just curious, i haven't tried it because I managed to build it from scource successfully using the instructions higher up this thread.

---

### Post by UbuWu on 2008-02-07
> **Telescope_Nerd said:**
> I thinks it is already in the repositories for hardy, does anyone know if it's possible to add a hardy repository to gutsy? Or is this just unwise?
Just curious, i haven't tried it because I managed to build it from scource successfully using the instructions higher up this thread.

That is not a good idea.

---

### Post by Tantor on 2008-02-10
I have followed the instructions from post #2 (thanks thisismalhotra!) and installed Octave 3.0. Everything is working fine but I have a couple of questions with respect to the installation.

I did a "checkinstall" instead of "make install". It has generated a Debian package

(1) Can I now delete the package (.deb) as well as the source code or is it needed for something?

(2) Having used the "checkinstall" method, should I now be able to uninstall Octave from Synaptic PM or do I have to type some command in the terminal? (I don't mind using the command line, but I would like to have a centralized list with everything that is installed.)

(3) After installing Octave 3.0, the update manager inmediately offered my an "update" to 2.9 !!!! Is there some way to permanetly reject this "downdates"?

Thanks to everyone for your help!

---

### Post by Telescope_Nerd on 2008-02-11
Hi Tantor
I think synaptic just deals with the repositories and as octave 3.0 is not in there you will have to go with the command line. In order to remove octave 3.0 after it has been installed from the .deb package you will have to use

sudo dpkg --remove octave

or

sudo dpkg --purge octave

purge is a more complete removal thet gets rid of some config files that remove leaves behind.

I also have the 2.9 update issue, very annoying. You can try doing

sudo aptitude hold octave

This should stop octave "updating" to 2.9 when you run updates from the command line but It does not stop the annoying update messages.

also when a new octave comes out in the repositories and you do want to upgrade remember to

sudo aptitude unhold octave

---

### Post by thisismalhotra on 2008-02-11
> **Tantor said:**
> I have followed the instructions from post #2 (thanks thisismalhotra!) and installed Octave 3.0. Everything is working fine but I have a couple of questions with respect to the installation.

I did a "checkinstall" instead of "make install". It has generated a Debian package

(1) Can I now delete the package (.deb) as well as the source code or is it needed for something?

(2) Having used the "checkinstall" method, should I now be able to uninstall Octave from Synaptic PM or do I have to type some command in the terminal? (I don't mind using the command line, but I would like to have a centralized list with everything that is installed.)

(3) After installing Octave 3.0, the update manager inmediately offered my an "update" to 2.9 !!!! Is there some way to permanetly reject this "downdates"?

Thanks to everyone for your help!

1 -> Yes you can delete the deb package and the source but I would keep the deb as it will be handy for a later reinstall.

2-> I think you should see octave 3.0 in syanptic and can uninstall from there (no install for sure) but I would not count on it and will stick to the terminal. (I can see it on mine -  attached picture)

3 -> Do what telescope says, I don't know of a way YET

TC

---

### Post by phinn on 2008-02-16
How do you get Octave 3.0 anyway? Every windows user has had it for a while.  I have been unable to compile it from source or find packages anywhere.

If only Debian/Ubuntu would update their repos once in a while I would be in heaven :confused:

---

### Post by LaserJock on 2008-02-16
> **phinn said:**
> How do you get Octave 3.0 anyway? Every windows user has had it for a while.  I have been unable to compile it from source or find packages anywhere.

If only Debian/Ubuntu would update their repos once in a while I would be in heaven :confused:

Well,  Octave 3.0 was released 2007-12-21, Debian had it 2007-12-23, and Ubuntu had it 2008-01-28 after some discussion around upgrade paths, etc. For a non-trivial package that has a fair amount of reverse dependencies and is making a major version shift that's a pretty good turn-around time.

-LaserJock

---

### Post by ConstableRoark on 2008-02-17
I have encountered a problem with Octave which I have been unable to solve.  While Synaptic says that libqhull5 and libreadline5 are installed, the octave3.0 ./configure process does not see them.  I receive the following error message if you simply run: 

```
sudo ./configure 
```

```

...
...
checking for log2... yes
checking for struct stat.st_blksize... yes
checking for struct stat.st_blocks... yes
checking for struct stat.st_rdev... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct tm.tm_zone... yes
checking whether closedir returns void... no
checking for struct group.gr_passwd... no
checking if mkdir takes one argument... no
checking for tputs in -lncurses... no
checking for tputs in -lcurses... no
checking for tputs in -ltermcap... no
checking for tputs in -lterminfo... no
checking for tputs in -ltermlib... no
configure: WARNING: I couldn't find -ltermcap, -lterminfo, -lncurses, -lcurses, or -ltermlib!
checking for rl_set_keyboard_input_timeout in -lreadline... no
configure: WARNING: I need GNU Readline 4.2 or later
configure: error: this is fatal unless you specify --disable-readline

```

If I use the recommended --disable-readline options I receive the following: 

```

configure: WARNING: command editing and history features require GNU Readline
configure: WARNING: I couldn't find -ltermcap, -lterminfo, -lncurses, -lcurses, or -ltermlib!
configure: WARNING: I didn't find gperf, but it's only a problem if you need to reconstruct oct-gperf.h
configure: WARNING: I didn't find flex, but it's only a problem if you need to reconstruct lex.cc
configure: WARNING: I didn't find bison, but it's only a problem if you need to reconstruct parse.cc
configure: WARNING: UMFPACK not found.  This will result in some lack of functionality for sparse matrices.
configure: WARNING: COLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CCOLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CHOLMOD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CXSparse not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: FFTW library not found.  Octave will use the (slower) FFTPACK library instead.
configure: WARNING: GLPK library not found.  The glpk function for solving linear programs will be disabled.
configure: WARNING: HDF5 library not found.  Octave will not be able to save or load HDF5 data files.
configure: WARNING: PCRE library not found.  This will result in some loss of functionality for the regular expression matching functions.
configure: WARNING: Qhull library not found --- This will result in loss of functionality of some geometry functions.
configure:

NOTE: libraries may be skipped if a library is not found OR
      if the library on your system is missing required features.

```

Can anyone shed some light on this issue?

Thanks,
-Roark

---

### Post by thisismalhotra on 2008-02-18
> **ConstableRoark said:**
> I have encountered a problem with Octave which I have been unable to solve.  While Synaptic says that libqhull5 and libreadline5 are installed, the octave3.0 ./configure process does not see them.  I receive the following error message if you simply run: 

```
sudo ./configure 
```

```

...
...
checking for log2... yes
checking for struct stat.st_blksize... yes
checking for struct stat.st_blocks... yes
checking for struct stat.st_rdev... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct tm.tm_zone... yes
checking whether closedir returns void... no
checking for struct group.gr_passwd... no
checking if mkdir takes one argument... no
checking for tputs in -lncurses... no
checking for tputs in -lcurses... no
checking for tputs in -ltermcap... no
checking for tputs in -lterminfo... no
checking for tputs in -ltermlib... no
configure: WARNING: I couldn't find -ltermcap, -lterminfo, -lncurses, -lcurses, or -ltermlib!
checking for rl_set_keyboard_input_timeout in -lreadline... no
configure: WARNING: I need GNU Readline 4.2 or later
configure: error: this is fatal unless you specify --disable-readline

```

If I use the recommended --disable-readline options I receive the following: 

```

configure: WARNING: command editing and history features require GNU Readline
configure: WARNING: I couldn't find -ltermcap, -lterminfo, -lncurses, -lcurses, or -ltermlib!
configure: WARNING: I didn't find gperf, but it's only a problem if you need to reconstruct oct-gperf.h
configure: WARNING: I didn't find flex, but it's only a problem if you need to reconstruct lex.cc
configure: WARNING: I didn't find bison, but it's only a problem if you need to reconstruct parse.cc
configure: WARNING: UMFPACK not found.  This will result in some lack of functionality for sparse matrices.
configure: WARNING: COLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CCOLAMD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CHOLMOD not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: CXSparse not found. This will result in some lack of functionality for sparse matrices.
configure: WARNING: FFTW library not found.  Octave will use the (slower) FFTPACK library instead.
configure: WARNING: GLPK library not found.  The glpk function for solving linear programs will be disabled.
configure: WARNING: HDF5 library not found.  Octave will not be able to save or load HDF5 data files.
configure: WARNING: PCRE library not found.  This will result in some loss of functionality for the regular expression matching functions.
configure: WARNING: Qhull library not found --- This will result in loss of functionality of some geometry functions.
configure:

NOTE: libraries may be skipped if a library is not found OR
      if the library on your system is missing required features.

```

Can anyone shed some light on this issue?

Thanks,
-Roark

DO following and post back if does not work...

Uninstall the qhull and readline libraries....(I dont know why you need read line).

run..

```
sudo apt-get build-dep octave
```

Reinstall qhull and readline

try again.. (dont do sudo ./configure do only ./configure)

if it still does not work, try without readline.

Post again if you are still stuck...

---

### Post by ConstableRoark on 2008-02-18
I do not think I should remove readline as a number of GNOME programs (not all of which I am familiar with) depend on it.  In removing readline, firefox, gaim, amarok, etc. would be removed as well.  I did, however, re-install it.  

With regards to downloading dependences for Octave, I receive the following message:

```

crisson@crisspc:/tmp/octave-3.0.0$ sudo apt-get build-dep octave
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for octave2.9
crisson@crisspc:/tmp/octave-3.0.0$ 

```

I also tried the same string using octave2.9 and octave3.0 instead of simply "octave", which led to the same error:  

```

crisson@crisspc:/tmp/octave-3.0.0$ sudo apt-get build-dep octave2.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for octave2.9
crisson@crisspc:/tmp/octave-3.0.0$ sudo apt-get build-dep octave3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for octave3.0

```

---

### Post by thisismalhotra on 2008-02-18
Do you have all the repositories enabled.??

Also, trying running the same command out of your tmp folder (though it should not make any difference)

---

### Post by ConstableRoark on 2008-02-18
**thisismalhotra**, it looks like the lack of source repositories was the primary culprit.  That and not having qhull-dev, which is apparently needed by the application beyond just libqhull

---

### Post by thisismalhotra on 2008-02-19
> **ConstableRoark said:**
> **thisismalhotra**, it looks like the lack of source repositories was the primary culprit.  That and not having qhull-dev, which is apparently needed by the application beyond just libqhull

Well I am glad it worked, they must have changed something in the repos as when I installed libqhull5 it installed the dev for me automatically. I know they are doing something in repos as Octave 3.0 will be in hardy repos by default.

---

### Post by ItalOz on 2008-02-26
I am having the same problem,
when doing ```
sudo apt-get build-dep octave
```

the answer is
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

```

so... which is this repository I should add??!?

If ConstableRoark could give me the correct tip would be appreciated

EDIT:

found out, just enable all the repositories in the source manager... run again "sudo apt-get build-dep octave" and the work is done...

Now it is time for compiling :-)))

---

### Post by ItalOz on 2008-02-26
I've successfully built and installed Octave3.0 for amd64

If it can be of help for anyone, tell me how to build the dev files and I will.

I'll keep the directory for a few days.

:KS

---

### Post by thisismalhotra on 2008-02-26
> **ItalOz said:**
> I've successfully built and installed Octave3.0 for amd64

If it can be of help for anyone, tell me how to build the dev files and I will.

I'll keep the directory for a few days.

:KS

Yes it really helps people. To make a .deb file, install a pckage called checkinstall from synaptic. 
Once you have this package, instead of doing sudo make install in last step, do a sudo checkinstall and it will install octave as well as give you a .deb file to distribute.

And if you have/know of a website where you can put this up for people to download, you will have lot of fans out there.

---

### Post by DeeD2k2 on 2008-03-03
> **Tantor said:**
> I have followed the instructions from post #2 (thanks thisismalhotra!) and installed Octave 3.0. Everything is working fine but I have a couple of questions with respect to the installation.

I did a "checkinstall" instead of "make install". It has generated a Debian package

(...)

(3) After installing Octave 3.0, the update manager inmediately offered my an "update" to 2.9 !!!! Is there some way to permanetly reject this "downdates"?

Thanks to everyone for your help!As far as I know, this can only be solved when you are making the package. At the point checkinstall asks for information about the package, change the version from 3.0.0 to **1:**3.0.0. Now update manager will recognize it as a later version.

---

### Post by thisismalhotra on 2008-03-03
Guys I have finally posted deb links for Octave 3.0, Qtoctave and Easyplot1.1.

Links are in the end of the following post

[http://ubuntuforums.org/showthread.php?t=707854](http://ubuntuforums.org/showthread.php?t=707854)

---

### Post by ItalOz on 2008-03-03
> **thisismalhotra said:**
> Yes it really helps people. To make a .deb file, install a pckage called checkinstall from synaptic. 
Once you have this package, instead of doing sudo make install in last step, do a sudo checkinstall and it will install octave as well as give you a .deb file to distribute.

I've downloaded checkinstall but you write that if I run that it will not only build the .deb package but also install Octave.

The point is that I've already installed it, so what is it going to happen if I run 
"sudo make install"?

That's one thing, the others being:
where is going to be saved the package?
Is it going to be only one file?
How can I be sure that it is going to work and I am not going to upload a lot of rubbish onto some server?

If you can give me these advices otherwise point me in the right direction

Cheers

---

### Post by thisismalhotra on 2008-03-03
> **ItalOz said:**
> I've downloaded checkinstall but you write that if I run that it will not only build the .deb package but also install Octave.

The point is that I've already installed it, so what is it going to happen if I run 
"sudo make install"?

That's one thing, the others being:
where is going to be saved the package?
Is it going to be only one file?
How can I be sure that it is going to work and I am not going to upload a lot of rubbish onto some server?

If you can give me these advices otherwise point me in the right direction

Cheers

I am kinda confused in the way you have asked this question but I think these are the answers you were looking for: -

1. After you install checkinstall, you don't do 'sudo make install' you do 'sudo checkinstall.

2. I have octave installed to but let me try and do 'sudo checkinstall' on my machine and see what happens. I will post back

3. .deb package will one file ONLY, for me it was 16mb in size, and the package will be save in directory where your source is, i.e. the directory you are in when you run checkinstall.

4. 2 ways to confirm your package ir right: -

a. if you have 2 machines, use the .deb to install on the other machine.

b. if you have just one, uninstall your present install and use .deb package to install it again and see if it works...

Hope this answers .. all you needed to know:KS

---

### Post by ItalOz on 2008-03-04
OK I did not get that I have to run "sudo chekinstall"... my mistake.

But yes, those were the answers I was looking for. I'll give it a go and I'll post the results.

EDIT:

Done! my package is 8.5Mb large.
I'll try to test it when I have some time but if, in the meantime, somebody wants it or if anyone is willing to host it for others to download you are very welcome

---

### Post by thisismalhotra on 2008-03-04
> **ItalOz said:**
> OK I did not get that I have to run "sudo chekinstall"... my mistake.

But yes, those were the answers I was looking for. I'll give it a go and I'll post the results.

EDIT:

Done! my package is 8.5Mb large.
I'll try to test it when I have some time but if, in the meantime, somebody wants it or if anyone is willing to host it for others to download you are very welcome

I already have them hosted.. here

[http://ubuntuforums.org/showthread.php?t=713880](http://ubuntuforums.org/showthread.php?t=713880)

Also, my octave deb is 16mb large... you must have a better compression dude..

Please see the above link and let me know or post there if you are willing to participate or contribute..

TC

---

### Post by thisismalhotra on 2008-03-05
> **DeeD2k2 said:**
> As far as I know, this can only be solved when you are making the package. At the point checkinstall asks for information about the package, change the version from 3.0.0 to **1:**3.0.0. Now update manager will recognize it as a later version.

Dude thanks a ton.. your idea worked and now I don't have that annoying message every time..

---

### Post by elexhobby on 2008-03-06
I followed the above methods.. However, I cannot use functions such as imread, jpgread, dlmwrite, dlmread in octave 3.0.. How do I get these functions to work in Octave 3.0? Is there any Octave 3.0-forge?

Please help.

---

### Post by thisismalhotra on 2008-03-06
> **elexhobby said:**
> I followed the above methods.. However, I cannot use functions such as imread, jpgread, dlmwrite, dlmread in octave 3.0.. How do I get these functions to work in Octave 3.0? Is there any Octave 3.0-forge?

Please help.

Sure there is .. look up on octave - forge website

[http://octave.sourceforge.net/](http://octave.sourceforge.net/)

---

### Post by elexhobby on 2008-03-08
Thanks a lot thisismalhotra!

I did download the packages and could install them without a problem.

However, I still feel octave 2.1 is much more "stable" and comfortable to work with. For instance, imagesc in octave 3.0 is able to display images that are only small in size (say 100*100 image) If I ask it to display a 700*700 matrix as an image, the imagemagick window simply opens and closes again instantly without displaying the image.

What I then tried was saved all my current variables to a file and loaded that file from octave 2.1, and octave 2.1 was easily able to display the matrices as images!!

The only reason I am being forced to use octave3.0 is that octave 2.1 doesn't have sparse matrices functionality. (I read that it existed in edgy and dapper versions, but was removed from fiesty and gutsy) I would be grateful if somebody could let me know how I can somehow borrow the octave3.0 sparse matrices functionality into octave 2.1

Please help.

---

### Post by thisismalhotra on 2008-03-11
> **elexhobby said:**
> Thanks a lot thisismalhotra!

I did download the packages and could install them without a problem.

However, I still feel octave 2.1 is much more "stable" and comfortable to work with. For instance, imagesc in octave 3.0 is able to display images that are only small in size (say 100*100 image) If I ask it to display a 700*700 matrix as an image, the imagemagick window simply opens and closes again instantly without displaying the image.

What I then tried was saved all my current variables to a file and loaded that file from octave 2.1, and octave 2.1 was easily able to display the matrices as images!!

The only reason I am being forced to use octave3.0 is that octave 2.1 doesn't have sparse matrices functionality. (I read that it existed in edgy and dapper versions, but was removed from fiesty and gutsy) I would be grateful if somebody could let me know how I can somehow borrow the octave3.0 sparse matrices functionality into octave 2.1

Please help.

NO offense here but you are using way too old octave and I would say it is time to upgrade. Regarding your problem, I dont really use much of built in functions in octave-forge so could not really help you out.

I would post there problems on octave mailing list or web view available from nabble. Many function in 2.1 had bugs or memory leaks in it and were deprecated and replaced with other functions doing similar work in newer releases. I am sure if you post on octave mailing lists you can get the alternate options to your function in Octave 3.0.0 which is the current stable release. 

One more thing, what is your plot manager and do you have libqhull5 and libqhull-devel??

---

### Post by Wolf-Ekkehard on 2008-03-16
> **elexhobby said:**
> Thanks a lot thisismalhotra!

I did download the packages and could install them without a problem.

However, I still feel octave 2.1 is much more "stable" and comfortable to work with. For instance, imagesc in octave 3.0 is able to display images that are only small in size (say 100*100 image) If I ask it to display a 700*700 matrix as an image, the imagemagick window simply opens and closes again instantly without displaying the image.

What I then tried was saved all my current variables to a file and loaded that file from octave 2.1, and octave 2.1 was easily able to display the matrices as images!!

The only reason I am being forced to use octave3.0 is that octave 2.1 doesn't have sparse matrices functionality. (I read that it existed in edgy and dapper versions, but was removed from fiesty and gutsy) I would be grateful if somebody could let me know how I can somehow borrow the octave3.0 sparse matrices functionality into octave 2.1

Please help.

Hmmm,

I had a similar problem with displaying images when I had older versions of octave (2.1) laying around.  Octave started using imagemagick to display images - not good.  After I wiped everything clean and installed 3.0.0 and gnuplot 4.2.0 from scratch, displaying images worked fine (I just tried 710 x 710 before I answered you).  The problem becomes already evident when octave uses imagemagick to display images.  Octave 3.0.0 is not supposed to do that anymore.  It uses gnuplot 4.2 to display images just like any other graphics (just like Matlab does).  BTW, if you are using qtoctave and easy-plot, disable easy-plot and use gnuplot straight.  For some reason, easy-plot doesn't handle display of images right.

I know it is a bitter pill to re-do everything, but this is what I ended up doing, and it now works fine.  Maybe somebody else has a less drastic way of fixing this?

---

### Post by keithspg on 2010-02-28
Here we go again. I am running Karmic 9.10 and regretting it pretty much daily. It seems to be a recurring theme that it is difficult to compile Octave and may benefit from a howto. I will create it once I figure out how to get this done. please help. 

I have downloaded 3.3.50 source because all of the versions in synaptic do not have the basic dlmread function that I need to read my data into Octave. I do not know how or why it vanished, but the windows version of 3.2.2 has it and I need it to work in Ubuntu as well.

My 9.10 is updated. I have found that there is a certain level of uncertainty in trying to following the steps laid out in these posts. Either things have changed in versions or I am unable to decipher what is being said. 

Here is what I have tried am having the same problem,
when doing
     ```
sudo apt-get build-dep octave 
```the answer is
     
     ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list 

```I am running apt-get this from the 3.3.50 root directory I downloaded. It is on my desktop if that is important.

This comment I do not completely understand 

> EDIT:

found out, just enable all the repositories in the source manager... run again "sudo apt-get build-dep octave" and the work is done...My guess is that this refers to the synaptic package manager under Settings -> Repositories and make sure that they check boxes are filled. I have a check mark on a filled background for the top 4 and a filled block without a check mark for the 'Source Code'. I am downloading from the US server. 

Any and all help appreciated.

KeithG

---

### Post by keithspg on 2010-02-28
Update,

I have finally made an octave-3.3.50.... It appeared to compile after I installed imagemagic. I read the install docs and made sure all this was installed:
> GNU Make, `gcc', and `libstdc++', `gnuplot', `bison', `flex', and Texinfo . The base install of 9.10 does not install imagemagic by default, so I installed that as well as ensuring that all the rest of this required stuff was installed. 

I did it as a ./configure and a make (no flags) and had to hit return many times as it was creating the doc files it appears. 

One key was that I needed to run
```
sudo apt-get autoremove
sudo apt-get build-dep octave3.0
sudo apt-get install libftgl-dev

``` instead of 
```
sudo apt-get build-dep octave
sudo apt-get install libftgl-dev
```

Also, I ran

```
apt-get install checkinstall
checkinstall

```Instead of "make install" so that it would create a deb for installation on other machines and so that I could uninstall it cleanly (If I read all that correctly).

Hope this helps someone else. This was painful. Also, I think this was all I did. 

KeithSPG

---

### Post by UbuWu on 2010-03-03
> **keithspg said:**
> 
I have downloaded 3.3.50 source because all of the versions in synaptic do not have the basic dlmread function that I need to read my data into Octave. I do not know how or why it vanished, but the windows version of 3.2.2 has it and I need it to work in Ubuntu as well.

That is a bug in the octave-io package in ubuntu 9.10. You could try installing the octave-io 1.0.9-1 package from debian or lucid to fix this.

See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=535281](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=535281)

---

### Post by keithspg on 2010-11-23
And with the developments with Lucid and Maverick, it seems a bug has crept back in. 'sudo checkinstall' does not work as it cannot create directories. I was able to get it to 'checkinstall' by running: 'sudo checkinstall -D --fstrans=no --install=yes'

Keith

---

