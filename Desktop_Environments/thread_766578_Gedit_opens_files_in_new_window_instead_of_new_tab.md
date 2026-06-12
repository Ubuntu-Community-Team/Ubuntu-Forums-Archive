---
title: "Gedit opens files in new window instead of new tab"
date: 2008-04-25
forum: Desktop Environments
---

### Post by ayoli on 2008-04-25
Hi,
In hardy, gedit keeps opening files in new window instead of in a new tab when there is already an instance running.
Is this a bug or a feature ?
I've searched every where an option about that (even in gconf) but didn't find anything or missed it).
Any clue ?

---

### Post by Tim Sharitt on 2008-04-25
The only time files open in a new window instead of a new tab for me is if I open a file from a different desktop than the one gedit is running on.

---

### Post by ayoli on 2008-04-25
Here it happens even if I open a file from the same desktop.
It is very annoying :(

---

### Post by obscenic on 2008-08-29
I'm having the exact same issue.  This started happening as best I can tell, after the upgrade to heron.

---

### Post by KayWren on 2008-11-08
I have the same problem! I had no problem with my former laptop (using hardy), the problem appeared with my new one (using hardy too).

Did ayoli or obscenic resolve finally this problem?

---

### Post by ayoli on 2008-11-08
> **KayWren said:**
> I have the same problem! I had no problem with my former laptop (using hardy), the problem appeared with my new one (using hardy too).

Did ayoli or obscenic resolve finally this problem?

I've just tried on my new 8.10.
Opening a file from the same virtual desktop where gedit is, the file opens in the same gedit window. If you try to open a file from another virtual desktop, it opens in a new window.
Not sure but I'm guessing that is possibly more a compiz issue than a gedit issue.

Bonne journée :)

---

### Post by KayWren on 2008-11-10
I guess I should therefore upgrade my system. Thanks!

Et bonne journée !

---

### Post by KayWren on 2008-11-10
I've just upgraded my system... and gedit continues to open files in new windows instead of new tabs. Damned!

---

### Post by KayWren on 2008-11-12
> **ayoli said:**
> Not sure but I'm guessing that is possibly more a compiz issue than a gedit issue.

Without compiz I still have this problem. I took a look in gconf-editor, but there is nothing about our tab problem in gedit configuration.

---

### Post by ayoli on 2008-11-12
> **KayWren said:**
> Without compiz I still have this problem. I took a look in gconf-editor, but there is nothing about our tab problem in gedit configuration.

Feel free to post a bug on gnome bugzilla (or comment an existing bug). I'll do the same when I'll have some time.
If you do so, please post the bug link here :)

---

### Post by b0b138 on 2008-11-12
right click said file > open with > open with other application. At the bottom expand use custom command. Then scroll though the list and click on Text Editor. Back at the bottom it should say gedit. If it happens to say gedit --new-window, delete the --new-window part

---

### Post by ayoli on 2008-11-12
> **b0b138 said:**
> right click said file > open with > open with other application. At the bottom expand use custom command. Then scroll though the list and click on Text Editor. Back at the bottom it should say gedit. If it happens to say gedit --new-window, delete the --new-window part

not a bad idea but :
let say I have gedit opened on desktop 1, now I go to desktop 2 for some reason and try to open a text file from this 2nd desktop : gedit will open a new window.
Now if I stay on the desktop 1 and try to open a text file from the desktop 1 gedit opens the file in a new tab.

---

### Post by b0b138 on 2008-11-12
Did it say --new-window?

Mine does the same thing. Seems to make sense though. If I'm on desktop 2, I'm not sure I would want an opened file to go to another desktop

---

### Post by ayoli on 2008-11-12
> **b0b138 said:**
> Did it say --new-window?

Mine does the same thing. Seems to make sense though. If I'm on desktop 2, I'm not sure I would want an opened file to go to another desktop

nope, it doesn't say --new-window

And I've choosen to have gedit on desktop one for some reasons but may have to open a file in gedit from another desktop, that was working before hardy.

---

### Post by KayWren on 2008-11-15
> **b0b138 said:**
> right click said file > open with > open with other application. At the bottom expand use custom command. Then scroll though the list and click on Text Editor. Back at the bottom it should say gedit. If it happens to say gedit --new-window, delete the --new-window part

I tried that but it just says '*gedit*', there is no '*--new-window*'.


[quote=ayoli]Feel free to post a bug on gnome bugzilla (or comment an existing bug). I'll do the same when I'll have some time.
If you do so, please post the bug link here[/quote]

Thanks ayoli!

I've just took a look in gnome bugzilla, and I've found [something interesting](http://bugzilla.gnome.org/show_bug.cgi?id=559280) (your former idea about compiz seems to be the good one).

But I don't know where is '*gedit-app.c*'...

---

### Post by ayoli on 2008-11-15
> **KayWren said:**
> I tried that but it just says '*gedit*', there is no '*--new-window*'.




Thanks ayoli!

I've just took a look in gnome bugzilla, and I've found [something interesting](http://bugzilla.gnome.org/show_bug.cgi?id=559280) (your former idea about compiz seems to be the good one).

But I don't know where is '*gedit-app.c*'...

A .c file is a source code file, means you'll find this in gedit source code. you can get it from the repositories using 
```
apt-get source gedit
```
Before doing that, check that you have the deb-src (sources repos) enabled in System > Admin > Software sources

---

### Post by KayWren on 2008-11-15
I'll try that!

I guess I should uninstall gedit first, shouldn't I? And when I'll modify source files, I should compile gedit?

(Me, a noob? :mrgreen: )

---

### Post by grossvogel on 2009-02-14
I was having this problem, too. The bug report noted above and the proposed patch indicate the the problem is with the size of the currently-open gedit window, so here's an idea:

**Just un-maximize your existing gedit window to be just a little bit shorter than your screen.** If you're lucky like me, subsequent invocations of gedit will open the doc in the same window!

Not as easy as if the app worked exactly the way I want, but quicker than mucking around in the source code.

---

### Post by nortexoid on 2009-11-02
I have the same problem as well and it has to do with whatever handles virtual workspaces (or with how gedit handles interacting with them). Opening in new tabs within the same window is fine if you're opening the files from the same workspace as gedit. Otherwise it opens a new window.

This might be desired behavior, but it isn't for me and apparently others as well. It would be nice if there were some option to change this (even it requires mucking around with config. files). Is there?

---

### Post by ZankFrappa on 2011-02-08
I just stumbled upon that bug (/ feature or whatever). The bug filed in bugzilla says "fixed" though.

It doesn't help to unmaximize the window, when I execute 'gedit --new-document' from another workspace I get a new toplevel window - no matter what I do with the existing gedit...

Should I file a new bug?

---

### Post by arkmundi on 2011-09-02
New Dell Inspiron 15R, fresh install of Ubuntu 11.04, same problem and I have not yet found a cure.  As with others, I prefer one gedit session and all files displayed in tabs, rather than what is apparently the default for Unity:  openning files in a new window.  Its possible to open files using the open button, which then opens the files in new tabs.  But if using Nautilus to navigate and open - new window.  Maybe its Nautilus thing?  Help would be appreciated.

---

### Post by ThomWilhelm on 2011-10-23
Sorry to bring up a really old thread but I'm having this exact same issue but in 11.10, I was having the same problems in 11.04.

Basically if I already have a text file open then double click another file in Nautilus, it creates another gedit session rather than just opening it in a new tab in the current session.

As I find Unity very awkward to switch windows it makes this bug even more annoying. If anyone has any ideas then let me know. I'm going to file it as a bug to see if I can get some help with it.

Cheers.

---

