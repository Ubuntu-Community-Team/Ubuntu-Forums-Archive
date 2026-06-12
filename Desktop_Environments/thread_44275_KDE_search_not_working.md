---
title: "KDE search not working"
date: 2005-06-25
forum: Desktop Environments
---

### Post by Flawed on 2005-06-25
I installed KDE over regular Ubuntu Hoary and everything's working pretty well, except that the KDE search dialogs aren't working for me. I'm pretty new to Linux but  eventually remembered how to build a file index using the locate command. 

Well, thing is, locate works now, but the KDE search functions still don't. Could anyone point me to what I seem to have forgotten to install?

One more thing: If I try to do a search with Kat, I get the following error message:

1000:CPPSQLITE_ERROR[1000]: Database not open

Is this a clue? What am I doing wrong? Thanks a lot in advance.

---

### Post by Takis on 2005-06-25
Out of curiousity, how do you consider yourself new to Linux if you know how to use the 'locate' command? I consider myself reasonably proficient, and I'm still hopeless with it!  ;-) 

Anyway, what happens when you try to do a search?

---

### Post by ltmon on 2005-06-25
Kat is beta quality software.  I think you'd have to get in touch with the Kat developers to get any help there.  Their homepage is kat.sourceforge.net.

As far as the search goes, is it the "Find Files/Folders" that is in the kmenu you are talking about?  I don't think it uses "locate" unless you check the "Use Files Index" box.

I just had a go at using the KDE search (never used it before as I'm a bit of a command line junkie) and found that interestingly enough you either have to type a full file name or use a regular expression.

For example. if I wanted to find the file "01 - Godhopping.ogg" I would have to type in the full file name or simply "*godhopping*" (minus the double quotes) to succesfully the file.  

Strange behaviour I would have thought... it's more intuitive just to find any file with a name containing the text you typed in (i.e. the * at the start and end of the regexp would be automatically appended.

L.

---

### Post by Flawed on 2005-06-26
Takis, I've been playing with Linux on and off during the last one and a half years or so, that's why I still consider myself new to Linux. The first distro I ever tried was Fedora Core 2 and I bought the "Fedora Linux for Dummies" book which taught me a bunch of commands. :)

ltmon, I think I may just have forgotten to use  regular expressions, guess I've been spoiled by the Windows search function. :/
Unfortunately, I'm posting this from Windows as I managed to break my Ubuntu installation after a lazy day of playing with it, X won't start any more, telling me the nvidia driver module can't be loaded. Funny, I didn't even mess around with anything video card or xorg.conf-related. I'll let you know when I've got it working again.

---

### Post by Flawed on 2005-06-26
You were absolutely right, I started using regular expressions and now searching works flawlessly. My video card driver problem magically fixed itself, by the way, I can only pray my video card isn't on its way out...

---

### Post by ltmon on 2005-06-26
If you do a lot of searching you might find "kio-locate" to be worthwhile (you'll find it on kde-apps.org).  

It's a frontend to "locate" that runs as a io slave in konqueror... really powerful and quick to use.

L.

---

