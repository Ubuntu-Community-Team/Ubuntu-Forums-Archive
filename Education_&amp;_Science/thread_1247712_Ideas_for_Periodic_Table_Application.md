---
title: "Ideas for Periodic Table Application"
date: 2009-08-23
forum: Education &amp; Science
---

### Post by Galvin Tjime on 2009-08-23
Hello,

I recently installed GPeriodic on my copy of Fedora and I was fed up with the GUI and felt that it could use a boost. I decided that I would write a new periodic table application for Gnome with the hopes of making it better than GPeriodic and hopefully take some lessons and improve upon or add some new features not included in Kalzium. I am currently in the planning stages of development and am looking for ideas on what I should include in the program. If you have an ideas or requests please tell me and I will see if I can work them in.

Regards,

Galvin

P.S. After the core of the program is written and working in Gnome, I would like to make it OS / DE Independent.

---

### Post by jbrefort on 2009-08-24
What new features do you intend to implement? Did you have a look at GChemTable (from [http://gchemutils.nongnu.org)?](http://gchemutils.nongnu.org)?) It needs a lot of improvements because of lack of available time, but might be a good starting point.
You might also have a look at gElemental. It would be nice if everybody intersted in a periodic table in gnome join and build a great application, instead of all theses isolated efforts (you might disagree, of course).

---

### Post by ssam on 2009-08-24
also look at kalzium.

---

### Post by Galvin Tjime on 2009-08-24
> _**jbrefort says:**_

What new features do you intend to implement? Did you have a look at GChemTable (from [http://gchemutils.nongnu.org)?]("http://gchemutils.nongnu.org%29/?") It needs a lot of improvements because of lack of available time, but might be a good starting point.
You might also have a look at gElemental.I have been planning on adding the atomic number, element name, and average atomic weight to the buttons, making it when you mouse over the different cells they expand so they are easier to read, and that when you mouse over them all elements of a similar classification are highlighted in different colors. Other than that I liked what was already included in the program information wise.

> **_jbrefort says:_**

It would be nice if everybody intersted in a periodic table in gnome join and build a great application, instead of all theses isolated efforts (you might disagree, of course).I have no problems with working together on one project. As a matter of fact, that is what I had originally intended however when I went to view the source code for GPeriodic I realized that I would have to write a LOT of new code, to the point where I might as well make an entirely new package. I also have never created a program before so I thought that it might be interesting to do it on my own however I completely support all ideals of Open Source Software  and the cooperation between coders.

> **_ssam says:_**

also look at kalzium.     I would like to, however I have had problems with KDE and Gnome cooperating and I can't install Kalzium as a separate package from the education bundle. I'll probably setup a VM with another distro on it to experiment with Kalzium soon.

---

### Post by jbrefort on 2009-08-25
[QUOTE=Galvin Tjime;7841711]I have been planning on adding the atomic number, element name, and average atomic weight to the buttons, making it when you mouse over the different cells they expand so they are easier to read, and that when you mouse over them all elements of a similar classification are highlighted in different colors. Other than that I liked what was already included in the program information wise.

This should be easy to implement in GChemTable, at least the first part. GChemTable already allows various color schemes for the buttons. I initially wrote it as a demonstrator of what is possible, because one guy asked for it and said he volunteered to develop it (unfortunately I never heard of him since) so many things are missing. If you join, I'd be very pleased.
In Ubuntu, GChemTable is part of the gcu-bin package, if you want to try it.

---

### Post by ssam on 2009-08-25
> **Galvin Tjime said:**
> 
I would like to, however I have had problems with KDE and Gnome cooperating and I can't install Kalzium as a separate package from the education bundle. I'll probably setup a VM with another distro on it to experiment with Kalzium soon.

i have often installed a couple of KDE apps on a gnome system. it will download a lot of kde libraries, but should not cause any problems. if you install all of kde (via the kubuntu-desktop metapackage) then you do get weird issues such as the splash screen changing, but just the odd app should be fine.

---

### Post by ad_267 on 2009-08-25
Maybe you could have a panel showing more comprehensive information on the selected element, stuff like how it is obtained and what applications and uses it has. You could possibly show the entry for the element from Wikipedia.

---

### Post by Galvin Tjime on 2009-08-26
> **_jbrefort says:_**

If you join, I'd be very pleased. In Ubuntu, GChemTable is part of the gcu-bin package, if you want to try it. 	

I would be more than happy to join your project. Just so you know, I am running Fedora Core 11 x86_64, but I'll probably have a VM of Ubuntu up later tomorrow. I am also new to coding (program coding that is; I do web mostly) so my work may take some time to complete. I don't know exactly how to go about joining but, if you don't mind taking the time, then I can start fairly soon.

---

### Post by jbrefort on 2009-08-27
> **Galvin Tjime said:**
> I would be more than happy to join your project. Just so you know, I am running Fedora Core 11 x86_64, but I'll probably have a VM of Ubuntu up later tomorrow. I am also new to coding (program coding that is; I do web mostly) so my work may take some time to complete. I don't know exactly how to go about joining but, if you don't mind taking the time, then I can start fairly soon.

There is no strict time schedule. At release time, what is ready is included, and other stuff waits for next release. To join, we have a low trafic mailing list (gchemutils-main@nongnu.org), or better, the #gchemutils channel at irc.gimp.net (I'm often there at European day time).

---

