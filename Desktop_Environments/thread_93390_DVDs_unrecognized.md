---
title: "DVDs unrecognized"
date: 2005-11-21
forum: Desktop Environments
---

### Post by myke on 2005-11-21
Howdy ... I've got a successful new installation of Kubuntu (including a relatively easy installation of skype) except for one thing.  It recongizes my two dvd drives but all programs I try will not play any dvd I put in I've downloaded several programs and none will recognize a dvd.  Most just shut down immediately after putting in a dvd while kaffeine gives an error.  I'm lost.

Any suggestions.

---

### Post by GeneralZod on 2005-11-22
Have you installed libdvdcss2? This is the codec required to read encrypted (i.e. most commercial) DVDs, which Ubuntu cannot provide due to legal reasons.  If not, try that; if you do a search on the forums, you'll find plenty of guides to doing this :)

Edit:

Try here:

[http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs+easy](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs+easy)

and also check out the Automatix project, which aims to get your system set up with all sorts of other goodies with a few mouse-clicks:

[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

---

### Post by myke on 2005-11-22
Hey, thanks for that.  That really helped alot.  I downloaded the automatix  and thought I'd have trouble installing it but it had a really easy install script that made the installation as easy  as a win or mac installation.  Installation of packages not in the repositories are not easy for me.  Automatix did have alot of good packages toincluding those dvd codecs and it worked perfectly.   My dvds are working nicely and Totem is an excellent player.  Also was a great way to easily get skype put on my system (& several other things).


Though I initially installed Kubuntu, I have now switched over to the Gnome based Ubuntu.  I couldn't get used to the KDE environment and for some reason program menus and toolbars such as those on Firefox looked really bad.  They are much clearer and look better overall in gnome.  I don't know why, but the graphics overall look better from the get-go with gnome.

---

### Post by GeneralZod on 2005-11-23
Glad you got it all working! If you ever feel like giving Kubuntu another shot, try installing [gtk2-engines-gtk-qt](http://ubuntuforums.org/showthread.php?t=22232&highlight=gtk2-engines-gtk-qt) - it helps to make apps like firefox and Thunderbird (which are gtk based) fit into KDE a little better.

Good luck!

---

