---
title: "Has anybody managed to Install Cantera 1.7.0 in Ubuntu...?"
date: 2009-03-07
forum: Education &amp; Science
---

### Post by AlexVader on 2009-03-07
Hi Forum users...

I have downloaded this app, Cantera-1.7.0 from sourceForge...  

It solves chemical kinetics problems, and chemical reactor networks.

I want to use it to model a Deflagration to Detonation transition in a chemical laser optical resonator, just to ascertain if it is physically realizable to create a standing detonation wave in a reacting hypersonic flow. That standing detonation wave will be the geometric locus of the short lived excited chemical species which will constitute my lasing medium.

...Well, leaving the technicallity stuff out, this package will require Python 2.5, which i have from the repos, as well as numpy, sciPy, sundials, as well as lapack and blas.

So far so good, everything installed from the repos.
So I download and untar the cantera-1.7.0 from sf.net, cd to cantera-1.7.0 ddirectory and run ./preconfig as root, following the install instructions.

Then I run make, but the process aborts with a cryptic error msg... :


g++ -c State.cpp -I. -O3 -Wall   
In file included from State.cpp:20:
stringUtils.h: In function ‘int Cantera::intValue(std::string)’:
stringUtils.h:34: error: ‘atoi’ was not declared in this scope
stringUtils.h: In function ‘doublereal Cantera::fpValue(std::string)’:
stringUtils.h:38: error: ‘atof’ was not declared in this scope
make[1]: *** [State.o] Error 1
make[1]: Leaving directory `/home/alex/Desktop/cantera-1.7.0/Cantera/src'
make: *** [kernel] Error 2


Is my error reproducible...?

What have i done wrong...   is this correctible...? if it is, does anyone have a hint on what to do...?

Thanks in advance...  :-)

Best regards

Alex

---

### Post by AlexVader on 2009-03-08
Hi again Forum...

Just forgot to mention...

I am using Ubuntu 7.10 x32 kernel 2.6.22-14-generic.

If this info may help...   

Best regards

Alex

---

### Post by onthemoon on 2009-03-10
Same Problem here (exactly the same error message, with 
Ubuntu 8.10
kernel 2.6.27-11-generic

---

### Post by AlexVader on 2009-03-10
Hi Onthemoon,

Well, I guess that the problem is not "Distro specific" then...

Guess I will have to delve into the code headers :( so see what is going on...

But the very simple idea of debugging ( "trying to" are more realistic words... lol ) a code that i have not written is a bit creepy...   :(

Thx anyway...

Best regards

Alex

---

### Post by onthemoon on 2009-03-11
Well, it probably has something to do with the c++ (pre)compiler. I'll give it another shot this morning, but I can already tell you it's ubuntu specific (there was no problem installing it on a linux/GNU cluster).
I'd like to use it in local...

---

### Post by onthemoon on 2009-03-11
Maybe this will help you

[http://sourceforge.net/forum/forum.php?thread_id=2695728&forum_id=268952](http://sourceforge.net/forum/forum.php?thread_id=2695728&forum_id=268952)

It did not really help me :-S, but in case you figure it out...

---

### Post by AlexVader on 2009-03-11
I have been messing with the code, and so far I managed to delay the error in the build process...:

When it states that atoi and atof are not defined in the scope of stringUtils.h, i just added #include <cstdlib> in the begining of stringUtils, and it solved the problem, the another undefined function popped out in another header file, and i just added #include <cstring> ( had to do with string manipulation interinsic functions ) in that file, and it went further in the build process.

But then it started to complain about code specific functions...   :-(

...Well... I didn't write it, so dunno where else to tackle, but i will check out that link...  see what i can do.

Thanks a lot  :-)

Alex

---

### Post by onthemoon on 2009-03-12
Now I get to the point where it tries to use Python... and then a new error occurs.

I added the following flags (file preconfig) . But I dont get why I have to force it that way.

CXXFLAGS=${CXXFLAGS:="-O3 -Wall -include /usr/include/stdlib.h -include string.h -include stdio.h"}

The pb is that some files (really few, like 2) dont work with stdlib, so I compiled these two manually.

I think I'll give it a break, and come back to it later, but if you manage to install it all, please post your fix...

---

### Post by AlexVader on 2009-03-12
Thks for the hint Onthemoon,

I will try to pick this from the python thing...

Man, i really think that the developers should write more specific instructions on how to install this...


You said you have installed this on another distro.... which one...? a Fedora, RedHat, OpenSUSE, FreeBSD...?


BRGDS


Alex

---

### Post by onthemoon on 2009-03-13
The other one is a redhat distri...

I realized yesterday that I had two python installed :
python2.5 with the alias python
python3.x with the alias python3

It does not compile with python3, but works with the older one.

Here is a sumup of what works and does not up to know
[https://sourceforge.net/forum/message.php?msg_id=6765228](https://sourceforge.net/forum/message.php?msg_id=6765228)

The only results I got is from the c++ version... We're getting closer!

---

### Post by AlexVader on 2009-03-13
Hi again

I will resume my work tryin to compile Cantera tonight when I will have my install DVD of Ubuntu 7.10.

I do not have python3 on my system, I have the Python 2.5 installed but I do not have the headers ( -dev ).

I also have Python 2.4 installed since a Scientific viewing package specifically asked for that... : MayaVi

So I will uninstall Py 2.4, install all of Py 2.5 ant try again...

... man it would be awesome if they just added cantera to the repos... wouldn't it...?

Anyway... always thought that in terms of install configurations, Red Hat was way more "cranky" than Ubuntu...   anyway... C++ is C++, what the heck does  gcc and g++ complaint about...?

Really don't understand...   :-( with a so called "preconfig.sh" to take care of distro specific issues...   :-(


BRGDS

Alex

---

### Post by andmk13 on 2009-08-06
Hi everyone,

I know this is an older thread but I was wondering if anybody had worked out how to install Cantera onto Ubuntu.  I'm pretty new to Ubuntu in general so any help would be appreciated.  I attempted to follow the help previously mentioned but I do not know if I have actually been doing everything right or if anybody has installed everything on 9.04.  

Thanks
Andrew

---

