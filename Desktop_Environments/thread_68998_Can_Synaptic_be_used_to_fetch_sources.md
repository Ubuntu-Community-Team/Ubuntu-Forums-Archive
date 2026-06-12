---
title: "Can Synaptic be used to fetch sources?"
date: 2005-09-25
forum: Desktop Environments
---

### Post by Blueshell on 2005-09-25
In Hoary, current Synaptic (0.56):

I can't for the life of me figure out how to fetch a source package using Synaptic.  I've got several deb-src lines uncommented in /etc/apt/sources.list, and Synaptic shows them to me (but see PS).  But I can't find -anywhere- in the UI a way to actually fetch one!  All I see is ways to get binary packages.  The so-called documentation is no help (and apparently has screenshots from a previous version, e.g., the Repositories screenshot doesn't match the screen you get if you're actually there), and lots of searching has failed to turn up this information.  (Typically, people start talking about Synaptic but then jump into using apt from the command line instead.  And the Ubuntu 5.04 Starter Guide, while mentioning uncommenting deb-src lines, doesn't say anything at all about -using- them.)

Do I really need to use apt-get from a command line to fetch sources?  If so, why is this handwaved away in all of the Synaptic documentation?  A clear declaration that Synaptic cannot handle source distributions would save a lot of time---or a clear example of using one.

P.S.  It's incredibly misleading that Synaptic apparently tries to emulate a piece of fanfold paper in its listing of repositories in the Repositories dialog---every other repository is grey.  However, since every other repository is a source repository (if you've added a deb-src for every deb in your sources.list), this makes it look like -all source repositories are somehow different- and probably disabled 'cause they're grey!  This is an extraordinarily poor choice of UI conventions; if someone could point me to the best way to bug-report this to the Synaptic developers, I'd appreciate it.

Thanks.

---

### Post by cwaldbieser on 2005-09-25
[QUOTE=Blueshell]In Hoary, current Synaptic (0.56):

I can't for the life of me figure out how to fetch a source package using Synaptic.  I've got several deb-src lines uncommented in /etc/apt/sources.list, and Synaptic shows them to me (but see PS).  But I can't find -anywhere- in the UI a way to actually fetch one!  All I see is ways to get binary packages.  The so-called documentation is no help (and apparently has screenshots from a previous version, e.g., the Repositories screenshot doesn't match the screen you get if you're actually there), and lots of searching has failed to turn up this information.  (Typically, people start talking about Synaptic but then jump into using apt from the command line instead.  And the Ubuntu 5.04 Starter Guide, while mentioning uncommenting deb-src lines, doesn't say anything at all about -using- them.)

Do I really need to use apt-get from a command line to fetch sources?  If so, why is this handwaved away in all of the Synaptic documentation?  A clear declaration that Synaptic cannot handle source distributions would save a lot of time---or a clear example of using one.

P.S.  It's incredibly misleading that Synaptic apparently tries to emulate a piece of fanfold paper in its listing of repositories in the Repositories dialog---every other repository is grey.  However, since every other repository is a source repository (if you've added a deb-src for every deb in your sources.list), this makes it look like -all source repositories are somehow different- and probably disabled 'cause they're grey!  This is an extraordinarily poor choice of UI conventions; if someone could point me to the best way to bug-report this to the Synaptic developers, I'd appreciate it.

Thanks.[/QUOTE]

I don't see any way to get sources from synaptic-- I guess I would probably use apt-get.  I am not sure where this is "handwaved away" in the Synaptic docs.  I couldn't find any claim in mine that you *could* actually download sources.  

I pulled this URL out of the man pages: [http://savannah.nongnu.org/projects/synaptic](http://savannah.nongnu.org/projects/synaptic) 
It is supposed to be the project page, so contact info for the developers should be there.  It does seem like it should have been easy enough to add an option to the GUI to let you download sources, though I have not really looked very closely to see what would be involved.

I don't seem to be getting the "greyed out" effect you observed, though.  When my xxx-src lines are checked, they show up the same way as all the other checked lines.  Only the unchecked lines seem greyed out.

Finally, a lot of people who don't like synaptic as an apt-front end often mention "aptitude" or "kpackage".  I have never used either of these, but they might be worth looking into if you are interested in an alternative fron end.

---

