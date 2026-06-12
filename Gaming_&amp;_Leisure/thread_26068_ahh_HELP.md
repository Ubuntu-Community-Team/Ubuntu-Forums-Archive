---
title: "ahh HELP"
date: 2005-04-11
forum: Gaming &amp; Leisure
---

### Post by ninjag5 on 2005-04-11
can somone help me install cedega im new to linux and i dont have a clue howto install it, ive been told to open terminal type gnome-terminal or xterm and hit enter use dpkg to install : sudo dpkg -i cedega... etc

but it doesnt work O_o



help

---

### Post by ninjag5 on 2005-04-11
i just get messages saying dpkg: unable ton install....etc

---

### Post by nobodysbusiness on 2005-04-11
I'm a Cedega subscriber, and I just installed it recently. It's not that hard. (If you want to install it through CVS, then my instructions here won't help you).

First thing, add some extra repositories by following these instructions:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Install a required library by typing this at a console (Applications->System Tools->Terminal):

sudo apt-get install libpng3

Then go to the transgaming web-site, log in, and download the following file:

point2play_1.3.3-1_i386.deb

Install this file by going to the directory where you saved it and installing it:

cd /home/my_username/download/cedega
sudo dpkg -i point2play_1.3.3-1_i386.deb

This should add a transgaming menu item (Applications->Transgaming->Point2Play). Open up Point2Play and go to the Versions tab. Click on "Get Latest Version." Then you can go back to the Main tab and start installing games.

Good luck!

---

### Post by nobodysbusiness on 2005-04-11
I almost forgot, you'll probably want to install NVidia drivers as well, following these instructions:

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

(I sure hope you have an NVidia video card. I hear that ATI puts out slow Linux drivers)

Come to think of it, you may just want to go through the whole guide:
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Another bit of advice: read the release notes for each game that you want to install. The file you want is cedega-4.3_releasenotes.html and it can be downloaded from the same place on Transgaming's website that you got the Point2Play package. Sometimes you have to jump through some hoops to make certain games work. ie. for WoW, you have to copy the four CDs to a dir on your hard drive and run the install from there.

---

### Post by ninjag5 on 2005-04-11
nope no luck i think its bcoz im on a macUX (mac-linux)

ive tryed all that u told me i couldnt install the extra repositrys

i cant install cedega, nothing


i give up i guess ill just cancel my subcription n hope i dont lose to much money

:'(

back to os x for me then


unless anyone can help?

---

### Post by Muchacho_Gasolino on 2005-04-11
hmm i dont know much about PPC
but i can say that you are probably out of luck
cedega only comes in an i386 package, which can be functional on a 64 bit system with adequate libraries, but I don't think that is the case for powerpc.
what I would try is compiling vanilla wine from CVS [www.winehq.org](www.winehq.org) and attempting to install the mac version of whatever game you want to run with wine. What game is it, by the way?

---

### Post by nobodysbusiness on 2005-04-11
You're on a Mac? You should have mentioned that in the initial post. Well, I guess installing the Transgaming packages is out of the question. Maybe it could be compiled from their source-code? I don't know much about that, but there have been other posts to the forums on the subject. I just bought my fiancee a new Powerbook, and Mac OS X is pretty nice. At least you won't have to go back to Windoze.  :smile:

---

