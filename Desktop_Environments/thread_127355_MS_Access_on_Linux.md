---
title: "MS Access on Linux"
date: 2006-02-08
forum: Desktop Environments
---

### Post by BlackJack on 2006-02-08
MS Access 2003 will not run under Wine or CrossOver Office. Does anybody know of any way to run Access under Linux short of installing an x86 emulator and then installing Windows on top of that?

Thanks...........

---

### Post by el3ktro on 2006-02-09
Are you sure about Access not running in Wine? Well if it does really not run, then you might purchase a copy of VMware, install Win2k/XP within VMware and run Access there - you could also try QEmu, which does the same, is free, but a little slower. If you just need any database & not necessarely Access then you can also use OpenOffice Base which also is pretty functional.

Tom

---

### Post by GrumpyBob on 2006-02-09
I got fed up with incomaptibilities between Access versions and exported the data in my (admittedly small) Access databases and switched to OOo Base.

Note that the pre 2.0 version of OOo that is in Breezy 5.10 seems a little broken, it's fixed in 2.01, which can be installed via Automatix.  Report creation is still ludicrously slow, but at least it works.

Regarding qemu, I'm using this for Win98SE on my laptop, and it seems fast enough for use.

Robert

---

### Post by BlackJack on 2006-02-09
I tried OpenOffice Base and was unable to create any databases, just set it up a a front end connector to other existing data bases. I then checked out openoffice.org and it "looked like" it is only good as a front end connector to some other back end data base. Admittedly it does seem to connect ot almost anything, but if I still need another application to create teh back end data base then why not just keep using that other dazta base system rather than complicating matters with another front end?

If the new version will allow me to actually create data bases from within OpenOffice Base then I will upgrade and look at it.

As for installing VMWare, well i am trying to avoid that because my goal is to eliminate Windows. If I have to run some sort of emulation with Windows on top of it then I have not eliminated Windows and there is no reason for me to continue moving forward with Linux. Good suggestion, just does not accomplish what I am looking for.

Thanks..........

---

### Post by el3ktro on 2006-02-09
Well I don't know which version of OpenOffice you've been using, but with OpenOffice Base 2 can create & edit tables, connect them, make queries on them etc. Just like with Access. It may not be as feature-rich as it (yet) but it's a real desktop database.  Those database back ends that you mention are actually the real databases, ike MySQL, PostgreSQL. They don't have a front end at all, they're "just" database servers. OpenOffice2 comes with it's own database backend called HSQL or so, so you don't have to care about this and you don't need to install another backend.

Tom

---

### Post by rado_london on 2006-02-09
I installed MS Office XP using CrossOver office and it worked as a charm. Of course it was just an experiment so I removedd it later, because the speed wasn't good and I wasnt satisfied.

---

### Post by BlackJack on 2006-02-09
el3ktro,
I checked and I am running 2.0. I heard somewhere that creating data bases within Base is an issue in 2.0 bu is fixed in 2.01 which can be installed through Automatix, not sure how accurate this is but I sure am having problems.

Anyway, I installed Automatix and ran the OpenOffice install listed there. It still says that it is OpenOffice 2.0 and I am still unable to create a data base from scratch, but the error message is different this time. I am now getting the error message

The connection to the data source “<file name>” could not be established.
libhssldb2: file not found

I checked the list of libraries available in Synaptic and do not see this library listed.

Anybody have any idea where I can get this library file?


rado london

Yes, I installed Office 2003 and everything works flawlessly EXCEPT Access. I checked CodeWeavers web site and they specifically list Access 2003 as an application that does not work, wish it did as it would ease my transition into Linux!


Anyway... if anybody can help me with finding libhssldb2 I would appreciate it.

Thanks for all the help.........

---

### Post by el3ktro on 2006-02-09
Can you please go to the "Help->About" dialog of OO and check which version you're running? The last line with very small letters gives you the EXACT version. I have 2.0.1 installed, but it's still just called 2.0 (it's just a bugfix release)


Tom

---

### Post by BlackJack on 2006-02-09
Tom,
You are right. The very bottom says “openoffice.org2-core breezy1, Sat Jan 7 01:11:04 UTC 2006” in type so small that an old guy like me can barely see it. So I guess that my real problem is the lack of that particular library. Any idea what repository it might be on?

Thanks..........

---

### Post by steve.horsley on 2006-02-09
My openoffice works (downloaded from Sun) including the database stuff, but I don't have a file called libhssldb2 anywhere on my system. Are you sure you spelled that right? 

What version of java are you using?

---

### Post by BlackJack on 2006-02-09
Tom,
you are right it is libhsqldb2, sorry about the typo.

I'm afraid i am not familiar enough with Linux tofind teh Java version information, where do I look for it?

Thanks..........

---

### Post by el3ktro on 2006-02-09
I have a newer version of OOo though, here's the repository I'm using, you can get the newest OOo there:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./


Tom

---

