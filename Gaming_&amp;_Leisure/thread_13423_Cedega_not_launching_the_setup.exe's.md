---
title: "Cedega not launching the setup.exe's"
date: 2005-01-31
forum: Gaming &amp; Leisure
---

### Post by peter_barb on 2005-01-31
I installed cedega just now it doesn't seem to be launching the setup files... I type in the command, it doesn't do anything. I will be willing to let someone do SSHD to see what the problem is.. that is how ansioux I am.

---

### Post by jdodson on 2005-01-31
[QUOTE=peter_barb]I installed cedega just now it doesn't seem to be launching the setup files... I type in the command, it doesn't do anything. I will be willing to let someone do SSHD to see what the problem is.. that is how ansioux I am.[/QUOTE]

are you in the directory with the .exe file?  remember gnu/linux console is case sensitive so if the file is QW.EXE you have to type it in all caps.

so basically if you are in the directory and you know because you can type "ls" and you get something like:

QW.EXE 
QW.DOC
foo.dll
bar.dll

you can then type:

cedega ./QW.EXE

and it "should" work.

---

### Post by peter_barb on 2005-01-31
[QUOTE=jdodson]are you in the directory with the .exe file?  remember gnu/linux console is case sensitive so if the file is QW.EXE you have to type it in all caps.

so basically if you are in the directory and you know because you can type "ls" and you get something like:

QW.EXE 
QW.DOC
foo.dll
bar.dll

you can then type:

cedega ./QW.EXE

and it "should" work.[/QUOTE]
 Yeah, I do that.. I type it in, and it just acts like nothing happend and "peter@LANParty:~ $
" appears again :P

---

### Post by jdodson on 2005-01-31
[QUOTE=peter_barb]Yeah, I do that.. I type it in, and it just acts like nothing happend and "peter@LANParty:~ $
" appears again :P[/QUOTE]

what game or app are you trying to run?

---

### Post by peter_barb on 2005-01-31
[QUOTE=jdodson]what game or app are you trying to run?[/QUOTE]
 I am trying FarCry, but even then any other game doesn't work. I even tryed Doom 3

---

### Post by jdodson on 2005-01-31
[QUOTE=peter_barb]I am trying FarCry, but even then any other game doesn't work. I even tryed Doom 3[/QUOTE]

do you have your 3D video card drivers setup up correctly?  what kind of card are you using?

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) - for info on how to do that.

there is no error message generated at all?

try running tuxkart.  it is a game that you can apt-get from universe.

---

### Post by peter_barb on 2005-01-31
[QUOTE=jdodson]do you have your 3D video card drivers setup up correctly?  what kind of card are you using?

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) - for info on how to do that.

there is no error message generated at all?

try running tuxkart.  it is a game that you can apt-get from universe.[/QUOTE]
 Thats the part where i need help :P

Can someone please help me to see if they are in properly? I am still a newbie!

<b>EDIT</b>: For Doom 3, I tryed another .exe file! It launched the setup... but look what it shows... [http://peterbarbosa.com/Screenshot.png](http://peterbarbosa.com/Screenshot.png)

---

### Post by fng on 2005-01-31
doom3 has native linux executables. I would use those instead of trying to get doom3 running with wine/cedega

---

### Post by peter_barb on 2005-01-31
[QUOTE=fng]doom3 has native linux executables. I would use those instead of trying to get doom3 running with wine/cedega[/QUOTE]
 Even then, why isn't FarCry working :P

---

### Post by Dylanby on 2005-01-31
Did you install Cedega into a chroot?
Do you have Point2Play installed?
If so, what are the results of the P2P system tests?

---

### Post by peter_barb on 2005-01-31
[QUOTE=Dylanby]Did you install Cedega into a chroot?
Do you have Point2Play installed?
If so, what are the results of the P2P system tests?[/QUOTE]
 I don't have Point2Play nor do I know what that is... and I installed it in root, I don't know what chroot is....

What is chroot, and what is Point2Play.. 

Thanks!

---

### Post by DJ_Max on 2005-01-31
chroot() is a Unix system call that's used to provide an additional layer of security when untrusted programs are running. I would use it when running a gamerserver for example.

---

### Post by Dylanby on 2005-02-01
My questions were leading up to others, none of which apply to your case.

Some people who are running amd64 have set up a 32bit chroot to install some programs which don't run as well on a 64bit platform.

---

### Post by ahyden on 2005-02-01
[QUOTE=peter_barb]Even then, why isn't FarCry working :P[/QUOTE]

From what I've heard, the FarCry installer doesn't work with cedega. There is a native linux installer (and others) available on this site: [http://www.liflg.org/](http://www.liflg.org/)

But you need cedega to run the game itself :)

---

### Post by rykel on 2005-03-19
Hi,

You can try right-clicking the .exe file and choose Properties, then Custom Command...

Simply type "cedega" and it should work...

If not, your installation could have been faulty, OR perhaps your download was erroneous?


Best Regards

---

### Post by titus on 2005-04-14
i get this with world of warcraft, using cedega from command line.

it just dumps back to the bash shell, no output of anykind. command is :

$ cedega /media/cdrom0/installer.exe

---

