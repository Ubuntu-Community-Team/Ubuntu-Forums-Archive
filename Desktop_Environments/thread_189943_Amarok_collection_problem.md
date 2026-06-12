---
title: "Amarok collection problem"
date: 2006-06-05
forum: Desktop Environments
---

### Post by ohzopants on 2006-06-05
Today I upgraded to Dapper (a totally clean install, my laptop is now totally windows free).  I finally got amarok to play mp3s properly after manually updating to 1.4.0,  however when it scans my music directory it scans and gets to 100% but then reports 0 tracks.  The same music in the same directory goes into rythmbox's library just fine though.
Rythmbox is actually my preferred player, but amarok allows me to search and stream my music amazingly via obsidianmusic ([http://sourceforge.net/projects/amarokwebfront/)](http://sourceforge.net/projects/amarokwebfront/)), or at least it used to in Breezy.

Anyone having a similar problem and have a solution??
I'm using gnome btw. none of that fancy compiz or xgl...

I'm trying to use mysql as a database, which seems to be installed and working... sqlite works, but I need to use mysql

---

### Post by titus1950 on 2006-06-05
[QUOTE=ohzopants]Today I upgraded to Dapper (a totally clean install, my laptop is now totally windows free).  I finally got amarok to play mp3s properly after manually updating to 1.4.0,  however when it scans my music directory it scans and gets to 100% but then reports 0 tracks.  The same music in the same directory goes into rythmbox's library just fine though.
Rythmbox is actually my preferred player, but amarok allows me to search and stream my music amazingly via obsidianmusic ([http://sourceforge.net/projects/amarokwebfront/)](http://sourceforge.net/projects/amarokwebfront/)), or at least it used to in Breezy.

Anyone having a similar problem and have a solution??
I'm using gnome btw. none of that fancy compiz or xgl...[/QUOTE]


Read this could be helpfull

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

---

### Post by ohzopants on 2006-06-05
I fixed it... turns out I had a permission problem in mysql.

---

