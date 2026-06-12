---
title: "Danger From the Deep -- Permissions?"
date: 2007-07-29
forum: Gaming &amp; Leisure
---

### Post by gjtoth on 2007-07-29
I've managed to get it installed ok but, when I go to run it, I get nothing.

Starting it from the terminal produces:

Caught exception: DftD error: Can't open directory /usr/share/games/dangerdeep/objects/airplanes/
Stack trace: (5 frames)
0x8070202 in dangerdeep at ??:0
0x806d431 in dangerdeep at ??:0
0x806d4f1 in dangerdeep at ??:0
0xb7a5b040 in __libc_start_main at ??:0
0x804e6a1 in dangerdeep at ??:0

I'm thinking this may be a permissions problem but, I can't figure how to get around it.

Can anyone give me some insight to this?

---

### Post by cogadh on 2007-07-29
I get this message when I try to run it:
```
dangerdeep: error while loading shared libraries: libfftw3f.so.3: cannot open shared object file: No such file or directory
```
I have no idea what the libfftw3f.so.3 library is. Which package did you use to install it?

EDIT - nvm, I figured it out, it needed the fftw3 package from the repositories

I don't have the same problem as you however, the game runs fine. I'll ask again, which package did you use to install it? I used the .bin file from the site.

---

### Post by gjtoth on 2007-07-29
> **cogadh said:**
> I get this message when I try to run it:
```
dangerdeep: error while loading shared libraries: libfftw3f.so.3: cannot open shared object file: No such file or directory
```
I have no idea what the libfftw3f.so.3 library is. Which package did you use to install it?

I just downloaded what they had on their website and let 'er rip.

---

### Post by cogadh on 2007-07-29
There are three or four different Linux packages on the site, which one did you use?

---

### Post by gjtoth on 2007-07-29
> **cogadh said:**
> There are three or four different Linux packages on the site, which one did you use?

I couldn't seem to get the .bin to run so:

dangerdeep_0.3.0.1_i386.deb  is the one I used.

---

### Post by cogadh on 2007-07-29
That might be the problem, that is the unstable, unmaintained version of the game. 

In order to get the .bin to run, you first need to make it executable. I just do that by right-clicking on the file, select permisions, go to the permissions tab and check the box that says "Allow executing this file as a program". Then its just a simple matter of running it like this:
```
sudo ./dangerdeep-0.3.0-linux-installer.bin
```
After that, I just had to install the Fast Fourier Transform library and the game runs fine.

---

### Post by gjtoth on 2007-07-29
> **cogadh said:**
> That might be the problem, that is the unstable, unmaintained version of the game. 

In order to get the .bin to run, you first need to make it executable. I just do that by right-clicking on the file, select permisions, go to the permissions tab and check the box that says "Allow executing this file as a program". Then its just a simple matter of running it like this:
```
sudo ./dangerdeep-0.3.0-linux-installer.bin
```
After that, I just had to install the Fast Fourier Transform library and the game runs fine.

Nope.  That didn't work.  I copied it to my home directory and tried it from there.  Nada.

-----------  GOT IT!  Forgot to change permissions on the file.

Thanks for your help.

---

### Post by Daveth on 2007-08-15
Fast Fourier Transform library ??? Where from?

I played this on 64 bit sabayon the other evening - very nice!

---

### Post by cogadh on 2007-08-16
From the Ubuntu repositories, just search Synaptic for it, you'll find it.

---

### Post by KingHanco on 2007-08-16
I will give this game a try. Looks cool.

---

### Post by yoyoned on 2008-02-15
install fftw3

---

### Post by iheartubuntu on 2008-02-26
> **cogadh said:**
> That might be the problem, that is the unstable, unmaintained version of the game. 

In order to get the .bin to run, you first need to make it executable. I just do that by right-clicking on the file, select permisions, go to the permissions tab and check the box that says "Allow executing this file as a program". Then its just a simple matter of running it like this:
```
sudo ./dangerdeep-0.3.0-linux-installer.bin
```
After that, I just had to install the Fast Fourier Transform library and the game runs fine.

I just changed the permissions and nothing happens when I run the command. I get this, instead:

> ./dangerdeep-0.3.0-linux-installer.bin: 1: cannot open !DOCTYPE: No such file
./dangerdeep-0.3.0-linux-installer.bin: 1: html: not found
./dangerdeep-0.3.0-linux-installer.bin: 2: Syntax error: newline unexpected

Any suggestions? Thanks!

---

### Post by AR_Kozz on 2008-06-19
Well this game is pretty cool even though it is in alpha version, my pc doesn't get much of a framerate but I have been able to successfully sink 25000 tons with a type VII

One thing that has been really making me mad though, is how do you aim the dang deck gun? The controls just say how to man it and shoot it. Whenever I shoot it, it always falls short of my target, and eventually I fire it and the game suddenly ends "you have been sunk" does it blow up, or what? 

Until the dang thing can be aimed or aims by itself properly it is quite useless, next time I run out of torpedoes I will just end the mission

---

