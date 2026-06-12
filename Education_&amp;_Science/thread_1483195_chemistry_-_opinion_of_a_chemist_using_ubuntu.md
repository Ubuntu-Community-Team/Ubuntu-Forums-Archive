---
title: "chemistry - opinion of a chemist using ubuntu"
date: 2010-05-14
forum: Education &amp; Science
---

### Post by gregbahun on 2010-05-14
Who I am - finishing my PhD in chemistry - using Ubuntu, the netbook remix version. My knowledge and experience with Linux is still limited, but I have been able to install a number of programs that require numerous commands in Terminal...then again, some have not installed. So, I'm no pro, but with a bit of googling, "you too can make the switch". I do still use windows for most things, but find myself occasionally wanting to get work done on my netbook too, in linux.


1) Chemical drawing programs - Marvin - free, cross platform (java based).

[http://www.chemaxon.com/marvin/release-notes.html](http://www.chemaxon.com/marvin/release-notes.html) 

This is by far the best free program I've used in linux. It can do most things you can do in ChemDraw (although no NMR prediction) and even then some. Note that the folks over there also have an inventory program (Instant JChem is what you want) that can do searches by substructure. Very wicked. It has its own quirks, but once you get to figure them out, it's as useful as you'd think.

I have just recently tried ChemDraw 7 in Wine - and to my surprise installed and runs without much difficulty. Upon launching, you have about 30 sec maybe until it actually comes up, but once it does it works flawlessly.

2) NMR processing - Spinworks - free - cross platform (.NET based)

Version 3.17 has some issues, but can run with Mono. Basically, go to the terminal and navigate to the directory where you have your spinworks program, and (provided Mono is installed) just type mono (spinworks filename).exe     and hit enter and it should load up. The only issue I've had is with the buttons on the right hand side. I've emailed the programmer, and he's keen to resolve any issues people have - so, if you find any "bugs" please report them to him. He was very quick to respond to my previous emails.

3) Reference/Citation/Bibliography program - Zotero - free - cross platform (just needs firefox as far as I know)

Ok, I was very reluctant to go this route - however, so far it's worked the best. I have (time and time again) tried Bibus, Referencer, Pybliography - I've had problems with all of them. Bibus doesn't seem to recognize OpenOffice is even on the computer. And I have not been able to import my reference file from endnote no matter what file formats I've tried. Oddly enough, JabRef was able to import the file. From here, I was able to export it such that Bibus could import it...but still no OpenOffice connection.

Zotero however - a firefox and openoffice plugin later - was able to insert references into a document i typed and insert the bibliography separately if i wanted. it has a growing amount of support and knowledge - and best of all, a move to make this a stand alone application. personally, i don't like firefox much as a browser, so i'm very excited to see this application move along in its development. i look forward to the day when you can download this as an individual application.

4) Molecular modelling - Avogadro - free - cross platform

I am a synthetic chemist (polymer and organic) so my knowledge on this matter is limited. I imagine it's not "that" impressive to some people - but, it's certainly simple to use and does give very nice images. It is also cross platform.



At this point, other programs I've not had to use too much, or at all, yet. So, the following comes from just some googling:

Graphing - in Windows I'd do my graphs in Excel or Origin. I've seen this as a Linux alternative:

[http://scigraphica.sourceforge.net/](http://scigraphica.sourceforge.net/)


SciFinder - haven't tried. Our school recently changed from a client based version to a web based version, so I don't see there being a problem at all...famous last words

I can't think of any other programs I use on a daily basis, for chemistry purposes. But, I will have to try other versions of ChemDraw on Wine along with Origin...and Endnote really. But, I didn't think Endnote worked with Openoffice, so, at that point, there's not too much use. I guess I can try MS Word in Wine...we'll see.

Please please comment on this. I know people that are either considering moving to Linux, or reconsidering their move to it - mainly because they are unaware of the software that exists for it. Updated Threads like this are needed. As much as I first liked BKChem when i found it (compared to some other programs), Marvin blows it out of the water. This knowledge should be more easily accessible to people rather than have to dig through forums and posts from 2006.

---

### Post by FreeTheBee on 2010-05-15
Hi, I am chemist as well. At home I run ubuntu and at the uni winXP. I went though your poll and have to say that none of the above were reason for concern really.

I have little need for chemistry specific software such as drawing and modelling tools. I noticed a bunch of chemistry programs in the software center. Also there is the Gnome Chemistry Utils bundle. I haven't really used any of them though, so I can't say anything about them. 

I do have a few programs that came with lab equipment which I need on occasion. Since I did not manage to install these in wine I installed winxp in virtualbox, so I can use these programs in there. This is probably a bit heavy if you're on a netbook though.

When it comes to installing programs in general, I rarely do this manually. If the program is not in the repositories, there is often a launchpad ppa, allowing me to use synaptic in almost every case. I think this is actually more convenient than in windows, since all updates are taken care of by synaptic as well. The only significant exceptions were texlive 2009 and matlab. tl2009 is now in the repositories but I would still prefer the manual install, since this gives me more control over latex package management.

For data analysis and plotting I use matlab, which runs in windows as well as linux. Possible alternatives are octave, scilab or a combination of numpy, scipy and matplotlib.  

Some origin alternatives I have played with a little bit are, grace, Qtiplot and scidavis.

My writing I do in LaTeX, with kile and sometimes TeXworks as my editor. For reference management I use Jabref, which is cross platform. I hardly use office software and when I do it is such basic stuff that switching between openoffice and ms office is no issue.

I prefer using google scholar, scirus and scopus over scifinder to find articles. Scifinder has a bigger database I guess, but the search options are terrible imho. Sometimes, I use it in my office, but never tried to install it in wine.

Some other tools I find handy are: 
Liferea, to keep track of rss feeds. Most journals have a feed so it is an easy way to keep up to date with current literature. 
Unison, to synchronise folders. I also use krusader sometimes for this purpose. 
Dropbox, as a central storage. I prefer this over ubuntu one, since it is cross platform.
Keepnote and Basket, for note keeping. I haven't really decided which one to use yet.

These are not really chemistry related of course, but I do use them a lot when working.

---

### Post by Leo2099 on 2010-08-24
Hi i'm using Ubuntu for about a year by now... and i wanna know what was the answer from the programmer of SpinWorks because i'm having the same trouble as **gregbahun**.

Greetings!:D

---

### Post by gregbahun on 2010-08-25
i got extremely busy and sidetracked and never got back to emailing the spinworks programmer.

he had made one initial adjustment, but it was still problematic. at least on a netbook. not sure about full screen resolution.

if you email him with your issues, there's a good chance he'll reply soon enough. solutions to the problem are maybe another issue, but at least the response should be in a reasonable time provided he's not on vacation.

greg

ps - here's his page (or one of them i guess)
[http://www.umanitoba.ca/chemistry/nmr/people/index.html](http://www.umanitoba.ca/chemistry/nmr/people/index.html)

---

### Post by bouncingwilf on 2010-08-25
Unable to participate in the poll as there was no options to indicate No Concerns! However, as I'm now long retired I suspect my opinions are of little direct value BUT when I was working as a troubleshooting peripatetic chemist for a large Multi-national, my most powerful tools were statistical/mathematical and Linux has a variety of these in spades! (mostly however, we wrote our own software) 

bouncingwilf

---

