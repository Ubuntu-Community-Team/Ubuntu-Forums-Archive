---
title: "ADSL -&gt; PPPOE = Failure = Big issue that needs attention"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Jh00 on 2006-03-13
Hi all.

In my [last thread]("http://www.ubuntuforums.org/showthread.php?t=143607"), it was clear that I was very disappointed by an issue related to  ubuntu. But nothing better than a day after the other, and this morning I remembered that I had a spare HD that I could use to test out ubuntu for the first time.

As my last desktop Linux experience was back in 1998, I wanted to try Ubuntu so I could recomend it for a friend that just bought his first computer. I was somehow convinced that Ubuntu would offer a better experience than what I faced back in my early linux days.

**Please, accept this comments as constructive commentary rather than flaming... :( **


First off, I downloaded Ubuntu 5.10 Live CD and, although everything was fine, I couldn't setup my PPPOE connection. So I decided to grab the Dapper Flight 4 release and install it into my spare HD.

** Coments about the Installation **

I was somehow disappointed by the install procedure, because not only it is extremely tedious and ugly, but I felt that my friend would be overwhelmed just by paying attention to the contents being installed (libX, libXX, libXX_Y etc.). Where is the "humanity to others" in that?

I think it would be a great idea to provide some "What to expect in Ubuntu" texts while the system is installing, or at least a tetris game so we can use the computer for something a bit more useful. 

Anyway, the install went smoothly and I couldn't wait to browse the internet...


** The Frustration Chain **

As soon as I logged in, I rushed to the PPPOE config, just to find none. Oh well, time to switch HD's so I can use windows and read online documentation.

I found [http://www.ubuntuguide.org/#rp-pppoe](http://www.ubuntuguide.org/#rp-pppoe) , where it is was suggested to grab the rp-pppoe packet. Unfortunatelly, the link provided there **doesn't work** so I google'd for it and got rp-pppoe-3.7.tar.gz instead. 

Then, I saved the .tar.gz file into a floppy, as well as the instructions that I cut and pasted from that URL.

Back in Ubuntu, I followed the instructions, but then I noticed that I forgot to copy the "Read How to refresh GNOME panel?" section of it. No problem, I can use the Help System in Ubuntu right? Wrong! There is no info abou it there.

Ok then, let's just restart the system and see what happens. There it is! The icon to RP-PPPOE just where it was supposed to be! Now we just click it and... and... nothing. Nothing happens.

Strange. Well, time to go to the console and see if something is broken. I cd /opt/rp-pppoe-3.7/  and read the README file. "Just type ./go and you are game". My friend wouldn't be able to do this, but I could give a little hand if this was the only probem. Let's see...

Ahh, the configure script is complaining that there is no compiler installed. I find it strange that gcc is not installed by default, since in the Linux world it is so usual to compile stuff. My friend, though, would never know about this.

Anyway, I launch the "Add programs" application and install GCC just fine. Let's try again...

```

julio@jh00:/opt/rp-pppoe-3.7$ sudo ./go
Password:
Running ./configure...
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
Oops!  It looks like ./configure failed.

```

OMG! The RedHat 5.0 nightmare is back again! Just the thing that pushed me away from Linux, the fact that I can't just install a simple program unless I tweak every compile script on the face of earth!

Anyway, I thought that maybe it was something related to gcc, so I remembered that back in my time, we used cc to compile things too. Can't find it in the cd though. "Ah heck, let's see what's wrong in this config.log file", I told myself:

(config file is in the end of this thread to preserve readability)


Obviously, by the huge ammount of useless information (at least for me) from the config.log, I can't find out what the problem is.


** Darn! I can't believe Ubuntu doesn't ship with a pppoe solution! **

No, I must be wrong. There MUST be something out-of-the-box to solve my pppoe problem. Let's look for it in the help section... Voilá! Ubuntu Desktop Guide has a section called "ADSL Modems", let's read what it says:

> 
All PPPOE and router-style ADSL modems are supported by Ubuntu (that use ethernet for the connections), and some USB ADSL modems are supported too. For router-style ADSL modems, just connect it up, configure the modem as per your ISPs instructions and configure networking in Ubuntu. For information on PPPOE modems see [ADSLPPoE]("https://wiki.ubuntu.com/ADSLPPPoE") on the Ubuntu wiki.


Now we just click the link and... WTF?! Page not found?! I can't believe it, the link points to [https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE) !!! How on earth can I connect to it if I'm just looking for information about connecting to the internet in the first place!??!

No wait, if there is a link in the ubuntu wiki, there must be something already installed that I'm missing. Ahhh, I do a "find pppoe" and actually find a binary called pppoeconf !!!

julio@jh00:/opt/rp-pppoe-3.7$ pppoeconf        #crossing my fingers

The application runs and detected my 2 eth cards! Nice! Now go, go find my ADSL... The progress bar slowly progresses, and when it reaches 100% some red text popups in the speed of light and disappear right before I can actually read it. I'm sure it is an error, but let's wait.

The app probes my 2 eth cards 2 times, and displays the misteryous error message in all tries. At the end, the app complains that it couldn't find the aggregator or something like that...

"I can't believe it...". Let's do a "man pppoeconf" and see if I'm missing something. Unfortunatelly, man pppoeconf yelds so much useful information that I decide to bang my head against the table.

Let's try pppoeconf --help ... OHH FINEEEE!!! Now pppoeconf found my new ethernet card named... "--help". I feel so depressed that I don't even think about shutting the system down properly, I just smash the power button and put back my Windows HD.

**Conclusion**

I just can't believe that Ubuntu doesn't ship with a reliable PPPOE solution, and that information about it must be get from the internet. I'm glad that I tried it first before handling a CD to my friend, because I know he isn't a geek and he would probably have a hell of a time trying to figure out what was going on.

The weird thing is that I saw so many applications being installed that I would never use (like Gimp, for example), and this tiny little rp-pppoe that SHOULD solve my pppoe problem was left behind (please note, I don't even know if rp-pppoe would actually work anymore). Why?

Anyway, If someone can help me with this problem, I'm still willing to give Ubuntu another shot. I really really like the concept of an open source OS and I know that it has some limitations, but I was frustrated to see that almost 10 years has passed since I first tried a Linux desktop and I was still facing the same problems.

I have lots of suggestions about things that could be changed to make Ubuntu more appealing for a new Linux user, and I wish I knew where to post them and if they would be read anyway.

Here goes my config.log as mentioned earlier:

> 
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.59.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = jh00
uname -m = i686
uname -r = 2.6.15-15-386
uname -s = Linux
uname -v = #1 PREEMPT Thu Feb 9 19:41:22 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/X11R6/bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1348: checking for gcc
configure:1364: found /usr/bin/gcc
configure:1374: result: gcc
configure:1618: checking for C compiler version
configure:1621: gcc --version </dev/null >&5
gcc (GCC) 4.0.3 20060212 (prerelease) (Ubuntu 4.0.2-9ubuntu1)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:1624: $? = 0
configure:1626: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 20060212 (prerelease) (Ubuntu 4.0.2-9ubuntu1)
configure:1629: $? = 0
configure:1631: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1634: $? = 1
configure:1657: checking for C compiler default output file name
configure:1660: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1663: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1702: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_prog_ac_ct_CC=gcc

## ----------------- ##
## Output variables. ##
## ----------------- ##

CC='gcc'
CFLAGS=''
CPP=''
CPPFLAGS=''
DEFS=''
ECHO=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
ID=''
INSTALL_DATA=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
LDFLAGS=''
LIBEVENT=''
LIBOBJS=''
LIBS=''
LIC_DEFINE=''
LIC_INCDIR=''
LIC_LIB=''
LIC_LIBDIR=''
LIC_MAKEFILE_INCLUDE=''
LINUX_KERNELMODE_PLUGIN=''
LTLIBOBJS=''
OBJEXT=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PPPD=''
PPPD_H=''
PPPD_INCDIR=''
PPPOE_RELAY=''
PPPOE_SERVER_DEPS=''
RANLIB=''
RDYNAMIC=''
SETSID=''
SHELL='/bin/sh'
TARGETS=''
WRAPPER=''
ac_ct_CC='gcc'
ac_ct_RANLIB=''
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${prefix}/share'
datadir_evaluated=''
exec_prefix='NONE'
host_alias=''
includedir='${prefix}/include'
infodir='${prefix}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""

configure: exit 77 


Cheers.
Jh00

---

### Post by Jh00 on 2006-03-13
Ops. My session timed out and I ended up pasting my original post in the Desktop Support forum. Maybe it would be better if a moderator could move this thread to the " Ubuntu 5.10 Support (GNOME)  " forum. 
Thanks.

---

### Post by planetcall on 2006-03-13
I second your suggestions. I am also having some bad experiences regarding pppoe. I am able to connect to adsl using pon dsl-provider but the connection drops very often. rp-pppoe does connect to the internet but I dont know why it doesnt allow any inbound connection.....no matter what configuration I opt for.
Also, I have very serious issue regarding Screen resolution. I never got 1152x864 resolution figured out. I tried all I could have. It is very frustrating indeed.
Ubuntu does need some more work on it. Hopefully dapper would take care of these two issues.

---

### Post by MichaelZ on 2006-03-13
Hello,

May be this could help:

[http://www.linuxhelp.net/guides/pppoe/]("http://www.linuxhelp.net/guides/pppoe/")
[http://www.linuxquestions.org/questions/showthread.php?t=276827&highlight=ADSL+PPPOE+ubuntu]("http://www.linuxquestions.org/questions/showthread.php?t=276827&highlight=ADSL+PPPOE+ubuntu")
[http://www.linuxquestions.org/questions/showthread.php?t=250172&highlight=ADSL+PPPOE+ubuntu]("http://www.linuxquestions.org/questions/showthread.php?t=250172&highlight=ADSL+PPPOE+ubuntu")
[http://www.linuxquestions.org/questions/showthread.php?t=373450&highlight=ADSL+PPPOE+ubuntu]("http://www.linuxquestions.org/questions/showthread.php?t=373450&highlight=ADSL+PPPOE+ubuntu")


Best wishes,
Michael

---

### Post by Jh00 on 2006-03-13
[QUOTE=planetcall]Hopefully dapper would take care of these two issues.[/QUOTE]

I don't think so because, as I said, I'm using Dapper Flight 4, and according to [this page]("http://www.ubuntu.com/testing/flight4"):

> 
Aside from a few exceptions such as GNOME 2.14 and Espresso, most of what is in Dapper now is what will be in the final release in April.



MichaelZ: Thanks for the links, however:

1st link -> as I said earlier, I can't compile rp-pppoe.
2nd link -> I don't want to mess with the kernel yet.
3rd and 4th links -> These two are somewhat cumbersome solutions and I'm a little intimidated by then... I can try it later, but I think it would be easier if I could just figure out why gcc isn't working with rp-pppoe sources.

Still waiting for a solution ...
Cheers!
Jh00

---

### Post by planetcall on 2006-03-14
for the compilation issue, you may install gcc-3.3-base  and gcc-4.0-base  It will solve your this problem for sure. It happened with me before.

---

### Post by Jh00 on 2006-03-14
For Christ's sake, someone help me please!

This is my last try... I've been for hours waiting for this thread to be replied and nobody seems to be interested... 

After LOTS of research, I finally found out that I'm the lucky owner of a 3Com HomeConnect ADSL Modem Dual Link, the only one that needs aditional parameters to work on PPPOE.

As said in [http://www.nzdsl.co.nz/howtos/3Com/3ComDualLink.html](http://www.nzdsl.co.nz/howtos/3Com/3ComDualLink.html) :

> 
4) Edit /etc/ppp/pppoe.conf and change:

LCP_INTERVAL=14 (if you don't do this it will hang up every 3-4 mins)
LCP_FAILURE=6
PPPOE_TIMEOUT=100
Uncomment the line saying PPPOE_EXTRA="-f 3c12:3c13 -S ISP" (**the 3com's use NON-RFC pppoe**)


I tried the Gentoo Live CD and after editing those settings, I was able to connect using rp-pppoe. The problem is: 
[SIZE="5"]I CAN'T COMPILE RP-PPPOE ON UBUNTU[/SIZE](see first post).

And there is no such option to change in pppoe-conf either!!!! That's why I get the timeouts in pppoe-conf.


Ah, you know what, to hell with linux, I'm fed up.

---

### Post by Jh00 on 2006-03-14
[SIZE="4"][COLOR="Red"]SOLUTION![/COLOR][/SIZE]

This post is for the sake of archiving, so that it can be useful to someone, as I doubt this thread will EVER be read by anyone from the dev team.

The compiling problem was due the lack of "lib6c-dev" and "make" packages. Why they didn't get installed along with gcc is beyond my comprehension (gcc wasn't installed by default either).  After installing those and tweaking the pppoe.conf file like I mentioned before, I finally got my ADSL working and I'm posting this from ubuntu.


I thank the few people who tried to help me (I really appreciated that), but I don't understand how this problem got overlooked by the rest of the community. By the ammount of compiling most of you have done already, this would be a piece of cake.

I was brought to the Ubuntu world because of 2 promises widely spread everywhere: that Ubuntu "just works"  and that Community support was one of the best and most responsive. 

However, I lost 2 days trying to figure out all by myself just how could I set my ADSL connection. That's too much. I feel cheated.

I'm going to sleep now. All my excitement is gone, and I doubt that by the morning Ubuntu will still be installed here.

Cheers, see you again in 10 more years. Keep up the good job.

Jh00

---

### Post by htinn on 2006-03-14
If you look at "gcc" it merely "suggests" make and "recommends" libc6-dev. I generally assume with something that important that a suggestion is the same as an outright command. ;)

---

### Post by SteveHoffmanUK on 2006-03-14
Jh00:

Your thread may never be read by the dev team, but others like me, who (like you) wish Linux and Ubuntu well, will read it and shake our heads in dismay. We would very much like a Linux that "just works" (as Windows does), but we seem to be a long way from achieving that. People like your friend (and I), who can't be bothered (or are incapable of trying) to go through what you have gone through, will stick firmly with M$. 

I am not an experienced Linux user, but, as I see it, the breakthrough for Linux must await a hardware manufacturer who will push a series of systems pre-installed with Linux and connectable to a range of Linux-friendly devices that will work straight away, without users needing to know the niceties of compilation, device mounting and all the procedures that need the intervention of terminal line input. 

Until then, Linux will continue to live in the land of those who love technical challenges. The rest of us (99%) will remain in Microsoftland, full of dodgy software, unexplainable glitches, insecure and accident-prone systems, but systems that don't require us to get our hands dirty. We have lives to get on with, in which computers are the means, not the end.

Actually, I will keep a foot in both camps. I recently installed Ubuntu on my somewhat ancient Dell laptop. Not only does it work, but last week I plugged my digital camera into its USB port, and Ubuntu actually recognised it immediately and downloaded my pix. I was thrilled, although really I should have taken it for granted. On that basis, I have bravely ordered a wireless Linux-friendly PCMCIA modem for it. Who knows, I may be surprised again.

Maybe you should return sooner than 10 years!

---

### Post by OffHand on 2006-03-14
So now it works you gonna re-install Windows again?

(Btw, I see were you are comming from but in Windows you have to configure and tweak stuff too before it works. I do agree though it is still too much for ordinary user.)

---

### Post by planetcall on 2006-03-16
Well said steve. Same applies here as well as to many other windows people trying to use linux.

---

### Post by index_0@ya.com on 2006-04-14
yep , 
Thr 's always a complexity in getting the pppoe connection in Ubuntu 

But did u take a note on how does fedora handles ? They have by default a diffrent interfaces to connect with pppoe connections and all types of connection which are UNIFIED to one gui dialog ( i think it 's under System -> networking ) 

Perhaps ubuntu can provide us one , to make internet  Connections hassle-free  

Will they ?

...

---

### Post by az on 2006-04-15
In Dapper(or any other version of ubuntu), you type

sudo pppoeconf

out-of-the-box.


[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
[https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

---

### Post by Reshin on 2006-05-06
FINALLY! IT WORKS!

Do ```
sudo echo "modprobe pcnet32 homepna=1" >> /etc/modprobe.d/pcnet32
``` and make sure that in /etc/networking/interfaces the three lines made by pppoeconf are AT the bottom :D

---

### Post by Jh00 on 2006-06-07
[QUOTE=Reshin]FINALLY! IT WORKS!

Do ```
sudo echo "modprobe pcnet32 homepna=1" >> /etc/modprobe.d/pcnet32
``` and make sure that in /etc/networking/interfaces the three lines made by pppoeconf are AT the bottom :D[/QUOTE]

Does this solution need Dapper? Because I only have ubuntu 5.10 here...

---

### Post by Jh00 on 2006-06-07
It didnt work either in 5.10 or 6.06.

The file pcnet32 doesn't even exist in that directory. Even if I create one, pppoeconf still time out. Since gcc isn't included in 6.06 either, I cant compile rs-pppoe. 


That's a big let down: I'm just a windows user that is crazy to see the benefits from a Ubuntu live CD, but even though my problem is already known (and I posted the solution before, about the special string in my mdem), no solution has appeared yet.

I'm feeling like if I was using MS software: "Just buy another modem and you are fine". Except that the modem works under windows.

---

### Post by dmizer on 2006-06-08
and you can save yourself the headache that most people encounter with pppoe in ANY os, and simply purchase a $10 pppoe capable wired router (or shell out a few more dollars for a wireless one), configure it to do the auth for you and shezam ... no headache.

and having worked internet tech support for 2 years ... yes i know first hand that pppoe is a pain in any os.  win xp has just as many bugs with pppoe as linux, or osx.  pppoe is a pain to get configured, and in many cases the only solution we could get to work was a router solution ... even in windows.

surely $10 for a router is a better deal than several hundred for a legal copy of windows?

remember ... all os' have problems.  none are perfect.  but unlike with any other os available for you to choose from ... with linux, if you don't like it, you can change it.

---

### Post by Jh00 on 2006-06-08
U$10 doesnt sound a big deal. Sorry for changing topics, but I have my ADSL modem for ages and I don't want to fall into another trap (i.e. "custom" protocols), since I don't know what is available today. Do you have any suggestion of a good router around that price? Any brand/model that I should avoid?

Thanks for your concern.

---

### Post by dmizer on 2006-06-08
[QUOTE=Jh00]U$10 doesnt sound a big deal. Sorry for changing topics, but I have my ADSL modem for ages and I don't want to fall into another trap (i.e. "custom" protocols), since I don't know what is available today. Do you have any suggestion of a good router around that price? Any brand/model that I should avoid?

Thanks for your concern.[/QUOTE]
since i don't know where about's you reside, here's some super cheap generic brands on newegg: [http://www.newegg.com/Product/ProductList.asp?N=2000400028+4093&Submit=ENE&Manufactory=1015&SubCategory=28&Description=router](http://www.newegg.com/Product/ProductList.asp?N=2000400028+4093&Submit=ENE&Manufactory=1015&SubCategory=28&Description=router)

linksys, belkin, netgear are all good name brands ... all of which you can also find on newegg,

i'm sure you will be able to pick them up locally for similar prices.  if not, just bring along a newegg ad and they'll match.

---

### Post by Jh00 on 2006-06-08
**FINAL (PSEUDO) SOLUTION!!**

I was about to follow our friend's advice and order a new router for me, but then I remembered out of nothing that I've read somewhere that this cr4p modem could be turned into a router by using a different firmware.

After googling a lot, I finally found it! This is a translation of the original post (in PT-BR):
[http://www.fotonica.fis.unb.br/adsl/default_en.htm](http://www.fotonica.fis.unb.br/adsl/default_en.htm)

This link provides instructions to convert a 3Com HomeConnect into a router! Basically, you just use the firmware of another specific 3Com router and voila! The USB connection wont work anymore, but who cares? Its buggy as hell anyway.

After some tweaking, I got the beast working as a router, and finally, after months of waiting, I'm posting this directly from (K)Ubuntu!

If it wasn't for dmizer, I wouldn't have thought about this. Thank you! So I hope that future (poor) owners of this crap hardware can find this post and help themselves too.

KEYWORDS: 3Com HomeConnect PPPoE router modem connection rp-pppoe pppoeconfig convert internet dialer 3CP4130

I will be happy to help anyone on this, because I know how painful it was to cope with it. My email is [email]jha_ga_@w_net.com.br[/email] (without the "_").

Cheers!

---

### Post by dmizer on 2006-06-08
a router is often the most headache free solution to any network issue in any os.  glad to know you've got things up and running.  congrats!

---

