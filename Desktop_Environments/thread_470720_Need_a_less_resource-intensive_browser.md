---
title: "Need a less resource-intensive browser"
date: 2007-06-11
forum: Desktop Environments
---

### Post by lduperval on 2007-06-11
Hi,

Can anyone recommend a browser that is less resource-intensive than Firefox? I use FF for most of my browsing but on certain sites, it is just too slow. The CPU shoots to 100% and it can take almostt 30 seconds to get a page rendered. I am not sure what the problem is, but I am rpetty sure I don't see that behaviour with FF on Windows.

I used to use opera, but it has since been deprecated (it's not in Feisty).

I tried Dillo but that doesn't render correctly, plus it looks like it doesn't support Javascript, which I need.

Galeon crashes on my system.

Epiphany used the same engine as FF and at times feels just as slow.

So far, I haven' t tried Konqueror yet because of the KDE dependency.

Any suggestions?

L

---

### Post by L14UX_1NS1D3 on 2007-06-11
well you have quit a few options in linux.
you can use epiphany, gnome default web-browser.
there's the mozzila web-browser. I'm not sure how resource intensive that might be.
next theres dillo. I tried it, it's really light weight but doesn't have alot of features.
There are quit a alot  of browsers available, to many to list here but I would recommend to use dillo for now and lookup other browsers [here]("http://www.itp.uni-hannover.de/~kreutzm/en/lin_browser.html") 

hope this helps ):P

---

### Post by ugm6hr on 2007-06-11
> **lduperval said:**
> 
I used to use opera, but it has since been deprecated (it's not in Feisty).


Opera works fine in Feisty.  Just download the .deb from:
[http://www.opera.com/download/](http://www.opera.com/download/)

And double-click the downloaded file.

I use it on my lower spec Xubuntu laptop - just haven't managed to integrate flash (I believe flash 9 misbehaves with Opera anyway).

---

### Post by tagra123 on 2007-06-11
These tweaks will speed things up and you can set your own memory limits. There are many other twaeks too. I recall seeing some on the Firefox website too. Google will give plenty of results for ubuntu tweak firefox

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by dominator22 on 2007-06-11
You might want to check out [Links](http://links.twibright.com/) from Twibright Labs.

EDIT: It's in the repositories, just run: 

sudo aptitude install links2

---

### Post by Nythain on 2007-06-11
i would highly recomend opera... it hasnt really been depreciated... you can either download the deb from thier site, or if you dare (wich i have heard works from numerous sources) install from the most recent debian repository... i would suggest the deb file method though... it worked for me

---

### Post by dlldll on 2007-06-12
I've been looking for the same thing. I think a big problem with Firefox is javascript - it's really slow. I went on windows to see if firefox there is any faster but it's the same.
 I tried the new window's safari and javascript on that is lightening quick. I use this test - [http://celtickane.com/projects/jsspeed.php](http://celtickane.com/projects/jsspeed.php) - but it is confirmed with gmail and google reader. Gmail opens like a regular html page with safari on windows. How do they make javascript so fast? And ie7 and firefox are so slow? There is a huge pratical difference when opening javascript heavy pages for me.

 Incidentally, opera is quick on that test if you have no pages open that use javascript but its slowest browser out there when gmail is open. Mine went from 500ms to 5500ms. 
 (On xubuntu, i get about 3600ms with firefox no matter if other javascript pages are open. In windows i get a 3200ms with firefox and 550ms with safari. ie7 gave 4200ms)

---

### Post by Dragonbite on 2007-06-12
Safari is nice and quick, and since it's based off of khtml (according to a co-worker) it should re reproducable in Linux (Konquerer perhaps?).

Let the browser wars begin! :)

---

### Post by bailout on 2007-06-13
> **ugm6hr said:**
> Opera works fine in Feisty.  Just download the .deb from:
[http://www.opera.com/download/](http://www.opera.com/download/)

And double-click the downloaded file.

I use it on my lower spec Xubuntu laptop - just haven't managed to integrate flash (I believe flash 9 misbehaves with Opera anyway).

To get flash working just download it, unpack it and copy the files to the opera plugin directory. See tools > preferences > advanced > content > plugin options, for details and address but should be /usr/lib/opera/plugins. either click rescan in above dialogue or restart. There are a few problems but it handles most things.

---

### Post by lduperval on 2007-06-13
Hmmmm I like the javascript angle. I find that sites like Google reader, GMail, SugarCRM are the ones that give me the biggest issues, and they are all heavy on JS (because of AJAX, most likely).

So maybe I'll try Konqueror, just to see. If I do, and I don't like it, can I uninstall it as well as all its dependencies automagically? Or will the uninstall remove konqueror and leave all the KDE stuff on my machine?

I will also load Opera again.

L

---

### Post by moore.bryan on 2007-06-13
[I]not so long ago, i too was in the same boat.  when i started looking for browsers i found the following to be true:
firefox=too much drain,
opera drain>firefox,
konqueror drain>opera.

i checked-out kazehakase (in the repos) and was pleasantly surprised.  took a while to get used to the "bareness" for some reason, but it might be what you're looking for.  lots of people suggested links2, but i just couldn't get it to work right...
[/I]

---

### Post by tgalati4 on 2007-06-13
Point of Interest:  Javascript test mentioned earlier

Tiger 10.4.8, PPC G4, 1 GHz, 1.25 GB RAM:

Camino Browser (version 1.1b, Mozilla rewrite for Tiger/PPC):  ~5,200 ms

Safari Browser (native Tiger version 2.0.4):  ~2,450 ms

based on 3 tests each.

So native Safari beats a respun Mozilla on PPC running Tiger.

---

### Post by dominator22 on 2007-06-13
> **lduperval said:**
>  If I do, and I don't like it, can I uninstall it as well as all its dependencies automagically? Or will the uninstall remove konqueror and leave all the KDE stuff on my machine?

If you use apt-get or an apt-get front-end like Synaptic to install, you will have to remove the dependencies yourself.  If you use use aptitude it will remove KDE dependencies as well. 

To install run:
```
sudo aptitude install konqueror
```

To remove run: 
```
sudo aptitude purge konqueror
```
This will also remove Konqueror konfiguration files.  To keep the config files replace purge with uninstall.  
If you want to see what other konqueror related packages there are, run: 

```
aptitude search konqueror
```

---

