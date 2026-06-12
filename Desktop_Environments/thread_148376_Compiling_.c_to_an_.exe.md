---
title: "Compiling .c to an .exe"
date: 2006-03-21
forum: Desktop Environments
---

### Post by roostishaw on 2006-03-21
Hello all, 

I recieved a program a friend was working on a few days ago. It's a simple script written in c. How can I compile this code (just one text file named album.c) into a exe file?

Thank You!

---

### Post by art on 2006-03-22
I never compiled C, only used C++, and the syntax is
g++ -o output.exe album.c

and the manual for g++ says it is also C compiler, so might work

---

### Post by stuporglue on 2006-03-22
As long as you mean "executable" and not a Windows exe file, then 
gcc -o ProgramName album.c 
will do the trick. 

I don't know about making it into a Windows exe file though, if that's what you're after.

---

### Post by MrDan on 2006-03-22
[QUOTE=stuporglue]

I don't know about making it into a Windows exe file though, if that's what you're after.[/QUOTE]


I don't know, I have a dumb question.  Can't you just compile source in C in windows??  Just curious if you can compile linux stuff in windows development software??

---

### Post by roostishaw on 2006-03-22
Well, I am after a windows exe file... but thanks for the replys so far. I'll try them out now.

Anyone know how to get it into a windows exe file?

Thanks!

---

