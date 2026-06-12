---
title: "add m-files to octave"
date: 2008-04-04
forum: Education &amp; Science
---

### Post by Cerny on 2008-04-04
I need to download some m-files for my linear algebra class and i can't figure out where to place the files in order for octave to find them. If anyone knows where they would be placed that would be great.

---

### Post by dedmonds on 2008-04-04
I believe you can add the directory in which the m-files are located to the search path that octave uses using the **addpath** command as shown below:

```

octave:2> addpath("/home/dedmonds/octave/mfiles/");

```

This will not survive through a shutdown of the program, so you would have to do this each time you start octave.

I believe you can also run the **path** command to see the directories currently in the octave search path. You can place your m-files in one of these directories and, octave should find them.

```

octave:3> path

Octave's search path contains the following directories:

.
/home/dedmonds/octave/mfiles
/usr/local/share/octave/site-m
/usr/lib/octave/3.0.0/oct/i486-pc-linux-gnu
/usr/share/octave/3.0.0/m
/usr/share/octave/3.0.0/m/deprecated
/usr/share/octave/3.0.0/m/audio
/usr/share/octave/3.0.0/m/control
/usr/share/octave/3.0.0/m/control/obsolete
/usr/share/octave/3.0.0/m/control/base
/usr/share/octave/3.0.0/m/control/hinf
/usr/share/octave/3.0.0/m/control/system
/usr/share/octave/3.0.0/m/control/util
/usr/share/octave/3.0.0/m/geometry
/usr/share/octave/3.0.0/m/elfun
/usr/share/octave/3.0.0/m/finance
/usr/share/octave/3.0.0/m/general
/usr/share/octave/3.0.0/m/linear-algebra
/usr/share/octave/3.0.0/m/image
/usr/share/octave/3.0.0/m/io
/usr/share/octave/3.0.0/m/plot

```

---

### Post by wangji on 2008-04-05
> **Cerny said:**
> I need to download some m-files for my linear algebra class and i can't figure out where to place the files in order for octave to find them. If anyone knows where they would be placed that would be great.

you can put whereever you want ! just do in an octave session

addpath(genpath("/path_where_you_want/";
savepath;

and all the where_you_want including subdirs behind are included
and even saved for subsequent sessions

---

### Post by random_a on 2010-04-25
My Matlab code in Octave gives an error when a class is referenced as;

MY_ITEM = items.A(param);


where "items" is defined as a directory named as "+items" under the current directory. The file A.m is under the +items directory.

The error message is:

'items' undefined near line xxx...

How do I make it run under Octave ?

Thanks.



> **wangji said:**
> you can put whereever you want ! just do in an octave session

addpath(genpath("/path_where_you_want/";
savepath;

and all the where_you_want including subdirs behind are included
and even saved for subsequent sessions

---

### Post by carandraug on 2010-04-25
> **random_a said:**
> My Matlab code in Octave gives an error when a class is referenced as;

MY_ITEM = items.A(param);


where "items" is defined as a directory named as "+items" under the current directory. The file A.m is under the +items directory.

The error message is:

'items' undefined near line xxx...

How do I make it run under Octave ?

Thanks.

First you should have created your own thread for this question. Anyway, on to solve your problem.

I don't know much about OOP but I think you need octave 3.2 for that. Check first which one you are using with the command [FONT="Courier New"]version[/FONT].

I think [FONT="Courier New"]items.A[/FONT] means the variable [FONT="Courier New"]A[/FONT] in the structure [FONT="Courier New"]items[/FONT] but maybe it works different with OOP. Try asking in the octave mailing list, they are very helpful [EMAIL="help-octave@octave.org"]help-octave@octave.org[/EMAIL].

---

### Post by random_a on 2010-04-27
Thanks for your useful comments.

---

