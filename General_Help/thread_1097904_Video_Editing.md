---
title: "Video Editing"
date: 2009-03-16
forum: General Help
---

### Post by hacker_at_linux on 2009-03-16
Hey all I have got a project form skool to make a movie on some social Issue.
I am now using ubuntu for quite some time but not have came across any good video editing software.
People I want some good video editing software like ULEAD VIDEO STUDIO or SONY VEGAS in windows for my project.

Can you name any good software on Linux or you prefer software on windows to do the job

---

### Post by cd-r80 on 2009-03-16
Try Kino or Kdenlive (crashes more). In my opinion a good movie is not thousand transition effects or other effects.

---

### Post by hacker_at_linux on 2009-03-16
even I know this man that video edditing is not about thousand effects.
But I want some powerful tool with easy interface like ULEAD.
I have tried kino is just like windows movie maker not very customisable.
aaa so if you have any other software weather proprietary dosent matters Please give its name and also the lnk if you wish.

And if you have some good movie making ideas on Social issues Please post here

---

### Post by GrfyGrumpyBear on 2009-03-16
If you want the barebones minium, try PiTiVi. A powerful video editor is also Open Movie Editor.

---

### Post by cd-r80 on 2009-03-16
Well that kdenlive is easy to find in google and it is powerfull and quite easy. I know others but they like Cinelerra are not any Ulead like.

---

### Post by hacker_at_linux on 2009-03-16
But you said that this kdenlive crashed often.
DOes it really work????

---

### Post by mb_webguy on 2009-03-17
Since most of the suggested apps are in the repos or available through PPAs, my suggestion would be to install each of them and spend a few minutes playing around to see which one you like best.  What works for one person may not work for another.  Kino, KdenLive, Open Movie Editor, LiVES, Cinelerra, and Blender are all good video editing applications used by many people.  Which one is best for you depends on your specific needs and preference.

---

### Post by redxine on 2009-03-17
I second using Cinelerra for video editing. It's simple enough and definately powerful. Just need to spend a little time getting used to it's interface. All you need to know is the [ in and ] out keys. I've used Kino before and it used to work just great for me, until it reecently started crashing in 8.10.

---

### Post by hacker_at_linux on 2009-03-17
Man a great problem in installing Cinelerra.
I extracted it them to a folder on desktop. Gave the command [FONT="Century Gothic"]./configure[/FONT]. It said "configured successfully. now you can install me by 'make'" so I did the same issued the command make but then It is now showing me an error "Error 2" the code was as following 

libmjpeg.h:34:71: error: png.h: No such file or directory
make[2]: *** [i686/jpeg.o] Error 1
make[2]: Leaving directory `/home/ashmeet/Desktop/cinelerra-4/quicktime'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ashmeet/Desktop/cinelerra-4'
make: *** [all] Error 2

what is this error and how to with it??

And when I issue the command make install the following error comes:

 make install
make -f build/Makefile.cinelerra install
make[1]: Entering directory `/home/ashmeet/Desktop/cinelerra-4'
make -C plugins install
make[2]: Entering directory `/home/ashmeet/Desktop/cinelerra-4/plugins'
mkdir -p ../bin/fonts
cp fonts/* ../bin/fonts
mkdir -p ../bin/shapes
cp shapes/* ../bin/shapes
cp ../thirdparty/mjpegtools*/mpeg2enc/mpeg2enc ../bin/mpeg2enc.plugin
cp: cannot stat `../thirdparty/mjpegtools*/mpeg2enc/mpeg2enc': No such file or directory
make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/ashmeet/Desktop/cinelerra-4/plugins'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/ashmeet/Desktop/cinelerra-4'
make: *** [install] Error 2


Please tell

---

### Post by mb_webguy on 2009-03-17
You shouldn't be trying to install Cinelerra from source.  Cinelerra provides deb packages for Ubuntu on [its website]("http://cinelerra.org/getting_cinelerra.php#ubuntu").  You can optionally add the Cinelerra repositories to ensure that you have the most updated version of Cinelerra.

Compiling from source should always be a last resort.

---

### Post by hacker_at_linux on 2009-03-17
Hey man how to do this there is only one deb file and that is Akirad.
I dont know what is that
I issued all the commands there but It is not installing anything.

Dont you have some good link where the instructions are clear ????? to nistall

---

### Post by cd-r80 on 2009-03-17
[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php) and there was one repository have you tried that?

8.10 Intrepid Ibex

    for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
    deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-intrepid main

I still recommend Kdenlive & save often your work. It has almost human friendly interface.

---

### Post by hacker_at_linux on 2009-03-18
Kdenlive I dont think so It switches on.
It crashes as and when it starts so no point using kdenlive but I have tried Cinelerra. that is the thing I needed in my life for editing its good

---

### Post by fragos on 2009-03-18
I'm a noob at video editing. Lives is the only video editor I found that was easy to use and very flexible about video sources. It even let me make a video from a single jpeg and even supports animated GIFs as video output.

[http://www.getdeb.net/search.php?keywords=lives](http://www.getdeb.net/search.php?keywords=lives)

---

### Post by hacker_at_linux on 2009-03-19
From where did you got a good download of that software
I was not able to gat a good mirror for that Mali me its link also .

---

### Post by fragos on 2009-03-19
> **hacker_at_linux said:**
> From where did you got a good download of that software
I was not able to gat a good mirror for that Mali me its link also .

I'm in the US and am not familiar with any mirrors in your country. In the US I regularly download debs from this site.

[http://www.getdeb.net/search.php?keywords=lives](http://www.getdeb.net/search.php?keywords=lives)

---

