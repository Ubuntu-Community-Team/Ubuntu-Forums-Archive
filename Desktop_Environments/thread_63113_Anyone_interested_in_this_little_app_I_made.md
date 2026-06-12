---
title: "Anyone interested in this little app I made?"
date: 2005-09-07
forum: Desktop Environments
---

### Post by Mishura on 2005-09-07
Out of bordom and curiosity, as well as a interest in Kommander, I threw together a very simple Kommander script that acts as a "Alien" and "Dpkg" frontend. 

The program is called "AlienTools" until I can come up with a better name, and all it really does is, using a dialog interface it allows the user to select RPM files and convert them to DEB packages.  You get the option to install it or just save it to a directory.  Also, there is a section of the app that allows you to install local Debian packages by selecting the deb and clicking Install.

Pretty much, just made to scratch an itch and to experiment.  I don't want to host it on KDE-apps.org yet, and I'm not quite sure how the program would work on other systems.

Here is a screenshot so you can get an idea what I mean.

[[IMG]http://img149.imageshack.us/img149/2791/alientoolsscreenshot2mj.th.png[/IMG]](http://img149.imageshack.us/my.php?image=alientoolsscreenshot2mj.png)

If there is some interest, I'll freely release it on a public site like KDE-apps, but I don't really expect to do much more for it, except to fix a bug or two if its serious enough.

BTW:  The sidebar graphic was my first foray with Inkscape (The alien guy).  It took me roughly an hour to finish it (The whole program, not the graphic!)  Kommander is quite an impressive tool.

---

### Post by masteryoda on 2005-09-07
Sounds good.... will be gr8... especially for newbies like me :D

---

### Post by daller on 2005-09-07
Anywhere we can download the source, to test the app?

---

### Post by rwabel on 2005-09-07
[QUOTE=daller]Anywhere we can download the source, to test the app?[/QUOTE]
 I'm also interested in testing it

---

### Post by phreak9 on 2005-09-19
I would also like to test it, mostly since I'm dealing with trying to convert rpm files right now... and I'm a super-noob to linux. Would be a helpful tool IMO. \\:D/

---

### Post by tasulo on 2005-09-19
I too would like to test it, wonderful idea!

---

### Post by Freddy on 2005-09-19
Great idea dude, I like your idea alot.  /// Freddan

---

### Post by kianziack on 2005-09-20
hmm sounds good.. so where can i get that thing so that i can try it to...

---

### Post by mulletman13 on 2005-09-20
This would be wonderful :)

Im really surprised nobody has done it already, it's such a good idea.

Please share! :)

---

### Post by rwabel on 2005-09-20
[QUOTE=mulletman13]This would be wonderful :)

Im really surprised nobody has done it already, it's such a good idea.

Please share! :)[/QUOTE]
 I've tested some months ago several deb intsaller gui's. have a look at my blog entry: [http://ralph.n3rds.net/index.php?/archives/30-GUI-installer-for-debian-packages.html](http://ralph.n3rds.net/index.php?/archives/30-GUI-installer-for-debian-packages.html)

---

### Post by winxp2kubuntu on 2005-09-20
Sounds like a terrific idea, specialy for people like me who are not very familiar with the command line. I am lost when it comes to the freaky tar, bz2 .deb, rpm  files etc... At this point, installing anything in Linux is a chore. I have to say, the only thing I miss about Windows so far is the straight forward .exe installs, fully automated, perfect for people in a rush. I will play around with the command line at some point out of curiosity but in the mean time, I would like to be able to perform basic tasks without headaches. Alien Tools sounds like something that should be built in to the next update. A graphic interface is the way to go. By all means, fire away. How can we test it?

---

### Post by f1dave on 2005-09-21
If you want to stay away from the command line, testing apps probably isn't the way to go :P If something goes wrong you might have to dive into the console and fix it with dpkg, apt or whatever... But for sure I recognise there's a need for more apps like this, even if everyone /should/ eventually learn *nix commands- after all, it is linux. We can seperate our graphical interface from our OS :D

---

### Post by treris on 2005-09-21
I think this is a great idea, altough I've become accustomed enough to linux to work with the command line, I still like the idea of just having the click a few buttons and get an installation going, That's also why I love synaptic, i think the combination of synaptic and repo's is for instance even better and simpler than the windows .exe installation process

I'd sure like to give this program a try when i get a chance to

---

### Post by jbinc1 on 2005-09-21
Sounds interesting. Will you be making this app available???

---

### Post by Mishura on 2005-09-22
Lets see, right now it *appears* to work.  If I tell it to alien-ize a RPM and install it, it does.. but I have no way of proving that it works.  Some kind of output at least saying "yea!" or "nay!" would suffice.

I'm not too happy with the interface right now, but if you got gimp skillz,  or just plain better ideas lemme know.

Sorry for the wait, been busy.  Here's the tarball:  [http://mystra.homelinux.net/~mishura/downloads/alientools.tar.gz](http://mystra.homelinux.net/~mishura/downloads/alientools.tar.gz)

Consider it GPL and Alpha quality.  ;)

