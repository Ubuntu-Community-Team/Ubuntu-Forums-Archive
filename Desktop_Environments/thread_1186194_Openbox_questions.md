---
title: "Openbox questions"
date: 2009-06-13
forum: Desktop Environments
---

### Post by 37fleetwood on 2009-06-13
I recently posted a thread with all the window managers and desktop environments I could get going. recently I was playing with Openbox and ran into a curious thing at least to me. I decided to set Nautilus as the pinboard instead of Rox. well the problem is when you do this you lose the Openbox menus and end up with the Nautilus right click context menu, ie you lose the ability to launch applications except through the terminal which I'm not that good at. this gave me an idea, I created a launcher on the desktop for Gnome-panel. when I clicked it voila! it looked just like my Gnome desktop! well sort of, some things were a bit different. one of the things that didn't work were the shut down/logout commands for Gnome on the panel. it was kinda cool as it was fast like Openbox but looked like Gnome. (I guess I could have as easily started the Xfce4-panel, LXPanel etc.
ok, the questions, if someone is interested in going into this, if not I understand.
is there any advantage to running Openbox if you just clutter it up with docks, panels and pinboards etc? (I may not have put that right)
is there any way to go back after you set Rox or Nautilus etc. as the pinboard?
if I decided to play with this some more what would the code look like to get the user switcher functioning properly and how would I go about it?
and finally is there a way to keep from altering my Gnome desktop while in Openbox or one of the others? I'm afraid I'm going to make changes and have them come back to haunt me when I log back into Gnome.
thanks!
Scott

---

### Post by Mark76 on 2009-06-13
Have you tried using Thunar or PCManFM as the desktop manager?

---

### Post by 37fleetwood on 2009-06-13
Thunar and Pcman are just file managers right? you would still have to use Rox to get such things as desktop icons and wallpaper etc right? there may be other ways of going about these things but so far I haven't found them. I'm at that dangerous stage where I'm trying to learn a bit more about how things work.;)
Thanks
Scott

---

### Post by Mark76 on 2009-06-13
PCMan can manage your desktop and icons as well (though they have to be in the desktop folder to show).

Actually, I'm not sure if it's Thunar or XfDesktop that manages desktop icons in Xfce. I suspect it's the latter.

---

### Post by m_duck on 2009-06-13
PCManFM can manage desktop icons. You can enable it by going to Edit -> Preferences, clicking the Desktop tab and checking the "Manage the desktop and show file icons" checkbox. From the same window PCManFM can also control your desktop wallpaper (as it will turn it black by default if solely managing desktop icons. To keep the regular Openbox right-click menu when doing this you also need to check the "Show menus..." check box.

Apart from the programs you mentioned above there is also a program called [Idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page"). However, not being a user of desktop icons my knowledge is somewhat limited!

> **37fleetwood said:**
> is there any advantage to running Openbox if you just clutter it up with docks, panels and pinboards etc?
I think so. I like it as it begins as pretty much a blank cavas which you can add only the apps you want to. My main PC is powerful enough to happily run Gnome and compiz or KDE 4 but I tend to use openbox anyway out of preference. I used to use it with pypanel/tint2 as a panel (though AFAIK pypanel is no longer in the Jaunty repos) but my current setup consists of no panel - just Openbox and Conky.

> **37fleetwood said:**
> if I decided to play with this some more what would the code look like to get the user switcher functioning properly and how would I go about it?
The stuff like user switcher and log in/out and shutdown options on Gnome panel I ***think*** are quite tightly integrated into Gnome and so am not sure how to enable them in Openbox. I tend to just give the following in a terminal when I need to shutdown or reboot respectively:```
sudo shutdown -h now
sudo shutdown -r now
```> **37fleetwood said:**
> is there a way to keep from altering my Gnome desktop while in Openbox or one of the others? I'm afraid I'm going to make changes and have them come back to haunt me when I log back into Gnome.
The only sure fire way I can think of to ensure you don't mess up (or change) your Gnome settings is to create a new user for Openbox so any settings you change stay with that one user.

If you haven't seen it yet, [Urukrama's Openbox guide](http://urukrama.wordpress.com/openbox-guide/) is worth a read. Actually, there is a section in that guide which outlines a couple of different ways to get shutdown/reboot etc to work properly in Openbox.

---

### Post by Mark76 on 2009-06-14
If you run OpenBox with PcManFm as the desktop manager you've basically got the beginnings of an LXDE desktop.

---

