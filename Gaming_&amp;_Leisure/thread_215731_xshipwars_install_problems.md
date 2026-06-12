---
title: "xshipwars install problems?"
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by crocco on 2006-07-14
Can anyone out there help me install xshipwars?  I have downloaded the tar file and have followed the install instructions (command line stuff).  I keep getting a script error when it trys to find my system's compiler.  Do I have to have the files in exactly the right folder prior to running the command lins stuff?

---

### Post by Perfect Storm on 2006-07-14
Please post the output of the terminal.

Yes you need to be in the right folder.

cd /where/you/extracted/the/.tar

---

### Post by crocco on 2006-07-14
chris@chris-desktop:/usr/share/games/xshipwars/xsw-2.5.5$ sudo ./configure.clien t Linux
Generating Platform Configurator and testing system's compiler...
./configure.client: line 104: make: command not found
./configure.client: line 105: make: command not found
Could not generate Platform Configurator and/or compiler not functioning,
you may not be able to compile/build any programs on this system. Please
review any errors encountered above and consult with vendors.

---

### Post by Perfect Storm on 2006-07-15
You need to configure and compile xsw from your home directory. Unpack xsw on your Desktop and configure it from there

./configure Linux

Then you'll see this:
[IMG]http://www.imageviper.com/displayimage/46694/0/xsw.jpg[/IMG]
Your will properly looks diffrent than mine, but make sure that the dependency are meet before advancing further.

make
sudo make install

There after you move all the data, sound and image folder to its installed location.

---

### Post by crocco on 2006-07-15
followed your instructions, but got the same error

---

### Post by Perfect Storm on 2006-07-15
Have you installed build-essential (you can do it with synaptic package manager or via apt-get)?

Are you sure it's the right file you have downloaded?

---

### Post by crocco on 2006-07-15
I installed "build-essential" and that has gotten me much further, however, it seems that I did not do the dependency thing first.  I am not sure how to handle this...what does this mean?

---

### Post by Perfect Storm on 2006-07-16
It means the application/game need some specific libaries. 
Usually when compiling stuff you also need the development files of the libaries, they are marked with a -dev after the name. Eg: libxpm-dev

---

### Post by crocco on 2006-07-16
So what do I do with them when I get them?  Plop them on my desktop?

---

### Post by Perfect Storm on 2006-07-16
You download them via synaptic package manager then it take care of the rest. Just run the ./configure Linux a couple of times to see if you get all the libs that are required.

---

### Post by crocco on 2006-07-16
Thanks for all you help!  I got it running :KS ...however, I can not get my sounds to work.  I have all the proper files installed in the right libs, however, when I go to the Options > Sounds (within the game) it does not allow me to select any "sound server type" other than "none", so I can not seem to "initialize" according to the test sound button instructions.

---

### Post by Perfect Storm on 2006-07-16
Did you copy the sound files to the right place?

---

### Post by crocco on 2006-07-16
I put the sound folder into:

usr/share/games/xshipwars/

Here is my terminal output:

chris@chris-desktop:/usr/share/games$ cd xshipwars
chris@chris-desktop:/usr/share/games/xshipwars$ ls
etc  images [COLOR="Red"] sounds [/COLOR] xsw-2.5.5
chris@chris-desktop:/usr/share/games/xshipwars$

chris@chris-desktop:/usr/share/games/xshipwars$ cd [COLOR="Red"]sounds[/COLOR]
chris@chris-desktop:/usr/share/games/xshipwars/sounds$ ls
alts      cloak       engine      ring01.wav    transporter
beeps     com         explosions  shield        weapons
bg_music  default.ss  menu        tractor_beam  xsw_logo01.wav

---

