---
title: "Has anyone realised that Pymol is not free?"
date: 2010-03-11
forum: Education &amp; Science
---

### Post by superarthur on 2010-03-11
Well, it's an open source project, and it's free to download the latest source code, only the binary of an "outdated" version can be downloaded for free.
You have to pay to download the latest binary and for the manual, and they discourage people to share the binary of pre-compiled Pymol.

According to [The Free Software Definition]("http://www.gnu.org/philosophy/free-sw.html"), one of the essential freedom is "The freedom to redistribute copies so you can help your neighbor (freedom 2).", and "The freedom to redistribute copies must include binary or executable forms of the program, as well as source code, for both modified and unmodified versions."
Also, "Software manuals must be free, for the same reasons that software must be free, and because the manuals are in effect part of the software."

For more, read:
[http://mwinkelmann.com/2009/03/more-on-pymol/]("http://mwinkelmann.com/2009/03/more-on-pymol/")
[http://www.mail-archive.com/pymol-users@lists.sourceforge.net/msg05696.html]("http://www.mail-archive.com/pymol-users@lists.sourceforge.net/msg05696.html")
[http://www.mail-archive.com/pymol-users@lists.sourceforge.net/msg06761.html]("http://www.mail-archive.com/pymol-users@lists.sourceforge.net/msg06761.html")

Pymol is not free as in "free speech". I am not judging it, but just simply pointing it out. It's your choice to pay or a software or use an "outdated" version or not to use it at all.
Personally, I would prefer a free alternative that works as good and doesn't look as ugly as Rasmol (but I can't find one). And I think that good scientific software should be free, simply because people should not be ignorant to science. If there is a barrier to science (e.g. price), people would be put off to learn about it.

Please share you point of view here ;)

---

### Post by cascade9 on 2010-03-11
Yes, open source doesnt make it FOSS. But while it might not be totally free, at least you have the option of compliling it yourself.

---

### Post by superarthur on 2010-03-11
> **cascade9 said:**
> Yes, open source doesnt make it FOSS. But while it might not be totally free, at least you have the option of compliling it yourself.
There aren't instructions for compiling neither. (most Pymol users aren't hardcore computer scientists)

P.S. I only know Java and Perl, and they don't need compiling. :P (When I program with Java, I just press the run button on netbeans.)

---

### Post by hubie on 2010-03-12
It is free.  The PyMOL license would appear to be simply an [X11 License]("http://www.xfree86.org/3.3.6/COPYRIGHT2.html#3"), aka an MIT License, which is [GNU compatible]("http://www.gnu.org/licenses/license-list.html").

[PyMOL license]("http://pymol.svn.sourceforge.net/viewvc/pymol/trunk/pymol/LICENSE?revision=3882&view=markup"):
```
Open-Source PyMOL Copyright Notice
    3  ==================================
    4 
    5  The Open-Source PyMOL source code is copyrighted, but you can freely
    6  use and copy it as long as you don't change or remove any of the
    7  Copyright notices. The Open-Source PyMOL product is made available
    8  under the following open-source license terms:
    9 
   10  ----------------------------------------------------------------------
   11  Open-Source PyMOL is Copyright (C) Schrodinger, LLC.
   12 
   13  All Rights Reserved
   14 
   15  Permission to use, copy, modify, distribute, and distribute modified
   16  versions of this software and its built-in documentation for any
   17  purpose and without fee is hereby granted, provided that the above
   18  copyright notice appears in all copies and that both the copyright
   19  notice and this permission notice appear in supporting documentation,
   20  and that the name of Schrodinger, LLC not be used in advertising or
   21  publicity pertaining to distribution of the software without specific,
   22  written prior permission.
   23 
   24  SCHRODINGER, LLC DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE,
   25  INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN
   26  NO EVENT SHALL SCHRODINGER, LLC BE LIABLE FOR ANY SPECIAL, INDIRECT OR
   27  CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS
   28  OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE
   29  OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE
   30  USE OR PERFORMANCE OF THIS SOFTWARE.
   31  ----------------------------------------------------------------------

```

X11 License:
```
Copyright (C) 1996 X Consortium

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE X CONSORTIUM BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Except as contained in this notice, the name of the X Consortium shall not be used in advertising or otherwise to promote the sale, use or other dealings in this Software without prior written authorization from the X Consortium.

X Window System is a trademark of X Consortium, Inc.

```

---

### Post by Chronon on 2010-03-13
It doesn't seem any different than Sun offering a free version and a commercial version of VirtualBox.  I don't see a problem.

---

