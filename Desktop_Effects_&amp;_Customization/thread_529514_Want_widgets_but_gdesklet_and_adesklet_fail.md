---
title: "Want widgets but gdesklet and adesklet fail"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by imnotryan on 2007-08-19
Wanting desklets...

when I install gdesklets, and attempt to run it, a window titled gdesklets appears, but without definition, within a moment it goes dark (unresponsive) and if left alone will simply close itself.  The post below shows my exact problem but the problem was never solved.

> [http://ubuntuforums.org/showthread.php?t=522068&highlight=desklets](http://ubuntuforums.org/showthread.php?t=522068&highlight=desklets)

So I immediately turned to adesklets. It installs, and than using the GUI mode to pick desklets to load - it has an error when loading any of them, and does not.

So than I read that if you are using Beryl, as I am, you have to try this method : 

> [http://www.aldolat.it/?p=214](http://www.aldolat.it/?p=214)

Seems simple enough, the first command downloads the file it needs and than sits idle without the command prompt, if left for 30 minutes it still goes nowhere.  So if I then hit enter, it will say 
> [1]+  Done                    wget [http://forum.beryl-project.org/download.php?id=830](http://forum.beryl-project.org/download.php?id=830)

Trying to move along and inputing the next command returns this.
> ryan@ryan-desktop:~$ tar xzf screenlets0.0.7-6pre0.0.8.tar.gz
tar: screenlets0.0.7-6pre0.0.8.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Thus ending my third adventure into desklets.

Anything else I can try?  I just want weather and a clock for crying out loud.

---

### Post by hyperair on 2007-08-19
I'm all for screenlets. Take a look at the instructions here: [http://hendrik.kaju.pri.ee/screenlets/](http://hendrik.kaju.pri.ee/screenlets/)

---

### Post by imnotryan on 2007-08-19
Any way to get screenlets to work as widgets with beryl... Right now they run on top like regular applications, i want it more like OSX.  Is there a screenlets manager or something that has options?  Is there a weather and radar screenlet?

I'm a bit of a beginner and have trouble installing packages manually, so if there is something I could just copy/paste into the console that would be great.

---

### Post by hyperair on 2007-08-19
If you mean the Widgets Layer, then add "screenletsd.py" under forced applications.

---

### Post by imnotryan on 2007-08-19
What are "forced applications?

I just did a search for "forced applications" and according to the results, this is the first and only thread which has ever mentioned that term.

---

### Post by hyperair on 2007-08-20
Applications forced to be deemed "widgets" by the Widget Layer.

---

