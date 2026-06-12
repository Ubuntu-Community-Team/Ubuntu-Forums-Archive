---
title: "feature request (2)"
date: 2006-02-04
forum: Forum Feedback &amp; Help
---

### Post by towsonu2003 on 2006-02-04
I'm using dial up (as appearant from my signature...) and to search the forum and to post a new thread, I need to wait for the full page to load (takes from 5 to 25 seconds depending on how many other connections I have, and if apt-get is updating / upgrading, it takes 2-3 minutes for the full load of the page). That's due to heavy use of javascript in this forum's code I believe. 

I would like to request 2 features:
1. a search box on top of the main forum page (ubuntuforums.org) that works without having to wait for the full page to load,
2. "Post new thread" and a similar search box on top of every forum section (this would also be kinda nice for newcomers who don't know that "post new thread" is under "forum tools") 

hopefully these are possible w/out major tweak...
thanks.

---

### Post by imagine on 2006-02-04
[QUOTE=towsonu2003]I'm using dial up (as appearant from my signature...) and to search the forum and to post a new thread, I need to wait for the full page to load (takes from 5 to 25 seconds depending on how many other connections I have, and if apt-get is updating / upgrading, it takes 2-3 minutes for the full load of the page). That's due to heavy use of javascript in this forum's code I believe.[/QUOTE]
That's the joy of table based design. The administrators can't do much about it (except changing the forum software or rewriting vBulletin).

If you worry about Javascript: vBulletin runs fine without Javascript, you can turn it off. Have a look at [NoScript](http://www.noscript.net) if you're using Firefox.



You could also make an Ubuntuforums search plugin for your browser of choice (maybe there already is one), so you can enter the search string in the search field of your browser without waiting for a page to load.

---

### Post by towsonu2003 on 2006-02-04
[QUOTE=imagine]
You could also make an Ubuntuforums search plugin for your browser of choice [/QUOTE]
any help with that? this forum doesn't exactly use the .html?keywords format, so I have no clue how to write one...
I'm using firefox 1.5.0.1

---

### Post by towsonu2003 on 2006-02-04
never mind, found it here: [http://mycroft.mozdev.org/download.html?name=ubuntuforums&submitform=Search](http://mycroft.mozdev.org/download.html?name=ubuntuforums&submitform=Search)

but my requests are still here...

---

### Post by imagine on 2006-02-05
[QUOTE=towsonu2003]any help with that? this forum doesn't exactly use the .html?keywords format, so I have no clue how to write one...
I'm using firefox 1.5.0.1[/QUOTE]
The search form uses the POST-method by default, but it also works with the GET-method.

Have a look: [http://www.vbulletin.com/forum/showthread.php?t=107955](http://www.vbulletin.com/forum/showthread.php?t=107955)

---

