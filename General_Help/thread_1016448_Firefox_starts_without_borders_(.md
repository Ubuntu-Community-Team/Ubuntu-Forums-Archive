---
title: "Firefox starts without borders :("
date: 2008-12-19
forum: General Help
---

### Post by ironslave on 2008-12-19
Ok, for some reason firefox starts up without a border and I have to press F11 (full screen) 2 times to make it return to a border.

has anyone else encountered this problem?

---

### Post by Rosewood_Arts on 2008-12-19
> **ironslave said:**
> Ok, for some reason firefox starts up without a border and I have to press F11 (full screen) 2 times to make it return to a border.

has anyone else encountered this problem?

Yes, same problem and workaround here...not sure, but it may have started after 3.0.5 update.  Window borders spontaneously disappear producing an (incomplete) fullscreen mode.  Have to keep resorting to double clicking F11...a nuisance.

---

### Post by Nevon on 2008-12-20
Same here. It's sooo annoying. However, I've only encountered the bug when using compiz as my window manager. Metacity works okay.

---

### Post by ironslave on 2008-12-21
I figured this probably has something to do with compiz

---

### Post by tisk on 2009-01-08
+1 have problem also :(

---

### Post by Monkeysailor on 2009-04-23
This is a indeed a compiz problem, you need to go into the "workarounds" section of the utility menu in compizconfig, and deselect the "Legacy Fullscreen Support" option. That should fix firefox :)

Andrew

---

### Post by braikar on 2009-05-01
I have the same problem I found a way to restart firefox without the fullscreen mode, but it involves killing the profile.. so all the bookmarks are lost etc until you reset to the previous profile??? SO the problem is somewhere in the firefox profile in: /home/USERNAME/.mozilla/firefox/PROFILEID/ ... but I haven't figured out which file yet. If you change IsRelative to '=0' in /home/USERNAME/.mozilla/firefox/profile.ini it will restart firefox with a new profile and the problem will be solved, so you can just export all your bookmarks and do that fix and reimport them

```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1  <-- change to 0
Path=9j60o17a.default

```

But I'm sure there is just a simple thing to change in some file in the profile to get that problem fixed.. I'll let you know if I find it.

It's not entirely a compiz problem!

---

### Post by braikar on 2009-05-01
Yoopie I found a workaround :)

As I said in the previous post, go in:
/home/USERNAME/.mozilla/firefox/profile.ini

```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1  <-- change to 0
Path=9j60o17a.default

```

Then restart firefox, it will create a new profile and change the path to something new.

Close firefox.

Then just delete every file in that new profile directory /home/USERNAME/.mozilla/firefox/PROFILEID/ except the file localstore.rdf.
Then just copy all the files from your previous profile into the folder without replacing localstore.rdf as it is the file that is creating that problem.

launch firefox and everything should be back to normal. :) At least it solved the problem on my ubuntu '8.10 amd64'

---

### Post by Oldhacker on 2009-05-10
I had the same problem - not a critical bug but annoying just the same. Following your instructions, IT WORKED!

Thanks for posting the solution.

---

### Post by inearlygaveup on 2009-05-11
There was also this easy fix at 
Seems to have helped some people 

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/276640/comments/7](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/276640/comments/7)

---

### Post by Oldhacker on 2009-05-19
The same problem of Firefox starting without borders returned today. :-(

I did the same fix as before, but WHY did it return?
And, one wonders if this will keep recurring.

---

### Post by Oldhacker on 2009-05-20
Yesterday, the same occurrence happened with Firefox.
I applied the same fix again. But why did it happen again?

---

