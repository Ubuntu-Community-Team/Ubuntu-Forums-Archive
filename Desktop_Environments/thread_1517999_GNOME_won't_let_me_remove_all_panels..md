---
title: "GNOME won't let me remove all panels."
date: 2010-06-25
forum: Desktop Environments
---

### Post by clicker4721 on 2010-06-25
Is there any way to take down all panels in GNOME? I'm using the newest AWN, and have no need for the panels. Any way to get rid of the eyesore last one?

---

### Post by yvsong on 2010-06-25
Select "Auto hide" in the Properties dialog of the panel.

I found Glx-dock fancier.

---

### Post by clicker4721 on 2010-06-25
So I can only hide it? No removal?

---

### Post by kerry_s on 2010-06-26
run-> killall gnome-panel
then you need to goto preferences-> startup-> options
& click on that remember running

make sure you close everything you don't want to start.

---

### Post by yossell on 2010-06-26
I'm finding that, on 10.04, gnome panel restarts after the command killall gnome-panel. There are some fields in required_components that point to gnome panel - and others report success in mucking around with these fields, but I tried this and nothing happened. I tend to use openbox at the moment, so I've not tried this myself, but the techniques in this thread - though maybe a bit ugly - seem to have worked for some.

[http://ubuntuforums.org/showthread.php?t=1444461&page=1](http://ubuntuforums.org/showthread.php?t=1444461&page=1)

---

### Post by clicker4721 on 2010-06-26
> **yossell said:**
> I'm finding that, on 10.04, gnome panel restarts after the command killall gnome-panel. There are some fields in required_components that point to gnome panel - and others report success in mucking around with these fields, but I tried this and nothing happened. I tend to use openbox at the moment, so I've not tried this myself, but the techniques in this thread - though maybe a bit ugly - seem to have worked for some.

[http://ubuntuforums.org/showthread.php?t=1444461&page=1](http://ubuntuforums.org/showthread.php?t=1444461&page=1)

Oh, yes. asmoore82's fix worked perfectly. Thanks a million.

---

### Post by w0Rm210 on 2010-06-27
If you dont wanna have all those apps running on boot, just hit ALT-F2 and go to gnome then desktop then panel and edit the key.... More of a perminant fix i suppose :).

---

### Post by clicker4721 on 2010-08-18
Oh, for anyone wondering, here's what to do:
Hit ALT+F2, and type in "gconf-editor", but without the quotes. Then, under "/desktop/gnome/session/required_components/panel", change the value from "gnome-panel" to "avant-window-navigator" and you're good to go! **OR**, you can achieve the same end much easier if you have [Ubuntu Tweak]("http://goo.gl/YwLV"). On the left side of this window, click "Session control" and change the "Panel" value from "gnome-panel" to "avant-window-navigator". Okay, you're clear!
):P

---

### Post by nick_goodfate on 2010-08-18
> **clicker4721 said:**
> Oh, for anyone wondering, here's what to do:
Hit ALT+F2, and type in "gconf-editor", but without the quotes. Then, under "/desktop/gnome/session/required_components/panel", change the value from "gnome-panel" to "avant-window-navigator" and you're good to go! **OR**, you can achieve the same end much easier if you have [Ubuntu Tweak]("http://goo.gl/YwLV"). On the left side of this window, click "Session control" and change the "Panel" value from "gnome-panel" to "avant-window-navigator". Okay, you're clear!
):P

NOTE: Doing that (thats what i 've done too) you won't have ALT+F2 any more. But Gnome-Do is a good replacement ...

---

### Post by Mi11z on 2010-09-25
> **nick_goodfate said:**
> NOTE: Doing that (thats what i 've done too) you won't have ALT+F2 any more. But Gnome-Do is a good replacement ...

Double quotes you two thank you very much. :)

---

### Post by - inferno - on 2011-03-09
I did this..!!

---

### Post by rykel on 2011-03-12
I am running Maverick.

None of the above-mentioned solutions was able to remove the top GNOME panel.

gconf-editor/desktop/gnome/session/required_components/panel - REMOVED KEY
---> Did NOT work

Setting Ubuntu Tweak Session panel to "cairo-dock" ---> Did NOT work


Why is it so HARD to remove this last panel??

---

### Post by false truths on 2011-03-12
I took the easy way out in removing the last panel.

```
gksudo nautilus /usr/bin
```

find the program "gnome-panel"

cut it, and paste it to your home folder in case you need it later. Don't delete it, though, because trust me, you will need it later.

Once you've done that, close your root terminal, log out, log back in, no panels!

---

