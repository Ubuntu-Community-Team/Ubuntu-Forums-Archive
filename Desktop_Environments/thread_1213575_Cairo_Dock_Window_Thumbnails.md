---
title: "Cairo Dock Window Thumbnails"
date: 2009-07-15
forum: Desktop Environments
---

### Post by Topher88 on 2009-07-15
Hi.  I've been messing with  Cairo dock, and there's one thing that I can't seem to get to work that I would like to...  If I am in Firefox or any other application, and I minimize the screen, I would like to see the thumbnail of the screen on my dock so that when I click on it, I can maximize the screen back up.  Further, if I click on the Firefox launcher, instead of opening the window that's already open, it should open a new Firefox session.  I have tried checking "show a window thumbnail when minimized" under the taskbar section, but it doesn't do any good.  How can I do this, or is it even possible?  Thanks!

---

### Post by Topher88 on 2009-07-15
Okay, I figured out how to do it by observing the way other dock themes work.  If you care to know what I found out, it's a per-application setting, so if you want a certain application to work that way, like Firefox, then you would right-click on the launcher in the dock, click "modify this launcher," and under "extra parameters," it should have the name, in this case "Firefox," and you just change that to "Firefox-bin," and then every time you click on it in the panel, it will act like you have opened an application that wasn't already in the dock, thus giving you an extra window that wouldn't normally be there.

---

### Post by fabounet on 2009-07-15
in such case, you should just delete the launcher and re-import it from the Applications Menu.
the class of Firefox has changed with the 3.0, maybe the launcher you had was a bit old.

---

### Post by Topher88 on 2009-07-15
I had been using the applications Firefox, and it wouldn't do it...  To me, it doesn't look like the dock is supposed to work that way in the first place, which was a misunderstanding on my part because I just thought it would, being that that's how (I think) it works on a Mac.  I noticed, however, that in certain themes, namely the Chrome Round theme, Firefox (and only Firefox) was set up to behave in the manner that I describe above, which to me was desirable, so I kept switching back and forth and examining the differences between the two themes (mine and Chrome Round) until I finally found they key difference.

The "Firefox-bin" solution was the only solution I found...  If this is faulty (which it very well could be, I'm a Linux N00b) and/or there is a better solution, by all means, clue me in.

Thanks!

---

### Post by Topher88 on 2009-07-15
And it appears that I was quite vague about what I'm actually trying to do, now that I read back over what I wrote.  I would provide screenshots, but I'm currently at work, away from my linux machine.

Basically...  For certain applications like Firefox, I want the dock to treat their perspective launchers just like the system would treat any other launcher.  For instance, if you drag Firefox to the dock from Applications or what have you and you click on it, by default it will open Firefox and the icon will become translucent, indicating that you are currently using that application.  If you click on that same Firefox launcher while Firefox is currently running, instead of opening a NEW instance of Firefox like any other launcher outside of the dock would, you can only maximize/minimize your current session.  Further, when I minimize it, not matter what I do, it won't show me the thumbnail; it just stays translucent.  Even if it did correctly dispay the thumbnail, however, I don't WANT the thumbnail to take the place of the existing Firefox launcher, but instead I want there to be a NEW area for that thumbnail on the dock, so that way, if I want to open a new Firefox session for any reason, I could click on the original Firefox launcher.

In the workaround that I have found, changing the parameters to "Firefox-bin" causes the dock to act like you're opening an application that DOESN'T already have a launcher (even though it does), so it creates a new, temporary icon that will only be present while the application is open.  Meanwhile, the original launcher does not act like the applicatoin is being used, it simply acts exactly how you would expect any other launcher in Linux to act; you click it once, it opens the application you want, and it doesn't prevent you from opening more instances of that application simply because the application is already being used.  Make sense?

So in this regard, I have found a solution that APPEARS to work the way I want it to, but since I am new to Linux and could very well be over complicating the matter and/or doing something unwise by setting the parameters to "Firefox-bin," please let me know if there is something I should be doing differently.  I ASSUMED it was ok since one (or more?) of the included themes actually implements this procedure, but you never know.  Otherwise, if anyone else is wanting their dock to behave in this manner, this appears to be a good workaround.

---

### Post by fabounet on 2009-07-16
ok so let's summarize :)
you have a firefox launcher, but when you launch ff, you want a new icon in the dock.

so you can just untick the option that says to mix appli and launchers.

OR, if you want this behavior only for ff or a few launchers, you can edit the launcher, and tick the option that says to not steal the icon in the taskbar.


PS : launchers don't change their icon to thumbnails. It would be a bit confusing in my opinion.
so only new taskbar icons can become thumbnails.

---

### Post by Topher88 on 2009-07-16
I've noticed that it seems like other applications do it automatically, but with certain applications I have to change the parameters, as with Firefox.  I don't remember my specific settings, like whether or not I have those things checked, so I'll look at that when I get back home...  Thanks!

---

### Post by Topher88 on 2009-07-16
> **fabounet said:**
> ok so let's summarize :)
you have a firefox launcher, but when you launch ff, you want a new icon in the dock.

so you can just untick the option that says to mix appli and launchers.

Doesn't do it.  This option is unticked, but certain launchers (like FF) don't do it while others do.

> OR, if you want this behavior only for ff or a few launchers, you can edit the launcher, and tick the option that says to not steal the icon in the taskbar.Never tried that one...   Might be the same as the "-bin" thing.

---

