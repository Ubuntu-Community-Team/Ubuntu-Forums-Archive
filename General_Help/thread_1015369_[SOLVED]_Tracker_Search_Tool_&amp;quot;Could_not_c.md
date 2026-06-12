---
title: "[SOLVED] Tracker Search Tool: &amp;quot;Could not connect to search service as it may be busy&amp;quot;"
date: 2008-12-18
forum: General Help
---

### Post by deltaromeo on 2008-12-18
Hi, I get the following error when entering a search term in the tracker search tool:

"Could not connect to search service as it may be busy"

I enabled indexing and watching from the Preferences -> Search and Indexing a few hours ago - and have rebooted since then.

Any ideas?

---

### Post by deltaromeo on 2008-12-19
still getting this error.

are there log files i can look at to try to solve this?

---

### Post by deltaromeo on 2008-12-19
bump.
anyone?
bueller?

---

### Post by SEMW on 2009-01-04
I'm getting this as well.  Anyone?

---

### Post by rmtatum on 2009-01-04
I am getting the same error.

---

### Post by deltaromeo on 2009-01-10
Hello Folks, I found a cure for this, I went into **Preferences** -> **Sessions** and ticked both **Tracker** and **Tracker Applet**.

Also worth noting, ensure Indexing is enabled under **Preferences** -> **Searching and Indexing**

---

### Post by buixuanduong1983 on 2009-01-18
I have just written a new search tool: QuickSearch. Give it a try and let me know your comment:
[http://ubuntuforums.org/showthread.php?p=6570132]("http://ubuntuforums.org/showthread.php?p=6570132")

Download and source: [http://quicksearch.sourceforge.net/]("http://quicksearch.sourceforge.net/")

---

### Post by buixuanduong1983 on 2009-01-19
Hi again, I have just update QuickSearch to version 2009-01-19. Have a look!
([http://quicksearch.sourceforge.net/]("http://quicksearch.sourceforge.net/")).

In this release:
- now you can resize its window
- press Escape key when browser sub-window is opened will close it
- fixed the error of duplicate entry in Path combo box
- store window setting on exit

---

### Post by motang on 2009-03-24
I was getting the samething but I made sure all tick marks were there and restarted the computer (as I needed to after a update) and it seems to indexing now.  If this doesn't do it then I am uninstalling it and installing Beagle search. :)

---

### Post by James1293 on 2010-09-14
In case anyone else is having this problem, here's how I solved it:
Basically, tracker 0.6 is severely outdated, so what you have to do is update to 0.9.
Here's how:

1) go to [https://launchpad.net/~tracker-team/+archive/tracker-unstable](https://launchpad.net/~tracker-team/+archive/tracker-unstable)
2) add the ppa's to System->Administration->software sources
2a)go to the "other software" tab
2b)"Add..."
2c)paste the 2 lines (separately, do "add" and "add source" twice)
```
deb http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu lucid main
deb-src http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu

```
(The "unstable" release is actually much more stable than the version in the ubuntu repo's)

3)open the Update Manager (system>administration>update manager)
3a)do a "partial update" when the window comes up
3b)watch for what it plans to uninstall, you *may* (probably won't, but may) need to manually reinstall these later. The way you do that is "sudo apt-get install <whatever-it-uninstalled>", but don't do that till the end.

4)in terminal, "apt-get remove ^tracker* ^libtracker*"

5)in terminal, "apt-get install tracker"

6)log out and log in

7) (this step is optional. Actually, you can do this at any point in the installation to check what's going on.)in terminal, "tracker-status-icon" or "tracker-status" 


If you have any questions, either post here or check
irc://irc.gimp.org/tracker

James
with lots of help from abustany

---

### Post by nutznboltz on 2010-09-21
> **James1293 said:**
> In case anyone else is having this problem, here's how I solved it:
Basically, tracker 0.6 is severely outdated, so what you have to do is update to 0.9.
Here's how:

1) go to [https://launchpad.net/~tracker-team/+archive/tracker-unstable](https://launchpad.net/~tracker-team/+archive/tracker-unstable)
2) add the ppa's to System->Administration->software sources
2a)go to the "other software" tab
2b)"Add..."
2c)paste the 2 lines (separately, do "add" and "add source" twice)
```
deb http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu lucid main
deb-src http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu

```
(The "unstable" release is actually much more stable than the version in the ubuntu repo's)


All of that is outdated too.

Either run

sudo add-apt-repository ppa:tracker-team/tracker-unstable

-OR-

run System->Administration->Software Sources
Then switch to the "Other Software" tab
Then click "Add"
Then paste in only: ppa:tracker-team/tracker-unstable
Then click "Close"

---

### Post by James1293 on 2010-09-21
nutznboltz:
I'm curious. I did it in the way that I posted; is that incorrect, or just inefficient? Should I undo the changed I made and do what you suggested, or did I accomplish the same task in a more round-about way?

---

### Post by LewRockwellFAN on 2011-01-22
> **deltaromeo said:**
> Hello Folks, I found a cure for this, I went into **Preferences** -> **Sessions** and ticked both **Tracker** and **Tracker Applet**.

Also worth noting, ensure Indexing is enabled under **Preferences** -> **Searching and Indexing**
Where are you finding this menu? I don't seem to have it.

P.S. ...duh ... I get it now. That must be a menu on the updated version you are talking about - one not present on the one in USC-synaptic. You'd think they would have either taken out the non-functional version or replaced with the working one by now.

---

