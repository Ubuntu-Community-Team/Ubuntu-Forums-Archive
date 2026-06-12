---
title: "Text games or interactive fiction"
date: 2005-08-13
forum: Gaming &amp; Leisure
---

### Post by dbeckham32 on 2005-08-13
Yes, I have ET and Doom 3 installed but I'd really like to know where I can get a few old text-based games such as Zork 2?

I Googled "interactive fiction" and there's some info out there, but I'd like to hear from anyone who's managed to get these types of games running on Ubuntu.

Thanks!

---

### Post by aveline on 2005-08-14
[QUOTE=dbeckham32]Yes, I have ET and Doom 3 installed but I'd really like to know where I can get a few old text-based games such as Zork 2?

I Googled "interactive fiction" and there's some info out there, but I'd like to hear from anyone who's managed to get these types of games running on Ubuntu.

Thanks![/QUOTE]
 try infocoms website

aveline

---

### Post by DirtDawg on 2005-08-14
The [Interactive Fiction Archive](http://www.ifarchive.org/) has hundreds of games written by amature authors. 
The two most popular authoring systems are [TADS](http://www.tads.org/) and [Inform](http://www.inform-fiction.org/). Many games are available for each system and both the interpreters and authoring packages are available in the Ubuntu Repositories. 
And of course **Zork rawks**! Infocom released all the Zork games to public domain a few years ago and they're all [available for download](http://www.infocom-if.org/downloads/downloads.html).
Word.

---

### Post by SuperMike on 2005-08-14
[QUOTE=aveline]try infocoms website

aveline[/QUOTE]
 I believe eMacs editor comes with a plugin for playing interactive fiction. Then again, eMacs also comes with a can opener, tire tester, cell phone, thetan crusher, you name it. (Just kidding, but I have seen something like Eliza and Advent running inside it before on RH9.)

Actually, what you need is to turn on Universe setting in /etc/apt/sources.list, do an "apt-get update", then "apt-get install frotz". Once there, then google on infocom games and you can download special infocom files that end in extensions like .z3, .z4, .z5, etc. These are interpreted by frotz. Once done downloading and installing, be sure to turn off universe downloads and do apt-get update because that's the way Ubuntu intended for you in order to be safe for updates.

---

### Post by potrick on 2007-06-20
This looks really good:

[http://www.logicalshift.demon.co.uk/unix/zoom/](http://www.logicalshift.demon.co.uk/unix/zoom/)

If someone could compile that and make a package, I think we'd all be a lot happier with the state of IF on Ubuntu. I'd do it myself, but I'm on dialup and it's kind of impossible to install build-essential.

---

### Post by DoktorSeven on 2007-06-20
I'm trying Zoom, but I get a blank screen when trying to play a game (my test game is Zork 1).  Looks like either the colors are wrong or the fonts are, but the config file seems to be correct...

edit: if anyone wants to try, [here's the quick and dirty **checkinstall** .deb](http://doktorseven.miskie.net/files/zoom_1.1.0-1_i386.deb); USE AT YOUR OWN RISK.

Have to copy /usr/local/share/zoom/zoomrc to ~/.zoomrc and edit it to tell it where your IF files are, and any *.DAT IF files have to be renamed to something like filename.z3.

---

### Post by potrick on 2007-06-20
Installed the deb, couldn't get it to work either. Disappointing, because this program looks pretty fantastic. I wonder how much work a GTK version would be?

---

### Post by Golyadkin on 2007-06-20
In my opinion the best textgame in history is called 'nethack".
It is in the repositories.
> 
sudo apt-get install nethack


---

### Post by potrick on 2007-06-20
Nethack's a totally different ballgame than interactive fiction. These games have more to do with literature than a standard game. Anyway, I found another program that might satisfy our z-machine needs, but I fear it's too dated: 

[http://users.pandora.be/peter.bienstman/kwest/](http://users.pandora.be/peter.bienstman/kwest/)

  Anyone think they can work some magic?

---

### Post by Cappy on 2007-06-20
You should try the Enchanter trilogy!
[http://en.wikipedia.org/wiki/Enchanter_(computer_game](http://en.wikipedia.org/wiki/Enchanter_(computer_game))
It definitely plays differently than Zork.

---

### Post by DoktorSeven on 2007-06-20
Kwest seems to do much better, though it depends on KDE and Qt, so unless you're using Kubuntu, you'll need to get the basic KDE libraries and such.

[Another quick & dirty checkinstall DEB.](http://doktorseven.miskie.net/files/kwest_1.0-1_i386.deb)  Use at own risk, etc.

---

### Post by johnb820 on 2007-06-20
I'm glad to see someone else interested in Interactive Fiction.  There is an annual IF competition for amateur writers thats been held for over 10 years now.  You can find a list of works at the IF archives.

[http://ifarchive.smallwhitehouse.org/indexes/if-archiveXgames.html](http://ifarchive.smallwhitehouse.org/indexes/if-archiveXgames.html)

Also, a list of the needed interpreters.

[http://ifarchive.smallwhitehouse.org/indexes/if-archiveXprogramming.html](http://ifarchive.smallwhitehouse.org/indexes/if-archiveXprogramming.html)

---

### Post by potrick on 2007-06-21
Yeah, kind of new to that community but the contest is exciting. I've thrown something together using Gnome Inform 7, but it's more just for practice. Right now I'm just trying to figure out a more complete way to play these games in Ubuntu than just Frotz in the Terminal. Specifically, I'd like to play with nicer looking fonts than a terminal app can offer. I'll see how Kwest works out and let you guys know. 
  Anyway, I'd like to see more interplay between the Ubuntu community and the IF community.

---

### Post by matthewcraig on 2007-12-14
Use [FROTZ]("http://frotz.homeunix.org/frotz/") to play back these Interactive Fiction games.  It's part of the Ubuntu repository.  Interactive Fiction is wonderful for imaginative gamers on a budget.

---

