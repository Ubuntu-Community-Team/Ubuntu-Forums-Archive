---
title: "Installing Octave"
date: 2012-02-22
forum: Education &amp; Science
---

### Post by LinuXofArabiA on 2012-02-22
Hello Everyone,

I am trying to install Octave on my 11.10 Ubuntu, but apparently it is not as easy as I thought.

I downloaded the binary, extracted, navigated to the extracted folder in terminal, and ran ./configure

after a long list of checks and logs configure stops. I assuming it aborted since the few messages I got were

[I]checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking how to get verbose linking output from ... configure: WARNING: compilation failed

checking for Fortran 77 libraries of ... 
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... configure: error: in `/home/oshak/octave-3.4.3':
configure: error: cannot compile a simple Fortran program
See `config.log' for more details[/I]

then I type 'make' and I get 

*make: *** No targets specified and no makefile found.  Stop.*

I am assuming ./configure didnt finish properly and hence didnt create the make file properly.

Any help is greatly appreciated.

I wonder how tough using Octave is going to be if that trouble is only for installing :(

---

### Post by PGScooter on 2012-02-22
If .configure doesn't finish properly there's no point in running make, in my opinion.
Is there a reason you're compiling from source?

Why not:
sudo apt-get install octave3.2
?
or whichever version 11.10 has (if you're not sure, type octave and then [tab] [tab] and you will see on the list).

---

### Post by LinuXofArabiA on 2012-02-22
Thanks PGScooter. I dunno why I was trying to compile from source, I did what you said and it worked. The challenge now is to learn it. Do you have any good help sources that you would recommend?

Thanks again

---

### Post by PGScooter on 2012-02-22
LinuXofArabiA,

I'm glad it worked! I actually don't know how to use Octave. I have been meaning to learn it myself as well.
This book seems to be pretty good:
GNU Octave Beginner's Guide [Paperback]
Jesper Schmidt Hansen (Author) 
[http://www.amazon.com/Octave-Beginners-Jesper-Schmidt-Hansen/dp/1849513325/ref=sr_1_1?ie=UTF8&qid=1329936481&sr=8-1](http://www.amazon.com/Octave-Beginners-Jesper-Schmidt-Hansen/dp/1849513325/ref=sr_1_1?ie=UTF8&qid=1329936481&sr=8-1)

---

### Post by sudodus on 2012-02-22
There is a built-in manual, but I suggest that you browse the internet for ***octave tutorial***

---

### Post by Aielyn on 2012-03-01
> **PGScooter said:**
> If .configure doesn't finish properly there's no point in running make, in my opinion.
Is there a reason you're compiling from source?

Why not:
sudo apt-get install octave3.2
?
or whichever version 11.10 has (if you're not sure, type octave and then [tab] [tab] and you will see on the list).

Octave on Ubuntu, for some unknown reason, seems stuck in 3.2 (even in Precise), despite the fact that Octave is up to 3.6.1, now. That's probably a good reason for compiling from source. In fact, I've just spent some time trying to find some sort of ubuntu deb to install it using, and have yet to find any - the most up-to-date I can find is 3.2.4-12 (the Ubuntu repositories has 3.2.4-11). Meanwhile, debian, fedora, and suse all have 3.6.1 already, as does arch (it has been less than two weeks since 3.6.1 released)... and 3.4.0 released over a year ago, so you can't even argue that Ubuntu had the most up-to-date version for 11.04, let alone 11.10.

And as I said, it looks like, even in Precise, all we'll be getting is Octave 3.2.4, yet again.

On that point, who should I be contacting about this absurdity? This isn't just a minor issue, because functionality is really quite important when you're developing code to solve mathematical problems.

---

### Post by Swiss_Knight on 2012-03-17
Hi there,

I am also an Octave user, and I would [COLOR=SeaGreen]_**really**_[/COLOR] appreciate that the latest version (3.6.1) is taken into account for Lucid, even through backports. :D

It's a mess to compile for new users... I'm ok with that, but I advised some people to use some of my scripts and if they want to install Octave, it would be really great to have an easy way to do it. :cool:

If some of the octave dev team are aware about that... ;)

Cheers.
Swiss.

---

### Post by PGScooter on 2012-03-17
Is there no Octave PPA? I think you would have more luck trying to convince someone to make a PPA.

---

### Post by HasanYavuzOZDERYA on 2012-03-20
Hi I had the same problem and after installing "gfortran" package I have managed to compile octave 3.6.1. "INSTALL.OCTAVE" file inside of the source package, contains a list of necessary tools/libraries to compile. I had missed the fortran compiler :)

---

### Post by userdce on 2012-04-09
Updated Octave binaries:

[http://octave.org/wiki/index.php?title=Octave_for_GNU_Linux:_Binary_Octave_packages_for_GNU_Linux](http://octave.org/wiki/index.php?title=Octave_for_GNU_Linux:_Binary_Octave_packages_for_GNU_Linux)

---

### Post by userdce on 2012-04-10
Here is PPA also
[https://launchpad.net/~picaso/+archive/octave](https://launchpad.net/~picaso/+archive/octave)

---

### Post by PC_load_letter on 2012-05-30
This is AWESOME! I was trying to compile from source and I was hit by:
```
configure: error: A BLAS library was detected but found incompatible with your Fortran 77 compiler settings.
```

I posted the output from ./configure on the Octave forum before I saw this thread here. Many thanks.

---

### Post by mju.cat on 2012-07-29
Hi all,
I'm an ubuntu newbie who's trying to get some matlab code to run in octave, but I keep running into problems with installing the latest version (Octave 3.6). I'm running 12.04 Precise and I installed it after running 

apt-add-repository -y ppa:picaso/octave

Whenever I try to install packages for octave I get an error which says:
'make: mkoctfile not found'

After a little google-ing, I learnt that I'm supposed to install headers - the only problem is I was unable to find explicit instructions on how to do this for Octave 3.6!

simply typing in
sudo apt-get install octave-devel
or
sudo apt-get install octave3.6-headers

doesn't work at all. It simply returns an "unable to find package".



I'm pretty desperate to get this to work - I need the xlswrite function (>=Octave3.4) so I can't use Octave3.2 which seems to work on 12.04. 
Any help on getting mkoctfile to work would be really appreciated!

---

### Post by PGScooter on 2012-07-30
Hi mju.cat,

A good way to solve "<file> could not be found" problems is to install the program apt-file:
```

sudo apt-get install apt-file
apt-file find mkoctfile

```

For me this gave back
octave3.2-common
and
octave3.2-headers

But I see that you don't want version 3.2. Maybe this will find a package with an updated version of that file for you because you have the ppa (apt-file searches through all of your repos). Then after you find the package, install it.

Please post back if you find an answer. Good luck!

---

### Post by hackTHEgibson on 2012-08-08
> **mju.cat said:**
> 
Whenever I try to install packages for octave I get an error which says:
'make: mkoctfile not found'



Sounds like you need to install the liboctave-dev.  
```
sudo apt-get install liboctave-dev
```

xlswrite is part of the io package so you need to get the source if you don't already have it.
[http://octave.sourceforge.net/io/index.html]("http://octave.sourceforge.net/io/index.html")

After downloading you can compile it in octave with.
```
sudo octave
```
**The following commands must be executed inside a rooted octave.**  

Also your octave working directory must be the one with the io tarball. To check working directory type **pwd** you will get something like **ans = /home/user**  Then **cd** into io directory if not already there.
Next.
```
pkg install io-1.0.18.tar.gz -auto
```

The -auto modifier, tells the package manager to load that specific package when octave starts.

---

### Post by hackTHEgibson on 2012-08-16
Hi mju.cat,

There is a tutorial on this at [http://embeddedprogrammer.blogspot.com/2012/06/ubuntu-tip-02-octave-361-in-ubuntu-1204.html]("http://embeddedprogrammer.blogspot.com/2012/06/ubuntu-tip-02-octave-361-in-ubuntu-1204.html")

Also another way of doing this is in Synaptic.

First sort by Origin.  Then click on the appropriate PPA. Now you can easily see which files, from that PPA, you have installed and which ones you don't.

[IMG]http://en.zimagez.com/miniature/synapticpackagemanager001.png[/IMG]

---

### Post by OldNovice on 2012-10-27
I'm just a beginner, but this seems to be what you want:

[http://embeddedprogrammer.blogspot.ie/2012/06/ubuntu-tip-02-octave-361-in-ubuntu-1204.html](http://embeddedprogrammer.blogspot.ie/2012/06/ubuntu-tip-02-octave-361-in-ubuntu-1204.html)

I'm just trying it out now, having been assured by forum member
danielbauwens that this source is kosher.  It seems to run just fine.

By the way, the nice graphical interface QtOctave seems to have been abandoned
by its developer, and cannot be used with octave versions beyond 3.2.  
If you install it using sudo apt-get, it will uninstall Octave and reinstall Octave 3.2

---

### Post by mJayk on 2012-11-10
Anybody tried QToctave its good if your used to matlab or trying to learn octave

---

