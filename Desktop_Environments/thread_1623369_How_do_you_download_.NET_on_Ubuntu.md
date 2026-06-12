---
title: "How do you download .NET on Ubuntu?"
date: 2010-11-16
forum: Desktop Environments
---

### Post by joeyarnold on 2010-11-16
Microsoft Expression Web Software


Microsoft Expression Web Software


Microsoft .NET 4


I download Microsoft .NET (from the link below) in order to install Web Expression software. But as soon as I use wine to install .NET, I run into an error & it stops. It's a typical Microsoft Windows kind of error message that asks if you want to send the result or problem back to their website, & I just click on yes. I tried several websites, including the following for downloading .NET onto Ubuntu. I don't have Windows.

[http://www.microsoft.com/downloads/en/details.aspx?FamilyID=9cfb2d51-5ff4-4491-b0e5-b386f32c0992&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=9cfb2d51-5ff4-4491-b0e5-b386f32c0992&displaylang=en)

I have installed things off wine before. Wine is working. But .NET is not.



Microsoft Expression Web Software

Microsoft Expression Web Software



Microsoft .NET 4

---

### Post by 3Miro on 2010-11-16
There are things that wine cannot do. Go to winehq forums to make sure the software that you want to install can in fact run under wine.

For many things such as .NET, you may consider using winetricks:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by sanderd17 on 2010-11-16
.NET uses a lot of specific windows libraries. So it won't be installable under wine. 

mono can run a lot of C# code and some Visual Basic code. Maybe that helps. I don't know what you want to reach.

---

### Post by joeyarnold on 2010-11-16
Microsoft Expression Web Software

Can I install Mono onto Ubuntu in order to install .NET? Or is there something else I can install? Or can I trick Wine into installing .NET?


Microsoft Expression Web Software

---

### Post by deconstrained on 2010-11-16
[s][.NET is usable in Wine](http://appdb.winehq.org/appview.php?iVersionId=3754). Just make sure you get the x86 version and not the 64-bit version, regardless of your Linux architecture, because Wine can only run applications as 32-bit.[/s]
[s]Correction: it works if you have Crossover, a commercial program, installed. That will auto-configure everything.[/s]

ADDENDUM: I spoke too soon. Now I'm trying the 'winetricks' installation script for it. Scroll down on the WineHQ page I linked to and you'll find the instructions. ;-)

---

### Post by soldier1st on 2010-11-16
you could try installing playonlinux and try to install .net framework in wine but on Windows it is .net framework but in linux it is mono.

---

### Post by joeyarnold on 2010-11-19
Microsoft Expression Web Software

Microsoft Expression Web Software

Microsoft Expression Web Software



Microsoft .NET 4

I tried Mono but failed. I tried PlayOnLinux & that didn't help either. I'm trying to install a program for school. Tried Wine. Tried CrossOver. Tried Mono. Tried PlayOnLinux. Failed each time. I can't buy Microsoft Windows 7 or Apple because I'm broke. I need options or a guide or a how-to manual on trying Mono.

After installing Mono, I went to install my other program but it ended up still demanding that I must have Microsoft .NET 4 in order to install, but I thought it would see that I had Mono which could install it instead, that Mono is the equivalent of .NET (for Windows) but for Linux, you know, but it didn't even know that I installed the newest version of Mono, but why is that?

And what can I do now?


Microsoft .NET 4



Microsoft Expression Web Software

Microsoft Expression Web Software

Microsoft Expression Web Software

---

### Post by asmoore82 on 2010-11-19
You'll probably get tremendously better help if you say what software
you are really trying to install/use and maybe even change the thread title.

---

### Post by joeyarnold on 2010-11-19
Microsoft Expression Web Software

Microsoft Expression Web Software



That is what I am trying to install on Ubuntu 10.04. But I already said what I was trying to install on an earlier post. I already was specific. You just got to read it to see it. DO I have to always repeat myself? But I titled it to be about the Microsoft .NET 4 because that is what it asked me to have when trying to install Web Expression.

Web Expression wanted Microsoft .NET 4 in order to install.

I tried that but failed. I tried installing Web Expression using Wine, PlayOnLinux, & Mono, but failed each time. What should I do? Should I try Mono again?

The bottom-line still is that I wanted to be able to install Microsoft .NET 4 onto Ubuntu & there has to be a way to do that, right?


.
.

How can I install?

Microsoft .NET 4 or the latest .NET available for Ubuntu?

.
.



Microsoft Expression Web Software

Microsoft Expression Web Software

Microsoft Expression Web Software

---

### Post by asmoore82 on 2010-11-19
> **joeyarnold said:**
> The bottom-line still is that I wanted to be able to install Microsoft .NET 4 onto Ubuntu & there has to be a way to do that, right?

not necessarily...

Linux is Free Software. Linux is not Free Windows.

Is this what you are talking about? [http://en.wikipedia.org/wiki/Microsoft_Expression_Web](http://en.wikipedia.org/wiki/Microsoft_Expression_Web)

If you want to play Micro$oft's ridiculous game;
you have to play by their rules - and you always lose.

---

