---
title: "Alt-f2 to open &quot;run application&quot; not working anymore"
date: 2015-02-09
forum: Desktop Environments
---

### Post by farenji2 on 2015-02-09
Since a while the keyboard shortcut alt-f2 to open the "run application" doesn't work anymore. Nothing happens. When I look in the keyboard settings, under shortcuts, I see that alt-f2 is correctly mapped to xfrun4. However when I edit the keyboard shortcut I can't enter "alt-f2". I don't get an error but the key combi is just not accepted. My guess is there is a conflict and that key combi is already in use somewhere else. However I checked all shortcuts I could find (also in the window manager settings) and can't find any other alt-f2 occurrences. BTW, alt-f3 and other key shortcuts still work.

I already tried resetting all shortcuts to default, and also deleting all my user settings (all hidden . dirs like ~/.config/ etc) and logging out & in again but the problem persists. I'm at the point of doing a clean reinstall (I really use xfrun4 a lot) but I'm hoping there's a simpler solution... ok I could map it to another key combi but that seems not a fix but a workaround.

I'm running xubuntu 14.04.1 with all updates installed. Thanks for any help!

---

### Post by Habitual on 2015-02-09
Create a new user on the system and login as that new user, does the issue remain?

---

### Post by farenji2 on 2015-02-09
> **Habitual said:**
> Create a new user on the system and login as that new user, does the issue remain?

Yes, still doesn't work. Thanks for the suggestion.

---

### Post by mc4man on 2015-02-09
Don't use  xfce ect. so just a thought - 
is  xfce4-appfinder installed?
Also what happens if you run xfrun4 from a terminal?

---

### Post by farenji2 on 2015-02-09
Yes, xfce4-appfinder is installed, and launches when I press alt-f3 just fine. Also xfrun4 is installed and working if I run it from a terminal. I can also bind it to another key combi; I even managed to bind it to the alt key (which is not a very good idea btw ;P). Just the alt-f2 key seems impossible to use.

---

### Post by farenji2 on 2015-03-08
For the record: turned out I had a faulty keyboard. The F2 key was broken. So I bought a new one and the problem's solved.

---

