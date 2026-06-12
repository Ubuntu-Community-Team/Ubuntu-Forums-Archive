---
title: "Plotting software options in GTK???"
date: 2009-12-17
forum: Education &amp; Science
---

### Post by mdshaver on 2009-12-17
Are there any currently maintained plotting software programs written in GTK for better integration with the Gnome desktop? My main interest is in a a GUI-based program like Origin or SigmaPlot for those who need to produce simple publication-quality graphs but do so infrequently enough that learning programs such as R or Gnuplot is not worth the time. I realize there are good options written in QT (e.g., QtiPlot, SciDavis) that can integrate into the KDE desktop but it seems the only GTK-based program with a GUI was SciGraphica which is no longer maintained.

I realize functionality is the most important thing but I just thought it would be nice to have a good, easy-to-use plotting program to fit in with OpenOffice, Bibus, PSPP, etc.

Any thoughts?

---

### Post by s3a on 2009-12-17
I can't think of a GTK program but kmplot is (really) good.

---

### Post by gunksta on 2009-12-17
This is one of those never-ending questions, kind of like EMACS v. Vim debates. I suppose you could use the spreadsheet built into OpenOffice.org or install Gnumeric (another GTK+ based spreadsheet program). Truthfully, I can't think of any GTK+ apps that are as good as the apps you already mentioned, but you really can get nice looking results out of a spread-sheet if you take some time and do it right. I admit that I really like the color-scheme built into newer versions of OpenOffice.org, although they are a little problematic if you need it to work well when photocopied on a black and white photocopier.

While I do understand why some people hesitate to install all of the KDE dependencies on a Gnome-based desktop, especially if the machine is older and has a smallish hard-drive, it seems silly to worry about installing QT. In fact, odds are decent it's already installed. There are lots of good apps out there that use QT. Apps built on top of QT4 (most) actually do a pretty good job of blending in to a GTK+ desktop. In the grand scheme of things, it seems like a minor thing to worry about.

For the record - I do eat my own dog-food. While Kubuntu is my preferred flavor of Ubuntu, I have several GTK+ apps such as FireFox, PSPP, etc. installed here at work, because I find them useful. In fact, FireFox is my primary browser although I do have my eye on Chrome (also GTK+). The fact that these apps are based on GTK+ and not QT doesn't really concern me. Where I have the option of installing a GTK or QT front-end, I will usually lean towards the QT version (example - Celestia, which I have installed at home) but if there's an app I want, I install it.

All of the commonly used Operating Systems (Windows, Apple, Linux, BSD) support multiple widget sets. I'll admit that many of these look similar on older versions of Windows (not so much Windows 7) but Apple and Linux apps have a long and I argue rich tradition of allowing different widget sets to look a little different from one another. In fact if you look at a lot of the crap-ware that Windows comes with from Dell, HP, etc. you will find that these developers actually spent time making their app look different from the rest of the Windows applications. The irony here humors me. There are days where I am running QT, GTK+ and the uglier than sin TK widgets all at the same time. I will admit that TK is ugly but the other two look just fine.

Variety - 'tis the spice of life.

---

### Post by peter d on 2009-12-17
> **s3a said:**
> I can't think of a GTK program but kmplot is (really) good.

I also have used Kmplot and found it to be very good.

---

### Post by samden on 2009-12-17
If you already think QtiPlot and SciDavis will work, why not just use them? 

Quibbling over QT vs GTK seems irrelevant to the basic users you are considering here. Someone who has the time to worry about that probably has the time to learn R. Someone who doesn't want to learn a command-line tool probably doesn't have a clue about QT or GTK either, and just wants something that works.

---

### Post by sprince09 on 2009-12-18
If you're familiar with MATLAB's plotting interface, the programs GNU Octave and FreeMat might be of interest to you. They both provide pretty simple plotting interface (eg, plot(x,y) generates a plot of x and y points) and you can do pretty much anything with them, 2D, 3D, polar, etc...

The program wxMaxima also has a pretty good plotting interface, which is suprisingly easy to use considering how finicky Maxima is (at least for me).

Other than that, OpenOffice Calc is always an option...

---

### Post by sprince09 on 2009-12-18
Here's a list of plotting tools for Ubuntu I found completely by accident:

[https://help.ubuntu.com/community/UbuntuScience#Plotting](https://help.ubuntu.com/community/UbuntuScience#Plotting) Tools

---

