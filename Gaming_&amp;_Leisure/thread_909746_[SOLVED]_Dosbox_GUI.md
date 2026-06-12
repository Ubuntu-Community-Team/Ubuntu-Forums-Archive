---
title: "[SOLVED] Dosbox GUI"
date: 2008-09-03
forum: Gaming &amp; Leisure
---

### Post by johnno56 on 2008-09-03
I am running Hardy 8.04 with Gnome desktop. Does anyone know of a dosbox frontend or gui that I can use? (please provide step-by-step install instructions)

I have had dfend running when I had KDE and it worked fine. Cannot get it to run under Gnome. I have heaps of dos games that I play (yes, I know my age is showing...) and I am getting a bit tired of typing the commands directly into dosbox.

Dosbox, running manually on Gnome, runs great. I would appreciate any info about a gui or frontend that runs on Gnome.

many thanx

J.

---

### Post by lakersforce on 2008-09-04
I don't know of a gui, but try opening a console and write ```
man dosbox
```

It tells you everything you need to know about how to make configuration files, so you don't have to write all those annoying mount lines every time.

---

### Post by Perfect Storm on 2008-09-04
[http://gaming.gwos.org/doku.php/guides:64bit:dosboxgui](http://gaming.gwos.org/doku.php/guides:64bit:dosboxgui)

---

### Post by ronnielsen1 on 2008-09-04
I just use dosbox in the background. You can file associate with dosbox to where the dosgame opens up automatically with dosbox

---

### Post by johnno56 on 2008-09-04
Thank you Lakersforce. Quite a bit of reading ahead of me.... Much appreciated.

---

### Post by johnno56 on 2008-09-04
AI,

I already had dbgl installed but did not know how to execute it.

Followed all instructions. Everything installed fine. Dbgl ran without a hitch.

Much appreciated.

J.

---

### Post by johnno56 on 2008-09-04
Many thanx to all who have helped solve my problem.

Could not have done it without you all.

Regards.

J.

PS: I do not know how to close the post. Relatively new at this stuff.

---

### Post by DarthBrady on 2009-03-07
> **johnno56 said:**
> AI,

I already had dbgl installed but did not know how to execute it.

Followed all instructions. Everything installed fine. Dbgl ran without a hitch.

Much appreciated.

J.

I am Having Trouble Both Installing And Executing. After following the instructions on the website, It wouldn't run. Then I went back, and discovered I needed a java runtime update.

I updated java in synaptic, and the dbgl autorun file worked ONCE. After i closed it, I wont open back up. Instead,  When I run it now, Ubuntu gives me a message saying 'Do you want to Run "dbgl", or display its contents?' I try to run, but it will not start.

*Sorry for my ignorance to this, I just switched from Windows a few weeks ago. Any Help is very appreciated. *

---

### Post by Perfect Storm on 2009-03-07
> **DarthBrady said:**
> I am Having Trouble Both Installing And Executing. After following the instructions on the website, It wouldn't run. Then I went back, and discovered I needed a java runtime update.

I updated java in synaptic, and the dbgl autorun file worked ONCE. After i closed it, I wont open back up. Instead,  When I run it now, Ubuntu gives me a message saying 'Do you want to Run "dbgl", or display its contents?' I try to run, but it will not start.

*Sorry for my ignorance to this, I just switched from Windows a few weeks ago. Any Help is very appreciated. *

Properly you have many diffrent java installed, but it's set to a diffrent default version on your machine.

```
java -version
```

---

### Post by DarthBrady on 2009-03-07
> **Artificial Intelligence said:**
> Properly you have many diffrent java installed, but it's set to a diffrent default version on your machine.

```
java -version
```

> java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu5) Runtime Environment (build 1.6.0_0-b12)
CACAO (build 0.99.3+hg, compiled mode)

That's what I got. I *think* I may have fixed it. I renamed the folder I stored /dbgl064/ folder inside of to contain no spaces in the folder name (always worked in XP using 'D-Fend'), and created a shortcut to it in my Applications Menu. Seems to run from there ok so far, Now I just need to learn my new frontend! Thanks for the quick reply!

..Switching from Windows just gets easier and easier.

---

### Post by Perfect Storm on 2009-03-07
Well you could instead switched to sun java instead of using Icedtea.

```
sudo update-alternatives --config java
```

---

### Post by DarthBrady on 2009-03-11
> **Artificial Intelligence said:**
> Well you could instead switched to sun java instead of using Icedtea.

```
sudo update-alternatives --config java
```

Thanks! I did not know that. DBGL starts right up now.

---

### Post by Thanatos_DTH1 on 2009-07-11
> **Artificial Intelligence said:**
> [http://gaming.gwos.org/doku.php/guides:64bit:dosboxgui](http://gaming.gwos.org/doku.php/guides:64bit:dosboxgui)

Helped out when I was trying to set up DBGL, but since boundlesssupremacy.com doesn't exist anymore, I had to find another source for the package.
Replace the line:
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb

with:

wget http://taurinocerveza.com/scripts/getlibs-all.deb

and it works just fine.

---

