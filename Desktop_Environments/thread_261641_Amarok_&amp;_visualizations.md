---
title: "Amarok &amp; visualizations"
date: 2006-09-20
forum: Desktop Environments
---

### Post by juraj on 2006-09-20
I have Dapper 6.06.1, fully updated, with enabled all official Ubuntu repositories, XGL/Compiz (doesn't work on Xorg/Metacity too). Also have Amarok 1.4.2 and libvisual-0.4-0 installed, all from Ubuntu repositories. When I open Visualizations in Amarok a small blank window appears and quickly disappears.

I've read Amarok package description:

"Support for XMMS and libvisual visualization plugins is also compiled in (you need to have xmms or libvisual0.4-plugins installed to be able to use it)."

...but there's no libvisual0.4-plugins. A quick view at packages.ubuntu.com reveals that there exists a package of a similar, not exact, name - but only for Edgy ([http://packages.ubuntu.com/libvisual-0.4-plugins)](http://packages.ubuntu.com/libvisual-0.4-plugins)). And, oh, I don't really want to install xmms.

How can I get Amarok to show me some visualizations? ;)

---

### Post by juraj on 2006-09-20
Bump... :(

---

### Post by rpalyvoda on 2006-09-20
Try searching for libvisual on

[http://www1.apt-get.org/search.php](http://www1.apt-get.org/search.php)

I found it there for Ubuntu 5.10. However, there are only 3 very, very poor visiualisations. I haven't seen such a thing since 90ies :o(

Otherwise, if you really want some visualisations, you may give a try to winamp with wine, it'd work.

---

### Post by rpalyvoda on 2006-09-20
And, above all:

DONT INSTALL XMMS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by juraj on 2006-09-20
Thanks on your reply. I was afraid of this - but oh, never mind. Visualizations aren't so important at all. I tried running winamp 5 classic in wine but I wasn't much satisfied ;)

BTW I installed xmms at one point but didn't like it at all so I removed it, why did you mention that?

---

### Post by rpalyvoda on 2006-09-21
Well, I just don't like xmms at all ;)

---

### Post by n3il on 2006-09-22
Bump, anyone know how to get some visualizations? :)

---

### Post by yeehawjared on 2006-09-22
yeah i was wondering the same thing.  There's got to be an active community for amarok plugins... the equivalent to winamp's plugin community.

---

### Post by atraylen on 2006-09-30
I too have run in to this problem.  However I had some success utilizing google to locate [debian's version of this package.]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibv%2Flibvisual-plugins%2Flibvisual-0.4-plugins_0.4.0.dfsg.1-1_i386.deb&md5sum=d41d441c7355dd9c324ae9b0296d1b63&arch=i386&type=main")  Upon installing I encountered some dependency errors.  I assumed that It would not work.  Just to be sure I restarted Amarok and 8 vizualisations were available.  I am not sure if it works the way it is supposed to one or two of the viz's don't seem to work.  I wonder if there is some sort of Amarok plugin community.  Anyhow I suppose it will suffice for now.  btw, not to be off topic, I just dumped winbloze for good :-D

---

### Post by Bizmac on 2006-10-11
Works great, I have now 8 visuals GOOD!!!
Amarok is just the BEST...Go kubuntu, vista out!

How to avoid the problem with the dependencies evreytime I launch "apt-get"?

and the fullscreen is great (right click). Love Jess!

---

### Post by jdunn on 2006-10-14
I have Amarok 1.4.3 on Kubuntu Dapper.  I just decided one day that I wanted to try out the visualizations.  I received an error message saying I needed the libvisuals-plugin (or maybe it was "libvisual-plugin") package so I went to the Dapper repositories and there it was.  I downloaded it and there are 12 visuals on Amarok (10 of them work).  Not sure why you couldn't find it but I only have the basic main, restricted, universe, multiverse and backport repositories in my list.

I was looking in this forum because I was wondering how to get the other two visuals to work.  I suspect they are glx visuals.  I'm using a nvidia card with the glx driver.  Its no big deal if I can't get the two visuals to work, though.

---

### Post by easytiger on 2006-11-22
He's right Guys. just search for libvisual in adept or synaptic. install libvisual-0.4-plugins .

Rightclick on the scope at the bottom of amarok and click visualization. there should be quite a few. The best is probibally 'jess'. I have to say winamp's Milkdrop was, literally, awesome. pity we can't have it

---

### Post by devilsadvocate1987 on 2006-11-23
Actually, you can. 
[http://amarok.kde.org/wiki/ProjectM_HowTo](http://amarok.kde.org/wiki/ProjectM_HowTo)

Havent had the time to try it out. Maybe I will in a week or two. If anyone gets this to work please post how. The page talks of 'unresolvable' depependacies somewhere :/

---

