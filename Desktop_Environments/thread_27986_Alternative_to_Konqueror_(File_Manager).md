---
title: "Alternative to Konqueror (File Manager)"
date: 2005-04-18
forum: Desktop Environments
---

### Post by griphiam on 2005-04-18
Is there a good KDE-based file manager as an alternative to Konqueror?  On my system, Konqueror is really buggy... crashing when I try to manipulate the view settings.  Are these known bugs?  I haven't had much luck looking through KDE's bugzilla.

(On a whole, I'm really impressed with KDE 3.4, but I just don't remember Konqueror being this bad with file management.

Thanks!

---

### Post by weeguy on 2005-04-18
[QUOTE=griphiam]Is there a good KDE-based file manager as an alternative to Konqueror?  On my system, Konqueror is really buggy... crashing when I try to manipulate the view settings.  Are these known bugs?  I haven't had much luck looking through KDE's bugzilla.

(On a whole, I'm really impressed with KDE 3.4, but I just don't remember Konqueror being this bad with file management.

Thanks![/QUOTE]
 It's probably Kubuntu causing all these crashes, rather than KDE. I just tried SUSE 9.3 and the KDE 3.4 implementation works perfectly.

---

### Post by fdoving on 2005-04-18
try krusader.

it's in universe.

- Frode

---

### Post by tristure on 2005-04-18
Krusader is indeed the best filemanager I've used in Linux so far.

It litteraly buries the concurrence if you use KDE. (In my opinion)

I just have one (big) regret : the krusader package actually available in ubuntu repositories is a 1.50 version ; this release has MANY very annoying bugs.

I'm eagerly waiting for a new package with version 1.60 which is way better.

---

### Post by fdoving on 2005-04-18
Would be great if you would suggest and upgrade on [http://www.ubuntulinux.org/wiki/KubuntuSuggestedPackages](http://www.ubuntulinux.org/wiki/KubuntuSuggestedPackages)

- Frode

---

### Post by rwabel on 2005-04-18
there are deb files on krusader's homepage.

And also check out tux commander, it's gnome style and works fine too. Unfortunately drag and drop isn't yet implemented, otherwise it's a great product.

The only two which really are good file manager à la Total Commander.

---

### Post by tristure on 2005-04-18
I submitted a new entry on the wiki page.

And I checked on the home page : there are deb files.
But I read here and there that ubuntu packages are different from the "classical" debs? Is it safe if I use them like this?
If it's safe, please let me know, you could save fdoving's time!!  :wink:

---

### Post by rwabel on 2005-04-18
[QUOTE=tristure]I submitted a new entry on the wiki page.

And I checked on the home page : there are deb files.
But I read here and there that ubuntu packages are different from the "classical" debs? Is it safe if I use them like this?
If it's safe, please let me know, you could save fdoving's time!!  :wink:[/QUOTE]

where did you submit it to the wiki?

they should work too, I've several deb's installed as for example also opera 8 beta and they work fine. I guess that it can be possible to get in trouble especially if you mix debian with ubuntu for the same program (I mean dependency packages). But don't take my words as 100% correct. Just my experience!
at least programs like tuxcmd, krusader, opera etc shouldn't be any problem. The thing that could happen is that you have dependency problems and the application won't get installed (happened to the newest krusader, but a beta version worked fine for me)

---

### Post by dlpfmVfH on 2005-04-19
[QUOTE=rwabel]where did you submit it to the wiki?

they should work too, I've several deb's installed as for example also opera 8 beta and they work fine. I guess that it can be possible to get in trouble especially if you mix debian with ubuntu for the same program (I mean dependency packages). But don't take my words as 100% correct. Just my experience!
at least programs like tuxcmd, krusader, opera etc shouldn't be any problem. The thing that could happen is that you have dependency problems and the application won't get installed (happened to the newest krusader, but a beta version worked fine for me)[/QUOTE]
 krusader rulez....deb files work from krusader website on kubuntu

---

### Post by tristure on 2005-04-19
Well, although I fully agree with you on krusader (which, indeed, rules), the latest .deb package on the site doesn't seem to work with kubuntu : when installing it complains about libfontconfig1, because the latest version available in ubuntu reps isn't up to date...

---

### Post by fdoving on 2005-04-19
[QUOTE=tristure]Well, although I fully agree with you on krusader (which, indeed, rules), the latest .deb package on the site doesn't seem to work with kubuntu : when installing it complains about libfontconfig1, because the latest version available in ubuntu reps isn't up to date...[/QUOTE]
 Take a look at my wiki page. [http://wiki.ubuntu.com/FrodeDoeving](http://wiki.ubuntu.com/FrodeDoeving)
I've made some unofficial krusader packages for hoary.

Please contact me if you experience problems with the packages in hoary.

- Frode

---

### Post by tristure on 2005-04-20
[QUOTE=fdoving]Take a look at my wiki page. [http://wiki.ubuntu.com/FrodeDoeving](http://wiki.ubuntu.com/FrodeDoeving)
I've made some unofficial krusader packages for hoary.

Please contact me if you experience problems with the packages in hoary.

- Frode[/QUOTE]
 This package works! Thanks a lot for your time.
This version is so much better than 1.50.
You should submit it to the official reps, I think the kubuntu community really needs this one.

There are a few other packages that I would like to see in kubuntu, but I think I could try and contribute myself. Do you have any link to some information about making packages? Is there a steep learning curve?

Thanks a lot!

---

### Post by Terracotta on 2005-04-20
Is there any way of using split view in konqueror too? I remember I made that work once, but it was an older konqueror :s and it was so looooooooong ago ;-).

---

### Post by fdoving on 2005-04-20
[QUOTE=tristure]This package works! Thanks a lot for your time.
This version is so much better than 1.50.
You chould submit it to the official reps, I think the kubuntu community really needs this one.

There are a few other packages that I would like to see in kubuntu, but I think I could try and contribute myself. Do you have any link to some information about making packages? Is there a steep learning curve?

Thanks a lot![/QUOTE]


There are good intros arround on the wiki pages. [http://wiki.ubuntu.com](http://wiki.ubuntu.com) browse/search arround.

In the first place, if you add your wishes to [http://wiki.ubuntu.com/KubuntuSuggestedPacakges](http://wiki.ubuntu.com/KubuntuSuggestedPacakges)
it's easier for people like myself to catch the request, and make a test-package.

If the test-package is good, I'll have it included in the UNIVERSE repository.

- Frode

---

### Post by rwabel on 2005-04-20
[QUOTE=fdoving]Take a look at my wiki page. [http://wiki.ubuntu.com/FrodeDoeving]("http://wiki.ubuntu.com/FrodeDoeving")
I've made some unofficial krusader packages for hoary.

Please contact me if you experience problems with the packages in hoary.

- Frode[/QUOTE]

thanks for your krusader packages, because the one from krusader did really not work due to that little dependency problem.

---

### Post by Jagasian on 2005-04-28
[QUOTE=Terracotta]Is there any way of using split view in konqueror too? I remember I made that work once, but it was an older konqueror :s and it was so looooooooong ago ;-).[/QUOTE]

Yes.  I am in Fedora right now, so I can't confirm that this is how it works, but there is an icon or something that can be clicked on the bottom of a Konqueror frame that causes the frame to split vertically or horizonatally.  It is great for doing what krusader does.  I especially like it when doing FTPing.

---

