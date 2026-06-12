---
title: "CVS Cedega"
date: 2005-10-02
forum: Gaming &amp; Leisure
---

### Post by L1nVx on 2005-10-02
Hey i'm trying to install cvs cedega but i get a make in error problem.. here's the error does anyone know whats' wrong and what i need to do... ??

Also how do i exit x server so i can update my nvidia drivers??

List of profiles (b to go back):

0 ) cvscedega_head
Enter choice:
0


Running Profile : cvscedega_head
/home/kmalik/.WineCVS/sources/cvscedega/wine



List of profiles (b to go back):

0 ) cvscedega_head
Enter choice:
0


Running Profile : cvscedega_head
/home/kmalik/.WineCVS/sources/cvscedega/wine













WineCVS.sh - Progress(u) : Green is current

0 = Uninstall
1 = Cleanup
2 = CVS checkout
3 = Configure
4 = Make depend
5 = Make
6 = Make install
7 = Finish up

-------------------------------------------

Compiling ...




--------- Error log - file /home/kmalik/.WineCVS/sources/cvscedega/ErrorLog : ---------
make[1]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools'
make[2]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/wrc'
gcc -MMD -c -I. -I. -I../../include -I../../include -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools'make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)











WineCVS.sh - Progress(u) : Green is current

0 = Uninstall
1 = Cleanup
2 = CVS checkout
3 = Configure
4 = Make depend
5 = Make
6 = Make install
7 = Finish up

-------------------------------------------

Compiling ...




--------- Error log - file /home/kmalik/.WineCVS/sources/cvscedega/ErrorLog : ---------
make[1]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools'
make[2]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Entering directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/wrc'
gcc -MMD -c -I. -I. -I../../include -I../../include -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/kmalik/.WineCVS/sources/cvscedega/winex/tools'make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

---

### Post by DJ_Max on 2005-10-02
To be brief, there could be nothing wrong on your end. You're using a CVS version, which will not be stable, and sometimes, developers will leave the CVS version in an unusuable condition. I don't see anything that leads me to believe there is a problem on your end.

---

### Post by L1nVx on 2005-10-02
Okay, But only reason i am hesitant to use cedega real is becuase what if the games i want don't work or upcoming games don't work (obviously it wqould take them time to get them to work but what if they never do) and as well isn't it a monthly payment...? I still use windows but am looking at linux and one thing i do is gaming... not VERY heavy but yea. lol.  I know i could use windows instead of linux but i wanted to try this...

---

### Post by DJ_Max on 2005-10-02
I understand where you're coming from. I myself have never used Cedega, as I rarely play games. Anyway, there's a list of games [http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/) and their status with Cedega.

---

### Post by L1nVx on 2005-10-02
Yea i've seen that list but for the new games coming out (for example games like oblivion , civ 4) etc. etc. you never know if they'll work for cedega or not and... with paying monthly i'd only pay the minimum and i'd then not get updates i believed which might mean i can't play those anyways


either way i got cvs cedega but...
 idk how to run it the tutorial on linux-gamers.net says to test do someting like cvscedega War3.exe obviously changing War3.exe to whatever your trying to run... but were do i do this i typed this in terminal and it said command not found... i downloaded steam.exe to test.

---

### Post by L1nVx on 2005-10-03
Installing launcher script ...
Packing sourcetree...
All done ... CVS installed

Installed as: cvscedega
Config path : <homedir>/.cvscedega

This is what it says... then i try cvscedega and it says command not found... it's installed it says it is!

---

### Post by L1nVx on 2005-10-04
Can anyone help please i'm so stumped.

---

### Post by katu on 2005-10-04
How did you get it to compile?

---

### Post by L1nVx on 2005-10-04
sh WineCVS.sh

then i followed instructions and it installed itself

---

### Post by L1nVx on 2005-10-04
But even though it installed itself it's not running!

---

