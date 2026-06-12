---
title: "Working out whats causing system freezes"
date: 2009-01-15
forum: General Help
---

### Post by Shades404 on 2009-01-15
What program / logs / etc should I install / run / check to see what application is causing my system to freeze up from time to time.

My system is a dual core laptop with 4gb of ram and a solid state drive, so it should have enough power to run the applications I do for work. I have a cpu monitor running and I don't see that spike overly high which is why I think it must be some application not playing nicely.

The applications I generally run at work are:
VMPlayer (sometimes two or three copies of this)
Eclipse + PDT
Firefox (any sometimes multiple copies, always lots of tabs)
Skype
Pidgin
XChat
Thunderbird
Mplayer (connected to a windows share for music over samba)

The os is Intrepid Ibex and I've installed all the updates to date for that.

The freezes generally last for a few seconds and normally effect all the apps, but not always, mouse movement is not unaffected and the Gnome menus still work but new apps won't start till it unfreezes.

If I am running compiz (which is rarely enabled these days) then the frozen application windows grey out as well.

If anyone can give me some pointers that would be most helpful.

---

### Post by superoptimo on 2009-01-15
My advice is to disable all desktop effects.

I've also experienced some freezes with Compiz. But after disabling all desktop effects the system becoming more stable and Gnome runs smoothly.

Go to System->Preference->Appearance, go to the VisualEffects tab and disable all desktop effects. You will get a not nice but functional system.

---

### Post by Shades404 on 2009-01-15
Sorry I wasn't clear. I get freezes anyway, but with compiz on the application windows go grey rather than only unresponsive.

Currently, and most of the time, I have all desktop effects off.

---

### Post by walter_j on 2009-01-15
Check out this article on softpedia re system freezes and firefox. i t seems to match your issues.

[http://news.softpedia.com/news/Who-Freezes-The-System-Firefox-or-ext3-86242.shtml](http://news.softpedia.com/news/Who-Freezes-The-System-Firefox-or-ext3-86242.shtml)


walter

---

### Post by HermanAB on 2009-01-15
On one of my systems, the periodic freezes are due to the CDROM drive.  If I unplug the drive, the problem goes away.

---

### Post by Shades404 on 2009-01-15
> **walter_j said:**
> Check out this article on softpedia re system freezes and firefox. i t seems to match your issues.

[http://news.softpedia.com/news/Who-Freezes-The-System-Firefox-or-ext3-86242.shtml](http://news.softpedia.com/news/Who-Freezes-The-System-Firefox-or-ext3-86242.shtml)


walter

I'm using ff 3.0.5 while it claims should have that patch, however that article lead me to a link about solid state drives and apparently the default scheduler isn't great for them and can lock-up apps like I'm getting as well.

So I've changed that and moved firefox's cache to a ramdrive just in case. We'll see how that goes :)

Thanks for the help so far. If anyone has any other comments I'd still like to hear them.

---

### Post by Shades404 on 2009-01-15
Nope your entirely right, it's Firefox 3. Everytime it does anything with it's files I get a massive drive access spike and everything slows down or freezes completely.

Is there any sensible solution for this? All I've seen so far is to turn off the security options.

---

