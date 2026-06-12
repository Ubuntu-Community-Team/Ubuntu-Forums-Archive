---
title: "general question: what is &quot;executable&quot;?"
date: 2008-12-12
forum: General Help
---

### Post by eugeneccampbell on 2008-12-12
Would someone please explain to this semi-newbie how an executable file is labeled in Linux? I started with Ubuntu 5.10, soon reinstalled Ubuntu 7.10, then upgraded to 8.04, and now 8.10, and am using Linux well (though I keep a Windows box at work where I've needed to do some things I haven't set up yet under Linux, for example, scan, print, run
a few programs I've come to depend on that I haven't got around to trying under Wine). Recently I installed Edubuntu 8.04 LTSP at work and now I'd like to be able to print from Linux, too.

In the Open Office Help for printers (for example -- only an example as I'm not asking for help with this program specifically) there is this:

--------------------------
Call the printer administration program spadmin as follows:
Change to the {install_path}/program directory.
Enter: ./spadmin
--------------------------

I ran this:

--------------------------
myself@ubuntu:~$ locate spadmin
/usr/lib/openoffice/program/spadmin
/usr/lib/openoffice/program/spadmin.bin
--------------------------

The text script spadmin doesn't contain the text string "spadmin.bin" so I wonder what the relationship between them is and how the binary would be called from the script.

Anyway I accidentally pasted this line, including the end-of-line, into my terminal while in my home directory:

--------------------------
myself@ubuntu:~$ /usr/lib/openoffice/program/spadmin
--------------------------

The spadmin program ran. I changed to the directory
/usr/lib/openoffice/program/ which as I understood was
what I'd been instructed to do in Help, and ran this
command:

------------------------
myself@ubuntu:~$ cd /usr/lib/openoffice/program
myself@ubuntu:/usr/lib/openoffice/program$ spadmin
bash: spadmin: command not found
------------------------

I tried again with this, which, specifically, is what Help says to do:

------------------------
myself@ubuntu:/usr/lib/openoffice/program$ ./spadmin
bash: spadmin: command not found
------------------------

Again nothing. I take this to mean that bash does not recognize the script file spadmin as executable. So I tried this:

--------------------------
myself@ubuntu:/usr/lib/openoffice/program$
/usr/lib/openoffice/program/spadmin
--------------------------

The program ran again. One, it's not running in the
way Help seems to be telling me it should run, that
is, it doesn't run with the "spadmin" command alone,
or with "./spadmin" even when I issue the command
from within the directory. Under DOS if a command
is issued that refers to an executable not in the
PATH then it won't run unless the command is issued
from within the directory containing the executable.
Natch. That's as I had understood -- until now -- is 
the case in Linux too. Something is different. Why 
did it not run?

Two, the program DID run when the command I issued included the path to it along with the command itself -- and it did so from my home directory as well as from the program directory. Why? In particular, this is NOT as was how the Help instructed -- but beyond that odd fact I need to learn what Linux considers an executable file or, better, the root file (initiating file) of a collection of executable files that make up an application program.

Related to these two questions: is there a PATH in Linux like there is under DOS/Windows, a collection of paths that ash or bash will use to search for an executable?

Three, this script file called spadmin does not anywhere refer explicitly to the file spadmin.bin and I'm curious what the relationship between them might be. Under DOS and Windows only files with certain file extensions will run as executables (unless some odd hacks are applied). Under DOS we had .com files and .bat files for OS scripts. Then
came .exe and under Windows there are various file extensions involved including .dll, etc., and there are things like .scr for screensavers, whatever.

Under Linux it seems as if the file extension is not a factor the same way as it is under DOS/Windows. I know this also because when I click (Gnome) on almost any text file a box pops up asking me whether I want to display it or run it. What is the first criterion for a file to be executable? Are there others?

Under DOS/Win a script file such as a .bat file is sometimes (but rarely except maybe at boot time) called; usually a compliled binary such as an .exe file is the direct executable or the initiating executable among various DLLs and other application files. Under Linux it seems as if scripts are used to call programs to run, a design that seems wise for the sake of the configurability I switched to Linux for.

I've searched through Linux documentation, help sites, many Google searches, but can't find an answer to this fundamental question.

Thanks for any help. I don't need someone to type in a long explanation for my sake if it has been done already. Just, please point. 

If on the other hand it hasn't been done for the sake of newbies, in language that Windows emigrants would understand, then I think it should be and included in Ubuntu documentation somewhere. For that, if someone will guide me I'll be happy to do the typing and make it linguistically pretty :-)

