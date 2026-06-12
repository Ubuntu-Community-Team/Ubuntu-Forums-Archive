---
title: "Basic setup help"
date: 2009-01-06
forum: General Help
---

### Post by xaephod on 2009-01-06
Hey folks.

Ok I just downloaded the latest version of Ubuntu (Jan 6, 2009) and I'm having a few issues.

Sound: I have onboard sound (AC97) on an Asus A8n32 SLI deluxe Mobo. I Dled the drivers from the asus site and could not get them to install. I installed a Creative Audigy and Dled drivers and could not install them.

I followed the directions as best I could but I really know linux on a basic level. I did ./install and it seemed to work.
But all the instructions tell me to Run make then make install. Well, how do I run make? is it the ./ thingy? or is there some command to run a program. The help instructions should really explain that to people who are migrating.


Since I'm typing this on my windows computer, let me just post one line of what I'm getting:
cp: cannot stat 'snd-hwdep.ko': No such file or directory.


I honestly have no idea whats going on. Isn't the install program suppose to create the proper folders and such? And why can't they just make a .exe like in windows that installs the drivers and all?

If this has been covered before, sorry. But before I pull my hair out, help me out :)

---

### Post by zeronothing on 2009-01-06
Ok when they say run "make" they mean to just simply type in terminal:

make

then to run "make install", just type in terminal:

sudo make install


in general the "make" command compiles the driver. The command "make install" takes the compiled driver and installs the driver.

---

### Post by gettinoriginal on 2009-01-06
First, may I suggest some helpful reading:  :P
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
It is important to realize that linux is NOT windows, so some of the things you tried will not fly here.  But then most of us went through that in the beginning.  Try the above reading, then if you still have problems, post them back here with descriptive titles, and help is on the way  (see sig)  :popcorn:

---

### Post by xaephod on 2009-01-06
Great! I'll read that thread!

thanks

---

### Post by redilyn on 2009-01-06
Im curious, you say you installed an Audigy??

You shouldn't have to download and install any drivers for the audigy it just works in ubuntu...

---

