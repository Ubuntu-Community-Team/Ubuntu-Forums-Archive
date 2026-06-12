---
title: "Why does add/remove show stuff that synaptic misses?"
date: 2009-04-01
forum: General Help
---

### Post by ubnewbie2 on 2009-04-01
For example, I wanted to install gimp.  I fired up synaptic, but when I searched for gimp - it found only some other bits of software that mentioned gimp, not the program itself.

I was able to install it from command line with "sudo apt-get install gimp" and later I noticed that ubuntu's "add/remove programs" app also found gimp when I searched.  So why not synaptic?


I am doing this on eeebuntu in case that makes a difference.

As a related point, what is a good list of repositories to use that will cover a broad range of software?

---

### Post by Sef on 2009-04-01
Add/Remove is simply a front end GUI for Synaptic.  Synaptic has GIMP in it.   If you type in GIMP or gimp in synaptic search, it will show up.

---

### Post by ubnewbie2 on 2009-04-01
> **Sef said:**
> Add/Remove is simply a front end GUI for Synaptic.  Synaptic has GIMP in it.   If you type in GIMP or gimp in synaptic search, it will show up.

Not trying to be difficult, but's exactly what it DOESN'T do.  Something's wrong with it, and I am trying to find out what.

Edit:  just discovered that it is the quick search that is broken.  Doing a search using the binoculars works, quick search does not work properly.

---

### Post by mcduck on 2009-04-01
> **ubnewbie2 said:**
> Not trying to be difficult, but's exactly what it DOESN'T do.  Something's wrong with it, and I am trying to find out what.

Edit:  just discovered that it is the quick search that is broken.  Doing a search using the binoculars works, quick search does not work properly.

The quick search works, but it often takes a bit of time after starting Synaptic until it's ready for use. (you can actually see a message above the quick search box telling that it's "rebuilding search index" or something like that. When that message disappears the quick search starts working.

Also note that the quick search doesn't search from the whole repositories, it searches from the packages currently listed. For example if you set the filter to "Installed" to view only installed packages, it will only search from those packages. Like comparing Google search (search from the web) with Firefox search (search from current page).. :)

---

### Post by ubnewbie2 on 2009-04-01
> **mcduck said:**
> The quick search works, but it often takes a bit of time after starting Synaptic until it's ready for use. (you can actually see a message above the quick search box telling that it's "rebuilding search index" or something like that. When that message disappears the quick search starts working.

Also note that the quick search doesn't search from the whole repositories, it searches from the packages currently listed. For example if you set the filter to "Installed" to view only installed packages, it will only search from those packages. Like comparing Google search (search from the web) with Firefox search (search from current page).. :)

When I start synaptic, there are no words saying rebuilding index, but I left it sit for 10 minutes anyway, just to be sure.

Before I was using quick search with 'all' selected, but I just tried something different.  I did a 'binocular' search for gimp, and noted that it is there in the result set.  Then, with the result set showing gimp showing in the window, I typed gimp in the quick search and gimp disappeared from the list (along with LOTS of other software) leaving just a short list of some libraries and documentation.  btw: it is case sensitive too, and if I type GIMP in capitals as another poster suggested, it finds nothing at all.

Quick search is definitely broken and not finding lot's of matches that the full search does!

---

### Post by dcstar on 2009-04-01
> **ubnewbie2 said:**
> 
.........
Quick search is definitely broken and not finding lot's of matches that the full search does!

Quick search just filters what is in the main screen underneath.

---

### Post by Backharlow on 2009-04-01
Did you make sure that Synaptic had the correct setting for Sections, Status, Origin and filters (on the left). Searches in Synaptic stay within the scope of what you have selected there on the left so if you had just one repo selected in Origin, (and Gimp isn't in that repo) or if you had "Email" selected for Sections, it will only search packages related to email and won't find Gimp again.

---

### Post by ubnewbie2 on 2009-04-01
> **dcstar said:**
> Quick search just filters what is in the main screen underneath.

Yes, and it fails to find something that is there and plain to see. gimp is in the screen when I type gimp and it removes it from the list (as if it doesn't match.

---

### Post by ubnewbie2 on 2009-04-01
> **Backharlow said:**
> Did you make sure that Synaptic had the correct setting for Sections, Status, Origin and filters (on the left). Searches in Synaptic stay within the scope of what you have selected there on the left so if you had just one repo selected in Origin, (and Gimp isn't in that repo) or if you had "Email" selected for Sections, it will only search packages related to email and won't find Gimp again.

Yes, mostly I try it with "All" selected.  It still fails.  I have another machine with Ubuntu on it, and it works fine there, just not in the eeebuntu installation on my netbook.

---

### Post by mb_webguy on 2009-04-02
Have you tried rebuilding the index from the terminal using "sudo update-apt-xapian-index"?  I'm not sure why, but a couple of times in the last few months my index got messed up, and Synaptic's search wasn't working.  Updating the xapian index fixed the problem.

---

### Post by ubnewbie2 on 2009-04-02
> **mb_webguy said:**
> Have you tried rebuilding the index from the terminal using "sudo update-apt-xapian-index"?  I'm not sure why, but a couple of times in the last few months my index got messed up, and Synaptic's search wasn't working.  Updating the xapian index fixed the problem.

That fixed it !!!!

Thanks you so much.  I think people were having trouble believing that it just wasn't working right, but it was broken, just as I said, and your index rebuild is an easy fix.

---

### Post by Backharlow on 2009-04-14
Seems obvious now but, could the giant Reload button in Synaptic perform the aforementioned sudo update-apt-xapian-index?

---

### Post by paradigm2 on 2009-04-15
> **mb_webguy said:**
> Have you tried rebuilding the index from the terminal using "sudo update-apt-xapian-index"?  I'm not sure why, but a couple of times in the last few months my index got messed up, and Synaptic's search wasn't working.  Updating the xapian index fixed the problem.

I've also seen it where immediately after adding a repository, applying, then reloading, the search function will not find the new package.  However hitting all and manually finding it by utilising the fact that it is in alphabetical order works.

---

### Post by mb_webguy on 2009-04-15
> **Backharlow said:**
> Seems obvious now but, could the giant Reload button in Synaptic perform the aforementioned sudo update-apt-xapian-index?

I don't think so.  The Reload button is the same as running "sudo apt-get update".  I believe Synaptic will periodically rebuild the index, but I don't think the Reload button has much to do with it.

---

