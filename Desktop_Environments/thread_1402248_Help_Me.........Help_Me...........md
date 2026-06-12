---
title: "Help Me.........Help Me.........."
date: 2010-02-08
forum: Desktop Environments
---

### Post by buntyrvm37 on 2010-02-08
How to find out whole history.....
tell me all possible all ways...........:p

---

### Post by mcoleman44 on 2010-02-08
Ok, you're going to have to give us a little more information than that. What history? Internet, Log files, what?

---

### Post by buntyrvm37 on 2010-02-08
Internet History............

---

### Post by mcoleman44 on 2010-02-08
What browser? Firefox, Opera, Google Chrome?

Im just going to assume that you're using firefox. Start firefox, and press ctrl+shft+h.

---

### Post by buntyrvm37 on 2010-02-08
If u see in XP all u opened sites will save in temp files........like that is there any folders or files which stores the history of internet???:confused:

---

### Post by falconindy on 2010-02-09
[http://en.wikipedia.org/wiki/History_of_the_Internet](http://en.wikipedia.org/wiki/History_of_the_Internet)

---

### Post by woodmaster on 2010-02-09
> **falconindy said:**
> [http://en.wikipedia.org/wiki/History_of_the_Internet](http://en.wikipedia.org/wiki/History_of_the_Internet)
ROTFLMFAO!!!!!!
 
Seriously, just open the histiry tab of the browser. It should all be there.

---

### Post by lovinglinux on 2010-02-09
> **buntyrvm37 said:**
> If u see in XP all u opened sites will save in temp files........like that is there any folders or files which stores the history of internet???:confused:

There is a terminology mix-up here. What you are referring too is the [cache](http://en.wikipedia.org/wiki/cache) - a folder where the browser stores all temporary downloaded files, like videos and photos displayed on web pages.

Firefox stores user stuff in a profile folder. This folder is located under /home/**[COLOR="Sienna"]you[/COLOR]**/.mozilla/firefox/ and probably has the word *default* on it, preceded by a bunch of random letters and numbers. You cannot see home/**[COLOR="Sienna"]you[/COLOR]**/.mozilla because it is a hidden folder (files and folders starting with a dot), so you have to hit CTRL+H to display it.

Once you open the profile folder, you will see a folder named Cache. That one is  where all temporary files are stored.

If you are looking for saving streaming videos, like those from YouTube, use [Video Download Helper](https://addons.mozilla.org/en-US/firefox/addon/3006). It's much simpler than going through the cache.

Internet History on the other hand is just a list of recent visited sites. It does not contain any files, just web site addresses. This can be accessed through you browser toolbar and menu. That information is also stored on your profile folder, but inside a database called *places.sqlite* (you need an sqlite manager to open it).

> **falconindy said:**
> [http://en.wikipedia.org/wiki/History_of_the_Internet](http://en.wikipedia.org/wiki/History_of_the_Internet)

:lolflag:

---

