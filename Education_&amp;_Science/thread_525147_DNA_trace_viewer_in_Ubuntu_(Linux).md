---
title: "DNA trace viewer in Ubuntu (Linux)"
date: 2007-08-14
forum: Education &amp; Science
---

### Post by takakia on 2007-08-14
Is there a good DNA trace viewer for Ubuntu yet? I use Linux only laptop for almost a year and it pains sometimes when I have to use a Windows PC to do most of my DNA assembly work.  BioEdit works decently well with wine, but FinchTV does not work well on my Kubuntu Fiesty Fawn.  It used to work well in Dapper, but what's wrong now.

Anyone using FinchTV with Fiesty? 

finchtv opens but I m not able to copy the sequences to clipboard which is very important.

---

### Post by tweedledee on 2007-08-14
> **takakia said:**
> Is there a good DNA trace viewer for Ubuntu yet? I use Linux only laptop for almost a year and it pains sometimes when I have to use a Windows PC to do most of my DNA assembly work.  BioEdit works decently well with wine, but FinchTV does not work well on my Kubuntu Fiesty Fawn.  It used to work well in Dapper, but what's wrong now.

Anyone using FinchTV with Fiesty? 

finchtv opens but I m not able to copy the sequences to clipboard which is very important.

No, there is not a good trace viewer.  FinchTV seems to be the best bet, or running something via Wine or in a virtual machine - I have a couple of decent free ones for Windows I've been meaning to try that way.  I had been running FinchTV fine in Edgy, but I don't kow that I have since the Fiesty upgrade, and I don't have any files with me to check right now.  I'll report back in a day or two.

---

### Post by DrOlaf on 2007-08-14
I've just replaced my old Edgy laptop with a new one, and put a fresh new Feisty install on it. The current version of FinchTV (1.3.1 for Linux) installed and worked OK. I can drag chromatograms onto the FinchTV window, and copy & paste the sequence text from FinchTV to a text editor: is that what you need to do?

This is under Ubuntu Feisty with Gnome, not Kubuntu Feisty btw.

---

### Post by tweedledee on 2007-08-16
> **DrOlaf said:**
> I've just replaced my old Edgy laptop with a new one, and put a fresh new Feisty install on it. The current version of FinchTV (1.3.1 for Linux) installed and worked OK. I can drag chromatograms onto the FinchTV window, and copy & paste the sequence text from FinchTV to a text editor: is that what you need to do?

This is under Ubuntu Feisty with Gnome, not Kubuntu Feisty btw.

I have an identical experience with my (upgraded to Fiesty) computer.  takakia, perhaps the problem is either something in KDE, or possibly a clipboard issue (I'm using the Gnome clipboard-daemon in the background, which sometimes improves copy+paste).  There are clipboard utilities for KDE; perhaps you can try one and/or remove one if you are already using it?

---

### Post by tylerspaska on 2007-11-03
I've been using FinchTV with Ubuntu 6.10, 7.04, and 7.10 without any problems. However I have been looking for another program. I use 4peaks (OSX) at work and have been very impressed with both the look and functionality of the program. 

I haven't been able to find a good program for compiling plasmids and looking at chromosomal DNA. I use DNA strider (OSX) at work. It's ok, although I feel it lacks some features, but I haven't been able to find anything equivelant with Linux.

---

### Post by takakia on 2007-11-27
I tried Chromaslite under wine and it works well. I can copy paste the sequence in text or fasta format.

---

### Post by Carambakaracho on 2009-03-30
In case someone's still interested in software being able to open .ab1 chromatogram files on Ubuntu.

Recently we were looking for a software being able to replace VectorNTI 10 whenever the old university licenses will run out and we found [ApE]("http://www.biology.utah.edu/jorgensen/wayned/ape/") which is able to open chromatogram files.

Only drawback might be that it's no open source software as far as I understood.

Carambakaracho

---

### Post by ajt on 2009-03-30
> **Carambakaracho said:**
> In case someone's still interested in software being able to open .ab1 chromatogram files on Ubuntu.

Recently we were looking for a software being able to replace VectorNTI 10 whenever the old university licenses will run out and we found [ApE]("http://www.biology.utah.edu/jorgensen/wayned/ape/") which is able to open chromatogram files.

Only drawback might be that it's no open source software as far as I understood.


Hello, Carambakaracho.

Take a look at "trev", which is part of the Staden package installed under Ubuntu 8.04 LTS in Bio-Linux 5.0:

[http://nebc.nox.ac.uk/tools/bio-linux]("http://nebc.nox.ac.uk/tools/bio-linux")

Bye,

Tony.

---

### Post by halocaridina on 2009-03-30
Hi Carambakaracho,

ajt has made a good suggestion in having you look at trev from the Staden Package.

The package takes some modifications to install.  Please read through the posts at this link to help with the installation:

[http://ubuntuforums.org/showthread.php?t=696449](http://ubuntuforums.org/showthread.php?t=696449)

halocaridina

---

### Post by ajt on 2009-03-31
> **halocaridina said:**
> Hi Carambakaracho,

ajt has made a good suggestion in having you look at trev from the Staden Package.

The package takes some modifications to install.  Please read through the posts at this link to help with the installation:

[http://ubuntuforums.org/showthread.php?t=696449](http://ubuntuforums.org/showthread.php?t=696449)



Hello, halocaridina.

No installation required if you use Bio-Linux 5.0 :-)

[Bio-Linux 5.0 is based on Ubuntu 8.04 LTS]

Bye,

Tony.

---

### Post by halocaridina on 2009-04-02
Hi ajt,

Yes, you are right.  I "forgot" about suggesting Bio-Linux as an alternative:

[http://envgen.nox.ac.uk/tools/bio-linux](http://envgen.nox.ac.uk/tools/bio-linux)

Thanks for the reminder.

Halocaridina

---

### Post by Genesis3800 on 2009-10-23
I use the free version of Ridom TraceEdit in my lab with Ubuntu since Hardy Heron.

It's much more simple than BioEdit but allows you to open the chromatogram files, visualize the peaks, copy the sequence, etc. Similar to FinchTV. Enough if you don't need an exhaustive analysis of your sequences.

[http://www.ridom.de/traceedit/](http://www.ridom.de/traceedit/)

---

