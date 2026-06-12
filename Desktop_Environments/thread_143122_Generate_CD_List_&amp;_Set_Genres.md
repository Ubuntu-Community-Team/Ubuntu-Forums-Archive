---
title: "Generate CD List &amp; Set Genres"
date: 2006-03-11
forum: Desktop Environments
---

### Post by Mike-97470 on 2006-03-11
Now I'm "Dreaming of iTunes"--

1.  After ripping my CD's (w/ Sound Juicer) I'm trying to generate a list of the CD's in my library in Artist/Album form.  I use the (printed) list to make sure that all CDs have been ripped, to find CDs, and to keep organized.  As new CDs are added and ripped, I would like to be able to generate a new list.  This can easily be done with iTunes . . . .  i've tried all the music players in Ubuntu that I know about, but the best I've been able to do is, with all music in one folder, using Nautilus select "View as List", highlight all Artist folders, copy into OO Writer and replace the pathname with (nothing) to get an alphbetic list of Artists.  I can't figure how to get Nautilus to open the Artist folders to show the Alubms, automatically in the same list format.  It does open them, but in separate windows.  In the Terminal I don't think that "ls" will do it, but maybe someone knows how to use "find" to do it.  Anyways, I'd appreciate help.

2.  I'd like to populate the genre fields automatically from one of the db's. I know they will be sometimes incorrect or not what I want, but it's a lot easier to fix that, than by keyboarding the genres manually.  Sound Juicer and the music players don't seem to be able to do this.  I don't want to spend a lot of time making playlists.  E.g.:, I just want to shuffle in Rock.  And if I'm in the mode to listen to classical guitar, I don't wan't to listen to London Calling.  Genres are good.  Help appreciated with this, too.  Thnaks!

---

### Post by Wolki on 2006-03-11
[QUOTE=Mike-97470]In the Terminal I don't think that "ls" will do it, but maybe someone knows how to use "find" to do it.  Anyways, I'd appreciate help. [quote]

No guarantees that it will work, but it seems to here:

```
find -maxdepth 2 | egrep "/.*/" | sed "s/^\.\///" | sort -fd -t "/"
```

or, with Artist - Album instead of Artist/Album

```
find -maxdepth 2 | egrep "/.*/" | sed "s/^\.\///" | sort -fd -t "/" | sed "s/\//\ -\ /"
```

As for the genres, I cant really help you. Maybe it's possible with easytag? I sometimes feel it can even brew coffee, if you know how... Still, genre are quite subjective, and I feel in databases often really messy. Maybe hand-sort them (temporarily) into genre-based folders, then auto-apply the genre tag to all in that directory?
Last suggestion would be, use a automatic playlist generator that is able to do last.fm lookup for similar artists/songs instead of just relying on genres.

(edit) forgot to mention it, run the command in the folder the artist folders are in. And there are probably more elegant solutions, with find's amazing capabilites, but I'm too lazy/dumb/tired to fully grok it's manpage... ^^;;

---

### Post by Wolki on 2006-03-11
hit quote insted of edit... -_-

---

### Post by Mike-97470 on 2006-03-12
Awesome, Thanks Wolki!  You the edit guru!  It worked perfectly, then I just copied into OO Calc into 2 columns, added a 3rd for the CD# and printed.  Just what I wanted.

Separating the Artists into genre folders and then batch editing the genre field using one of the music players is a good idea, and I think I'll do it.  For starters all I need is rock/pop/classical/jazz/other so it won't take long.  

I'll try to figure out last.fm lookup tomorrow.

Thanks again!

---

