---
title: "webkitkde"
date: 2007-12-27
forum: Desktop Environments
---

### Post by mojorising on 2007-12-27
Hi! 

Has anyone here successfully used the webkitkde plug-in for Konqueror?

I am running Gutsy and noticed the webkitkde package in the repositories. It is a plug-in for Konqueror that allows you to use the Webkit rendering engine instead of the default KHTML engine. 

Anxious to try it out, I installed the package, which subsequently installed lots of other KDE4 packages (maybe all of them?) but I still don't see it in my list of Konqueror plugins and I don't see any way to fire up the KDE4 desktop (if the whole thing is installed) to try it from there. 

Does anyone have any pointers/ information on this?

Thank you!
Mike

---

### Post by papabean on 2007-12-27
I saw the same thing in the repo and have installed webkitkde also.  It is seemingly a component for use with Konqueror in KDE4, however there are no clear instructions on its use.

The README in /usr/share/doc/webkitkde suggests building WebKit from the instructions at [http://webkit.org](http://webkit.org) as the first step.  That's where I get stuck.  I don't have a Mac and I see no reason to build it on a Windows machine.  At this time, however, I have been unable to use the build-webkit script include with the latest nightly build.

I have not yet been able to find clear instructions on how to build webkit or get this component working.  Just wanted to let you know there is at least one other person looking to make it work.

---

### Post by papabean on 2007-12-27
Ok.  I can't try this until I get home, but step 1 calls for building from the source.  When I grabbed the latest nightly, I mistakenly assumed that meant the latest nightly source.  That's incorrect.  I download pre-compiled nightly binaries explaining why I couldn't build the webkit kpart.

I've just grabbed a recent SVN snapshot and will try to build it all when I get home.  If I'm successful, I'll post the results here.  If I'm not successful, I'll let you know what I tried and what didn't work.

---

### Post by papabean on 2007-12-28
Well, that proved fruitless as well.  In attempting to locate clear instructions on how to compile the webkit kpart, I have instead learned more about the politics of open source software than I had ever hoped possible.

At this point, I'm resigned to believe that since clear instructions aren't obvious, perhaps I'm not the target audience for this project.  I am not a developer.  I'm a longtime linux user, former Mac junkie and recent KDE convert.  I would love to see a WebKit-based web browser for KDE.

In the meantime, I'll let the Kubuntu team do their thing.  I'm confident there will be a package release when it's ready for everyone.

Perhaps, the link to the [build instructions on the webkit.org site]("http://trac.webkit.org/projects/webkit/wiki/BuildingQtOnLinux") should be included in the README with the webkitkde package.

---

### Post by mojorising on 2007-12-31
Ah bummer. I'm in a similar situation as you. I want to play with webkit andI could probably figure this out and build it from source without much of a problem but I don't want webkit *that* badly. :) That's why I was psyched to see the package. 

I did find and mostly go though this tutorial on one of my home PCs a while back. [http://mondaybynoon.com/2007/04/23/installing-and-running-webkit-in-linux-using-qt/](http://mondaybynoon.com/2007/04/23/installing-and-running-webkit-in-linux-using-qt/) It didn't work out for me but I didn't try very hard either. There are a lot of instructions similar to these for anyone willing to build webkit from source and use a very simple KDE browser for it. If you really want to have webkit on KDE, this might be a good thing to try but I'm betting (like me and most people) just using whatever you're using now as a primary browser until a proper plug-in is distributed for ubuntu might be best thing.

Mike

---

### Post by papabean on 2008-01-02
Well, I DID get WebKit to build from source.  The instructions in the README were fairly vague, but I managed.   The demo browser that's built with the source works.  No idea on how to make it a Kpart for Konqueror, though.

Much like you, it's not critical that I run webkit, just thought it would be nice.  I'm content at this point to wait for a package that is either a complete WebKit browser for KDE or installs the Kpart properly.

---

### Post by albbas on 2008-03-04
I installed webkitkde too, and found at that I could switch between khtml and webkit by going to the View menu and choosing Viewing mode (or something like that, I use a localised version)

---

### Post by papabean on 2008-03-04
When did you install webkitkde?  There may have been an update since I last installed it.

Also, are you using Konqueror for KDE 3 or KDE 4?

---

### Post by mojorising on 2008-03-24
albbas, please let us know regarding papabean's questions. I am very curious about this as well. 

I'm going to check my KDE4 box when I get home to see if I can find this menu selection. It is a fairly current Hardy build so it should have the latest packages/ features.


Mike

---

### Post by kgeekworking on 2008-03-27
The ability to switch between KHTML & webkit is listed under View->View Mode (Kubuntu Hardy KDE4).  

One note is that it will not appear when viewing the default "about" startup page.  You need to go to an actual web page before this option is available.

---

### Post by mojorising on 2008-05-02
I never did find this in on my test box running KDE4. Likewise I have konqueror-kde4 on my work desktop now since I upgraded it to Hardy but the option isn't there either. 

I also noticed the webkitkde package doesn't seem to be in the repositories any longer. Does that mean it's gone now? Wondering if there are other sources to get it. 


Mike

---

### Post by onlineapps on 2008-05-19
Doesn't WebKit come by default in Konqi in KDE 4?

---

