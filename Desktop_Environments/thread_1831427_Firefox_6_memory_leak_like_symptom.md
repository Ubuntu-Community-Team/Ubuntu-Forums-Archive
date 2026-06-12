---
title: "Firefox 6 memory leak like symptom"
date: 2011-08-23
forum: Desktop Environments
---

### Post by maxfac on 2011-08-23
Hi guys,

First of all, I am not a computer expert. Would be grateful is someone could give me advice.

When using Firefox 6, after some time, the system appears to be slowing down over time. It's worse when there are a lot of javascripts or when javascripts are repeatedly used again and again. 

However when doing the same activities using Chromium, it's fine - no lagging/slow down over time.

I am using ubuntu 11.04.
uname -r  >  2.6.38-11-generic

Thanks.


Regards.

---

### Post by lovinglinux on 2011-08-24
It could be some extension causing the problem. Can you reproduce it in safe mode?

I would recommend trying Firefox 7.0b1, which has huge memory improvements. See [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for installation instructions.

---

### Post by maxfac on 2011-08-25
I disabled the add-ons and the problem is still reproducible. 

Well, even if it is solved without the add-ons, I still need to use the add-ons. 

Think I'll just wait for the version 7 release. Using chromium in the interim.

---

### Post by lovinglinux on 2011-08-25
> **maxfac said:**
> I disabled the add-ons and the problem is still reproducible. 

Well, even if it is solved without the add-ons, I still need to use the add-ons. 

Think I'll just wait for the version 7 release. Using chromium in the interim.

The procedure was to determine if any add-ons was causing the problem. You would turn them on again after finding the culprit.

Anyways, can you post the link of the page causing the problem?

I would suggest using NoScript to block unnecessary scripts from running. There are also other add-ons that can block stuff you don't need, like Ghostery, AdBlock Plus and Flashblock.

---

### Post by ralanyo on 2011-08-26
I am having the same issue, but I thought it was a memory leak in Ubuntu, but now that I think about it, every time it occurs I am using FireFox. I have to shut down firefox and restart the machine several times daily. It becomes unbearable, especially if you have many tabs open. 

However, I don't know why this would matter, but everyday I would run the ubuntu updates and without fail my machines would start to be sluggish. The last two days I have not performed the ubuntu updates and it is running much better. Not sure if its just a coincidence or not.

If anyone knows a fix for this please let me know.

---

### Post by maxfac on 2011-08-26
ralanyo:

Yes, that's exactly the problem I am having. Also happens when:
(1) multiple tabs are open (2Gb of ram here, and system resources show hardly 1gb is consumed at any point)
(2)Leaving websites like facebook or gmail logged in all night (system literally went crazy with swapping the day after) and I have to force shutdown.

lovinglinux:

i am not sure what output i can post on here. It's just the system slow down/sluggish > But what worries me most is, I tend to have Libreoffice open in the background whilst firefox running (whilst doing research on the internet) - and when the computer slows down to almost a total halt, I have to force shutdown and lost some work (well, i know i should regularly save my work but on the other hand, FF has evolved so much over the years within the open source community that I am not really anticipating this sort of thing will happen). 


I have googled "firefox memory leak". I think it is a known issue? But i was hoping with recent update to FF6, things would been sorted.

---

### Post by lovinglinux on 2011-08-26
I am not sure, but I think I can reproduce the problem, at least partially. I usually have Gmail and GReader open as app tabs. After some time Firefox memory builds up to 500 Mb, but not much more than that. Is not a big problem for me, specially considering I have more than 60 extensions installed. However, I have closed those app tabs and so far FF memory usage is holding at 200 Mb. I will let you now if indeed the memory stays below 300 Mb.

---

### Post by MS_free on 2011-08-26
I see similar issues in the last FF release. It used to be quite memory hungry lately, however, I can tell that  there's a memory leak in the version 6. 
I start with an open and simple page (single tab) and can see how firefox gradually eats memory looking at top. 

However, even if firefox has a memory leak it should not make you reboot the whole machine.  When your memory goes over board, just kill it , e.g., in the Terminal via command ```
killall firefox-bin
```You can also start it in the limited shell like this (also in the terminal):
```
bash -c 'ulimit -m 102400 -v 1000000;firefox 2>/dev/null' &
```Tailor the values for -m and -v  for your needs. The process will be killed when the mem consumption exceed the given limits. Just restart it then and it will restore the session.

---

### Post by lovinglinux on 2011-08-29
I suspect is Gmail the culprit. My elevated memory usage is also due to the fact that I save the Cache in RAM instead of disk.

Anyway, get [Cache Status]("https://addons.mozilla.org/en-US/firefox/addon/cache-status/") add-on. It allows to monitor you cache usage and clear it. It works with RAM cache and disk cache. Is not a solution but it can help to avoid restarting Firefox.

---

### Post by VanillaMozilla on 2011-08-30
Always suspect an extension first.  To check:  Help > Restart with extensions disabled.  If that doesn't work, create a new profile for testing (save the old one -- it has all your data!).

And aside from that, there are some problems with the Web sites themselves (G-Mail is or has been one of the problem sites).  They can continue to create objects on your computer infinitum.  Sometimes Mozilla has been forced to create a special patch to handle a popular Web site, but usually the Web site needs to be fixed.  Some Web browsers may have already devised appropriate defenses.

Finally, there are some problems with one or more recent releases, and they will be fixed.  Hang in there.  It will be fixed sooner or later.

---

### Post by MS_free on 2011-08-31
OK, suspecting extensions.... Turned them off and see how the memory still slowly oozing out. The paradox is, when you start with n1% of memory use and   N tabs open, you will see n2% memory usage when some tabs are closed and no new open, with  n2 greater than n1 !
This is called a "memory leak". 

I do not use firefox for gmail, I have mutt for it. Just for javascript sites and/or flash url-sniffing/downloading, not even watching. lynx, w3m and elinks are much more efficient for the rest.

One advantage of FF was a rich  collection of extensions. And add killers, flash removers are absolutely necessary.

FF's memory garbage collection gets worse from one version to another, imho.

---

### Post by VanillaMozilla on 2011-09-01
> **MS_free said:**
> OK, suspecting extensions.... Turned them off and see how the memory still slowly oozing out. The paradox is, when you start with n1% of memory use and   N tabs open, you will see n2% memory usage when some tabs are closed and no new open, with  n2 greater than n1 !
This is called a "memory leak".
Probably not.  A memory leak means that there is no means of releasing memory that has been allocated, and you can't determine that so easily.  See [http://en.wikipedia.org/wiki/Memory_leak#Other_memory_consumers](http://en.wikipedia.org/wiki/Memory_leak#Other_memory_consumers) .  Also read the introduction to that article.  It could still be a problem, of course, whether it's a memory leak or some other memory problem.

You and one or two others in this thread mentioned that the problem occurs with Gmail and Facebook.  These Web sites can allocate memory on your computer, almost without limit.  You may well see memory decrease from time to time.  That would be due to garbage collection, which may not happen for several minutes.

You may be able to see that the growth occurs in the memory cache.  Type 'about:cache' in the address box and you can see a display.  You can also get more detailed information on memory use if you type 'about:memory'.

If memory use becomes very large, or especially it grows without limit, you should file a bug report at bugzilla.mozilla.org .  However, you should first (1) make sure you have steps that can be reproduced by anyone; and (2) make sure the problem occurs if you create a new profile.  Remember that the problem could be due to the Web site.  And it's best not to call it a memory leak.  Better to say "high memory use" or some other accurate term.

To create a new profile, simply rename the old one (temporarily).  Type 'about:support' in the address box and press the button "Open Containing Folder".  That's your profile.  It's inside a hidden directory.

---

### Post by MS_free on 2011-09-09
Just would like to say that after the last two updates the problem seems to  have disappeared. Firefox is great again.

Thanks much, Mozilla !

---

### Post by oldsoundguy on 2011-09-09
Another tab that leaks like a sieve a lot of the time is Facebook.  Most of my slow down issues can be traced to that tab most of the time.  A quick shut down of the browser and reload will usually solve the problem .. but there are times when that FB tab just has to be closed and come back later!!

---

### Post by maxfac on 2011-09-25
Thank you for the help & info guys - especially loving_linux & MS_Free
(especially at the time when I think it's more of a psychological problem than a true app issue here)

Shall I mark it as [SOLVED] now then?

---

### Post by Francewhoa on 2012-02-22
Disable all firefox plug-ins worked for us. Not the extensions but the plug-ins. One of the plug-ins must be leaking RAM.

---

### Post by lovinglinux on 2012-02-22
Necromancy.

---

