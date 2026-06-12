---
title: "gonstruct Graal Level Editor"
date: 2008-12-21
forum: General Help
---

### Post by reydempto on 2008-12-21
Hello again forums.


I am trying to run this Level editor for a game called Graalonline. There is a user-made lightweight level editor for this game that i used on my other computer, and it ran just fine, but for some reason it will not execute on this one. I am running Ubuntu 8.10. the program is called gonstruct 0.1.6--i didn't want to link it in case it was against the rules, but if you google it, you'll see the only place you an download it from. 


any help on this matter would be greatly appreciated!


-Rey

---

### Post by zephyrcat on 2008-12-21
It looks like you will have to compile it from source. Check out this tutorial:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Post back any errors you get.

---

### Post by reydempto on 2008-12-21
I didn't have to last time--inside the tar.gz is this:

a readme
an html leading you to their homepage
and the x-executable application.

there's nothing to compile, it's supposed to work out of the box, but for some reason it isn't.

I tried dragging the file into a terminal window and i get this error:

/home/reydempto/Desktop/gonstruct: error while loading shared libraries: libboost_system.so: cannot open shared object file: No such file or directory


am i being a tard or is this part of the problem?

---

### Post by zephyrcat on 2008-12-21
How did you install it last time?

Try issuing the command ./*file name of x-executable* from the command line.

---

### Post by reydempto on 2008-12-23
Okay, last time all i did was download the tar.gz file. i opened it, inside are 2 readme's and one x-executable. the readme's simply state that all you have to do is extract and run, so that's what i did. For some reason, it's not working the same way on this pc. so i decided to try what you suggested (zephyrcat), and run ./gonstruct in a terminal window, and this is what i get:


> 
./gonstruct: error while loading shared libraries: libboost_system.so: cannot open shared object file: No such file or directory


I've been spending my time trying to successfully install libboost, but i have been having no luck. any ideas?

---

### Post by zephyrcat on 2008-12-23
I can't vouch for it, but this might be what you are looking for:

[http://packages.debian.org/lenny/libboost-dev](http://packages.debian.org/lenny/libboost-dev)

Is there any such file on the CD? Is it mentioned in the documentation?

---

### Post by reydempto on 2008-12-23
That's the confusing thing about it, when i apt-get install libboost-dev, it says i already have the latest version O.o

The specific file is not mentioned, but the readme said i would need boost to run it.

Anyone know what libboost_system.so is? It has to be in some specific package...

---

### Post by reydempto on 2008-12-25
-Christmas Bump-

---

### Post by reydempto on 2008-12-28
-Bump-

:)

---

### Post by reydempto on 2008-12-29
-Bump-

Arrgh!!! This is driving me crazy i tell you! I need to get this working before i get kicked off of the development team!   :(:(:(


                                   o--===UPDATE===--o

So, i decided to reinstall ubuntu, only this time i installed hardy instead of intrepid...i still have the same problem. the executable will not open! This is super confusing, because it worked fine on my last computer. all i had to do was unzip the folder and double click the program! wtf is going on here?! I am at my wit's end after attempting this for a WEEK!!!! Any ideas would be, like, totally appreciated! Thank you all

---

### Post by zephyrcat on 2008-12-30
Could you please provide a link to where you are finding this?

I can only find the 64-but version, which will not work unless you installed the 64-bit version of Ubuntu.

---

### Post by reydempto on 2009-01-01
Well, i got the file from londeroth.org, i am just noticing that the 32 bit version is no longer available for download for some reason! Hmm, would the 64 bit version of ubuntu run on my computer if i installed it? I'm still learning all this :)

---

### Post by zephyrcat on 2009-01-01
Yeah, hmmm...

It depends what CPU you are using. The best way is probably to look at the sticker on your machine or the box it came in, if you don't know. (Or look in your manual.)

If you don't want to reinstall, I would check with the author about why the 32-bit version is gone. It is possible there was some bug or something.

---

### Post by reydempto on 2009-01-02
> **zephyrcat said:**
> Yeah, hmmm...

It depends what CPU you are using. The best way is probably to look at the sticker on your machine or the box it came in, if you don't know. (Or look in your manual.)

If you don't want to reinstall, I would check with the author about why the 32-bit version is gone. It is possible there was some bug or something.


Well, my computer is a bit of a frankenstein (it was an old dimension 2400, but i upgraded the cpu, ram, video card, etc..), so no box, no sticker, and no manual lol.

I have a Pentium 4 2.4GHz, if that helps at all..

---

### Post by zephyrcat on 2009-01-02
I actually have a Dimension 2400, too. :-)

It does not look like your CPU supports 64-bit, so that will not be an option. Try contacting the author and see why the 32-bit version is not avaliable. Also, how big is the file? Would it be possible for you to send it to me?

---

### Post by reydempto on 2009-01-08
hey zephyrcat--

i got a new motherboard and made a clean install of ubuntu, and an XP partition for all the games and odd programs that aren't compatible, and now everything is at peace lol.

Thanks for all of your assistance!

+thx for u!!

---

### Post by reydempto on 2009-01-08
hey zephyrcat--

i got a new motherboard and made a clean install of ubuntu, and an XP partition for all the games and odd programs that aren't compatible, and now everything is at peace lol.

Thanks for all of your assistance!

+thx for u!!

---

### Post by WutCake on 2009-11-28
since there is a thread for this already, i'll bump it.

i want to install this by using the github link, 
how do i do that?
it also says something about needing scons to compile.

---

