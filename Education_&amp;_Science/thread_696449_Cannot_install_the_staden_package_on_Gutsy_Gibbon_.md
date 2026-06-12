---
title: "Cannot install the staden package on Gutsy Gibbon (ubuntu 7.10)"
date: 2008-02-14
forum: Education &amp; Science
---

### Post by HKey on 2008-02-14
Hi everyone,

I had installed the Staden package on my previous ubuntu install (Dapper Dake 6.06 LTS), and as far as I remember, I didn't encounter any particular problem. I recently upgraded to Gutsy Gibbon (well, technically, I didn't "upgrade", I re-installed Ubuntu from scratch), and today I tried to re-install Staden ... unsuccessfully. I'm clearly not an expert, but I had already managed to install packages, even without the help of Synaptic. But that one is really weird: I could download 'staden-linux-1-6-0.tar.gz' from [sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=100316&package_id=107815&release_id=361767") but this compressed archive does not contain any installation manual (the 'README' file is of no use in this respect). One of the created directories ("linux-bin") is full of binaries, but I can't execute all of them. Here are two examples of the errors I get:
```
herve@loire:/usr/local/bin/staden-linux-1-6-0/linux-bin$ ./convert
./convert: error while loading shared libraries: libg.so: cannot open shared object file: No such file or directory
```
```
herve@loire:/usr/local/bin/staden-linux-1-6-0/linux-bin$ ./gap4 
invalid command name "load_alignment_matrix"
    while executing
"load_alignment_matrix       [keylget gap_defs ALIGNMENT.MATRIX_FILE]"
    (file "/usr/local/bin/staden-linux-1-6-0/linux-bin/../lib/gap/gap.tcl" line 683)

```

