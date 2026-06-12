---
title: "Maxima problems"
date: 2006-10-18
forum: Education &amp; Science
---

### Post by danbert on 2006-10-18
I installed maxima and wxmaxima from synaptic to use it as a Maple alternative on my computer.  When I try to execute any command from wxmaxima, I get the error message:

CLIENT: Lost socket connection ...
Restart maxima with 'Maxima->Restart maxima'.

However, using that command doesn't fix the problem, nor did restarting wxmaxima, nor reinstallation via synaptic, nor rebooting.

Any other suggestions on how to fix this?  Because I really hate Maple with a passion.

---

### Post by mzilhao on 2006-10-18
here:
[https://help.ubuntu.com/community/wxMaxima](https://help.ubuntu.com/community/wxMaxima)

---

### Post by danbert on 2006-10-18
I followed those steps and during the installation of wxMaxima I get the error:

xml2 must be installed on your system
but xml2-config script couldn't be found.

Yet, I have xml2 installed and I have no idea how to tell it where the config script is located.  Any suggestions?

---

### Post by LaserJock on 2006-10-18
If you can wait for a bit we should have a fix in dapper-updates soon. We are waiting for final approval to upload new gcl and maxima packages. It's been a long ordeal to get this fixed but we are almost there. Edgy's version is already fixed. Also the command line version, maxima, works fine.

-LaserJock

---

### Post by mzilhao on 2006-10-19
try installing libxml2 and libxml2-dev...

---

### Post by danbert on 2006-10-24
Not an issue anymore.  Upgraded to edgy, and wxmaxima works great installed from synaptic.

---

### Post by sagibson on 2007-01-07
> **LaserJock said:**
> If you can wait for a bit we should have a fix in dapper-updates soon. We are waiting for final approval to upload new gcl and maxima packages. It's been a long ordeal to get this fixed but we are almost there. Edgy's version is already fixed. Also the command line version, maxima, works fine.

-LaserJock

Is there an update on the wxMaxima fix for dapper?

---

### Post by LaserJock on 2007-01-07
> **sagibson said:**
> Is there an update on the wxMaxima fix for dapper?

Yes, both gcl and maxima (rebuilt with the updates gcl) have updates in the dapper-updates repository that should fix this bug.

-LaserJock

---

### Post by boz on 2007-01-09
I installed gcl, maxima, and wxmaxima but wxmaxima still does not work.  I have the dapper-updates repository in my sources.list file but I don't see an update for gcl or maxima.  I executed sudo apt-get update and sudo apt-get upgrade.

---

### Post by LaserJock on 2007-01-10
> **boz said:**
> I installed gcl, maxima, and wxmaxima but wxmaxima still does not work.  I have the dapper-updates repository in my sources.list file but I don't see an update for gcl or maxima.  I executed sudo apt-get update and sudo apt-get upgrade.

What version of gcl and maxima do you have installed? dpkg -l | grep gcl and dpkg -l | grep maxima should give you the versions.

-LaserJock

---

### Post by boz on 2007-01-13
```

boz@xxxxxxx:~$ dpkg -l | grep gcl
ii  gcl                                    2.6.7-14ubuntu2    GNU Common Lisp compiler
boz@xxxxxxx:~$ dpkg -l | grep maxima
ii  maxima                                 5.9.2-2ubuntu3    A fairly complete computer algebra system--
ii  maxima-doc                             5.9.2-2ubuntu3    A fairly complete computer algebra system--
ii  wxmaxima                               0.6.4-1ubuntu1    a wxWidgets GUI for the computer algebra sys

```

---

### Post by jpkotta on 2007-01-13
I just found this thread.  Thanks guys!  I had built maxima to work with cmucl as recommended by some other article/thread for a work around.  It's nice to have it work straight from official repos.

> boz@xxxxxxx:~$ dpkg -l | grep gcl
ii  gcl                                    2.6.7-14ubuntu2    GNU Common Lisp compiler
boz@xxxxxxx:~$ dpkg -l | grep maxima
ii  maxima                                 5.9.2-2ubuntu3    A fairly complete computer algebra system--
ii  maxima-doc                             5.9.2-2ubuntu3    A fairly complete computer algebra system--
ii  wxmaxima                               0.6.4-1ubuntu1    a wxWidgets GUI for the computer algebra sys

I did not have to install gcl.  Doing a search with dpkg says it has never been installed (because if i purge/remove it, it always says so, I think).  I had cmucl installed before, but i removed that.

```
[jpkotta@euler ~](0)$ dpkg -l *cmucl*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
rc  cmucl                    19a-release-20040728-9   The CMUCL lisp compiler and development system
un  cmucl-docs               <none>                   (no description available)
un  cmucl-normal             <none>                   (no description available)
un  cmucl-safe               <none>                   (no description available)
un  cmucl-small              <none>                   (no description available)
un  cmucl-source             <none>                   (no description available)

[jpkotta@euler ~](0)$ dpkg -l *gcl*
No packages found matching *gcl*.

```

It seems like you don't need gcl to get maxima to work.

---

### Post by LaserJock on 2007-01-14
> **boz said:**
> ```

boz@xxxxxxx:~$ dpkg -l | grep gcl
ii  gcl                                    2.6.7-14ubuntu2    GNU Common Lisp compiler
boz@xxxxxxx:~$ dpkg -l | grep maxima
ii  maxima                                 5.9.2-2ubuntu3    A fairly complete computer algebra system--
ii  maxima-doc                             5.9.2-2ubuntu3    A fairly complete computer algebra system--
ii  wxmaxima                               0.6.4-1ubuntu1    a wxWidgets GUI for the computer algebra sys

```

That should be right. I'm really not sure why you are having problems. What exactly isn't working? What errors are you getting? Is this on ppc?

-LaserJock

---

### Post by boz on 2007-01-14
```

wxmaxima: Symbol `_ZTV7wxTimer' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV6wxMenu' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV16wxScrolledWindow' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxListBase' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV9wxProcess' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV8wxObject' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxClientDC' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxMenuBase' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV14wxBitmapButton' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV13wxJPEGHandler' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV7wxFrame' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV8wxButton' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV8wxBitmap' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV12wxPNGHandler' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV6wxFont' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV6wxIcon' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxSpinCtrl' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxCheckBox' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV10wxComboBox' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV14wxImageHandler' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV9wxControl' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV16wxTopLevelWindow' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV12wxXPMHandler' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV7wxPanel' has different size in shared object, consider re-linking
wxmaxima: Symbol `_ZTV8wxColour' has different size in shared object, consider re-linking
wxmaxima: relocation error: wxmaxima: symbol _Z31_wx_link_dummy_func_gnome_printv, version WXU_2.6 not defined in file libwx_gtk2u_core-2.6.so.0 with link time reference

```

My configuration is i386 ubuntu 6.06 32-bit.

---

### Post by yigal.weinstein on 2007-01-28
I have easily and successfully built maxima 5.11 and wxmaxima 7.1 for i686 32bit system i.e. my own, with checkinstall and the required dev packages which are in the Ubuntu repositories.  They both work perfectly without hitch.  I am however using Edgy so I don't know if I can help you.  If you would like to proceed this way I am more than willing to help you.

Note Maxima built with cmucl has had some errors in calculations that are lisp flavor specific.
To use gcl simply install gcl and
```
$sudo dpkg-reconfigure gcl
```

which will let you reconfigure with ansi enabled - which is what is required to build Maxima with gcl.  Gcl seems to have the least problems - I only know this from reading a lot of the Maxima mailing list.

---

### Post by boz on 2007-01-30
Thanks.  The source build with gcl enabled works great.

---

### Post by pvdg on 2007-03-15
I'm having a new(?) problem, this time with maxima help:
```

paulo@tecra:~$ maxima
Maxima restarted.
(%i1) describe(plot2d);
/tmp/gazonk_12026_0.c:174:18: error: math.h: No such file or directory
/tmp/gazonk_12026_0.c:262:20: error: setjmp.h: No such file or directory
/tmp/gazonk_12026_0.c:263:19: error: stdio.h: No such file or directory
/tmp/gazonk_12026_0.c:850: error: syntax error before ‘FILE’
/tmp/gazonk_12026_0.c:860: error: syntax error before ‘}’ token
/tmp/gazonk_12026_0.c:1036: error: field ‘sm’ has incomplete type
/tmp/gazonk_12026_0.c:1616: error: syntax error before ‘jmp_buf’
/tmp/gazonk_12026_0.c:1623: error: syntax error before ‘}’ token
/tmp/gazonk_12026_0.c:1977: error: syntax error before ‘size_t’
/tmp/gazonk_12026_0.c:2153: error: syntax error before ‘*’ token
/tmp/gazonk_12026_0.c:3237:20: error: stdlib.h: No such file or directory
/tmp/gazonk_12026_0.c:3495: error: syntax error before ‘size_t’
/tmp/gazonk_12026_0.c:3495: error: syntax error before ‘)’ token
/tmp/gazonk_12026_0.c:3712: error: syntax error before ‘*’ token
/tmp/gazonk_12026_0.c:3852:20: error: unistd.h: No such file or directory
/tmp/gazonk_12026_0.c:3894: error: syntax error before ‘*’ token
/tmp/gazonk_12026_0.c:3895: error: syntax error before ‘*’ token
/tmp/gazonk_12026_0.c:3896: error: syntax error before ‘*’ token
/tmp/gazonk_12026_0.c:4054: error: syntax error before ‘*’ token
/tmp/gazonk_12026_0.c:4141: error: syntax error before ‘*’ token

Maxima encountered a Lisp error:

 (SYSTEM "gcc -c -Wall -DVOL=volatile -fsigned-char -pipe  -I/usr/lib/gcl-2.6.7/unixport/../h  -O -c \"/tmp/gazonk_12026_0.c\" -o \"/tmp/gazonk_12026_0.o\" -w") returned a non-zero value 0.

Automatically continuing.
To reenable the Lisp debugger set *debugger-hook* to nil.
(%i2) ? plot2d;
/tmp/gazonk_12026_1.c:174:18: error: math.h: No such file or directory
/tmp/gazonk_12026_1.c:262:20: error: setjmp.h: No such file or directory
/tmp/gazonk_12026_1.c:263:19: error: stdio.h: No such file or directory
/tmp/gazonk_12026_1.c:850: error: syntax error before ‘FILE’
/tmp/gazonk_12026_1.c:860: error: syntax error before ‘}’ token
/tmp/gazonk_12026_1.c:1036: error: field ‘sm’ has incomplete type
/tmp/gazonk_12026_1.c:1616: error: syntax error before ‘jmp_buf’
/tmp/gazonk_12026_1.c:1623: error: syntax error before ‘}’ token
/tmp/gazonk_12026_1.c:1977: error: syntax error before ‘size_t’
/tmp/gazonk_12026_1.c:2153: error: syntax error before ‘*’ token
/tmp/gazonk_12026_1.c:3237:20: error: stdlib.h: No such file or directory
/tmp/gazonk_12026_1.c:3495: error: syntax error before ‘size_t’
/tmp/gazonk_12026_1.c:3495: error: syntax error before ‘)’ token
/tmp/gazonk_12026_1.c:3712: error: syntax error before ‘*’ token
/tmp/gazonk_12026_1.c:3852:20: error: unistd.h: No such file or directory
/tmp/gazonk_12026_1.c:3894: error: syntax error before ‘*’ token
/tmp/gazonk_12026_1.c:3895: error: syntax error before ‘*’ token
/tmp/gazonk_12026_1.c:3896: error: syntax error before ‘*’ token
/tmp/gazonk_12026_1.c:4054: error: syntax error before ‘*’ token
/tmp/gazonk_12026_1.c:4141: error: syntax error before ‘*’ token

Maxima encountered a Lisp error:

 (SYSTEM "gcc -c -Wall -DVOL=volatile -fsigned-char -pipe  -I/usr/lib/gcl-2.6.7/unixport/../h  -O -c \"/tmp/gazonk_12026_1.c\" -o \"/tmp/gazonk_12026_1.o\" -w") returned a non-zero value 0.

Automatically continuing.
To reenable the Lisp debugger set *debugger-hook* to nil.
(%i3)

```

Has this happened to anyone else? Any ideas? I have tried reinstalling all the maxima packages and the problem remains. Here are the versions I'm running:

Ubuntu 6.06.1, kernel 2.6.15-28-686 

```
paulo@tecra:~$ dpkg -l | grep maxima
ii  maxima                            5.9.2-2ubuntu3  A fairly complete computer algebra system--
ii  maxima-doc                        5.9.2-2ubuntu3  A fairly complete computer algebra system--
ii  maxima-emacs                      5.9.2-2ubuntu3  A fairly complete computer algebra system--
ii  maxima-share                      5.9.2-2ubuntu3  A fairly complete computer algebra system--
ii  maxima-src                        5.9.2-2ubuntu3  A fairly complete computer algebra system--
ii  maxima-test                       5.9.2-2ubuntu3  A fairly complete computer algebra system--
ii  xmaxima                           5.9.2-2ubuntu3  A fairly complete computer algebra system--
paulo@tecra:~$ dpkg -l | grep gcl
ii  gcl                               2.6.7-14ubuntu2

```

Thanks for any help.

---

### Post by yigal.weinstein on 2007-03-15
I would say the only problem is that you are using Ubuntu's package for Maxima.  Build your own.  You will be happier.  I don't say this about many other packages but Maxima is a package that is really quite easy to build and then you will have the latest version 5.11, which has some bug fixes of a more mathematical nature.

---

### Post by pvdg on 2007-03-15
Thank you for the advice, yigal.weinstein. One of these days I'll take a deep breath and try it. Are there any instructions or howtos on installing maxima from source? I haven't had much experience with it...
I have meanwhile tried running maxima in another computer with exactly the same OS, kernel and package versions to find that the problem doesn't show! There must be something wrong with the configuration in this particular computer, and I must try to solve it as I can't even be sure it wouldn't affect the built 5.11 version.

---

### Post by yigal.weinstein on 2007-03-15
pvdg.  The steps are simple although there are a few of them,

_In web browser_
1. download the package maxima-5.11.0.tar.gz by going to here,
[http://sourceforge.net/project/showfiles.php?group_id=4933]("http://sourceforge.net/project/showfiles.php?group_id=4933")

and clicking on maxima-5.11.0.tar.gz 

_In terminal_
2. ```
tar xfvz /"locationof"/maxima-5.11.0.tar.gz
```

3. ```
sudo aptitude install build-essential gcl checkinstall
```
(I am not sure I think these are the packages you need to compile it)

4. ```
sudo dpkg-reconfigure gcl
```

you need to enable ansi which is disabled by default.

5. ```
cd maxima-5.11.0/
```

6. ```
./configure --prefix=/usr/share --exec-prefix=/usr 
```

7. ```
make
```

8. ```
sudo checkinstall make install
```

9. say "yes" to create a document package and paste this (I don't remember the exact wording): 

Maxima is a system for the manipulation of symbolic and numerical expressions, including differentiation, integration, Taylor series, Laplace transforms, ordinary differential equations, systems of linear equations, polynomials, and sets, lists, vectors, matrices, and tensors. Maxima yields high precision numeric results by using exact fractions, arbitrary precision integers, and arbitrarily precision floating point numbers. Maxima can plot functions and data in two and three dimensions.

10. type 0 and enter your email address so that people know who you are if they use your package someone@somewhere as an example

11. hit return and tell me if you get any errors.  If it works it will install a Debian package of maxima 5.11 and you will have in the folder a maxima deb package that you should keep for later.  

Don't spend all day at it.  Just try this once if it works, great.  If it doesn't just post your errors.  I would give you my deb but it is built for Edgy.

---

### Post by pvdg on 2007-03-15
Thank you again! I will definitely try it and I'll let you know.

---

### Post by LaserJock on 2007-03-15
I'd just like to say, it'd be really helpful if people could file bug reports when they have issues with maxima (or any Ubuntu package for that matter). We've currently only got 2 open bugs for it and neither appear to be this issue.

From some digging I and another MOTU Science member did, it looks the the problem is that the describe() and ? functions, I assume those are the help, are trying to compile something and looking for libc6-dev (which has the headers it's looking for). Since that's not installed on a default Ubuntu machine it fails. Since libc6-dev is a dependency of build-essential when you go to build Maxima from source it gets installed along the way. So I think the issue is not whether you build it from source or not, but if you have libc6-dev present or not. This is a strange problem that I can't find reported in either Ubuntu or Debian and it doesn't seem to happen on Edgy or Feisty.

So please file bugs when you get errors, we'll try to have a look at the as timely as we can (we are all volunteers so sometimes things like school and work interfere). The URL for filing a bug on maxima is [https://launchpad.net/ubuntu/+source/maxima/+filebug](https://launchpad.net/ubuntu/+source/maxima/+filebug) .

-LaserJock

---

### Post by pvdg on 2007-03-15
> **LaserJock said:**
> 
From some digging I and another MOTU Science member did, it looks the the problem is that the describe() and ? functions, I assume those are the help, are trying to compile something and looking for libc6-dev (which has the headers it's looking for). Since that's not installed on a default Ubuntu machine it fails. Since libc6-dev is a dependency of build-essential when you go to build Maxima from source it gets installed along the way. So I think the issue is not whether you build it from source or not, but if you have libc6-dev present or not. This is a strange problem that I can't find reported in either Ubuntu or Debian and it doesn't seem to happen on Edgy or Feisty.


You are absolutely right. This was the only difference between my two computers: one of them had libc6-dev installed, the other didn't. After installing libc6-dev describe() and ? work normally.

> **LaserJock said:**
> 
So please file bugs when you get errors, we'll try to have a look at the as timely as we can (we are all volunteers so sometimes things like school and work interfere). The URL for filing a bug on maxima is [https://launchpad.net/ubuntu/+source/maxima/+filebug](https://launchpad.net/ubuntu/+source/maxima/+filebug) .


Bug filed: [https://launchpad.net/ubuntu/+source/maxima/+bug/92710](https://launchpad.net/ubuntu/+source/maxima/+bug/92710).

---

### Post by yigal.weinstein on 2007-03-15
I posted a "bug" feature request use 5.11 rather than 5.9.2 in Launchpad.  It has more features and is more stable.

---

### Post by wgrant on 2007-03-16
> **yigal.weinstein said:**
> I posted a "bug" feature request use 5.11 rather than 5.9.2 in Launchpad.  It has more features and is more stable.

As I responded in aforementioned bug report, we currently have 5.10 in Feisty, and that's unlikely to change without a very good reason.

---

### Post by yigal.weinstein on 2007-03-16
No problem here.

It is a very easy program to install however and like I responded to your response in Launchpad Feisty+1 should have the latest Maxima as it really is not difficult to build.

---

### Post by wgrant on 2007-03-16
This is where it would be nice to have the fora integrated into Launchpad. There's a lot of duplication between this thread and the bug. :(

---

### Post by yigal.weinstein on 2007-03-16
I agree.  I imagine for storing code etc. Launchpad is better and for software discussions the forums are superior but they are not so different and a joint system might be ideal.

---

### Post by pvdg on 2007-03-20
> **yigal.weinstein said:**
> pvdg.  The steps are simple although there are a few of them,


Hi, yigal.weinstein. Although I solved the previous problem by installing libc6-dev, I decided to compile from source followind your instructions, apparently with full success. Maxima 5.11 is now running in my computer. I also found these instructions (in Spanish) [http://jpromerobx.blogspot.com/2007/02/guia-prctica-para-la-compilacin-e.html](http://jpromerobx.blogspot.com/2007/02/guia-prctica-para-la-compilacin-e.html) which might be useful to someone.
I suggest you polish your instructions, turn them into a HowTo and post them in the ubuntu forum or elsewhere. Just a few minor notes:

I didn't follow your instructions on 6:

6. > ```
./configure --prefix=/usr/share --exec-prefix=/usr 
```

and left the default folders instead. Is this bad?

I think 8. should just read

8. ```
sudo checkinstall 
```

At least that's what I did and the package was created and installed. No errors!

Thank you very much for your help and encouragement. As you said, it's quite simple and in my opinion a good choice for those of us who:

1. want to keep Ubuntu  Dapper LTS because of its stability instead of upgrading;

2. want the most recent version of Maxima;

3. are not afraid of the command line and would like to use one of the freedoms of free software.

---

### Post by yigal.weinstein on 2007-03-21
1. Thank you for pointing out that checkinstall is all that is needed and not checkinstall make install.  I started using checkinstall when one had to dictate to it what you wanted it to do.  Its defaults are pretty good now.

2. 
./configure --prefix=/usr/share --exec-prefix=/usr

is for Debian based distributions.  The default isn't very good and usually ends up meaning that the documentation package is not installed correctly and 2. that the application is installed in an unusual place - /usr/local, where Debian programs are not stored.

3. I made the wiki : [https://help.ubuntu.com/community/Maxima]("https://help.ubuntu.com/community/Maxima") and I completely rewrote this wiki, because it had very bad problems [https://help.ubuntu.com/community/wxMaxima]("https://help.ubuntu.com/community/wxMaxima")

4. please check them out and tell me if I forgot something.  Thank you for suggesting that I make a wiki for maxima.

---

### Post by pvdg on 2007-03-22
Perhaps it would be useful to include the explicit reference to installing build-essential, gcl (included in the apt-get build-dep maxima?) and checkinstall in the wiki.

I haven't noticed any problems for installing in the /usr/local/ directory, but if I do, I'll reinstall using the prefixes you suggest. How do I check if the documentation is correctly installed? Meanwhile, I'll try to install wxmaxima by following the instructions on the wiki.

EDIT: Trying to install with the options

```
./configure --prefix=/usr/share --exec-prefix=/usr
```

in another machine resulted in having a /usr/share/share/ directory created. Also, in synaptic the program now appears as if installed from the 'universe' repository. Is this intended?

I would also like to enable the imaxima and emaxima modes in emacs. Any special care?

---

### Post by yigal.weinstein on 2007-03-22
Yes, it should be in the Universe category.  If one is trying to follow Debian scheme of package management, but for a single user it won't hurt to put applications in /usr/local.  For instance my Realplayer gold is in there. 

You have very valid points 

1. checkinstall should be explicitly declared as a package being used.
2. build-essential requires a lot of space to download so you are also right I should explicitly write down that it will be needed and must be installed.
3. I originally thought --prefix=/usr/share but this is obviously wrong and create /usr/share/share for both maxima and wxmaxima.  So --prefix=/usr .  This is awesome, points out what I don't know.  Sorry if this inconvenienced you in anyway.

Great! You have really helped me now, and hopefully this wiki will help others.

best

---

### Post by yigal.weinstein on 2007-03-22
I can't help you much to your question on {i,e}maxima Other than don't use emacs, I am a vim user :) - I am a vim user but I am joking about not using emacs.  No I used imaxima a long time ago, may be 2 years ago.  It was nice then but I was using Debian and had to install a whole bunch of tex .sty and .cls packages but I was using tetex not texlive.  With texlive and if imaxima has made any improvements you are probably about set.  

I remember reading in the Maxima mailing list that there _were_ a few bugs in imaxima so that it didn't behave so well, but it seems like a pretty good program.

---

### Post by pvdg on 2007-03-22
I have now rebuilt both maxima and wxmaxima (wxmaxima wasn't working properly) using the updated instructions (including the ./configure prefix options) in the wiki pages [https://help.ubuntu.com/community/Maxima](https://help.ubuntu.com/community/Maxima) and [https://help.ubuntu.com/community/wxMaxima](https://help.ubuntu.com/community/wxMaxima) and now everything appears to be working fine.

I've taken the liberty of editing the wiki to make a small correction to the wxmaxima wiki page, replacing 
```
sudo apt-get remove maxima maxima-doc wxmaxima
```
with
```
sudo apt-get remove maxima-doc wxmaxima
```
as the former would remove the newly installed maxima. Please correct me if I am wrong.

Thanks again to yigal.weinstein for creating these wiki pages. I'm sure they will be useful to someone else.

As to the maxima emacs modes, I'll find my way and post it here (and/or create a wiki page too).

---

### Post by yigal.weinstein on 2007-03-23
pvdg of course you are right about the wxMaxima wiki - thank you again.  
I encourage you to make a wiki page.  It was a great experience. best

---

### Post by jamaas on 2008-07-14
I'm trying to install maxima 5.15 on hardy and getting the following error from checkinstall, any clues?

Thanks

Jim


 /usr/bin/install -c 'rmaxima' '/usr/bin/rmaxima'
/usr/local/src/maxima-5.15.0/install-sh -d "/usr/lib/maxima/5.15.0/binary-clisp"
chmod: changing permissions of `/usr/lib/maxima/5.15.0/binary-clisp': No such file or directory
make[2]: *** [install-clisp] Error 1

---

### Post by egonskinny on 2010-09-28
I recently installed maxima using apt-get. 

It seemed to install fine. It has not problem opening. However when I use the solve function to solve for a system of equations it gives me the following error:


user-laptop:~$ solve([x+y=1,y=x^2],[x,y]);
bash: syntax error near unexpected token `[x+y=1,y=x^2],[x,y]'

Any suggestions?

---

### Post by pvdg on 2010-09-28
> **egonskinny said:**
> I recently installed maxima using apt-get. 

It seemed to install fine. It has not problem opening. However when I use the solve function to solve for a system of equations it gives me the following error:


user-laptop:~$ solve([x+y=1,y=x^2],[x,y]);
bash: syntax error near unexpected token `[x+y=1,y=x^2],[x,y]'

Any suggestions?
egonskinny, you must start maxima (by typing 'maxima' at the command line) before issuing maxima commands like 'solve'.

---

