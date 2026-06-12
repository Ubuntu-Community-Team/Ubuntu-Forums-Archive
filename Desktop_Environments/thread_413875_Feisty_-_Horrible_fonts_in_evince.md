---
title: "Feisty - Horrible fonts in evince"
date: 2007-04-19
forum: Desktop Environments
---

### Post by lolocaust on 2007-04-19
The fonts in the Feisty version of evince look really bad, as if there's no anti aliasing/decent scaling algorithm used. Is this a bug or is there some way to make the fonts smoother, at least the same as they did in Edgy? Thanks. (BTW everything else about Feisty is awesome!:) )

---

### Post by stchman on 2007-04-19
> **lolocaust said:**
> The fonts in the Feisty version of evince look really bad, as if there's no anti aliasing/decent scaling algorithm used. Is this a bug or is there some way to make the fonts smoother, at least the same as they did in Edgy? Thanks. (BTW everything else about Feisty is awesome!:) )

Go to the Add/Remove and install Adobe Acrobat.  It is far superior to viewing .pdf files than Evince.  Acrobat is also way better when printing .pdf files.

---

### Post by lolocaust on 2007-04-19
Thanks, but Acrobat doesn't seem to be in the feisty repos. I'd also prefer to stick with evince, but I'll grab a copy of Acrobat from somewhere as a last resort. Maybe there's a setting that I missed somewhere, although I've looked everywhere.

---

### Post by stchman on 2007-04-19
> **lolocaust said:**
> Thanks, but Acrobat doesn't seem to be in the feisty repos. I'd also prefer to stick with evince, but I'll grab a copy of Acrobat from somewhere as a last resort. Maybe there's a setting that I missed somewhere, although I've looked everywhere.

You can go to Adobe website and download Acrobat reader 7.0.9 in .rpm format.

Install alien if you don't have it installed.

sudo apt-get install alien

convert the .rpm package to .deb
change directory where you downloaded the .rpm

sudo alien --scripts --keep-version -d *.rpm

This will convert the .rpm into a .deb.  You can delete the .rpm if you wish.
Install the .deb

sudo dpkg -i *.deb

Acrobat Reader is installed.  Acrobat reader blows away Evince.  I could not get Evince to print .pdf files properly and the fonts are blurry.  Acrobat is far more useful.

I wonder why they did not put Acrobat in the Feisty repositories.

---

### Post by o_fortuna on 2007-04-19
> I wonder why they did not put Acrobat in the Feisty repositories.

Quite simply, Adobe removed the right of third parties to distribute the software, so Ubuntu can't provide the software anymore. But I do agree that evince just doesn't do the job very well. Adobe Reader blows it out of the water.

---

### Post by L0cKd0wN on 2007-04-19
I've got acroread to install.  The above people are right in that acroread is not available in the typical feisty repos.  So follow my instructions **(for feisty 7.0.4 only)**:

**1.  Add gpg key:**
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
[B]
2. Edit sources.list with new repo data:[/B]
sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

**3.  Apt-get update:**
sudo apt-get update

**4. Install**
sudo apt-get install acroread

There's also many other third party packages in the medibuntu repo, for example w32 codecs, skype, and google earth.  I encourage you guys to look around the Medibuntu web site.

Cheerz! Hope this helps!

~L0cK

---

### Post by ericzb on 2007-04-20
I believe the alien and repo will work just fine, but why not just download the tar file and install it there. 
only one line will solve the problem:
sudo ./install


:) :)

---

### Post by L0cKd0wN on 2007-04-20
Yea I just thought the medibuntu approach was better because you can use the repo for so many other things in addition to Adobe Reader.  To each his own!  People like choice, hehe.

~L0cK

---

### Post by stchman on 2007-04-20
> **o_fortuna said:**
> Quite simply, Adobe removed the right of third parties to distribute the software, so Ubuntu can't provide the software anymore. But I do agree that evince just doesn't do the job very well. Adobe Reader blows it out of the water.

Do you think my approach will work?  To me it sounds like a good approach.

---

### Post by stchman on 2007-04-20
> **o_fortuna said:**
> Quite simply, Adobe removed the right of third parties to distribute the software, so Ubuntu can't provide the software anymore. But I do agree that evince just doesn't do the job very well. Adobe Reader blows it out of the water.

That is ridiculous!!!!  Edgy still has it in the repos and you can download the Linux .rpm from their website.

What a crock!!!

Makes ZERO sense.  I wish Foxit would make their incredible reader for Linux native.

---

### Post by L0cKd0wN on 2007-04-20
I haven't tried your process.  I think mine is more straightforward and simpler but like I said, people like choice and having a couple installation methods to pick from doesn't hurt at all.  The people at Medibuntu rock and it's a great repo alternative until Saveas releases packages for 'acroread'. :-D

~L0cK

---

### Post by ADloser on 2007-04-22
I installed acrobat but it doesnt seem to want to open. can anyone help?
when I try to open it with run application, nothing happens.
when i open a PDF with firefox, firefox freezes.

 thanks.

---

### Post by lolocaust on 2007-04-23
I did a bit of googling, seems that there's a problem with poppler 0.5.4 which doesn't anti alias the fonts. I'll probably file a bug report now. Thanks everyone who tried to help.

EDIT: found a bug report already made for those who are interested: [https://bugs.launchpad.net/poppler/+bug/92296](https://bugs.launchpad.net/poppler/+bug/92296)

---

### Post by findik1 on 2007-05-15
Use Automatix to install fonts

---