### Post by katu on 2005-10-05
Try:
```

sudo updatedb
locate cvscedega

```
hopefully this will give a location where the script was installed.
if it is in a directory where the path is not set (and that's probably the case) you can either set the path temporarily to that dir (bash):
```

export PATH=$PATH:directory/where/the/script/is
cvscedega
```
or run it from there:
```
directory/where/the/script/is/cvscedega
```
note: the PATH setting is only temporary and in the terminal where you set it.

you can also try a:
```
ls .cvscedega
```
it's a "hidden" directory. The names of these start with a dot. You can look there for executables probably...


When I tried compiling it myself and got the error you did before. I tinkered around with different versions with weird effects. It turns out though that if you have an ATI card, (which I do), you're basically not going to get acceleration. So I sort of gave up on the idea...

hope this helps.

---

### Post by L1nVx on 2005-10-05
Heh well i was having trouble with grub and stuff so i just rewiped comp and put back Windows (as i NEED my games) and don't have linux on here ATM .... so idk if i should try to grub again (i reintsaleld ubuntu when grub was on and it messed all up) and well ... i'm sure if i install ubuntu i'd be fine as long as i don't reinstall like i did... i'd rather not be burdened but i want to try cedega heh... it's a tough choice... :-/ if a game asy Baldurs Gate is installed on your WINDOWS partition can you use cedega (if windows is mounted) and run that exe offa that partition??

---

### Post by DjKritical on 2005-10-13
I'm having the same problem,

I had to install heaps of packages to do this

gcc
build-essential
bison
flex

Then I got this error message

I guess I need more packages?... Anyone know what else we need to install?

:cool:

---

### Post by MemoryDump on 2005-10-17
has anybody been able to get around the compiling error in the first post using winexCVS.sh ? is it really a ATI card issue?

thxs

---

### Post by tlindner on 2005-10-21
Got it to work.  The problem is that cedega doesn't compile under gcc 4.0

get WinCVS.sh from [http://winecvs.linux-gamers.net](http://winecvs.linux-gamers.net)

sudo apt-get install cvs gcc-3.4 build-essential bison flex xlibs-dev

if you had gcc 4.0 installed, you probably need to do this
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

WineCVS.sh


.. and for the guy up there where he can't find where it installed... check you home/bin directory

---

### Post by jollygreen on 2005-10-22
after it finally compiled i simply typed in cvswine and it works don't know how to install the games but it went thru and finshed the defualt setups

---

### Post by katu on 2005-10-24
[QUOTE=MemoryDump] is it really a ATI card issue?
[/QUOTE]

That's not what I meant. The compile error is surely not an ATI related thing.  
I just gave up trying to install, because it seems, that even if you do install it, it won't work very well with an ATI card.  

[QUOTE=tlindner]
If you had gcc 4.0 installed, you probably need to do this
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
[/QUOTE]

I would say that deleting one file from a package like this can be potentially damaging to your system! 
if you must, rename it like this:
```

mv /usr/bin/gcc /usr.bin/gcc.old

``` and remember where it is if you want to change back later. 

A better idea is:
```

apt-get remove gcc 

```
and then with the link. 

But both of these should be unnecessary. It's usually possible to change the compiler in the Makefile of the compiled program. I'll see how to do this when I get home just for the fun of it.
cheers,
Katu

---

### Post by katu on 2005-10-24
to use gcc-3.4 as the compiler all you need to do is set the environmental variable CC. This usually specifies the default compiler. So, after having installed gcc-3.4 and all the other needed packages, one should do:
```
export CC=gcc-3.4
sh WineCVS.sh

```
I used the second profile (cedega with needed root privileges). This unfortunately asks for the root password. I have a root user on my machine so this was no problem, anyone would like to try maybe 
**sudo sh WineCVS.sh ** and post here? Anyway in my case everything compiled ok. 

note 1: This is of course for breezy. Hoary should work ok.
note 2: Once again I strongly advise against deleting your gcc. 
cheers, 
Katu

---

### Post by tlindner on 2005-10-25
You guys are right.  Sorry I was really just doing it as a hack to see if that would have fixed it.  I didnt realize simply changing the CC var would have done it.   Thanks for the follow ups!

---

### Post by npodges on 2005-10-25
I've been trying the same exact thing. it seems a lot of people were able to fix it by merely changing the cc variable.. that's not working for me though. i'm still getting:
```
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/nick/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/nick/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2

```

Any ideas from the people who *have* gotten it to work?

---

### Post by tlindner on 2005-10-25
silly question, but did you say the cc or CC variable?

---

### Post by npodges on 2005-10-25
CC

update: mine might be working now, i'll update if it does.

---

### Post by npodges on 2005-10-25
Okay it did work afterall.
it comes down to this: as well as setting CC to gcc3.4, you also have to start over the installation process. when using WineCVS.sh, it resumes from step 5, i believe (make). if you've already done that once, and it didnt work, set CC="gcc-3.4" (after installing gcc-3.4 that is) and then when it asks you 
```
  g) Get a profile from http://winecvs.linux-gamers.net/WineCVS
  c) Change command line action
  r) Run existing profile

``` 

click c for the command line.

then, hit 's' for start all over, and do just that. worked fine for me, let me know if it works for you.
gl,
nick

---

### Post by LuckyProphet on 2007-06-25
Hi,

I did google quite a while in regards to CVSCedega and Ubuntu and if I am not mistaken nobody with Feisty Fawn got it compiled and working, or?

Why is it running with other distros, but not with Ubuntu? I am still new to Linux, but I am certain that there are some "cracks" out there which have a clue about this.

Thanks in advance
... LuckyMe

---

### Post by handy on 2007-06-25
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=193814&highlight=patrick295767](http://ubuntuforums.org/showthread.php?t=193814&highlight=patrick295767)

It may be what you need.

---

