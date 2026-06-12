---
title: "Canon Pixma MP630 - got the drivers, don't know how to install them"
date: 2009-03-02
forum: General Help
---

### Post by gdp77 on 2009-03-02
Hi. 

I recently bought Canon Pixma MP630
 I downloaded from [here](http://software.canon-europe.com/software/0031301.asp?model=) the file **MP630_debian_drivers.tar**. I uncompressed the file and got some deb files and some other folders with various makefile(s) inside etc. 

I tried to execute the debs, the deb manager kicked in and installed them, but there was no option for my printer in the "printer configuration". I suppose I must do something with these makefile(s) but I am at a loss. 

Is anyone able to help me? Canon doesn't provide any further support.

P.S. These are the folders :

[[IMG]http://img145.imageshack.us/img145/9748/79800782.png[/IMG]](http://img145.imageshack.us/my.php?image=79800782.png)
By [gdp77](http://profile.imageshack.us/user/gdp77)

I installed the 2 debs but I couldn't print


These are the contents of the middle folder :

[[IMG]http://img523.imageshack.us/img523/1244/62890385.png[/IMG]](http://img523.imageshack.us/my.php?image=62890385.png)
By [gdp77](http://profile.imageshack.us/user/gdp77)

UPDATE : Through system --> administration ---> printing --> change (printer and model), I pointed to the PPD file in the folder above and at least I can now print.

BUT the printer UI is extremely poor ( I can't choose special papers, or change resolution etc), so I have the feeling I should follow a different procedure for the installation.

If anyone can, please help me

---

### Post by veloce on 2009-03-08
> **gdp77 said:**
> Hi. 

UPDATE : Through system --> administration ---> printing --> change (printer and model), I pointed to the PPD file in the folder above and at least I can now print.

BUT the printer UI is extremely poor ( I can't choose special papers, or change resolution etc), so I have the feeling I should follow a different procedure for the installation.

If anyone can, please help me

Sounds like you installed it correctly.  If you go into system - admin - printing and right click on the printer icon then select properties do you get a full set of properties?  Is the "make and model" set correctly?

---

### Post by gorski on 2009-04-29
Anyone with more info, please?

I am running Ubuntu 9.04 on a 64b machine [Acer 5920G lappy] and get the "wrong architecture" messages...

Do they exist, to begin with?

[echhhh...]

---

### Post by veloce on 2009-04-29
> **gorski said:**
> Anyone with more info, please?

I am running Ubuntu 9.04 on a 64b machine [Acer 5920G lappy] and get the "wrong architecture" messages...

Do they exist, to begin with?

[echhhh...]

I use a different canon printer, but I had to get the 64bit versions of the drivers.  I downloaded these from the same site as the 32 bit.

Also: I see in my notes that the Debian .debs didn't work for me - there was a dependency issue.  I ended up using the rpms with alien.

---

### Post by swatsbiz on 2009-05-01
I'm getting lost again, I've got 64bit system, 32bit RPMs for my MP510 printer but no way to install them :-(

Anyone help?

---

### Post by veloce on 2009-05-03
> **swatsbiz said:**
> I'm getting lost again, I've got 64bit system, 32bit RPMs for my MP510 printer but no way to install them :-(

Anyone help?

You need 64bit drivers for a 64 bit system.

If .deb files are available, try them first.  If they don't work, try the .rpm files.  For .rpm files, use alien to create .deb files then install the deb file.

---

### Post by gorski on 2009-06-05
Thanx!

But I am at a loss, like the previous poster, with how to do it exactly...???

I mean, developers are like little children, _***sometimes***_... sadly...

So much brain, so good with formulae but when it comes to simple words of explanation as to what exactly to do with it - they are at a a loss...

We need clear guidelines as to how to install it all...

Pretty please, we are not all IT pros...

Imagine asking from IT pros to know everything about medicine when they are ill and the doc just gives them "something" but no words of explanation, nothing... Bad, bad attitude!!!

Please, do something about that, IT guys!!!:(

---

### Post by veloce on 2009-06-07
> **gorski said:**
> 
Please, do something about that, IT guys!!!:(

You need to have that little rant at the Canon developers, not here.  

On this forum you find, not IT guys or pros, but **users** who, for whatever reason, choose to volunteer their time to helping other users.  (My background is Corporate Finance and Strategic Planning not IT).

My first time installing Canon drivers I found, by googling, the following link:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview")

---

### Post by gorski on 2009-07-02
First of all: THANX for the link! I didn' see it. Sometimes Google gets a lot of garbage...

That's exactly what I did - direct that at the IT developers who are - well, lost for words, as it were, or patience. Not to develop, sometimes - but to explain...

I would also add the lack of "professional competence" - what's the use of a SW which no one knows what to do, unless they are IT professionals?!?

How many of us are IT pros?

Ridiculous!

---

### Post by gorski on 2009-07-02
As for the link - this is directed at Linux as a whole:

> This does not work for AMD64.

Moreover, it's way too complex. This is one of the things Linux could learn from Windows, I think.

Windows learnt a few things from Linux, for sure. But no one is perfect. And this is one of those things where things could get better for Linux. Much better!

This is for geeks! Sadly. Not "for Human Beings", as stated by Ubuntu guys. That should be the goal but we have a long way to go, it seems...

Something should be done in terms of installation of drivers etc.

THIS IS WHAT IS KEEPING LINUX BACK!!!! Not just the development of drivers and appz but also - once you do have them - what to do/how to deal with them... And I WOULD LOVE TO GO AWAY FROM Windows COMPLETELY - but telling it like it is - if one is not IT educated [I am from Humanities] it is NOT going to be a straight forward experience. Hence, it is for geeks! Still! Sadly...

Good luck to us all!!!

---

