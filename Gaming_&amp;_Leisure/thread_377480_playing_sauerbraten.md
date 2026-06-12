---
title: "playing sauerbraten"
date: 2007-03-06
forum: Gaming &amp; Leisure
---

### Post by borgdrone89 on 2007-03-06
hi ppl,
im new to the unix environment, so plz dont use really technical terms n me...
(ubuntu 6.10 amd64)
ok, i downloaded the unix version of a game called sauerbraten (cube2)
i then did chmod +x sauerbraten_unix to allow it to be run, and then typed in ./sauerbraten_unix to run it.

the response was that I needed the SDL, SDL-image, SDL-mixer, openGL libraries and then needed to follow some more instructions to compile the game.
so, i have downloaded the SDL libraries, in RPM format, and cant find the right openGL library.

also, when trying to run the .rpm files, it turns out I need to get the RPM program to run the files.

so after scouring the [www.rpm.org](www.rpm.org) site for the correct source code to download (which needs "gcc" and "make")

so, can someone help me get RPM, openGL library and then tell me how to compile these?

---

### Post by Stephen Howard on 2007-03-06
Can I ask why you're using RPM?  The standard (ie supported) package distribution system on Ubuntu is .deb.  RPM is a Redhat, Mandrake etc distro method.

---

### Post by Stephen Howard on 2007-03-06
In any event, go to a command line at type:

[INDENT][FONT="Fixedsys"]sudo apt-get install libsdl1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev  libsdl-net1.2-dev [/FONT][/INDENT]

Then try to run it again.  If it doesn't work, type:

[INDENT][FONT="Fixedsys"]ldd {name of the executable}[/FONT][/INDENT]

A list of the libraries required by the application and whether they are found/not found will be printed out - see what libraries are missing and use apt-get / synaptic etc to install them.

---

### Post by borgdrone89 on 2007-03-06
ok, well i found out that rpm is not ubuntu's thing, .deb is...
anyway, i went to the sauerbraten/src directory and typed in make install,
and it said 
'configure:error:C compiler cannot create executeables'
I'm learning to use linux distros cos at the moment, ati's vista drivers are screwing with my system and not letting me use any 3d application.
I also need to know how to use linux to give me a head start for computer science stuff at uni..(2nd year we use red-hat?)
so i did some searching and found out about something called build-essential
so i tried installing that, but it said something about dependency error libc6-dev|libc-dev
so i tried installing these two files, but they both required other things like libc6....

I am really confused, and a little annoyed that it takes this much random installing just to get a game to compile and run

plz help...

---

### Post by borgdrone89 on 2007-03-06
im guessing that sudo apt-get........ needs an internet connection to work?

---

### Post by Phenax on 2007-03-06
> **borgdrone89 said:**
> ok, well i found out that rpm is not ubuntu's thing, .deb is...
anyway, i went to the sauerbraten/src directory and typed in make install,
and it said 
'configure:error:C compiler cannot create executeables'
I'm learning to use linux distros cos at the moment, ati's vista drivers are screwing with my system and not letting me use any 3d application.
I also need to know how to use linux to give me a head start for computer science stuff at uni..(2nd year we use red-hat?)
so i did some searching and found out about something called build-essential
so i tried installing that, but it said something about dependency error libc6-dev|libc-dev
so i tried installing these two files, but they both required other things like libc6....

I am really confused, and a little annoyed that it takes this much random installing just to get a game to compile and run

plz help...

It's not random, most applications abide by the GNU build system which is quite good and organized.

Second of all, you probably want to install *build-essential*

---

### Post by matthekc on 2007-03-06
i also do not have a good internet connection.  i have some advice i hope its useful.  I'm going to assume you use someone elses internet then put things on storage then to your pc.  packages.ubuntu.com is the viewable version of an apt-get library it has an easier to install sauerbraten.deb  building from source is just a lot harder and not worth it unless you need something not in the library  

does this help?

---

### Post by borgdrone89 on 2007-03-07
well, my net connection is fine, its just we haven't gotten in a router for the network yet..
so i am running back and forth between comps with a flash drive, except for at the moment im using the other computer's network cable.
um, i did try to install build-essential, but it came up with those dependency errors, for libc6-dev|libc-dev, which i couldnt find in the edgy release packages section.
so i will try the sudo apt-get thing now..

---

### Post by matthekc on 2007-03-07
those libc's  are in there in the libs or maybe the development section trust me i kind of know :(  but have fun with apt get i hear it's really nice :)  it might be useful for someone in a similar situation to know these things though.

---

### Post by borgdrone89 on 2007-03-07
ok, after doing that and then doing sudo apt-get install build-essential, i was able to make install and play the game.. lol i was getting 1-7 fps... will check that out. also, whenever i scroll down in a window or move a window, it does weirdly slow refresh things, and the screen "jumps". any ideas?

---

### Post by matthekc on 2007-03-07
i have an idea what the problem might be but i'm not an expert at resolving it.  Your probably running the default video card drivers you are going to need an upgrade .i've yet to do this on my system i think a program called envy makes it easy a quick forum search should help. i'll be on for a little longer pm me if you need more help

---