---

### Post by iaculallad on 2008-12-12
Try this just to execute the file:

While on the terminal, change directory to /usr/lib/openoffice/program and I'm assuming that spadmin.bin has an executable bit, try the command below:

```
sudo ./spadmin.bin
```

If that fail, try:

```
sudo chmod a+x spadmin.bin
```

then

```
sudo ./spadmin.bin
```

---

### Post by Sjeti on 2008-12-12
I think you found this out, but just incase: you have to be in the location of the file before you can execute it.

To do this, you just cd -etc- to the place and then use the ./filename to run the binary file.

Sometimes you will have makefiles and can use the 'make' or 'make all' command to compile the code, which you then run with the ./ command.

There doesn't seem to be any file extension name for executable files, most don't even have extensions.


As far as your problem opening up files and it asking you if you want to run it, you can get rid of this by looking at the file permissions.

Use ls -l to show the owner and permissions of the file.  Look up the chmod command and it will give you a good runthrough of the read/write/execute system.
The issue is that the file is being read as an executable, and if you go in and remove the executable tag from it, it will stop prompting you to run it.

---

### Post by Peter09 on 2008-12-12
As already indicated the executable function within Linux is set by file permissions, not, as in windows, file extension. So any file in Linux can be executed as long as the executable bit is set.

When you come to execute a file, the system looks. as default, in the directories defined by the path definition. This  normally includes /etc/bin and /etc/usr/bin (I think). To execute any other file you must explicitly provide the complete path.

So - if the file is in your current directory it would be ./<filename>

Or in another directory it would be <full path>/<filename>

This is part of the security mechanisms within Linux, any worm or virus that wants to be executed must gain root access to set the executable bit.

---

### Post by eugeneccampbell on 2008-12-12
Thanks everyone. The bin runs, too (either script or bin, from within an adminstrator session without need for sudo). 

I have since learned that what makes a file executable is the "executable bit." This bit can be changed by chmod, correct? 

When bash comes across a text file whose executable bit is set, and attempts to run it, what are the criteria for it to run? Python scripts, I see, have an intiating line.

What about bin files? For example, if I set the executable bit on a jpeg file, what would happen if I tried to run it?

---

### Post by prshah on 2008-12-12
> **eugeneccampbell said:**
> Would someone please explain to this semi-newbie how an executable file is labeled in Linux? 

I need to learn what Linux considers an executable file 

Related to these two questions: is there a PATH in Linux like there is under DOS/Windows, a collection of paths that ash or bash will use to search for an executable?



a) An executable file in linux is one that has it's "execute" bit set. The execute bit (+x) can be set for (u)ser (owner of the file), (g)roup (of the file) or (o)thers. If +x is set for other (o+x) then everyone can use (run) it. If set for u+x or g+x then only the user or group (of the file) members can run it.

b) An executable file has loosely followed naming conventions, which are not strictly adhered to; the file can end in .sh (for shell script, usually /bin/bash), .py (for python script), .bin (binary file), .out (compiled file, usually same as .bin), etc.

c) A "true" (ie, binary) executable file will have a ELF header; this is how linux can recognize a "executable" binary file; a binary file _without_ an ELF header will not (cannot) be executed, even if the +x bit is set, since it cannot be "understood". On the other hand, even a binary file _with_ an ELF header cannot be executed if -x (no execute bit)

d) To find out which file is being executed for any "command", use the which command, eg```
which spadmin
``` will tell you what is _actually_ being executed for the "spadmin" command.

---

### Post by eugeneccampbell on 2008-12-12
(Peter09)
> When you come to execute a file, the system looks, as default,
> in the directories defined by the path definition. This 
> normally includes /etc/bin and /etc/usr/bin (I think). To
> execute any other file you must explicitly provide the
> complete path.

Does that mean ONLY those two directories, or is it possible to set another directory path in addition, as can be done under DOS with the path command?

Anyway, I understand the concept, thanks.

Still, this question -- I ran:

>> myself@ubuntu:~$ /usr/lib/openoffice/program/spadmin
>> --------------------------
>> 
>> The spadmin program ran.

The executable bit is set. The entire path was specified.
Fine, and Bob's my uncle.

>> I changed to the directory /usr/lib/openoffice/program/
>> which as I understood was what I'd been instructed to
>> do in Help,

