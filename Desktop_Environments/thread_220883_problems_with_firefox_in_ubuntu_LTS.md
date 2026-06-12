---
title: "problems with firefox in ubuntu LTS"
date: 2006-07-22
forum: Desktop Environments
---

### Post by wikiguy on 2006-07-22
hi guys,ive recently discovred that you can take out all the toolbar and tabs and make firefox look like the version for OSX i mean just icons the bar of the tabs and the dir space.

thanks for your help

---

### Post by SimonJW on 2006-07-22
I don't quite understand your problem. You are definately supposed to be able to remove the toolbars and tabs if you want to (you can get them back from View->Toolbars). I don't know what you mean by the "dir space" though, sorry.

Perhaps I didn't understand you properly, and if so sorry, but what is the problem with being able to remove these things if you want?

---

### Post by wikiguy on 2006-07-23
sorry i didnt explain myself properly..so here it goes again.....


actually is not a problem is more something that i want, firefox has by default 3 bars: the one that shows the tabs,the navigation bar(you type in there the address) and the one taht i want to remove taht is the bar that contains the menus like edit,view,file,tools and help,etc. ive seen that many people remove that bar.it looks nice if you combine it with small buttons.

thanks for all

---

### Post by SimonJW on 2006-07-23
To make such a drastic UI change to firefox, you need to create a userChrome.css file and add the line
```
#toolbar-menubar {display: none !important;}
```
to it.

There are good instructions here:
[http://www.mozilla.org/support/firefox/edit](http://www.mozilla.org/support/firefox/edit)
that describe how to create and edit this file.

This post:
[http://www.extensionsmirror.nl/index.php?showtopic=96#entry5350](http://www.extensionsmirror.nl/index.php?showtopic=96#entry5350)
is where I found the relevant line, and has many more UI tweaks you can make if you like. I believe that the line at this link before the line I quoted should have been commented out, so I didn't include it.

As I have never actually tried this, let us know if it works!

Simon

---

### Post by art on 2006-07-24
You could also install the extensions here:
[https://addons.mozilla.org/search.php?q=menux&app=firefox](https://addons.mozilla.org/search.php?q=menux&app=firefox)
That will let you toggle menubar ON or OFF

---

### Post by wikiguy on 2006-07-24
thanks to everybody i should give a try im going to pass by this thread again that tell what heppened.

---

