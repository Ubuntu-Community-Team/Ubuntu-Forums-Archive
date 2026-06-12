---
title: "Reproduce my Ubuntu?"
date: 2009-03-04
forum: General Help
---

### Post by tsedrey on 2009-03-04
Hey guys, I have my system pretty thoroughly configured and such. A lot of my friends, especially the ones thinking about switching over, want to try linux, but want to start with my set-up rather than the default liveCD. I understand the security risks of copying my files and whatnot, but I am tired of setting up my friends' systems with my set-up. I was wondering if there was anyway/program that I can use in order to create an .iso which is a liveCD that has my specifications (programs, themes, packages, etc.)? I tried looking around a bit for this, but I wasn't exactly sure what search. I am using 8.10.

Thanks for the help?
David

---

### Post by boof1988 on 2009-03-04
I haven't tried it yet... but I have seen people recommend [Remastersys](http://sourceforge.net/projects/remastersys).  Other people will probably give some more ideas (and hopefully they have tried them).

---

### Post by benny bronx on 2009-03-04
Remastersys.  A handy little tutorial here:

[http://www.dedoimedo.com/computers/remastersys.html]("http://www.dedoimedo.com/computers/remastersys.html")

---

### Post by emarkay on 2009-03-04
FWIW, other than "eye candy" (no dissing implied) what's so different from your system's setup to a "virgin" install?

Curious as I have had to occasionally reinstall Ubuntu (usually due to bumblefingering on my part) and this is a similar concept...

---

### Post by tsedrey on 2009-03-04
There is nothing SO special I guess, but I have a bunch of 3rd party software install and I guess the main reason I am pursuing this is to give to friends. One of their main complaints against switching is the trouble of having to install codecs and what not. I figured this would take it away.

---

### Post by blazemore on 2009-03-04
If you're going to give it to friends, it's really easy.
```
sudo remastersys dist **mydistro**.iso
```

The iso is stored in /home/remastersys/remastersys or similar

Alternatively, direct them towards Linux Mint, which is (IMO) a more beginner-friendly version of Ubuntu with codecs already installed.

---

### Post by Therion on 2009-03-04
> **tsedrey said:**
> There is nothing SO special I guess, but I have a bunch of 3rd party software install and I guess the main reason I am pursuing this is to give to friends. One of their main complaints against switching is the trouble of having to install codecs and what not. I figured this would take it away.

Save yourself some effort and frustration.  Make them download (or hand out copies if you're feeling generous) of **Super Ubuntu: **
> Super Ubuntu is just Ubuntu 8.10 (Intrepid Ibex), but it also includes:

    * System and application updates: all updates released for Ubuntu + GIMP 2.6.3 + OpenOffice.org 3 + Firefox 3.0.4
    * Better Multimedia Support: MPlayer and VLC, DVD-playback, MP3 support and other multimedia codecs
    * Better Internet experience: aMSN, aMule, Adobe Flash player and Opera
    * Support for portable applications/other installation methods: Autopackage, SFS Technology, Smart Package Manager, Wine and Zero Install
    * Support for: Java RE, Microsoft Office 2007 file formats, others...
    * Graphical interfaces/managers: compizconfig-settings-manager (Compiz), Gufw (Uncomplicated firewall), ndisgtk (NDISwrapper) and padevchooser (PulseAudio)
    * Utilities: Adobe Reader, EnvyNG, Furius ISO Mount, GParted, NDISwrapper, Ubuntu Tweak and StartUp-Manager
    * Extra repositories 
Download links at the bottom of the page.

[http://hacktolive.org/wiki/Super_Ubuntu](http://hacktolive.org/wiki/Super_Ubuntu)

---

### Post by blazemore on 2009-03-05
I'd definitely recommend Mint over Super Ubuntu.
Super Ubuntu is just bloat.

---

### Post by Therion on 2009-03-05
> **blazemore said:**
> 

I'd definitely recommend Mint over Super Ubuntu.
Super Ubuntu is just bloat.
You consider what, exactly, "bloat"?

VLC? DVD-playback packages? All the other common multimedia codecs? Flash player? Wine? Java?

And Mint isn't bloated in your opinion??  

I'd love to hear your analysis of how Super Ubuntu is bloated and how trim and svelte Mint is by comparison.  Seriously.

---

### Post by tsedrey on 2009-03-05
So I understand I can make a backup of my system, but is there a way to give them the install options and everything, like choosing user name/pw, timezone, etc., and install my changes?

Thanks

---

### Post by blazemore on 2009-03-06
Therion my bad. I was thinking of Ultimate Edition.
Super Ubuntu is Super, but I personally think that Mint is more polished.

---

