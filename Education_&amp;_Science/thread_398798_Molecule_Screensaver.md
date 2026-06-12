---
title: "Molecule Screensaver"
date: 2007-04-01
forum: Education &amp; Science
---

### Post by skezza on 2007-04-01
Hello,
I am not sure whether this is in the correct section, however for the first time today (while using Ubuntu Feisty) I checked out the screensavers section and noticed theres a great screensaver (for scientists) called Molecule. I Wondered whether this was available for Windows as well, as I wouldnt mind putting it on my work laptop. I'm a science teacher at a school in the UK, thats why I thought it'd be nice.
Thanks

---

### Post by ssam on 2007-04-01
[http://www.jwz.org/xscreensaver/](http://www.jwz.org/xscreensaver/) is the site all the ubuntu screensavers come from

about a windows version he says
> There is no Windows version of xscreensaver, and there never will be. Please stop asking. Microsoft killed my company, and I hold a personal grudge. I don't use any Microsoft products and neither should you.

---

### Post by dreadlord_chris on 2007-04-01
> **skezza said:**
> Hello,
I am not sure whether this is in the correct section, however for the first time today (while using Ubuntu Feisty) I checked out the screensavers section and noticed theres a great screensaver (for scientists) called Molecule. I Wondered whether this was available for Windows as well, as I wouldnt mind putting it on my work laptop. I'm a science teacher at a school in the UK, thats why I thought it'd be nice.
Thanks

Google [Molecule screensaver]("http://www.google.com/search?hl=en&client=opera&rls=en&hs=kw6&q=Molecule+screensaver+Windows&btnG=Search") there are plenty of them out there.

---

### Post by freda on 2007-04-02
Yes, google is the best teacher.

:)

---

### Post by skezza on 2007-04-02
Ah ok, well, the reason  i liked that one so much is it actually gave real molecules, structured properly along with the name and i've never seen one like it. I've actually recently asked if I could install a version of Ubuntu on, however, when i used the live CD, I had serious problems with the Wireless Card, but its typical really its a RA2400 so i was expecting them. Its not a worry at the moment though, as i doubt ill be allowed. But I use it on my home PC all the time :)

Thanks again

---

### Post by Entity` on 2007-12-06
Glad I dug up this forum, anyway, whoever said this:

> There is no Windows version of xscreensaver, and there never will be. Please stop asking. Microsoft killed my company, and I hold a personal grudge. I don't use any Microsoft products and neither should you.

...is 100% right, especially with Vista.  On a related note (to this topic), however, the only thing I wish to see in that particular screensaver is at least 100-200 more molecules, that way there'd usually be something new you haven't noticed before.  I have never found a screensaver quite like this one and am quite fond of it.

I also miss the advanced options that let me configure the density and speed of the glyphs in glMatrix.

---

### Post by bruceschaller on 2009-03-02
Hi There!!

To Add molecules to the molecule screen saver do the following:  

Replace gnome-screensaver (which is a repackaging of the original Xscreensaver) with Xscreensaver.

In terminal:
```
sudo apt-get install xscreensaver
```

Then run xscreensaver-demo to configure xscreensaver.
```
xscreensaver-demo
```

Now a window will pop up listing all of the screen savers that are a part of the package.  You can select how they run, their refresh rate, and for the molecule screen saver, a number of other options.  One is selecting a source (folder) for pdb files.

You can download pdb files, put them in a folder, and have the screensaver display them.

I made a hidden folder called molecule in my home folder like this:
```
mkdir ~/.molecule
```

It's hidden because I don't want to see it cluttering up my home folder.  (Hidden folders are denoted by a . in front of the folder name, and can be displayed within a file browser by pressing Ctrl-H)

I made a folder with about 100 more molecules.  If anyone would like me to send them this folder, just shoot me a email at
bruce [at] schaller-solutions [dot] com

If you found this useful, and would you add any more molecules, let me know, and send me some more pdb's!

Thanks!
Bruce Schaller

---

### Post by bruceschaller on 2010-02-06
Molecule seems to be no longer included by default.

To install it and many other screensavers, use this command:

```
sudo apt-get install xscreensaver-gl-extra xscreensaver-data-extra
```

And you will be good to go.

---

### Post by Marinski on 2010-02-17
On my installation apt does not find xscreensaver-gl-extra and xscreensaver-data-extra, and says that xscreensaver-gl and xscreensaver-data replace them. However molecule is not installed. Anybody got a clue how to install it?

---

### Post by JAwuku on 2010-08-09
I just came across this thread, when looking to add to the Molecule Screensaver.

A nice coincidence :)

Someone was wondering if there is a Windows equivalent.

I was just looking on Google.

Check out an online viewer called Santorini,

and a screensaver called Patmos.

These allow you to see molecules on the computer.

These are written by Robert Oeffner at the University of Cambridge.

See:

[_Robert Oeffner's Santorini and Patmos Viewers_](http://www.oeffner.net/development/)

---