---

### Post by rwabel on 2005-09-22
I can't download the file, server is down
[QUOTE=Mishura]Lets see, right now it *appears* to work.  If I tell it to alien-ize a RPM and install it, it does.. but I have no way of proving that it works.  Some kind of output at least saying "yea!" or "nay!" would suffice.

I'm not too happy with the interface right now, but if you got gimp skillz,  or just plain better ideas lemme know.

Sorry for the wait, been busy.  Here's the tarball:  [http://mystra.homelinux.net/~mishura/downloads/alientools.tar.gz](http://mystra.homelinux.net/~mishura/downloads/alientools.tar.gz)

Consider it GPL and Alpha quality.  ;)[/QUOTE]

---

### Post by Mishura on 2005-09-22
Strange, since the server is MY computer  :-?

OK.  Ignore that link and lets try this attached file.  You probably caught me in the middle of my KDE upgrade, yet I didn't reboot...  oh well.

---

### Post by rwabel on 2005-09-22
[QUOTE=Mishura]Strange, since the server is MY computer  :-?

OK.  Ignore that link and lets try this attached file.  You probably caught me in the middle of my KDE upgrade, yet I didn't reboot...  oh well.[/QUOTE]
 ok, I did untar it and now I've a kmdir file. What shoudl I do with it? How does it?

btw your server is still not reachable :-)

---

### Post by Mishura on 2005-09-23
To use a kommander script, just do:

```
$ kmdr-executor /path/to/kmdr_script.kmdr
```

I ask that you be real careful when playing with it, since the only way the program is useful, is to run it as root.

As far as commandline vs. GUI:  I am quite familiar with the command line, and thanks to my DOS upbringing, the Linux console was nothing too intimidating.

However, I can't really expect everyone to be able to use it with ease.  I'm a technical thinker so its easy for me, but others *need* GUIs because they are more right-brained (or is that left?  Can't remember.) and think more *graphically* than the rest of us.

In the future, there would have to be away to deal with alien packages.  Repositories is a good idea, but I can't expect Ubuntu to package *everything* under the sun.  Not to mention, several commercial apps are packaged as RPMs, which make their use under Debian-based distros a pain.

Not to mention, that there should be some kind of GUI for every "most used" command line programs.  I'm always dropping down to a console to deal with stuff.  Like I said, this doesn't bother me, but it does bother others.  Of course, Windows isn't perfect in this either, since I often open up good ol' Command prompt to do crap there, but I blame that on my Linux experience ;)

So, my motivation to do this was merely to experiment a bit, and see if there is any better ideas on how to do it.  Not to mention that I've been looking for excuses to play with Kommander. 

Personally, the best way to do this, is right-click context menus inside Konqueror.  Nautilus, I hear has it as a plugin or something.  If I could right click on a RPM and convert/install it... or right click on a .deb and install it, that would be a million times better than this little kommander hack.  If anyone can point me at a nice beginners tutorial on Konqueror script hacking, I'll look into it myself;  barring that I don't require to know C++.

> btw your server is still not reachable :)

Strange, since I can access it using the outside DynDNS address..  I will look into it later.  Could be anything.

PS:  Sorry for the long post, but I'd figure I'd respond to several people at once and clear up my intentions a bit.

---

### Post by Paulus on 2005-09-23
this is great, but long overdue if you ask me.   Why isn't this part of kde/gnome, it's so simple (or so it seems).

---

### Post by munch3 on 2008-03-25
i wanna try,  I wanna try!!!

---

