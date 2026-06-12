---
title: "gtk theme not working after install new engine"
date: 2010-10-31
forum: Desktop Environments
---

### Post by quindonl on 2010-10-31
Hello,

Ubuntu 10.10
My wife wanted to use a new gtk-theme so she used the option "download more themes" and installed a new gtk-theme. The theme was not vissible for her so she just chose another default one. 
Now when ever either of us login into our accounts the default internal gtk-theme is used (the ugly grey square one). When we start the themes application (don't know the english name for it, it enables you to choose another theme for your desktop). The previously selected theme is then enabled even before the window of the util is shown.

My wife doesn't know which theme-engine she selected and I can't find it. 

Anyone any idea?

---

### Post by sagara on 2010-11-02
Is this what you see when you log in into your desktop?

Notice that the theme is applied correctly to the **Appearance Preferences** window but everything else is screwed up.  The ugly gray theme as you put it.

[[IMG]http://img688.imageshack.us/img688/1346/screenshotlh.th.jpg[/IMG]](http://img688.imageshack.us/i/screenshotlh.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by quindonl on 2010-11-02
Nope.
When just logged in the ugly grey theme is visible.
When I open "Appearance Preferences" everything goes back to the theme I had selected.
As if the gtk theme needs to "wake up".

p.s. everything execpt nautilus, that I need to first quit (nautilus --quit) but I've grown used to nautilus getting more and more irritating.

---

### Post by sagara on 2010-11-02
Lets try the following commands to see if this works for you:

```
killall -9 gnome-settings-daemon
gnome-settings-daemon
```

At this point, your theme should be applied properly.  Nautilus however should not be playing nice and still showing the ugly gray theme. Run this command and it should fix it:

```
rm -vr ~/.gconf/apps/nautilus && killall nautilus
```

After this, your theme should be fully loaded.

Let me know if this works.

---

### Post by quindonl on 2010-11-03
After trying to kill gnome-settings-daemon I found that gnome-settings-daemon wasn't running at all. It seems that when I log in the gnome-settings-daemon isn't started or won't start.

---

### Post by sagara on 2010-11-03
I see...

Did you run the other commands as well?

---

### Post by quindonl on 2010-11-03
> **sagara said:**
> I see...

Did you run the other commands as well?
Didn't have the time to do that this morning.
Will try tonight.

---

### Post by quindonl on 2010-11-14
gnome-settings-daemon kept on working (including nautilus) so didn't remove the gconf setting of nautilus. However, today gnome-settings-daemon didn't start.
Started gnome-settings-daemon and removed nautllus gconf settings and killall nautilus.

That did the job (for today at least :-) ).

B.t.w. instead of killall nautilus wouldn't a nautilus --quit have been enough?

---

### Post by sagara on 2010-11-14
Its a good point but I haven't tried it to see if it also works.

Do you have an SSD drive by any chance?  You might be affected by this bug mentioned in this bug tracker: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

Look at post [[COLOR="Red"]#68[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809/comments/68").  That fix did it for me.

---