(still, one program seems to work correctly: the program called "trev"; but its manual doesn't work: 
```
herve@loire:/usr/local/bin/staden-linux-1-6-0/linux-bin$ man trev
No manual entry for trev
```
which could mean, either, that the authors didn't write a manual for trev, or that trev is not fully installed)

I suspect that all these problems mean the installation is not complete (usually, I have to type obscure commands like "make", "configure", "install" and other things that I don't quite understand). But on the other hand, a little bit of googling shows that nobody else had a problem installing the package - even in the ubuntu forum, threads like [this one]("http://ubuntuforums.org/showthread.php?t=442453&highlight=staden") or [that one]("http://ubuntuforums.org/showthread.php?t=277590&highlight=staden") suggest that the installation is not a problem.

Does anyone know what I did wrong?

---

### Post by thisismalhotra on 2008-02-14
I would guess you are missing some dependencies here and so it can not fine the libraries you need. New version might have new paths or new names for those libraries.

Also, install buil-essential package and try to re-run it. Don't know but could you go on the website where you downloaded source and see if they have a list of dependencies??

---

### Post by DrOlaf on 2008-02-14
The Staden package sourceforge page is somewhat cryptic when it comes to advice on installing this package, I'm afraid. I've just installed the newer version of Staden (v1.7.0) on my Gutsy-x86 machine. Most of the problems I had were due to missing libraries, or calls to outdated versions of the libraries I did have. This is what I had to do to get it working. I'm afraid it does involve typing some of the commands that are unfamiliar to you, though.

1. Download io_lib-1.11.0b8.tar.gz and staden-linux-x86-1-7-0.tar.gz from sourceforge

2. Extract both tarfiles and move the directories you get into /usr/local

```
sudo mv io_lib-1.11.0b8 staden-linux-x86-1-7-0 /usr/local
```

3. Go to /usr/local/io_lib-1.11.0b8 and run 

```
./configure 
make
sudo make install 
```

This puts the io_lib executables into /usr/local/bin

4. Open my .bashrc file (in my home directory) with a text editor, and add these lines at the end: 

export PATH=$PATH:/usr/local/staden-linux-x86-1-7-0/linux-bin
export STADENROOT=/usr/local/staden-linux-x86-1-7-0
$STADENROOT/staden.profile

5. Run ```
sudo chmod +x /usr/local/staden-linux-x86-1-7-0/staden.profile
``` to make it executable.

6. Launch a new terminal to load the configuration files and update $PATH.

That got me to the point where I could test the installation by trying to run trev. The first problem I had was a missing libcurl.so library, so I had to apt-get install curl to fix that. Then, trev complained about not being able to find libssl.so.0.9.7 and libcrypto.so.0.9.7. I had the 0.9.8 versions installed, so I just went to /usr/lib and made links:

 ```

cd /usr/lib
sudo ln -s libssl.so.0.9.8 ibssl.so.0.9.7
sudo ln -s libcrypto.so.0.9.8 libcrypto.so.0.9.7
```

That enabled me to run trev OK. The next problem was trying to run pregap4. The first time I tried, pregap4 complained about not being able to find the iwidgets library. That was reasonable, as I hadn't installed it :) so I ran apt-get install iwidgets4 to fix that. Then, I had to edit the file /usr/local/staden-linux-x86-1-7-0/tables/iwidgetsrc to give it the correct path to the library. I replaced the line

source $env(STADLIB)/iwidgets/iwidgets.tcl

with 

source /usr/lib/iwidgets4.0.1/iwidgets.tcl

Now, I can run pregap4, gap4 etc without any problems. I realise that these problems are slightly different to yours, but in essence what I had to do was to hunt down the missing libraries that Staden needed, then install them and tell Staden where they were. There is no useful list of dependencies on the Staden sourceforge page, and I'm sorry to say that the discussion forum there assumes that you already know a lot about installing programs manually. 

Oh, and there are no man pages for any of these programs that I can find. The doc folder in the staden-x86-1.7.0.tar.gz file that you downloaded from sourceforge does have extensive documentation in html and pdf though.

---

### Post by s.dalas on 2009-02-17
Hi there,
i really need your help... I have done everything you say step by step, but i'm stuck in step 6.
I didn't have a .bashrc file so i created one and i paste these lines in the end as you said. After i type this command > sudo chmod +x /usr/local/staden-linux-x86-1.7.0/staden.profile
should i get something in the terminal (because i get nothing..)?

I am not very familiar in linux systems and in step 6 you say:
> Launch a new terminal to load the configuration files and update $PATH.

Maybe is a stupid question but what exactly do i have to do?
Please help me i really need this program for my laboratory work...

Best to you

---

### Post by s.dalas on 2009-02-18
> Code:

cd /usr/lib
sudo ln -s libssl.so.0.9.7 libssl.so.0.9.8
sudo ln -s libcrypto.so.0.9.7 libcrypto.so.0.9.8



Its wrong. First we put the oldfilename and second the newfilename.

> 5. Run
Code:

sudo chmod +x /usr/local/staden-linux-x86-1.7.0/staden.profile

to make it executable.

Its wrong. No <<1.7.0>> but <<1-7-0>>

---

### Post by s.dalas on 2009-02-23
Now i can run trev, pregap4 and others but i can't run the most powerfull gap4. I get this message: 
```
invalid command name "load_alignment_matrix"
    while executing
"load_alignment_matrix       [keylget gap_defs ALIGNMENT.MATRIX_FILE]"
    (file "/usr/local/bin/staden-linux-1-6-0/linux-bin/../lib/gap/gap.tcl" line 683)
```

I think staden pacakge is a very powerfull program for Molecular Biology, and a lot of people running ubuntu will need a "complete how to" for installing it.

---

### Post by halocaridina on 2009-02-24
In Synaptic Package manager, find and install (along with all dependences) the following two libraries:

libstdc++5
libg2c0

Now gap4 should run without that error.

Reference:

[http://sourceforge.net/forum/forum.php?thread_id=1373652&forum_id=347718](http://sourceforge.net/forum/forum.php?thread_id=1373652&forum_id=347718)

---

### Post by s.dalas on 2009-02-26
Thanks a lot!!!!!!  No problem now!!! 

Best to all of you!!

---

### Post by halocaridina on 2009-02-26
Good to hear that it worked.

FYI: One (significant) feature of the Staden package that appears to be seriously broken is accessing the EMBOSS package via the integrated menu in gap4.  This fails to work in both the Linux and Apple packages available from SourceForge (specifically, the create_emboss_files binary does nothing when executed).

If you need to access EMBOSS graphically, my suggestion is the EMBOSS Kaptain scripts:

[http://userpage.fu-berlin.de/~sgmd/](http://userpage.fu-berlin.de/~sgmd/)

Install EMBOSS, Kaptain and NEdit via Synaptic prior to running the install script that comes with the package.  Note that during the EMBOSS Kaptain install, you will have to modify the $PATH to nedit, which on Ubuntu is:

/usr/bin/nedit

Have fun with your sequence data.

---

### Post by vel123 on 2009-02-27
Anybody able to help with Fedora 10 32 bit 
I stuck here, gap4 gives above mentioned error:

invalid command name "load_alignment_matrix"
    while executing
"load_alignment_matrix       [keylget gap_defs ALIGNMENT.MATRIX_FILE]"
    (file "/usr/local/bin/staden-linux-1-7-0/linux-bin/../lib/gap/gap.tcl" line 683)

Libraries lib2c.so and libstdc++5 are ok but coming with slightly different packages

-veljo

---

### Post by halocaridina on 2009-02-27
vel123,

Please read through this link (from my earlier reply):

[http://sourceforge.net/forum/forum.php?thread_id=1373652&forum_id=347718](http://sourceforge.net/forum/forum.php?thread_id=1373652&forum_id=347718)

It looks like you are still missing the libg2c.so library and/or it might be installed in a directory that Staden isn't aware of.

Again, posts in the link above might offer some clues and/or solutions.

Please report how it works for you.

Cheers.

---

### Post by vel123 on 2009-02-27
yep, solved

on Fedora 10 one needs
libstdc++.so.5.0.7 toghether is link libstdc++.so.5 to it

and link to libstdc++.so.6.0.10 wouldn't work

the right library comes with 
compat-libstdc++-33.i386 : Compatibility standard C++ libraries

libstdc++.so.6.0.10 is in 
compat-libstdc++-296.i386 : Compatibility 2.96-RH standard C++ libraries

thanks those who supported to this thread, that was very valuable, I guess to anyone currently trying to get staden working

-veljo

---

### Post by vel123 on 2009-02-27
halocaridina,  thanks the for post but libg2c was not the problem

one should maybe mentioned how to do this STADEN_DEBUG
before running staden package e.g. gap4
export STADEN_DEBUG=1



-veljo

---

### Post by halocaridina on 2009-02-28
vel123,

Glad I was able to contribute and you offer a great tip in starting Staden in debug mode to see what is happening as the programs (like gap4) are executed.

Another set of powerful and academically free (although you need to register) software for contig assembly of sequences is the combination of Phrep/Phrap/Consed:

[http://www.phrap.org/](http://www.phrap.org/)

While it takes a little bit to get up and running (but not anymore then Staden), it is great for mid to large (i.e., mitochondrial genomes and bigger) size projects.  Though for basic work (paired-reads) with SCF and AB1 files, Phrep/Phrap/Consed is definitely overkill and Staden is preferable (though I wish they maintained and updated it more often and/or more people contributed to the project).

Cheers.

---

### Post by vel123 on 2009-03-02
yep, consed/phred/phrap is a great package, I am using it for several years by now. Highly recommend as it is updated frequently!  While staden is discontinued, right?


But I am more into 454 and de novo assembly at the moment, consed does not support it so far, only assembly of 454 and Solexa to reference.  MIRA which is one of de novo assemblers allows both consed and gap4 output and I just wanted to check gap4

btw  a great site for current sequencing technologies is seqanswers.com

-veljo

---

