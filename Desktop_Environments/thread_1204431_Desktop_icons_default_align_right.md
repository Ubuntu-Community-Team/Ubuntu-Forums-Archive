---
title: "Desktop icons default align right?"
date: 2009-07-04
forum: Desktop Environments
---

### Post by VOLKOV9 on 2009-07-04
Is there a way to make Desktop icons align to the right?  i.e., when I save something new to ~/Desktop/, have it appear on the right rather than the left?  Using standard hardy w/Gnome.

This is basically a bump of the now-read-only/archived [http://ubuntuforums.org/showthread.php?t=520264](http://ubuntuforums.org/showthread.php?t=520264)

---

### Post by justinmiller87 on 2009-07-30
I would like to bump this since I too would like to know, especially since I have my desktop looking like a Mac and widgets on the left side.

---

### Post by user11 on 2009-08-04
Mega bump

---

### Post by polax on 2009-08-31
Should be an option in Gnome settings - still not found by me ... will update if i do locate the same. In the meantime ... :guitar:

*mega-bump*

NOTICE:gconf-editor doesn't have an option for setting this, don't waste your time trying to set it using the same. On the other hand, there are a number of options you might want to fiddle with if you know what you are doing ;)

---

### Post by sohlside on 2009-10-19
Not sure why there are so many unanswered pleas for help concerning this so I too shall bump.  If it can't be done, for the love of Vader, someone just say as much.

*bump*

---

### Post by love4stupidppl on 2009-10-21
Bumb... because may wallpaper has a design on the left side, plus I like my icons on the right.

---

### Post by mcduck on 2009-10-21
> **sohlside said:**
> Not sure why there are so many unanswered pleas for help concerning this so I too shall bump.  If it can't be done, for the love of Vader, someone just say as much.

*bump*

Well, I just came to say that it can't be done. There's no such option in Gnome.

---

### Post by sohlside on 2009-10-24
> **mcduck said:**
> Well, I just came to say that it can't be done. There's no such option in Gnome.

Thanks, mcduck.  I've unintentionally figured out that if you move device icons then they seem to reappear in the same location the next time they are mounted. Still, I have downloaded files getting forgotten behind Conky when I have several at once.  My solution is to click-drag the desktop grabbing a visible icon as well as the space that is hidden behind Conky and then move all items by dragging the visible icon to the right. It's not a solution but it is a means of coping.

Another solution to this might be specify a different location for downloads and mount that folder to the desktop so it stays where you put it.  Barring that, viewing the desktop as a folder shows any icons that may be out of view.  I'm finding this to be an increasingly minimal issue when weighed alongside the multitude of improvements this OS has brought to my productivity and sanity.

---

### Post by luvgirl12345 on 2009-11-03
bump... isn't there a app that allows you to change this? i have mac4lin and i would like my new downloads etc to go left...

---

### Post by bigo72 on 2011-01-12
MegaBump on this: it's so strange, I can't believe it is impossible to do it :-(

---

### Post by goltoof on 2011-02-02
I don't know about aligning to the right, but no one has mentioned this yet..

Open gconf-editor and under applications > nautilus > desktop 
uncheck "volumes_visible"

This makes it so the volumes don't appear, and if you still want just make a shortcut to the drive and put it wherever you want!

---

### Post by Worgen on 2011-02-23
Kick... I don't like auto left align either. I want them on the right....

---

### Post by N00b-un-2 on 2011-04-08
instead of just bumping threads and asking someone else for answers I've done a little digging myself.

I'm not afraid of getting my hands dirty and doing a little hacking.  Right now I'm running a hacked Nautilus which I've increased the size of the icons in the side bar, so making modifications to nautilus is fairly easy to do -- if you know what you're looking for.  The first step is to grab the source files and build-deps.

There is no easy way to configure some things in Nautilus, but it doesn't mean they can't be done. After grabbing the source files for nautilus I found a file called 'fm-desktop-icon-view.c'.  The icon arrangement for the desktop seems to be handled separately from the regular nautilus windows ie; top to bottom then left to right as opposed to left to right then top to bottom.  I did find a couple places in the file mentioning left, right, top and bottom and I tried swapping instances of left for right and recompiling the source but to no avail.  Perhaps someone with a little more experience than me can help figure this out.  I think I'm on the right path though.

---

### Post by N33k on 2011-04-09
> **love4stupidppl said:**
> Bumb... because may wallpaper has a design on the left side, plus I like my icons on the right.

Bump, I want this for the same reason as L4SP.

---

### Post by SleepyLemur on 2011-11-30
I was able to remove all desktop icons by unchecking the following settings in gconf-editor under app > nautilus > desktop > volumes_visible 
and app > nautilus > preferences > show_desktop

This doesn't solve the problem of showing icons starting on the right hand side but there may no ever be a solution to that issue.

---

