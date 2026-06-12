---
title: "Using (or replacing) Adept"
date: 2008-03-05
forum: Desktop Environments
---

### Post by svk on 2008-03-05
Hello,

I recently switched from Gnome to KDE.  I like it more for the look and feel, but there's one thing I miss: Gnome's package manager.  In KDE, the default package manager is Adept, but I'm a little disappointed with a couple features.  I'm hoping to get some advice on either how to address these features in Adept, or how to switch the package manager.

[LIST]
[*]Too many clicks: in Adept, I have to first click on the tray icon, then on "Fetch list of updates", then I have to wait for it to download the list of headers among other things.  It's a small issue of convenience, but I don't remember having to do this in Gnome -- it simply felt a lot cleaner and more efficient.
[*]No indication of download speed in Adept.  Sometimes, I'm on a slow connection (using my laptop in my bedroom is really stretching the capabilities of my router and wireless card), and I'm not sure if it stopped working, or if it's just downloading really slowly.  Besides, I'm always kind of curious about download speed, just for its own sake.
[*]Most importantly: in Gnome, I remember being able to see exactly *what* was updated for every upgradeable package.  Even if it's as trivial as a memory leak fix, I always want to know what the update is all about.  How would I know about potentially useful new features?  By happening to stumble upon them on my own?  I'm sure there's a way to find this info in Adept, but I could not (I did find the "Developer's changelog", but I think it lists all the changes ever made to the software since its birth, which is not what I want).
[/LIST]

For these reasons, I think I would prefer to switch the download manager.  Is there a way to do this in KDE?

Another question: I commonly install things using the command line (sudo apt-get install packagename).  Sometimes, I download very useful things, but completely forget about them in a month.  For example, I was recently looking up how to download youtube videos, and found a somewhat complicated guide that involved messing with long and ugly URL's.  Then it struck me that no more than a month earlier, I installed the youtube-dl package, which does exactly what I wanted.  For times like these, it would be very useful to be able to call up a list of all the packages that I installed by my own initiative, preferably in chronological order.  Something as simple as a text file with one package name per line would do.  The list of all downloaded programs in Adept or Synaptic is OK, but I would prefer it to 1) list only the packages that I chose to install myself, and not the list of all other dependencies that were installed as a result, and 2) list the packages in the chronological order in which they were installed, not in alphabetical order.  Is there a way to accomplish this?

Thank you in advance for the help!

---

### Post by suibhne on 2008-03-05
this doesn't really answer your question, but for downloading you tube videos, why don't you try the download helper add-on in firefox? - its excellent and you can access it through the Tools>add ons option in Firefox

---

### Post by nabl on 2008-03-05
To answer your first question, you can just install Synaptic through Adept or apt-get just like any other program. It will probably need some Gnome/GTK+ dependencies, though, so make sure you are willing to have those installed (if they are indeed necessary).

---

