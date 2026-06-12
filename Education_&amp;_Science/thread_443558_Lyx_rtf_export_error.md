---
title: "Lyx rtf export error"
date: 2007-05-14
forum: Education &amp; Science
---

### Post by timmie on 2007-05-14
Hello,
the RTF export converter is not present in my Lyx-QT although I think that all packages are installed.

Can anyone confirm the following error description for me, please?

[RTF export not present on Ubunutu (Lyx 1.4.3) [was: Re: How to Spot a](http://article.gmane.org/gmane.editors.lyx.general/38446)

Greetings!

---

### Post by kleeman on 2007-05-14
I could not see that option on my system. This might be more reliable anyway:

[http://wiki.lyx.org/Tools/LyX2OpenOffice](http://wiki.lyx.org/Tools/LyX2OpenOffice)

Once a document is opened with oofice it can be saved in *.doc format.

The lyx wiki says oofice formats are better than ms word formats...

---

### Post by timmie on 2007-05-15
Then it is a error of the Ubuntu package. Because all other ML members seem to have this feature as you can see from my above mentioned link.
What do you think?

---

### Post by kleeman on 2007-05-15
Interesting I think you are right. I have a version 1.5 beta2 which I compiled myself from source and it has the rtf export option and it seems to work OK at least with simple files. I have an amd64 checkinstall deb if you are interested.

---

### Post by timmie on 2007-05-15
> **kleeman said:**
> Interesting I think you are right.
I was not right:
[LIST]
[*][[SLOVED] Re: RTF export not present on Ubunutu (Lyx 1.4.3) [was: Re: H](http://article.gmane.org/gmane.editors.lyx.general/38503)
[*][http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lyx-qt](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lyx-qt)
[*][http://www.lyx.org/announce/1_4_4.txt](http://www.lyx.org/announce/1_4_4.txt)
[/LIST]
> **kleeman said:**
> 
 I have a version 1.5 beta2 which I compiled myself from source and it has the rtf export option and it seems to work OK at least with simple files. I have an amd64 checkinstall deb if you are interested.

Thank you but I am finishing a very important text and don't want to switch to a beta version!

I shall be finished in the next 2 weeks and after that I will give 1.5.x a try.
I think I'd need a intel32 version, though.

What is your imprssion of 1.5 beta2?
Is it farely stable?
Shall we backport 1.5.x once the real version is out? (I donno exaclty when...)

P.S.: Allow one question:
Do you use tetex or texlive?
Do I just switch by installing texlive and deinstalling tetex via syaptic?

Greetings!

---

### Post by kleeman on 2007-05-15
Actually 1.4.4 is stable (more so than 1.4.3 actually) and is in gutsy. I took the source code files from the debs (dsc, orig.tar.gz and diff files) and recompiled the debs for feisty without too many problems and it works well with rtf export.

---

