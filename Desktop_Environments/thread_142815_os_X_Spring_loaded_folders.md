---
title: "os X Spring loaded folders"
date: 2006-03-11
forum: Desktop Environments
---

### Post by glug101 on 2006-03-11
Well, I didn't do a very thorough search, but I decided to ask here anyway:)

I used Linux for years, started using macs concurrently for awhile, and when I lost my x86 toy, just used mac for almost a year now.  Well, I have a project that I am working on that will involve a shiney new x86 box and that got me thinking about some of the nicer features of the mac OS.  

I've become quite accustomed to the spring loaded folders.  They're really intuitive for me now.  Just drag a file onto a folder, and *spring* the folder pops open.  No need to copy and paste, the whole thing happens visually.  Anyhow,  I was wondering if there is a similar function in Gnome or KDE.  If there isn't, then I would seriously like to send the suggested feature to gnome-devel, kde-devel, ubuntu-devel, or whomever might be able to add it.  Mac users would find it comforting, and I think it's a serious piece of polish on the OS.

Anybody have any comments?

---

### Post by stalefries on 2006-03-11
So, drag-and-drop an item to a folder, and the item gets added to the folder AND the folder opens? Neat. Doesn't sound too hard to implement. You may as well file a bug in Gnome's bugzilla. (bugzilla.gnome.org, if I'm not mistaken)

---

### Post by aarbear26 on 2006-03-11
I'm using ubuntu on one computer and SUSe 10 with KDE on the other.  The SUSE box does what you said after about a one second wait.  I think it's a pretty standard KDE feature.  I haven't seen similar in GNOME though.  Though gnome has the awesome feature of playing an mp3 if you just click it once and hold the mouse over the icon.  I like the graphics in gnome better too.

---

### Post by varunus on 2006-03-11
The issue with this is that apple has actually *patented* this feature.

I can't find the patent on it right now; there was a discussion about ways to get around the patent a few years ago in nautilus, but I think eventually GNOME decided to play it safe.  KDE implemented it anyway, due to their EU base and the lack of software patents there (for now). :)

---

### Post by engla on 2006-03-11
[QUOTE=stalefries]So, drag-and-drop an item to a folder, and the item gets added to the folder AND the folder opens? Neat. Doesn't sound too hard to implement. You may as well file a bug in Gnome's bugzilla. (bugzilla.gnome.org, if I'm not mistaken)[/QUOTE]
Yes, it's neat, but it's even better:
The file isn't moved until you release it, so you can continue to dig deeper by dragging the file to a subfolder etc...

Also, there usually is a delay before the folder springs open, but you can hit space to make it instant.

---

### Post by glug101 on 2006-03-11
Thanx for the tip Engla!  What I don't know about OS X could really fill volumes.  Too bad it's insanely proprietary, and so doesn't have a real long term chance on my primary machine:(  

I'm glad to hear that there are still no software patents in Europe. (perhaps one day the US will catch up ;) )

Engla, are you really still using a B&W g3?  I'm typing this on a g3-350.  Slow as a box of nails for many things, but surprisingly useable with the latest OSX (never tried linux on it, though I suspect I'd see a speed improvement ;) )  It's my main box till I can get enough money together to start my crackpot business selling x86 linux boxes.  Standard or custom build, ltsp server or standalone desktop.  (yeah, and I'll hold my nose and install windows for an extra $)

Perhaps I will be going with Kubuntu after what I heard here.  Thanx everybody for the interesting read! :D

---

### Post by m666 on 2006-03-15
Hi! As an user of both mac osx (ibook g3 600) and ubuntu linux (pc intel p3 600)
I 've been looking for linux file manager which could handle ''spring open'' feature.
rox-filer seems to be good at it, but I would like to force nautilus to do the same.
anyone succesfully enabled this feature in nautilus?

---

### Post by banjobacon on 2006-03-15
If you use the list view in Nautilus, folders will expand when you drag a file over to it. 

It's not the same, but it's similar.

---

### Post by m666 on 2006-03-15
no, they will not :(

---

### Post by banjobacon on 2006-03-15
[QUOTE=m666]no, they will not :([/QUOTE]
In the View menu, select "View as list".

Then drag a file over to a folder in the list, **don't** release the mouse button, and the folder will expand after a second or two. 

The only way I could see this not working is if tree view is somehow disabled, but from what I can tell, tree view and list view are the same thing. I don't see an option for turning off the tree functionality in list view.

Maybe it's because I use Ubuntu spatial mode?

---

### Post by engla on 2006-03-15
Is it's gnome policy to really steer clear of all software patents? I mean there must be lots and lots that are already implemented. Anyway, we should come up with something better that's inspired by this but still different.

And then I have two unrelated ideas that were inspired by this
A drag shelf built into nautilus? It would be useful. (Right now I'm programming Dragbox, an application that can for example work as a drag shelf. Look for it at gnomefiles in the coming days)

Pop-up windows? An old idea from OS9.. basically you make a window a pop-up window, and then it's sitting along the screen rim displayed like a tab. You click on the tab or drag to it, and it pops out... Really useful for launchers that you drag to or perhaps almost like a shelf (see above).


[QUOTE=glug101]Thanx for the tip Engla!  What I don't know about OS X could really fill volumes.  Too bad it's insanely proprietary, and so doesn't have a real long term chance on my primary machine:(  

I'm glad to hear that there are still no software patents in Europe. (perhaps one day the US will catch up ;) )

Engla, are you really still using a B&W g3?  I'm typing this on a g3-350.  Slow as a box of nails for many things, but surprisingly useable with the latest OSX (never tried linux on it, though I suspect I'd see a speed improvement ;) )  It's my main box till I can get enough money together to start my crackpot business selling x86 linux boxes.  Standard or custom build, ltsp server or standalone desktop.  (yeah, and I'll hold my nose and install windows for an extra $)

Perhaps I will be going with Kubuntu after what I heard here.  Thanx everybody for the interesting read! :D[/QUOTE]
I'm not using my B&W G3 much at all.. I have dapper to test with on it, as it's just a toy machine (and I run  "stable"* breezy on my ibook). I'm not totally sure gnome/dapper is really speedier than OSX on that box though.. if I'd use a different desktop env it would certainly be though.

*stable, one can wonder. In breezy, I've replaced the kernel, compiled Xorg from cvs and installed initng. All of it runs really really well.

---

