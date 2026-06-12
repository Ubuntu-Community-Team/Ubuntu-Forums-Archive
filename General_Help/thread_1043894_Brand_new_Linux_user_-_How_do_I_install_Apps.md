---
title: "Brand new Linux user - How do I install Apps?"
date: 2009-01-18
forum: General Help
---

### Post by Jynks on 2009-01-18
Hi there...

I am a new linux / ubuntu user. I have tried this os as everyone seamed to be telling me that is is a great way to go... so far i have really enjoyed it.

Anyway.. I wanted to install a C++ Dev environment but I am not sure how to really install anything on this OS. 

I downloaded a linux alterntive to visual C++ that people seamed to recommend. called CODEBLOCKS.

Anyway I got it from here [codeblocks_8.02-0ubuntu1.deb.tar.gz](http://www.codeblocks.org/downloads/5)

Also the site has this little exta thing on it to complicate things

> NOTE: The Linux packages above are compressed archives (tar.gz). When you decompress the package you downloaded on your system, you will find all the .deb packages required to install Code::Blocks.

NOTE 2: The Ubuntu packages have been linked against wxGTK-2.8.7, which is not available in the default Ubuntu repositories.To successfully install these packages, you have to add the wxWidgets repository for Ubuntu in your /etc/apt/sources.list (e.g. deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main).

So now i have this file downloaded... ... now what? how do i install it and everything?

---

### Post by redonwhite on 2009-01-18
One easy way to install applications is to go to Applications---Add/Remove Applications.  There you can search from a bunch of different Applications.  Just check off the box of one you want and then click apply changes.

---

### Post by mfox on 2009-01-18
You'll be happy to know that most apps you'll want to install are readily accessible through the Ubuntu respositories.  All you have to do is click on the Ubuntu menu to bring up Add/Remove.  You can search for the program of interest from there.  If the program is present, Ubuntu/Xubuntu will install it for you automatically.  Just set the program to install from the Add/Remove menu, and then from the menu, Apply.

---

### Post by Jynks on 2009-01-18
> **redonwhite said:**
> One easy way to install applications is to go to Applications---Add/Remove Applications.  There you can search from a bunch of different Applications.  Just check off the box of one you want and then click apply changes.

code:blocks and also the flash pluging for firefox is not in this area?

when I went to youtube for exampel it saud "get flash player" i click on it get sen t to adobe then there is a button says get .deb for unbuntu 8.04+... . i click that and it downloads a .deb file... what do i do with that?

---

### Post by redonwhite on 2009-01-19
> **Jynks said:**
> code:blocks and also the flash pluging for firefox is not in this area?

when I went to youtube for exampel it saud "get flash player" i click on it get sen t to adobe then there is a button says get .deb for unbuntu 8.04+... . i click that and it downloads a .deb file... what do i do with that?

i noticed code block IDE was in there.  Is that what you were looking for?  When in Add/remove...go up to where it says Show.  And then change it to All available applications.

---

### Post by redonwhite on 2009-01-19
Oh and install xubuntu restricted extras from the add/remove applications while your at it too.  This should help with your Video problem.

---

### Post by abhilashm86 on 2009-01-19
u can use synaptic package manager,u get details of what u need and not,by judging u can checkmark your options and apply changes,this suits for major applications, but when it comes to terminal applications like moc,htop u need to install from terminal,u can find commands just by asking in forums or google:)u got it

---

### Post by spartan_87 on 2009-01-19
When you decompress the codeblocks package you downloaded it gives you I think 7 .deb packages that you can click on and automatically install, but you need to install each .deb package in a specific order. Just click on one and if you cant click the install button it will say what dependency is missing. Also you can get the flash plugin from the adobe website or from the synaptic package manager under System > Administration > Synaptic package manager.

---

### Post by theWrkncacnter on 2009-01-19
If you're trying to install flash, the best way I know is to open up synaptic and search for "flash". The one to install is called something like "flash plugin non-free."

---

