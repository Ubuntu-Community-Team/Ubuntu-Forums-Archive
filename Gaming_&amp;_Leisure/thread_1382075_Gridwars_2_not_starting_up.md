---
title: "Gridwars 2 not starting up"
date: 2010-01-15
forum: Gaming &amp; Leisure
---

### Post by exkend on 2010-01-15
Hello, I'm pretty new to Ubuntu/Linux and was wondering how to start gridwars 2 on 9.10. I have made sure the "allow executing file" has been activated in gridwars properties and nothing seems to happen.
 I'm running 9.10 with an ATI 4850 card.

Any help would be appreciated.

exkend

---

### Post by 5nak3 on 2010-01-15
Hiya, 

Firs thing first, make sure the graphics card is actually working properly and has the latest drivers installed. This I'm guessing isn't the problem, but it will ruin the experience of any sort of gaming you may want to do on Linux. I have not used closed source ATi drivers before so I have no idea what the latest version is.

Secondly, where did you download Gridwars from? I think playdeb.net used to host a downloadable deb file for Gridwars although I couldn't find it when I looked for it just now. 

getdeb.net may indeed still host a file although again I couldn't find a .deb.

Anyway, if memory serves me right the reason Gridwars does not work is because of a dependency issue in Karmic. 

Best think to do is open up a terminal

Applications -> Accessories -> Terminal

And then drag the executable for Gridwars into the terminal and press enter, what this should do is try to launch the game and the terminal will in fact show an error output allowing you to see where the problem lies.

I also found this post that may be of use to you and will most likely solve the issue, but again I've not tried this personally.

[http://anjilslaire.wordpress.com/2009/12/08/gridwars-karmic-style/](http://anjilslaire.wordpress.com/2009/12/08/gridwars-karmic-style/)

Do update and let us know what happens :)

---

### Post by exkend on 2010-01-18
Hi, I downloaded gridwars 2 from softpedia: 

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Arcade/Grid-Wars-2-17865.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Arcade/Grid-Wars-2-17865.shtml)

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Arcade/GridWars-2-37625.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Arcade/GridWars-2-37625.shtml)

I have tried booting from the terminal with no luck:

 error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I have tried to install libstdc++5 but to no avail.

Good luck getting your version working. This game is definitely a GNU/Linux game treasure, shame it's not a default game on every distro.

exkend

---

### Post by 5nak3 on 2010-01-18
Hi there,

Well just out of curiosity as to where the problem may lie I went ahead and installed Gridwars 2.

To do this I downloaded and installed the libstdc ++.so.5 from here:

[http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download)

Please note that this link is for 32bit operating systems so if you are running a 64bit operating system you may have problems.

Then I downloaded and extracted the gridwars 2 game from this link:

[http://gridwars.marune.de/bin/gridwars_lin.zip](http://gridwars.marune.de/bin/gridwars_lin.zip)

Once extracted the folder should have a file named "gridwars" inside, right click, select properties and make sure it is set to run as an executable, then you can double click it and it should run with no problems. 

As I said, these are the steps I used just this minute and the game works perfectly, the error you mention seems to suggest it is simply a libstdc error as opposed to anything else. I would recommend you uninstall any gridwars and libstdc ++.so.5 you may have installed reboot and reinstall again as per the instructions from the following link

[http://anjilslaire.wordpress.com/2009/12/08/gridwars-karmic-style/](http://anjilslaire.wordpress.com/2009/12/08/gridwars-karmic-style/)

Or as I have stated (which to be hoenst with you I just followed from the above link).

If not post some more specs of your system maybe someone could help you out :)

---

### Post by exkend on 2010-01-19
I'm running 9.10 64bit and have tried every step you mentioned. I cannot install the 32bit version as Karmic won't allow me. 

 Thanks for the help

exkend

---

### Post by 5nak3 on 2010-01-19
Yeah I thought that you might be a 64bit user and that might be the problem.

From my understanding, Intrepid and Hardy included the libstdc++.so.5 dependency which was needed for the game.

Jaunty and Karmic if I'm not mistaken do not have this, that is why we need to install that dependency first.

Now the problem is the link I posted which comes from the debian repos is a 32bit file. I have never tried to install that on a 64bit system, and this maybe where the problem lies.

Your terminal output makes mention of that file not being installed or found and thus being your only problem. As a result my best guess would be you need that, but you need to ensure that it installs on your system.

Now unless the debian repos have a 64bit version of that dependency you may need to look elsewhere and find a version of the dependency which is compatible with 64bit OS. If you do that then you should be able to run the game without any problems.

This blog seems to mention a problem with 64bit OS and the aforementioned dependency:

[http://blog.dalejefferson.com/2009/09/gwt-on-64bit-ubuntu-karmic-910.html](http://blog.dalejefferson.com/2009/09/gwt-on-64bit-ubuntu-karmic-910.html)

This forum topic also seems - from my brief glance - to talk about the problem you are having:

[http://ubuntuforums.org/showthread.php?t=1282957](http://ubuntuforums.org/showthread.php?t=1282957)

Hope that helps you.


----EDIT----

Also there is another post in the gaming and leisure forums which is asking for a 64bit version of GW2 here:

[http://ubuntuforums.org/showthread.php?t=1384355](http://ubuntuforums.org/showthread.php?t=1384355)

Maybe this will solve your problem.

---

### Post by exkend on 2010-01-22
Having read you reply and link I have decided against trying "force install" libstdc++5 on my machine. I'm really happy with the way everythings running and don't feel like going that extra mile for gridwars2, even though it's pretty great.
 Has anyone told you that you are a credit to the human race? Well you are. Thanks so much for your help.

Exkend

---

### Post by 5nak3 on 2010-01-22
Well thank you for those kind words, although I must admit that most of my suggestions were in fact due to the fact I did some quick searches on your behalf. 

I'm sorry you couldn't get it working. I know one forum member around here "Artificial Intelligence" is quite good with 64bit systems and has I believe written a few guides, maybe he has some suggestions. 

Other than that, I agree that maybe choosing to force and break anything on the system may not be a good idea. Although I would recommend to bump the topic now and then maybe someone can give you an idea that will solve your problem.

---

### Post by Perfect Storm on 2010-01-23
> **exkend said:**
> Having read you reply and link I have decided against trying "force install" libstdc++5 on my machine. I'm really happy with the way everythings running and don't feel like going that extra mile for gridwars2, even though it's pretty great.
 Has anyone told you that you are a credit to the human race? Well you are. Thanks so much for your help.

Exkend

Instead of force install, use **getlibs** application. It's heaven send for the 64-bit users. You problem can easily be solved by like this: [http://ubuntuforums.org/showpost.php?p=8349139&postcount=10](http://ubuntuforums.org/showpost.php?p=8349139&postcount=10)

---

### Post by 5nak3 on 2010-01-23
Told you he'd have something to say about the whole situation and also makes all look so easy :)

Well Done AI!

---

### Post by exkend on 2010-01-27
Good news!

 After having tried everything that was previously advised I came upon A.I's 64bit guide. I was following the instructions to run Darwinia and installed the code into terminal. Darwinia refused to run due to a missing libgtk.1.2.so.0 or something. However I thought I'd give GW2 another try and it works.
 Ubuntu is an absolutely crazy OS for a beginner but it does pull through in the funniest of ways.

PS. I'm running this version of Gridwars 2:

[http://linux.softpedia.com/progDownload/Grid-Wars-2-Download-17865.html](http://linux.softpedia.com/progDownload/Grid-Wars-2-Download-17865.html)

PPS. Now how the hell do I get Darwinia running. The fun never ends..

---

