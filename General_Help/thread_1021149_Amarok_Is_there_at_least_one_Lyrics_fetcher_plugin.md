---
title: "Amarok: Is there at least one Lyrics fetcher plugin that works ?"
date: 2008-12-25
forum: General Help
---

### Post by frenchn00b on 2008-12-25
Regarding the Amarok program, is there at least one Lyrics fetcher plugin that works ?

I tried 5 out of the lyrics plugins adds-on... no way, and the default lyrc is something completely random. Does it read the artist, album, title...?

[screenshot]("http://polishlinux.org/reviews/amarok2revision/kde4_811150_amarok_scripts.jpg")

---

### Post by balaknair on 2008-12-25
Hmmm
I've been using the Wikilyrics plugin for a long time now.
[http://www.kde-apps.org/content/show.php/Wiki-Lyrics?content=35151](http://www.kde-apps.org/content/show.php/Wiki-Lyrics?content=35151)

It works just fine for me, no problems at all.
In fact the lyrc plugin(default) used to work pretty OK too.

Are you sure you've got your music tagged right? Most plugins would just read the ID3 tags for the track to search for lyrics.

PS: if you're running Amarok2, some plugins for Amarok 1.4 might not work.
You might also need a few additional packages(ruby, perl etc depending on the plugin)
For eg: Wiki-Lyrics needs Ruby 1.8 and QtRuby, Ruby/GTK or Ruby/Tk, and the lyrc plugin needs Ruby 1.8
Make sure the dependencies are installed(Amarok> Tools> Script manager--> select plugin--> check the 'About' option to see the dependencies and see whether they are installed in synaptic)

---

### Post by cute helles on 2009-01-05
have a look in [http://ubuntuforums.org/archive/index.php/t-781024.htmlhttp://ubuntuforums.org/archive/index.php/t-781024.html](http://ubuntuforums.org/archive/index.php/t-781024.htmlhttp://ubuntuforums.org/archive/index.php/t-781024.html)

It at least advises how to get Wikilyrics running. The results of it a pretty impressive.

---

