---
title: "Disappearing Gnome desktop..."
date: 2010-11-11
forum: Desktop Environments
---

### Post by WarrenL on 2010-11-11
Hi folks,

Yesterday I answered an emergency call from a friend. He had lost his Gnome panel and  his desktop icons and was staring at a blank desktop background. The mouse  pointer was active, but right-clicking had no effect. I played around a  bit and found the following:

- Alt + F1 = Gnome Menu
-  This allowed me to start Ubuntu Tweak, from which a desktop reset  reactivated the icons.
- Then I opened a terminal and entered "killall gnome-panel" which resurrected the panel.
- Rebooted the computer - and I was right back to Square One.
-  Started the process over, then logged out. Logged back in using  "failsafe Gnome" and everything was there - panel, icons and  right-click.
- Logged out, logged back in using "Gnome" option. No panel, no icons, no right-click.

Help!

OS is 10.04, updated fully.
Gnome is 2.30.2 Build 25/6/10.

Can anybody help? For the meantime I have disabled my friend's automatic login and have him choosing failsafe at the login screen, which should keep him from pulling his hair out for a little while at least.

---

### Post by darkhelmetchris on 2010-11-11
> **WarrenL said:**
> Hi folks, Yesterday I answered an emergency call from a friend. He had lost his Gnome panel and  his desktop icons and was staring at a blank desktop background...

Hmm, well, 2 things come to my mind.

First, I had some similar trouble with the desktop a while back.  Try cleaning out your /tmp folder and restarting.  This restored proper operation for me in 2 cases in the past.

Second, you could remove (or optionally rename) the following paths in your user's home folder:
```
./.gconf/apps/panel
./.gconf/apps/panel/toplevels/top_panel_screen0
./.gconf/apps/gnome-settings/gnome-panel
./.gnome2/panel2.d
```and that should get you back to a fresh panel by default.  I would suggest renaming them, instead of deleting them... just in case, so you could put them back if you need to.

---

### Post by WarrenL on 2010-11-11
Thanks for that. I'll head back around there on the weekend and try out your tips, then report back.

---

### Post by WarrenL on 2010-11-16
Well, I finally got round to my mate's place and tried the suggestions above. I could only locate .gconf/apps/panel, and it had no top_panel_screen0 under toplevels. However I renamed the directory and tried again - nothing changed.

I then renamed the tmp folder, and all hell broke loose when I tried loggin in again. I ended up having to reboot to a terminal and put it back before I could get Gnome to load again. So a fail there too.

After that I tried a complete removal of gnome-panel (including, supposedly, the config files) then reinstalling it from terminal, but that didn't help either.

So I'm still at Square 1, with no panel appearing unless I do a killall command, or log in on failsafe Gnome.

---

### Post by hariks0 on 2010-11-16
> Try cleaning out your /tmp folder and restarting.

> I then renamed the tmp folder, and all hell broke loose ...:)

---

### Post by WarrenL on 2010-11-16
I should clarify: I followed that instruction to the letter, cleaning out and then restarting, with the old tmp folder retained and renamed for safety purposes, and a new, empty, tmp folder in its place.

---

### Post by darkhelmetchris on 2010-12-29
Alright, I am curious to see if we can narrow this down to a user profile problem.  At your next opportunity, try creating a new user and logging in under that.  Does the new user have this problem as well?  If not, then there is definitely some kind of user-profile problem.

---

### Post by WarrenL on 2010-12-29
Hi there darkhelmetchris!

It's nice to see your reply, but the thread had gone dead for quite some time so in the interests of sorting things out for my frustrated friend I plunged ahead and rebuilt the machine. It was a sledgehammer to crack a nut, but the problem has, of course, been banished.

However if he manages to land himself in the same poo again, I'll resurrect the thread and send you a PM. I think that creating a new user profile banished the problem, but after even just a month my memory is a bit creaky and I have an alarm bell ringing in the back of my head telling me that that wasn't quite the whole story...

Thanks again Chris.

Warren

---

### Post by darkhelmetchris on 2011-01-04
Glad to try to help.  I'll keep an eye out for a PM.  Cheers.

---

### Post by Krytarik on 2011-01-04
It's most probably a video driver issue, I had an almost similar behaviour -- no working desktop, no panels, or both -- when I, for another reason, set the option "AddARGBGLXVisuals" in xorg.conf to "False".

---