### Post by superarthur on 2010-03-13
Sorry that I haven't read their license before, but they discourage people from distributing the binary of Pymol (see the links I put in my first post).
Even if the license allow you to redistributing the software, they emotionally blackmail you into paying.
Thus, so many universities uses Windows, and it's a lot harder to compile there. I can't format the computers in my university and install Ubuntu. :P
There is still the problem of documentation. They don't provide documentation unless you pay them. If you go onto their source forge page, it says "Files are at http://www.pymol.org/" in the README.TXT
You can only view the documentation if you are a subscriber.

Also, at the [PyMOL news page]("http://pymol.org/news.html") (March 16, 2009), they compare other molecular viewers, and claimed that the PyMOL license has "unrestricted reuse open-source code" while the GPL license only has "conditional reuse open-source code" because it's "encumbered by social ideology"

Compatibility with GPL doesn't make it completely free.

---

### Post by PC_load_letter on 2010-03-14
> **superarthur said:**
> ...
Thus, so many universities uses Windows, and it's a lot harder to compile there. I can't format the computers in my university and install Ubuntu. :P
...

Did you try the Wubi install? Using this method, you can install Ubuntu on any Windows machine as if it was just another application. Here: [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by superarthur on 2010-03-14
> **PC_load_letter said:**
> Did you try the Wubi install? Using this method, you can install Ubuntu on any Windows machine as if it was just another application. Here: [http://wubi-installer.org/](http://wubi-installer.org/)

I started using Ubuntu with wubi.
Still, so many other applications I need are window based. I can't keep rebooting all the time.

---

### Post by hubie on 2010-03-15
I'm not sure if I understand what you consider "free" software.  If PyMOL is licensed under an MIT license, this is an approved open source license and is considered free in the same sense as the GPL, BSD, Apache, etc. licenses are.  If you don't consider this "free," than you can't really consider much of any of a Linux distribution free.  The fact that PyMOL apparently doesn't provide a binary executable free to download doesn't affect its free-ness because (and someone correct me if I am wrong) none of the major open source licenses require one to provide free binaries; they require you to provide source code if you distribute the binaries.  I don't think any of the licenses require you to provide a nice set of documentation either.

I will disagree with you regarding whether this has any effect on whether a university deals with Windows or not.  In my opinion, the reason that many universities standardize on Windows is that Microsoft provides sweetheart deals to schools and universities with regards to software licenses.  Think how much a student copy of almost anything Microsoft costs verses what you'd have to pay for a commercial copy.  Microsoft learned very early on the value of getting people locked into their software while in school.

As for running Linux and Windows together, if you find you need to be on your Windows side primarily, you might want to look at [andLinux]("http://www.andlinux.org/index.php").  It runs Linux from within Windows just as if it was any other Windows application (it is based on [coLinux]("http://www.colinux.org/")).

---

### Post by superarthur on 2010-03-15
> **hubie said:**
> I'm not sure if I understand what you consider "free" software.  If PyMOL is licensed under an MIT license, this is an approved open source license and is considered free in the same sense as the GPL, BSD, Apache, etc. licenses are.  If you don't consider this "free," than you can't really consider much of any of a Linux distribution free.  The fact that PyMOL apparently doesn't provide a binary executable free to download doesn't affect its free-ness because (and someone correct me if I am wrong) none of the major open source licenses require one to provide free binaries; they require you to provide source code if you distribute the binaries.  I don't think any of the licenses require you to provide a nice set of documentation either.

I will disagree with you regarding whether this has any effect on whether a university deals with Windows or not.  In my opinion, the reason that many universities standardize on Windows is that Microsoft provides sweetheart deals to schools and universities with regards to software licenses.  Think how much a student copy of almost anything Microsoft costs verses what you'd have to pay for a commercial copy.  Microsoft learned very early on the value of getting people locked into their software while in school.

As for running Linux and Windows together, if you find you need to be on your Windows side primarily, you might want to look at [andLinux]("http://www.andlinux.org/index.php").  It runs Linux from within Windows just as if it was any other Windows application (it is based on [coLinux]("http://www.colinux.org/")).

okay. you won.
The software is free then, but people from its company is actively giving the impression that redistribution of newer versions are prohibited, and a license is required.

---

### Post by Chronon on 2010-03-16
I haven't investigated in depth so this may not be correct in this situation, however, in the VirtualBox case Sun maintained two different codebases -- one licensed with an open license and one with proprietary copyright protections.  Newer features and development would begin in the proprietary version and would often (usually?) later be merged into the open-source trunk a few revisions later.  It is perfectly within a copyright holder's rights to dual license their code.  Qt is also released under multiple licenses.

---

### Post by ssam on 2010-03-17
its more like the redhat business model, than virtual box.

sell a nice packaged, supported version. offer the source code with an opensource licence. lots of places do this, and it seems a good method for making a profit with opensource.

the "you are legally allowed to do this, but please don't" is a bit odd. if they were really against you redistributing, then they could change the licence.

they could prevent you distributing the binary that they compiled, because the licence looks like it only covers the source. if you compiled a binary from the source you could redistribute it.

"PyMOL license has "unrestricted reuse open-source code" while the GPL license only has "conditional reuse open-source code""
Thats the BSD vs GPL flame war. the GPL prevents you removing freedoms. BSD people want the freedom to remove freedoms, so that the code is truly free. GPL people want the freedom to be guaranteed forever, so that the code is truly free.

---

### Post by carandraug on 2010-03-19
> **superarthur said:**
> Still, so many other applications I need are window based. I can't keep rebooting all the time.

You are a bit inconsistent here. You're complain that PyMol in your opinion is not 100% free but you're still OK in using windows...

I use PyMol and about the documentation there's a community based wiki with tips on how to use it. Also, you can find manuals of PyMol on google. Probably not the ones they are selling but they are still good.

---

### Post by superarthur on 2010-03-19
> **carandraug said:**
> You are a bit inconsistent here. You're complain that PyMol in your opinion is not 100% free but you're still OK in using windows...

I use PyMol and about the documentation there's a community based wiki with tips on how to use it. Also, you can find manuals of PyMol on google. Probably not the ones they are selling but they are still good.
You have make the assumption that everyone is either a free software fanatic or a sole proprietary software user. You can see lots of people in this forum like me, who like the idea of free software but still use proprietary software.

I am a scientist (or a science student), not a computer scientist. I don't really care if the source code is free or not, because I am not going to change it as long as the software works. I believe that science should be freely accessible, so that people have no excuse to be ignorant of it. A good molecular viewer is a gateway to understanding science. Therefore, I think it should be completely free, including access to the newest stable release and the documentation. (I believe software developer should be paid, but it doesn't have to cost the end-user. And I do think business model of Ubuntu is one of the best.)

---

### Post by carandraug on 2010-03-19
> **superarthur said:**
> You have make the assumption that everyone is either a free software fanatic or a sole proprietary software user. You can see lots of people in this forum like me, who like the idea of free software but still use proprietary software.

I didn't made that assumption at all. I only made the assumption that if someone already uses windows, shouldn't have the morals to complain that a software is not completely free because binaries are not distributed by the developers of said software. They also don't supply binaries for Linux but thankful we have package maintainers. Maybe you should ask microsoft if they wouldn't mind get someone to do it.

If you notice, many free software do not supply binaries you have to compile it themselves. Can you imagine that if you were the developer, having to not only write the software but also have to compile it for all miriad of Linux distributions, windows and Mac? The code is free, what he's selling, is the extra work, a luxury that most users enjoy, which is having to compile the code.

---

### Post by superarthur on 2010-03-19
> **carandraug said:**
> I didn't made that assumption at all. I only made the assumption that if someone already uses windows, shouldn't have the morals to complain that a software is not completely free because binaries are not distributed by the developers of said software. They also don't supply binaries for Linux but thankful we have package maintainers. Maybe you should ask microsoft if they wouldn't mind get someone to do it.

If you notice, many free software do not supply binaries you have to compile it themselves. Can you imagine that if you were the developer, having to not only write the software but also have to compile it for all miriad of Linux distributions, windows and Mac? The code is free, what he's selling, is the extra work, a luxury that most users enjoy, which is having to compile the code.

As I explained, one of my main concern is the general public who remains ignorant of science. They have an excuse to be ignorant as long as scientific knowledge is not accessible. (It's impossible for everyone to do experiments for free, since scientific equipments and consumables are expensive. But at least they should be able to learn from scientists' research for free.) The general public don't know how to compile the codes. If you search on the internet, many people claimed that it's incredibly hard to compile the code in windows even for people with good knowledge about computers.

And you make it sound like the general public can choose which OS they use. Most people nowadays are brainwashed by microsoft. Most schools teaches students to use windows. The older generation uses windows and teach their kid to use windows. Most computer are preinstalled with windows and windows only when you buy them, so most people only know about windows.

I hate the attitude of "if they use a proprietary OS, they should get ripped off by companies". People don't chose windows, and poor people use windows too.

---

### Post by carandraug on 2010-03-19
> **superarthur said:**
> As I explained, one of my main concern is the general public who remains ignorant of science. They have an excuse to be ignorant as long as scientific knowledge is not accessible. (It's impossible for everyone to do experiments for free, since scientific equipments and consumables are expensive. But at least they should be able to learn from scientists' research for free.) The general public don't know how to compile the codes. If you search on the internet, many people claimed that it's incredibly hard to compile the code in windows even for people with good knowledge about computers.

And you make it sound like the general public can choose which OS they use. Most people nowadays are brainwashed by microsoft. Most schools teaches students to use windows. The older generation uses windows and teach their kid to use windows. Most computer are preinstalled with windows and windows only when you buy them, so most people only know about windows.

Science is not free to learn. Public does not have free access to most papers, not even the author (well, I guess they can go to a library but if the library does not pay the publishers...) You write a paper, and not only in some cases you need to pay to get it accepted into the magazine, you still have to give them the rights over your text. If you do take it seriously, then next time you publish something make sure you do so in a open access journal.

I've also heard it's incredibly hard to compile it in windows. I even heard rumors that the guy makes it harder on purpose so people give up and just buy the binary (I must stress here that I've heard it as rumor, I am not saying it is true).

And contrary to what you say, people do have a choice. They just don't bother checking their choices. I am not saying when they buy the computer. I mean that people that would go, just out of curiosity, look at protein structures, should have, way before that, check what is "that Linux thing". That said, it's very unlikely that people who use PyMol haven't heard about Linux so they are using Windows because it's their option (discussion if they would pick windows if they started with Linux is probably already too much out of topic).

I know it's hard to use only open-source stuff in a lab, that almost all software you're shown is proprietary, and they confuse open-source with freeware. I've heard it all before and went through all that. However, if you really care about that freedom, it's up to you to refuse those software because it's your principles and look for alternatives. You can find at least one alternative most of the times. For the most obscure things, it's usually a command line thing or the interface looks like 10 years old but there's also the choice to sell the soul and make it easier (choice was the keyword).

Next time a rep goes to your lab trying to sell something (machines or software), ask them if it will also work in Linux. And even if you're still a student, when you go have training on another machine and they recommend you software to read the files obtained (damn those proprietary files) ask them for a software that would work in Linux.

TIP: a good argument to make your supervisor think twice about open-source software is that if the file is proprietary, when the company closes or drops support for the file, you will no longer get access to the data. In ten years time, files obtained today may not be readable because the company dropped supported for them. If things are open, you'll still have the documentation to open the files. This has happened before and will most likely continue to happen. I just got a grant to set up a server that will organize all microscope images of the department and this was my main argument to use free software (OMERO) instead of any other (together with the fact that if it's open we can always hire a developer to make specific changes useful for us).

And if you really really care, maybe you could start developing the stuff that you need and give it back to the community. Maybe a graphical interface or making an old one better. My view on this open-source thing is that is mainly community driven. If the community has no interest on having free software for a specific thing appear, then it won't appear out of nowhere (and complaining that it doesn't exist does not count as having interest on making it appear).