### Post by art on 2006-03-22
Never done that, but this site
[http://rooster.stanford.edu/~ben/linux/crosshowto.php](http://rooster.stanford.edu/~ben/linux/crosshowto.php)
gives couple examples..., might wanna check that out...

---

### Post by harisund on 2006-03-22
What I use to compile C programs in Windows is gcc for Windows through Cygwin. 

I really think Cygwin is an awesome way to learn the Linux CLI through Windows itself. You have the entire command line power. 

I would suggest you install Cygwin (not an easy process, but then again, not very difficult either..) and then compile it to get your .exe file ...

---

### Post by MichaelZ on 2006-03-22
Hello,

In windows is also possible to use [MinGW]("http://www.mingw.org").

Best wishes,
Michael

---

### Post by roostishaw on 2006-03-22
[QUOTE=art]Never done that, but this site
[http://rooster.stanford.edu/~ben/linux/crosshowto.php](http://rooster.stanford.edu/~ben/linux/crosshowto.php)
gives couple examples..., might wanna check that out...[/QUOTE]

I followed these instructions and it made an exe and all... but when I run it under windows its says it encountered an error, and needs to close... then it gives me the whole error report thing.

By the way, the command I used to compile in linux was: i586-mingw32msvc-gcc -o album.exe album_source.c

Anyone know how to get it to work?

---

### Post by roostishaw on 2006-03-22
/bump
I made a *big* edit on my last post... if you read it before the edit, you know what I mean ;)

---

### Post by mjwood0 on 2006-03-22
So you installed MinGW?

Can you give the output of what you did so we can better assist you?

I'm very familiar with crosscompiling from Unix to PowerPC for embedded programming, but never crosscompiled for windows...

---

### Post by roostishaw on 2006-03-22
I installed mingw32. Then I put the source code (album_source.c) in my home folder. Then I ran: i586-mingw32msvc-gcc -o album.exe album_source.c

It made an exe called album.exe. Then I put that exe that it made onto my usb flash drive, and took it over to my windows box. I dubble clicked the exe and a cmd prompt came up for a split second, then the window that says "album.exe has encountered an error, and needs to close. To tell Microsoft about this problem..."

I'm trying to compile it under Ubuntu Breezy Badger, with the latest updates.

I don't know if it makes a difference, but the script includes as the first three lines:
#define WINVER 0x0500
#define _WIN32_WINNT 0x0500
#define WINNT 1

I'm saying this because I compiled a simple script without any #define things in it. That ran fine on the Windows box.

Anyone know whats going wrong?
Thanks!

---

### Post by mjwood0 on 2006-03-22
Hmm... since you can compile a simple program without #defines, the cross compiler seems to be working

Seems like some sort of windows programming problem.  I'm strictly an embedded programmer, so I'm out of my league.  Sorry!

Good luck though!

Out of curiosity, are any of the variables WINVER, _WIN32_WINNT or WINNT used anywhere else in the program?  Or are they simply environmental defines for the compiler?

---

### Post by roostishaw on 2006-03-22
[QUOTE=mjwood0]
Out of curiosity, are any of the variables WINVER, _WIN32_WINNT or WINNT used anywhere else in the program?  Or are they simply environmental defines for the compiler?[/QUOTE]

Well, since I'm not a programmer, I just used the find feature after opening the code in gedit. All it found was those listings at the top. That's it. As for "environmental defines for the compiler"... I have no idea what that/those are. :D 

And when I just delete those three snippets, it still gets the same error in windows.

Anyone... please?

---

### Post by seanmc42 on 2006-03-23
The command line you used to compile it, specifically the -o, gives the output file a name. You are compiling it with a Linux compiler, so the output file (the program) is a Linux executable. Giving it an extension of .exe does NOT make it a windows executable.

You will need to copmile it with a Windows compiler - most likely on a Windows machine. (It's possible to do it on a Linux box, but that requires a cross compiler and that IS a complicated matter).

I recommend following the above suggestion to install Cygwin - it's actually VERY easy - and you'll be able to command using the same command line you would in Linux (just use gcc, not that 586... crap).
[http://www.cygwin.com](http://www.cygwin.com)

Try it and post again here if you get stuck.

---

### Post by MichaelZ on 2006-03-23
[quote=seanmc42]The command line you used to compile it, specifically the -o, gives the output file a name. You are compiling it with a Linux compiler, so the output file (the program) is a Linux executable. Giving it an extension of .exe does NOT make it a windows executable.

You will need to copmile it with a Windows compiler - most likely on a Windows machine. (It's possible to do it on a Linux box, but that requires a cross compiler and that IS a complicated matter).

I recommend following the above suggestion to install Cygwin - it's actually VERY easy - and you'll be able to command using the same command line you would in Linux (just use gcc, not that 586... crap).
[http://www.cygwin.com]("http://www.cygwin.com")

Try it and post again here if you get stuck.[/quote] 
Sorry, but I tend to disagree with you.

Have a look at here for example:

[http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux]("http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux")

cygwin is ok, I have tested it for a bit, but it seemed MinGW was more suitable (at least for my work). Anyway, it is worth a try.

Best wishes,
Michael

---

### Post by seanmc42 on 2006-03-23
Sorry, what are you disagreeing with?
The link you posted is a cross-complier, which is one of the methods I said you could use...

---

### Post by roostishaw on 2006-03-23
[QUOTE=seanmc42]The command line you used to compile it, specifically the -o, gives the output file a name. You are compiling it with a Linux compiler, so the output file (the program) is a Linux executable. Giving it an extension of .exe does NOT make it a windows executable.

You will need to copmile it with a Windows compiler - most likely on a Windows machine. (It's possible to do it on a Linux box, but that requires a cross compiler and that IS a complicated matter).

I recommend following the above suggestion to install Cygwin - it's actually VERY easy - and you'll be able to command using the same command line you would in Linux (just use gcc, not that 586... crap).
[http://www.cygwin.com](http://www.cygwin.com)

Try it and post again here if you get stuck.[/QUOTE]

So this program, after it's installed of course, will compile .c source code in windows? Making a windows executable?

Thanks!

---

### Post by seanmc42 on 2006-03-24
Well cygwin is actually a collection of programs - you select packages, like you do with Ubuntu. You need to select the development packages (get nmake, and gcc), and you shouls be good to go.
Then, you'll just use gcc myfile.c -o myfile.exe from within the shell (bash), and yes - it wil compile a windows .exe file for you.

Cygwin is like having a linux distro INSIDE of windows.

---

### Post by MichaelZ on 2006-03-24
[quote=seanmc42]Sorry, what are you disagreeing with?
The link you posted is a cross-complier, which is one of the methods I said you could use...[/quote]

I tend to disagree about your first sentence. You can build Windows exec. on Linux :). The link I have posted has the following explanation:

[Cross-Compiling Under Linux]("http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux") - build your Windows executables on linux

I never tried it because I build my Windows exec on Windows, but it seems possible. Moreover I do not think that 586 is a crap :(.

Best wishes,
Michael

---

### Post by seanmc42 on 2006-03-24
I didn't say you couldn't do it - I said it's difficult.
If THAT was what you were disagreeing with, well then that's subjective.

Not much point in arguing about it; plus if you have a step-by-step tutorial (which it seems you do) then of course that simplifies things  a great deal.

Q: Does it interfere at all with compiling Linux apps after you've set it up?
The O.P>. probably won't care (he might); I'm curious myself.

---