myself@ubuntu:~$ cd /usr/lib/openoffice/program/spadmin

>> and ran this command:
>> ------------------------
>> myself@ubuntu:/usr/lib/openoffice/program$ spadmin
>> bash: spadmin: command not found
>> ------------------------

Huh? It isn't as if I need specific root permissions through sudo, as it already ran, from my home directory, without that (I am logged in with administrator privileges).

>> I tried again with this, which, specifically, is what
>> Help says to do:
>> ------------------------
>> myself@ubuntu:/usr/lib/openoffice/program$ ./spadmin
>> bash: spadmin: command not found
>> ------------------------

?? Same. Why does it run from my home directory, with the path included in the command but not not from within the program directory? Either the executable bit is set or it isn't, right? It ran from my home directory so it must be set. Why not from the program directory?

I ran:
------------------
myself@ubuntu:/usr/lib/openoffice/program$ ls -l spad*
lrwxrwxrwx 1 root root     7 2008-10-31 02:24 spadmin -> soffice
-rwxr-xr-x 1 root root 22712 2008-07-01 00:38 spadmin.bin
------------------

I have looked in several sites with Linux documentation and can't find what the information in those first ten columns means. Nor does "man ls" explain it, that I can decipher. Which column represents the executable bit? 

BTW, I'm not asking anything to do with spadmin itself, it's only an example.

Thanks for the help.

Oh, I found this:

[http://www.linux.org/docs/ldp/howto/Bash-Prog-Intro-HOWTO.html](http://www.linux.org/docs/ldp/howto/Bash-Prog-Intro-HOWTO.html)

It is answering questions (generating more questions, as well :-)

---

### Post by eugeneccampbell on 2008-12-12
(prshah)
> a) An executable file in linux is one that has it's "execute"
> bit set....for (u)ser...(g)roup...(o)thers....

If I run ls -l I should be able to see the execute bit, right?
Which column is it in?

> b) ...loosely followed naming conventions...
>
> c) ...ELF header...

OK, thanks.

> d) To find out which file is being executed for any
> "command", use the which command, eg```
which spadmin
``` 
> will tell you what is _actually_ being executed for the
> "spadmin" command.

I tested the which command on a few commands and it responds to some (for example bash, ls, student-control-panel, etc.) but not others -- including spadmin. Why might spadmin, which I can run from the command prompt, not respond to the which command?

---

### Post by eugeneccampbell on 2008-12-12
> **Sjeti said:**
> Look up the chmod command and it will give you a good runthrough of the read/write/execute system.


I found a very thorough article on chmod in Wikipedia. It's hard to understand in places but I'm going to look into it, thanks.

---

### Post by prshah on 2008-12-12
> **eugeneccampbell said:**
> I tested the which command on a few commands and it responds to some (for example bash, ls, student-control-panel, etc.) but not others -- including spadmin. Why might spadmin, which I can run from the command prompt, not respond to the which command?

which will work for files, not native commands and aliases. Since spadmin is clearly not a native command, then possibly it's setup as an alias. see```
alias
``` to list aliases setup on your system.

Another situation: If spadmin is not in your $PATH environment variable, then which will not be able to flag it. +x restrictions apply as well.

The execute bit is the "x" in the "rwx" section of the "ls" (directory") listing.```
ls -l
drwxrwx--- 1 root plugdev       0 2008-03-11 23:41 Temp
-rwxrwx--- 1 root plugdev   19968 2008-03-11 23:41 test.doc
-rwxr-xr-x 1 user user        231 2008-12-12 19:55 convert.sh

```

In the first part of the listing, note the first 10 characters; the breakup is as follows:
the first character is a special character denoting directory "d", ordinary file "-", block device "b", character device "c", and so on.

The next 3 characters are permissions for the owner of the file/directory; in case of files, r=read, w=write, x=execute. in the case of a directory, r=list contents, w=allows changes, deletions and addition of files, x=allow to "cd" into directory.

The following 3 characters are permissions for the other group members, and the last 3 permissions for others.

Taking each case;

The first listing is a directory "d" with full permissions for user "root" and other members of group "plugdev" but no permissions for anyone else.

The second listing is a file "-" with full permissions for user "root" and other members of group "plugdev" but no permissions for anyone else. Note that though it is set executable, it's just a doc file and thus the "x" has no meaning here.

The third listing is a file with full (read, write and execute) for the owner "user", but only read and execute (r-x), no write capability for other members.

---