> **superarthur said:**
> I hate the attitude of "if they use a proprietary OS, they should get ripped off by companies". People don't chose windows, and poor people use windows too.

It's a bit like when a killer is killed and people say "he got what he deserved". I think it's a perfectly natural line of thought.

Anyway, in your specific case, you can compile PyMol for windows and distribute it yourself for free because it seems the license allows you to do it.

---

### Post by superarthur on 2010-03-20
I am just a lowly undergrad. LOL

And I do believe that most of the undergrad who use Pymol never thought about checking out Linux.

To be honest, I looked into Linux because some people writes scientific software in Linux. (e.g. [HMMER]("http://hmmer.janelia.org/"), [MCCE]("http://134.74.90.158/")) There are several Linux computers in the biology department, and people connect to it via putty do do simulations. I thought it may be better to install Linux on my laptop so that I can try things out myself more easily. (anyway, it's getting out of topic)

---

### Post by mimble on 2010-05-10
The license has now really changed. Pymol has been bought by Schrödinger Software.
You can apply for a license to use it for teaching, but you are explicitly forbidden to use that one for research, even in academia.

The "evaluation" versions that one can download are crippled (image export, session saving).

---

### Post by Chronon on 2010-05-10
> Open-Source PyMOL For Everyone: No Subscription Required.

    * All interested parties are welcome to compile their own PyMOL builds from the current Open-Source Code (fetched via Subversion).

I don't see that anything has changed.

---

### Post by WebDrake on 2010-05-12
> **superarthur said:**
> Therefore, I think it should be completely free, including access to the newest stable release and the documentation. (I believe software developer should be paid, but it doesn't have to cost the end-user. And I do think business model of Ubuntu is one of the best.)

I think you are making that hoary old mix-up between free-as-in-freedom (liberty) and free-as-in-beer (price).

See: [http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

---

### Post by Morpholinux on 2011-11-28
I am using pymol and yes documentation is sometimes outdated, an easy to find, and still with that you can make very nice images

It is one of the most used molvis software out there
[http://rosettadesigngroup.com/blog/284/what-is-your-favorite-molecular-viewer/]("http://rosettadesigngroup.com/blog/284/what-is-your-favorite-molecular-viewer/") 

For the moment I think I do not need to get the most recent version therefore I do not have to pay anything, Maybe in the future and only to support them (because they are already supporting me in a way)

---

