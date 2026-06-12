---
title: "g95 fortran compiler"
date: 2005-12-09
forum: Desktop Environments
---

### Post by elementary on 2005-12-09
I am trying to get this working but I'm having a bit of trouble. I download the tar, unpack it...and it should work right? I unpacked it in /bin/g95.
When I tap the 'g95' command to compile something i get 'command not found'. What am I to do?

This is the command I used:

wget -O - [http://www.g95.org/g95-x86-linux.tgz](http://www.g95.org/g95-x86-linux.tgz) | tar xvfz -
ln -s $PWD/g95-install/bin/i686-pc-linux-gnu-g95 /usr/bin/g95


Thanks all.
Bart

---

### Post by Miguel on 2006-04-18
Hi elementary,

I am sure it is too late, but, anyway. Your problem is probably a syntax one. First, I would untar g95 to /usr/local (this is the common place for programs outside the repositories). And then I would create the g95 symbolic link... in your PATH:

```

$ cd /usr/local
$ tar -zxf route-to-g95/g95-x86-linux.tgz
$ cd /usr/local/bin
$ ln -s ln -s /usr/local/g95-install/bin/i686-pc-linux-gnu-g95 g95

```

This should work as long as /usr/local/bin is in your PATH. You can check it by typing "echo $PATH" on the terminal. Just two more things: yesterday (17-4) was released a new g95 version, although it is compiled with dapper's default gcc 4.0.3. I'm not sure if this will work on breezy, though it seems to work on dapper.

And last, but not least, sorry for the late answer. I just saw your topic.

---

### Post by Miguel on 2006-04-18
Oh! I forgot! Your problems were probably caused by trying to make the symlink without root permissions. It should have worked with sudo.

---

### Post by harishg on 2006-04-18
I got the g95 compiler from the repository using synaptic and it works fine.

-H

---

### Post by Miguel on 2006-04-18
g95 in the repositories? Are you sure, harishg? I mean, I'm currently running Dapper, but the only FORTRAN 90/95 compiler I've seen in the repos is gfortran... which is not the same.

Actually, the only program I have compiled with g95 in my laptop, PWscf, can be compiled with g95 but not with gfortran.

AFAIK, gfortran is the FORTRAN compiler of the FSF, like gcc and g++, and is the substitute of g77 in gcc-4.0. g95 is a fork of a long ago common source, due to differences.

---

### Post by harishg on 2006-04-18
I use breezy badger.

&&&& gfortran 4.0 
The GNU Fortran 95 compiler
This is the GNU Fortran compiler, which compiles
Fortran 95 on platforms supported by the gcc compiler. It uses the
gcc backend to generate optimized code.

---

