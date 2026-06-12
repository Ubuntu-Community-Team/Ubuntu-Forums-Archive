---
title: "Has any one managed to install EAGLE CAD lately?"
date: 2006-09-24
forum: Education &amp; Science
---

### Post by Gyrotwister on 2006-09-24
I'm having trouble installing EAGLE CAD (on Dapper 386i).  Synaptic has it under Electronics (multiverse).  Here is what happens.  

Synaptic downloads the files ok and begins the install procedure ok.  

A window pops up to asks if I want to enter the licence number or run as freeware.  I select freeware.  

It then asks for permission to create directory /root/eagle and I answer yes.  
As soon as I answer yes, EAGLE Control Panel  begins to run while Synaptic is left hanging with seemingly about 10% to do.  

Synaptic stays like that until the EAGLE Control Panel is closed, then Synaptic finishes and can then be closed.  

After this there seems to be no evidence of EAGLE CAD to be found on my pc.  
Did it really install?  If so where is it, and how can I find it?  

Oddly, I can run EAGLE ok while Synaptic is hanging.  After that I just can't find it.  

Any suggestions?

---

### Post by i386DX on 2006-09-24
It's installed: just type 'eagle' in the console

---

### Post by Gyrotwister on 2006-09-24
That works.  
I've created a launcher now too.  

Thanks.

---

### Post by Anders J on 2007-05-13
I went through the installation last couple of days, using synaptic. Worked fine after som intial problem with desktop effects, see other thread..

I can start by writing eqle as expected.

But when I enter the chosen location for the lib, project, ulp etc files, I am not allowed to do this, which seems logical. So I started eagle using gksudo, which then allowed me to choose accsesible location for these files.

Now, everything works fine as I invoke Eagle with gksudo, but as soon as I start the program by just typing eagle, the flie locations chosen by me are all gone and replaced with the default settings.

There is also a locked Eagle directory created directly under home.

This reminds very much with what Gyrotwister wrote and is obviously a very basic Linux question.

I do not want to change the file locations other than at installation, but it is obvious that locations for library files need to accessible not only from Eagle but also from "outside".

What am I doing wrong here?

---

### Post by kefir on 2007-05-13
Change the permissions on them perhaps? They were problably created with root as owner therefore u can only use them when you start the program with gksu i presume (never tried to install the program but from the logic point of view this sounds like the issue) ..chown youruser on the eagle directory in your home might just do the trick.

---

### Post by Anders J on 2007-05-14
The locked directory was not at all the problem, found that there was a default HOME director path in the setup. I did remove this and removed that directory.

So I still sit with the same problem, if I start the application with gksudo everything is as it should, but if I start it the normal way it uses the default settings.

It is as of the program is reading the setup script (or whatever that is called) from completely different locations.

---

### Post by Anders J on 2007-05-14
The trick was to set myself as an owner to the hidden .eaglesrc file in home directory. Solved the problem, only one and consistent setup.

---

