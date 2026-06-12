---
title: "how to change the default version of GCC"
date: 2009-05-11
forum: General Help
---

### Post by subjugater on 2009-05-11
Hi, guys,

I am now trying to compile a fortran subroutine using matlab by building MEX-file first. I come across the following error, when I was using command mex in the command window:

> >> mex yprimef.F yprimefg.F
Warning: You are using gcc version "4.2.4".  The earliest gcc version supported
with mex is "4.0.0".  The latest version tested for use with mex is "4.2.0".
To download a different version of gcc, visit [http://gcc.gnu.org](http://gcc.gnu.org) 
eval: 1: g95: not found

    mex: compile of 'yprimef.F' failed.

??? Error using ==> mex at 208
Unable to complete successfully.

This error message clearly tells me that I should use an older version of gcc, e.g. such as gcc-4.1.0, which I have on my computer as well. 

How should I set gcc-4.1.0 as default? Anybody knows&#65311;

---

### Post by subjugater on 2009-05-11
I'll try to make this thread in the first page until someone answer me.

---

### Post by bodhi.zazen on 2009-05-11
/usr/bin/gcc is a symbolic link , so unlink it and point it to the version off gcc you wish.

Alternate 

export GCC="gcc-4.1.0" 

then proceed with ./configure .. make .. make install

---

### Post by subjugater on 2009-05-11
> **bodhi.zazen said:**
> /usr/bin/gcc is a symbolic link , so unlink it and point it to the version off gcc you wish.

Alternate 

export GCC="gcc-4.1.0" 

then proceed with ./configure .. make .. make install

I appreciate, buddy. But could you give me more details about these two ways?

1. I didn't find any file named 'gcc' in /usr/bin, but only a file called 'gc' and two files called 'gcc-4.1' and 'gcc-4.2' respectively. Furthermore, by using which terminal command, I can 'unlink' and 'relink' gcc?



2. Could you detail the second way by telling me the commands I should use?

Anyhow, I thank you a lot.

---

### Post by mc4man on 2009-05-11
Assuming you have gcc-4.1 installed you could also try

CC=gcc-4.1 ./configure [COLOR="Blue"]configure options if any [/COLOR]

---

### Post by subjugater on 2009-05-11
> **mc4man said:**
> Assuming you have gcc-4.1 installed you could also try

CC=gcc-4.1 ./configure [COLOR="Blue"]configure options if any [/COLOR]

Thanks. Do you mean to try this line at terminal?

I tried this at the terminal. But it seems that I dont have such a directory 'configure'. Sorry, I am really new to linux.

---

### Post by mc4man on 2009-05-11
Sorry, I misunderstood what you ere trying to do (assumed you were compiling a source from the dir. prompt for that source

I would try what was suggested earlier by bodhi.zazen and then proceed as you were previously

---

### Post by bodhi.zazen on 2009-05-11
> **subjugater said:**
> Thanks. Do you mean to try this line at terminal?

I tried this at the terminal. But it seems that I dont have such a directory 'configure'. Sorry, I am really new to linux.

Take a look at this page : [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

That will outline how to compile packages ;)

---

### Post by subjugater on 2009-05-11
> **mc4man said:**
> Sorry, I misunderstood what you ere trying to do (assumed you were compiling a source from the dir. prompt for that source

I would try what was suggested earlier by bodhi.zazen and then proceed as you were previously

Thanks, buddy. But I am still confused with what suggested by bodhi.zazen, since I can not understand what he wrote.

> **bodhi.zazen said:**
> /usr/bin/gcc is a symbolic link , so unlink it and point it to the version off gcc you wish.

Alternate 

export GCC="gcc-4.1.0" 

then proceed with ./configure .. make .. make install

I did put in at command line 

export gcc="gcc-4.1.0"

but HOW should I proceed with ./configure.....

Could you provide any further details? Thank you so much.

---

### Post by subjugater on 2009-05-11
> **bodhi.zazen said:**
> Take a look at this page : [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

That will outline how to compile packages ;)

Thanks a lot. Let me try now.

---

### Post by bodhi.zazen on 2009-05-11
To compile a package you need to install build-essential.

You then extract the archive and read the README

You then cd into the archive and run

./configure --prefix=/usr
make
sudo make install

you may use checkinstall if you wish, IMO checkinstall is over rated on the wiki page I linked.

Most errors in compiling are due to a lack of dependencies.

---

### Post by mc4man on 2009-05-11
Just to clarify (if it turns out to be appicable here

If I wanted to compile a source that used a."/configure" and not use the default gcc then what I posted works fine

Ex. (with default gcc for 8.10 (4.3.2
> doug@doug-desktop:~/vlc9a/test/vlc-0.9.9a$ ./configure
....................
configure:4073: checking for gcc
configure:4100: result: gcc
configure:4332: checking for C compiler version
configure:4340: gcc --version >&5
gcc (Ubuntu 4.3.2-1ubuntu12andersk1) 4.3.2

switching to gcc-4.1

> doug@doug-desktop:~/vlc9a/test/vlc-0.9.9a$ CC=gcc-4.1 ./configure
......................
configure:4073: checking for gcc
configure:4100: result: gcc-4.1
configure:4332: checking for C compiler version
configure:4340: gcc-4.1 --version >&5
gcc-4.1 (GCC) 4.1.3 20080623 (prerelease) (Ubuntu 4.1.2-23ubuntu3)

---

### Post by subjugater on 2009-05-11
> **bodhi.zazen said:**
> Take a look at this page : [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

That will outline how to compile packages ;)

Buddy, I followed the instruction on the webpage you gave. It instructed me to type the following command

> ./configure --help | less

What I got is 

> bash: ./configure: No such file or directory


Any comments?

---

### Post by bodhi.zazen on 2009-05-11
You are not in the correct directory.

---

### Post by subjugater on 2009-05-11
> **bodhi.zazen said:**
> You are not in the correct directory.

I installed build-essential via Synaptic. Could you tell me where the archive probably is? 

Thanks.

---

### Post by bodhi.zazen on 2009-05-11
you downloaded an archive, no ?

Where did you save it ? Your desktop ? downloads ?

I would be guessing.

You then extracted the archive ? Where did you save it ?

open a terminal and 

cd /path/to/extracted/archive

Say you downloaded the package foo.tar.gz

You then extracted it with

tar -xvf foo.tar.gz

well, next 

cd foo

---

### Post by subjugater on 2009-05-11
> **bodhi.zazen said:**
> you downloaded an archive, no ?

Where did you save it ? Your desktop ? downloads ?

I would be guessing.

You then extracted the archive ? Where did you save it ?

open a terminal and 

cd /path/to/extracted/archive

Say you downloaded the package foo.tar.gz

You then extracted it with

tar -xvf foo.tar.gz

well, next 

cd foo

Perhaps, I am just stupid. Could you tell me where I can download this archive? What is its name? Thanks.

---

### Post by mc4man on 2009-05-11
I don't think this has anything to do with 'sources, extracting, compiling, ect., ect.' in a typical 'problem with compiling' query

maybe start here or somewhere similar

[http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f23674.html&http://www.google.com/cse?q=building+MEX-file&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f23674.html&http://www.google.com/cse?q=building+MEX-file&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8)

---

### Post by subjugater on 2009-05-11
> **mc4man said:**
> I don't think this has anything to do with 'sources, extracting, compiling, ect., ect.' in a typical 'problem with compiling' query

maybe start here or somewhere similar

[http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f23674.html&http://www.google.com/cse?q=building+MEX-file&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f23674.html&http://www.google.com/cse?q=building+MEX-file&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8)

Thanks, buddy. I went thru this Mathworks document a long time ago, and I can compile the fortran subroutine successfully in Windows via the Matlab command [COLOR="Sienna"]mex[/COLOR]. When I was trying to redo what I have done with Windows, I failed and ended up with the error message which I posted at the beginning of this thread. I think it is the problem that I could not use the right gcc. Conclusively, I should figure out how to make Matlab work with gcc-4.1.0, instead of gcc-4.2.3. 

But anyhow, I appreciate your help and patience. I have been using ubuntu for more than one years, but am not good at command skills, since I rely on Synaptic too much. I can realize how naive the questions I posted are.

---

### Post by mc4man on 2009-05-12
The export command should work, noting that you need to be less specific (CC=gcc-4.1) and *stay in the same terminal* to run your subsequent commands (you can cd to different dir. if need be, just stay in terminal you ran the export from

Ex. (same source as before, the fact I'm running a ./configure is irrelevant, just what gcc ver. is used is the point

> doug@doug-desktop:~/vlc9a/test/vlc-0.9.9a$ export CC=gcc-4.1
doug@doug-desktop:~/vlc9a/test/vlc-0.9.9a$ ./configure
........clipped
[COLOR="Blue"]checking for gcc... gcc-4.1
checking how to run the C preprocessor... gcc-4.1 [/COLOR]

---

### Post by subjugater on 2009-05-12
> **mc4man said:**
> The export command should work, noting that you need to be less specific (CC=gcc-4.1) and *stay in the same terminal* to run your subsequent commands (you can cd to different dir. if need be, just stay in terminal you ran the export from

Ex. (same source as before, the fact I'm running a ./configure is irrelevant, just what gcc ver. is used is the point

Hey, buddy, thank you so much. I have successfully overcome the issue. I actually phoned Mathworks company. The technical assistant suggested me the following thread

[http://ubuntuforums.org/showthread.php?t=29449](http://ubuntuforums.org/showthread.php?t=29449)

I followed the way mentioned there. Finally, it works fine. 

1. But it seems that I have sacrificed to use an older version gcc for everything, but not only for matlab, right? However, your method can choose version of gcc case by case, software by software, right?

2. I just can not find any ./configure folder in the folder where I installed matlab. Any comments?

Again, thank you all for your comments and patience.:)

---

### Post by mc4man on 2009-05-12
I'm just using ./configure (on the vlc source) as a means of running a command that will require gcc and show what version will be used.

By no means suggesting you run a ./configure  (there is none in the context of what your doing.

As a matter of fact what your doing is not only above my head, it's well beyond my universe.


My assumption is, that at a directory prompt your running a specific command or set of commands

So the suggestion is, that in the terminal that you intend to run your command(s) first run 
export CC=gcc-4.1

This should allow any futher command that are run in that terminal and use gcc to use the version exported.

When you close the terminal you lose the export so to speak. ( your default of 4.3 will remain so.

---

### Post by subjugater on 2009-05-12
> **mc4man said:**
> I'm just using ./configure (on the vlc source) as a means of running a command that will require gcc and show what version will be used.

By no means suggesting you run a ./configure  (there is none in the context of what your doing.

As a matter of fact what your doing is not only above my head, it's well beyond my universe.


My assumption is, that at a directory prompt your running a specific command or set of commands

So the suggestion is, that in the terminal that you intend to run your command(s) first run 
export CC=gcc-4.1

This should allow any futher command that are run in that terminal and use gcc to use the version exported.

When you close the terminal you lose the export so to speak. ( your default of 4.3 will remain so.

Yes, we had some miscommunication (sort of). I understand what you mean (I hope I really do). I think by using the command line 

> export CC=gcc-4.1

we can choose the version of gcc and use this version of gcc to do the things which can be done via the terminal. If something can not be fulfilled in the terminal (e.g. to compile a fortran code thru matlab interface/command window), the above command you gave perhaps does not work.

---

