---
title: "KDE4:  how do I change the login dialog's background image?"
date: 2008-04-01
forum: Desktop Environments
---

### Post by Halcyone1024 on 2008-04-01
Hello, all.  I've been away from my machine for a while, now, with the Ubuntu 7.10 random freezing bug and all, but now I've got Kubuntu 8.04 (KDE4) and a new (and much simpler) problem.  The login dialog background image changed the second time I booted from I-can't-remember-what to a unicorn, and there doesn't appear to be any control in System Settings capable of changing that.  Nothing personal, unicorns, but I have no idea how the background changed by itself (all I did was run adept and update all available packages), and I'd like to set my own.

I did find a tab in System Settings -> Login Manager called "Background", but the file selector there isn't working.  Every time I specify a new directory, it pops up a dialog saying "Cannot start process Cannot talk to klauncher: the name org.kde.klauncher was not provided by any .service files." [sic], and remains blank.  This is also confusing, because it used to provide the name of my desktop wallpaper, which is not and never has been a unicorn.

I know it's just a cosmetic issue, but you'd be surprised at how frustrating a unicorn can be.

I got past the lack of an "Admin mode" in System Settings (kdebase-workspace bug 184491) thanks to the advice of Martin Gräßlin on the KDE forums:
> Running "kdesu systemsettings" opens the KDE 3 version of systemsettings. So no chance to configure there. Only chance is to run "/usr/lib/kde4/lib/kde4/libexec/kdesu /usr/lib/kde4/bin/systemsettings" which opens the new systemsettings with root priviledges.

---

### Post by Footer on 2008-04-01
I take no offense to Unicorns either but this is not funny.  In fact, over in the kubunutforums, they claim it's an April Fools joke.  Here are a couple of links:

Topic: Ok, what's the deal with the unicorn?
[http://kubuntuforums.net/forums/index.php?topic=3092844.0](http://kubuntuforums.net/forums/index.php?topic=3092844.0)

Topic: Why oh Why??
[http://kubuntuforums.net/forums/index.php?topic=3092837.0](http://kubuntuforums.net/forums/index.php?topic=3092837.0)

There are more.  To make matters worse, I can't change it back either because in System Settings, my Login Manager crashes xorg!

So, HOW DO WE FIX THIS VERY CRUEL JOKE???

Thanks.

---

### Post by nosrednaekim on 2008-04-01
just wait for tomorrows updates and it will be gone :)\

and yeah, It is an April Fools Joke

---

### Post by trippinnik on 2008-04-01
to change the settings or any of the KDE4 system settings that require Admin rights,```
 kdesudo /usr/lib/kde4/bin/systemsettings
```

---

### Post by Footer on 2008-04-02
Thanks for the replies.  I haven't had a chance to update today yet but when I do, I presume the dreaded Unicorn will be gone.  :)

As for the crashing thing, I did determine that launching system settings with sudo (or kdesudo as you've pointed out) takes care of the problem and the modules don't crash xorg anymore.  But this has NEVER happened in the past.  I launch system settings, launch the modules, if they require admin, I'll get the dialog to enter my admin password, and carry on.

So I'm still a little puzzled and still not happy if this was indeed an April Fools joke.  Granted, Kubuntu is FREE software and Hardy is still in development ... but still.

Thanks!

---

### Post by Halcyone1024 on 2008-04-02
Man, April Fool's Day was really big this year.  Maybe I shouldn't have reinstated my webcomic bookmarks yesterday, since now my favicon cache is all messed up, thanks to the XKCD -> QuestionableContent -> Qwantz -> XKCD joke  (I know how to fix it, but I've got enough on my plate for now).

So, I should just reboot, and it'll be reset?  Wonderful.  It was a good prank, in hindsight, and I would have appreciated it more had I installed Hardy earlier.

Can someone pull some strings over at the KDE project?  I'm really getting annoyed that I don't have an "admin mode" button.  Maybe I could edit the application menu myself and change the run command?  How would I do that?  Also, I'd like for some of my non-KDE applications to show up, as well.  How do I add new items?

Oh, and remember the problem with the open dialog.

---

### Post by Footer on 2008-04-03
> **Halcyone1024 said:**
> 
Maybe I could edit the application menu myself and change the run command?  How would I do that?  Also, I'd like for some of my non-KDE applications to show up, as well.  How do I add new items?


I'm not 100% sure about KDE4 but in KDE3, you just right click on the K button (start button in lower left corner) and you should be able to edit the menu items, add items, etc.

Sorry about not being able to address your other questions but I'm just a lowly system user with no ties to the KDE developers.  I've tried KDE4 but it's a bit too early in development for my tastes so I'm sticking with KDE3 for now.

I think I'm finally over the Unicorn thing .... never been a big fan of April Fools and this particular prank came at a bad time for me.

Thanks!

---

### Post by Halcyone1024 on 2008-04-05
Right-clicking it was the first thing I tried, but the KDE4 applications menu is implemented as a widget (plasma), and the settings menu for it is somewhat lacking:  I get to say how many items it shows vertically without a scroll bar and whether or not to expand root menus on mouseover, and that's it.  I feel pretty certain that 8.04 isn't going to come out on time as expected unless it stays with KDE3 and lets KDE4 simmer for a while.

Anyway, the specific applications I wanted to add got added by Adept once I rebooted, so I guess as long as I'm willing to install only from the repos, I'll be fine.  Still, I'd like to edit the Dolphin (like Nautilus) run command so that it runs with kdesu.

---

### Post by oobuntoo on 2008-04-05
That unicorn pic ain't gay enough. They should've used a pic of Richard Simmons :lolflag:

---

