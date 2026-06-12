---
title: "Scilab error 998"
date: 2008-09-10
forum: Education &amp; Science
---

### Post by Proton Soup on 2008-09-10
hi.  i just installed Scilab via the Add/Remove programs interface of an Ubuntu Hardy Heron.  install appeared to go OK, but when i type help at the command prompt in Scilab, i get

> 
Can't go to directory /usr/lib/scilab-4.1.2/man/eng/programming
 !--error 998
chdir: Internal Error

(...etc)


hopefully no errors there because i couldn't copy the text and typed that in.  

also, a little window pops up labelled 'Scilab Progression Bar' that says 'Parsing help files', yet it never seems to finish parsing.

if i look in /usr/lib/scilab-4.1.2/ , there is indeed no /man directory.

i am a bit new to all of this, but i assume that maybe scilab is trying to do some additional configuration that falls under what Ubuntu considers program installation, yet the privileges that i entered password for at installation no longer exist?  any clues on how i can go about fixing this?

TIA

---

### Post by Proton Soup on 2008-09-11
ok, so i submitted a bug report at scilab and was informed that this is an ubuntu error.  resolution was 

> 
It is not a bug of Scilab, it is ubuntu related. Install the doc package
please:
# aptitude install scilab-doc

but i used "sudo apt-get install scilab-doc" instead and it seems to work now.

searching for scilab-doc, i then find [**this thread**]("http://ubuntuforums.org/showthread.php?t=166857") and it seems to be a known problem with the package manager?  

also, looking at [**this error here**]("http://ubuntuforums.org/showthread.php?p=3473349#post3473349") and its [**response**]("http://ubuntuforums.org/showpost.php?p=4723143&postcount=21"), i tried initiating Scilab from the Konsole and also got 
```
/usr/bin/scilab: 28: /usr/lib/pvm3//lib/pvmgetarch: not found
```

which i fixed by installing pvm as r4e suggested.


so, i'm not even sure this is all correct or complete, but it seems we need at a minimum:

```
$ sudo apt-get install scilab scilab-doc pvm
```

how do i go about verifying this and what is the process to get the package amended to save others from suffering?

actually, maybe scratch pvm.  if it's this: [http://en.wikipedia.org/wiki/Parallel_Virtual_Machine](http://en.wikipedia.org/wiki/Parallel_Virtual_Machine) , then it's more like an additional package that most users will never use, and the scilab command line "error" is just an annoyance.  but not including scilab-doc is silly, it really ought to be in there.

---

