---
title: "Firefox and Real Player problems"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Aggienator on 2006-08-13
I am having trouble with streamed video from the BBC which requires Real Player. FIrst I tried installing the Real Player 10 from .bin accoirding to instructions (I think on the Real Player site). When it asked for a location I gave /opt and aske it to create symbolic links. Sadly trying to view Gardners World just told me I didn't have Real Player installed. Not knowing how to uninstall things installed this way I went and deleted /opt/RealPlayer and its contents. 

I then tried mplayer installed via Automatix. This gave me sound, but as if recorde in a biscuit tin. It also displayed a small slice of the video in the bottom section of the window, not the full thing. So I uninstalled that using the instructions on the forum.

I then installed Real Player via Automatix. With this I get good sound, but no picture at all ](*,) . I'm feeling at a loss for what to do now. Also cannot find uninstall instructions for Real Player installed via Automatix! Any help gratefuly received!

---

### Post by vijirajan on 2006-08-13
I would remove the current RealPlayer installation and do a fresh install. Then start RealPlayer (Applications->Sound & Video->RealPlayer). This will ask you if you want to configure FireFox plugins. Say yes here and you should be able to watch streaming videos.

Also make sure you uninstall myplayer or at the least remove mplayer firefox plugins from /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins.

Hope this helps!

---

### Post by Aggienator on 2006-08-13
Can you advise on how to remove the existing install?
Ta Aggie

---

### Post by vijirajan on 2006-08-13
You can remove the directory and contents where RealPlayer was originally installed. They don't have a separate uninstaller for removing RealPlayer.

---

### Post by jacrider on 2006-08-15
I was looking to solve the same problem, also to watch BBC2 (Top Gear).

I went to the [www.realplayer.com](www.realplayer.com) site and downloaded the .bin installer file.  Then installed and it seems to work.

Here in North America, it is almost watchable in full screen.

---

### Post by Aggienator on 2006-08-15
> **jacrider said:**
> I was looking to solve the same problem, also to watch BBC2 (Top Gear).

I went to the [www.realplayer.com](www.realplayer.com) site and downloaded the .bin installer file.  Then installed and it seems to work.

Here in North America, it is almost watchable in full screen.


I'm very much a "linux by numbers" user still! Does it matter where it is installed and when the installer asks about making links should I say yes?

Thanks for your patience!

---

### Post by Aggienator on 2006-08-15
> **vijirajan said:**
> I would remove the current RealPlayer installation and do a fresh install. Then start RealPlayer (Applications->Sound & Video->RealPlayer). This will ask you if you want to configure FireFox plugins. Say yes here and you should be able to watch streaming videos.



Unfortunately when I ran RealPlayer it didn't ask about firefox plugins. How do I configure that manually?

Thanks

---

### Post by Aggienator on 2006-08-15
Update: a firefox restart and the video now starts in firfox, problem now is - no sound ](*,) . If I click on the "standalone player" option it opens and runs fine in Totem :confused: 

I'm determined I'll get this sorted in the end

---

### Post by Aggienator on 2006-08-15
Well, its finally working after re-starting my computer. Don't know why it required a restart, but after that it works.:D

---

