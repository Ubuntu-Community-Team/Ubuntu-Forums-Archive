---
title: "K3DSurf vs MathMod"
date: 2014-03-07
forum: Education &amp; Science
---

### Post by nextstep on 2014-03-07
Hi all,
Just to mention that right now I'm working a a new application, MathMod, as a remplacement of K3DSurf.
You can download the latest source code of MathMod v1.0 from sourceforge: [http://sourceforge.net/p/mathmod/branches/HEAD/tree/1.0/](http://sourceforge.net/p/mathmod/branches/HEAD/tree/1.0/)
The new sourceforge project is : [http://sourceforge.net/projects/mathmod/](http://sourceforge.net/projects/mathmod/)
 ( We hope that one day, MathMod will make its way to the Ubuntu Repos, as K3dSurf once did  :) )
Bugs reports and comments are welcome 
Have a fun ;)
Abderrahman

---

### Post by monkeybrain20122 on 2014-03-08
Well downloaded the src zip file, what am I supposed to do with it? There is no instruction or documentation and the readme file is empty.

---

### Post by nextstep on 2014-03-08
There is one at [https://sourceforge.net/projects/mathmod/files/MathMod-1.0/](https://sourceforge.net/projects/mathmod/files/MathMod-1.0/) :
*****************************************
Binary information:
A 32Bit Windows version of MathMod-1.0-Alpha is provided in the "bin" folder 
Source code compilation:
The source code is available in the "src" folder Use QtCreator from Qt5.x to compile this project 
MathMod roadmap: 
MathMod V 1.0 Alpha (done) 
MathMod V 1.0 Beta 
MathMod V 1.0 release candidate 
MathMod V 1.0 stable (April 2014)
*******************************************
Also, the stable release will include an install/uninstall process and a documentation for beginners in the mathematical modelling.


On youtube:

[http://youtu.be/7l86iN7eP_k](http://youtu.be/7l86iN7eP_k)


[[img]http://farm4.staticflickr.com/3755/11608078523_6355101784_o.png[/img]](http://www.flickr.com/photos/13168115@N05/11608078523/)

---

### Post by monkeybrain20122 on 2014-03-09
Well those are not really instructions. How to use qtcreator to compile? I don't think the version in the 13.10 repo is 5.x btw (I could be wrong on that) I will just wait for the stable release.

---

### Post by nextstep on 2014-03-20
Hi,
MathMod-1.0-Beta is available for download from : [https://sourceforge.net/projects/mathmod/files/MathMod-1.0/Beta/](https://sourceforge.net/projects/mathmod/files/MathMod-1.0/Beta/)
Three precompiled packages are available : 
MathMod 64/32 Bit for Windows  
MathMod for Linux-Ubuntu 64Bit (you should however install Qt5)
Cheers

---

### Post by Votlon on 2014-03-26
Good luck on le software :)

---

### Post by nextstep on 2014-03-28
Thank you Volton :)

---

### Post by sean-fitzpatrick on 2014-03-31
Thanks for reviving this project. Among the currently available downloads, there is one labelled Linux64. The .zip file contains two .js files and one binary file with no file extension. Is it just a binary blob meant to be executed? I'm not entirely clear on the instructions for compiling, so I might also wait for the RC. Will there be a .deb file for installation on Ubuntu?

---

### Post by nextstep on 2014-04-01
MathMod was compiled under Ubuntu 64Bit with Qt5.2.
The binary needs some libs from qt5 to be installed before running.
If you dont know exactly what to do, the easiest way is to install a Qt5 program that will install the needed library in the same process.
You can install, for example "Qt Creator" (look for it and install it with the Ubuntu Software Centre).Runing the binary after that should be OK
The ziped package should work for all Linux distro (Ubuntu, Debbian, Suze, Fedora, Schlakware...) and, for now, I can't support all there packaging file formats.
Cheers

---

### Post by sean-fitzpatrick on 2014-04-01
OK, thanks. And if I want to compile from source, you mention to use the Qt5 creator program. If I want to build a deb package I would normally run something like dpkg-buildpackage from the source directory. Is that an option, or is it necessary to use the Qt5 creator to go straight to the binary?

---

### Post by nextstep on 2014-04-01
To just compile from source, you don't realy need Qt Creator: 
Open a terminal and go to the folder where is the source code and execute:
[SIZE=4]**qmake ; make **[/SIZE]
Thats all!
For the debian package  you need a smal scrit for packaging for debian. There are plenty of examples of other packaged programs that you can adapt to your needs.
NB: you will need probably to install the QtCreator package to make the commands "qmake" and "make" (and others) available  on you Linux inatallation

---

### Post by sean-fitzpatrick on 2014-04-18
OK, got it running; thanks for the help. Some comments regarding the program itself, as it compares to its predecessor: the rendering looks good and I'm happy to see the library of prepared examples. It feels a little less intuitive/discoverable though. The main thing I liked with K3DSurf was that I could suggest it to my students as an easy way to render and visualise the various surfaces they would encounter in their homework. So for example if there was a particular level surface you're interested in, you could open up the program, replace the function for the Schwartz surface with a different function, and hit run. You could then play around with the various parameters. Right now that doesn't seem to work for me in MathMod - my guess is that I would need to write a script modelled on one of the existing ones if my surface wasn't already in the examples, which is more than I could reasonably expect from most students.
Any chance you're working towards an interface closer to what K3DSurf had? The use case here is one where I'd have my surface in mind, choose either the isosurface or parametric tab accordingly, type the relevant functions into the boxes, set my parameters, and hit run. Further interaction with the surface might involve moving sliders to adjust the mesh density, parameter ranges, etc. Thanks.

---

### Post by nextstep on 2014-04-19
Hi,
Hope [this youtube videos]("http://youtu.be/FBTSLBNCp1U") will help. As I mentioned before, MathMod is using a scripting language to describe it's mathematical models.
Scripts can become quite complex to read/update when it include more than one component (see the BlackHole example), this is why I'm working on a "script editor" that will make it easy to view/modify the scripting language.  As shown in the video, it already have some look and feel "a la K3DSurf" and support some basic operations, but it lacks some essential features and still unstable especially with complex scripts manipulations...
Working on it :)
Abderrahman

---

