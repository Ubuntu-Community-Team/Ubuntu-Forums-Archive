---
title: "Should I install kubuntu or kde on ubuntu?"
date: 2008-07-30
forum: Desktop Environments
---

### Post by ZeldaFan on 2008-07-30
I want to try out KDE 4.1 and possibly consider using it as my default desktop environment. However, if I dont like it, I want to be able to remove it without making a lasting footprint on my install. Should I install kubuntu in another partition or simple install KDE 4.1 in ubuntu as another desktop environment?

---

### Post by Syirrus on 2008-07-30
> **ZeldaFan said:**
> I want to try out KDE 4.1 and possibly consider using it as my default desktop environment. However, if I dont like it, I want to be able to remove it without making a lasting footprint on my install. Should I install kubuntu in another partition or simple install KDE 4.1 in ubuntu as another desktop environment?

I would install KDE 4.1.0 using this method...
[http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml](http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml)

If you don't like it, you can uninstall by doing an "apt-get remove kubuntu-desktop".  I'm assuming that it will take everything out, although I'm not sure.  I installed it using the method above and everything appears to be ok.  I have to say at least from my experience my lean and mean gnome / compiz installation runs better than with KDE 4.1.0 / compiz

---

### Post by lusiads on 2008-07-30
> **Syirrus said:**
> I would install KDE 4.1.0 using this method...
[http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml](http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml)

If you don't like it, you can uninstall by doing an "apt-get remove kubuntu-desktop".  I'm assuming that it will take everything out, although I'm not sure.  I installed it using the method above and everything appears to be ok.  I have to say at least from my experience my lean and mean gnome / compiz installation runs better than with KDE 4.1.0 / compiz
My experience was "apt-get remove kubuntu-desktop" only removing KDE, not its applications. Although KDE's QT applications still works well under GNOME, it's probbaly not what we expect to. You can uninstall QT apps if you know which they are in Synaptic.

---

### Post by ZeldaFan on 2008-07-30
So how do you install the KDE apps installed by default when installing kubuntu-desktop or whatever the KDE 4.1 package is called. And how does it treat KDE apps already installed on my gnome system such as amarok. Does it install a completely new version if a newer version is available with KDE 4.1 or does it upgrade my existing installation?

---

### Post by ZeldaFan on 2008-07-30
Okay so I installed KDE 4.1 on my ubuntu machine, I didn't have the patience to partition my hard drive for a kubuntu installation. I tried it, and it just felt funny. It seemed like one of those desktop enviro's that looks real nice when you look at screenshots of them, but when you actually get down to using them, its not really that great. It felt moderately sluggish (compared to my gnome/compiz fusion set up which flies in relation to this). This could or could not be due to the problems with Nvidia and their drivers (although I am not affected in gnome). I didn't have compiz fusion enabled, and window movement seemed laggy. The whole experience was "meh", so I uninstalled it via these commands:
```
sudo aptitude purge kubuntu-kde4-desktop
sudo aptitude purge kdm-kde4
sudo dpkg-reconfigure kdm
sudo aptitude purge ~nkde4
```
Just using the first command will not uninstall all the extra programs installed in the process. For some (fortunate) reason, it didn't uninstall kde programs I installed previously.

---

### Post by SaintStewart on 2008-07-30
I promise I am not trying to start a flame war, but KDE4 is still in it's infancy.  It took years for KDE3 to get to its current polish and speed.  Why does everyone expect KDE4 to be there after just a few months?  I really want to know...does no one have any patience any more?  Yes, KDE4 is sluggish, and its still not complete - although as of 4.1 is it snow *much* better than 4.0.  It will get better as things go along.  We just need to wait.  Heck, if this helps any, the Gnome folks are jumping on the bandwagon now and working on Gnome 3.  KDE4 must be doing something right if Gnome is going to play catch up now!  :lolflag:

---

### Post by Ataris on 2008-07-30
I've done some browsing, and the only solution I can offer is to uninstall everythign manually. Here's a very vague list: [http://en.wikipedia.org/wiki/List_of_KDE_applications](http://en.wikipedia.org/wiki/List_of_KDE_applications) I know there is an actual list somewhere, but I'm still looking for it.

Honestly? Just keep KDE and try not to let it bug you. There are some applications that require it, after all.

---

### Post by ZeldaFan on 2008-07-30
Actually, using the four commands I mentioned above, it removed mostly everything, except for adept and aggrekator. 

And I know I'm really not giving KDE4 a chance because to tell you the truth, I didn't explore with it longer than 10 minutes. If anything, I praise this version for its apparent ambitiousness, but I really wish releases like this were still kept in development. I do agree that no one's really showing any patience regarding KDE 4, yet 4.1 should have been 4.0 because 4.0 was pretty much a beta release. Personally, I felt that most of the impatience lies in the fact that KDE 4 is supposed to be an upgrade of KDE 3, not necessarily a completely new product. Thus, users were expecting 4 to be better (albeit a little different) than 3. Instead they were met with a trade off, a product that was better but also worse/buggier in a number of ways. I feel that KDE just rushed to release this version too soon, so my previous comments shouldn't really be considered to be my opinion of KDE 4 but of KDE 4.1 exclusively. I'm sure that especially because the program is available to end users now, many of the little kinks in the desktop environment will be worked out.

---

### Post by andrelukmana on 2009-04-06
I know that KDe can't completely remove bro....but u can use synaptic to remove KDe application that installed on your Ubuntu, on the Synaptic, choose Sections and select KDE, and remove all of installed KDE apps or libs on there, this should be removed all your KDE apps, :D

---

