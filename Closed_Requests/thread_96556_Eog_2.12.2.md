---
title: "Eog 2.12.2"
date: 2005-11-29
forum: Closed Requests
---

### Post by elleuca on 2005-11-29
There are a lot of interesting fixes

- Update window title when saving in another location.
  Fixes bug #318318. (Lucas Rocha)
- Asks to overwrite target file instead of source when 'Saving
  as'. Fixes bug #162627. (Lucas Rocha, Gustavo Noronha)
- Don't crash when removing images from a collection.
  Fixes bug #313003. (Lucas Rocha)
- Add image/svg+xml to the list of supported file types.
  Closes bug #314566. (Lucas Rocha)
- Fix RGBA->RGB conversion when saving PNG images to JPEG.
  Fixes bug #314742. (Felix Riemann)
- Update "recent files" when viewing images. Fixes bug #316004.
  (Lucas Rocha)
- Fix crash when trying to view an image from recent list that
  doesn't exist anymore. Fixes bug #312448. (Lucas Rocha, Claudio
  Saavedra)
- Change X development libraries checking in build system
  to work on every platform. Fixes bug #317828. (Christophe Belle)
- Fix crash when adding new non-image files to a directory eog
  watches and when trying to view a PNG image with a JPEG extension.
  Fixes bugs #316808 and #311925. (Callum McKenzie)
- Fix width of the information pane that was too small.
  Fixes bug #313674. (Ed Catmur)
- Make scrollbar buttons work in thumbnails pane. Fixes
  bug #124653. (Juan Carlos Inostroza)
- Make it possible to use '=' or '+' for zooming in. Fixes
  bug #320367. (Lucas Rocha)
- Translation Updates: Funda Wang (zh_CN), Priit Laes (et),
  Elnaz Sarbar/Meelad Zakaria (fa)

---

### Post by duffman25 on 2005-11-29
dapper has eog 2.13.2
[http://packages.ubuntu.com/dapper/gnome/eog](http://packages.ubuntu.com/dapper/gnome/eog)

So AFAIK only 2.13.2 could be backported, not 2.12.2 since dapper uses gnome 2.13. I've already asked for a backport for it, since it's new UI seems to be much more useful that the current one, but it hasn't hit the backport archive yet.

---

### Post by jdong on 2005-11-29
This backport was approved about two weeks ago, but due to my retardedness it got neglected in the build process... Sorry.

I filed a build request this morning for it, so it should start appearing on mirrors in a day or so.

---

### Post by duffman25 on 2005-11-29
[QUOTE=jdong]This backport was approved about two weeks ago, but due to my retardedness it got neglected in the build process... Sorry.

I filed a build request this morning for it, so it should start appearing on mirrors in a day or so.[/QUOTE]

you're refering to eog 2.13.2 aren't you?

---

### Post by jdong on 2005-11-29
yes, sorry, I did.... 2.13.2 is pretty nice, and remained stable throughout all my tests.

EDIT: MINOR UPDATE: It went through the build engine pretty recently...

---

### Post by duffman25 on 2005-11-29
[QUOTE=jdong]yes, sorry, I did.... 2.13.2 is pretty nice, and remained stable throughout all my tests.

EDIT: MINOR UPDATE: It went through the build engine pretty recently...[/QUOTE]

Thanxs jdong. Your efforts are very appreciated, ego 2.13.2 rocks!

---

### Post by jluscher on 2005-12-04
Hello,

I'm new to Ubuntu, just installed it on my laptop to replace a copy of Mandrake-64 which didn't work worth a darn :(     So far Ubuntu has been WONDERFULL !!

I have come across a bug with Eog, 2.12.1 is what is installed in Urbuntu 5.10 it seems.   Since you are apparently current of Eog bugs perhaps you can tell me how to report one, or check if it has already been reported?

I'm an old time computer user but a firmware developer rather than desktop designer, so it is a bit new for me to relate at this level to the community :???: 

The bug is a crash of Eog when it 'opens' a file which has an innapropriate extension - ".jpg" in this case - whereas the file seems to 'really' be a ".gif" image.   If Eog is started and then the file opened is works just fine, but if the file is "clicked on" to open it, Eog flubs it and crashes!

Thanks for your help.
James Luscher

---

### Post by duffman25 on 2005-12-04
[QUOTE=jluscher]Hello,

I'm new to Ubuntu, just installed it on my laptop to replace a copy of Mandrake-64 which didn't work worth a darn :(     So far Ubuntu has been WONDERFULL !!

I have come across a bug with Eog, 2.12.1 is what is installed in Urbuntu 5.10 it seems.   Since you are apparently current of Eog bugs perhaps you can tell me how to report one, or check if it has already been reported?

I'm an old time computer user but a firmware developer rather than desktop designer, so it is a bit new for me to relate at this level to the community :???: 

The bug is a crash of Eog when it 'opens' a file which has an innapropriate extension - ".jpg" in this case - whereas the file seems to 'really' be a ".gif" image.   If Eog is started and then the file opened is works just fine, but if the file is "clicked on" to open it, Eog flubs it and crashes!

Thanks for your help.
James Luscher[/QUOTE]

ok, first of all, this is not the appropiate forum for this, but anyway if you want to report a bug for ubuntu go here: 
[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)
you will need to login (or create an account for it) & there you can use the built in search. If you can't find anything similar, then create a new bug.

for more info please read this:
[https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs)

---

