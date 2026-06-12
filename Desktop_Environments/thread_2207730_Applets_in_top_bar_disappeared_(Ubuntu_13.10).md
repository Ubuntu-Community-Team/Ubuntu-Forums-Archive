---
title: "Applets in top bar disappeared (Ubuntu 13.10)"
date: 2014-02-24
forum: Desktop Environments
---

### Post by Alexis Wilke on 2014-02-24
I just upgraded to Ubuntu 13.10 from 13.04 and I lost the applets in the top *menu* bar. Any idea what I could do to see them again?

Interestingly enough, when I click on the Workspace Switcher (I have 4 workspaces) I can actually see the applets being rendered there. But once I select a workspace the bar becomes black.

Is there something I need to do to get them back to normal?

---

### Post by Frogs Hair on 2014-02-25
Try the following command and log out and back in.

```
sudo apt-get install --reinstall indicator-session
```

---

### Post by Alexis Wilke on 2014-02-26
I tried reinstalling the indicator session and still nothing even after a full log out + log back in... (I do not use lightdm as I prefer to boot to a console and start X11 with the startx command, which worked just fine for years.)

Is it possible that old Gnome session definitions could prevent the bar from appearing normally?

Just in case I'm adding screenshots to clearly show what my problem is.

Thank you.
Alexis

[IMG]http://alexis.m2osw.com/images/indicators-visible.png[/IMG]

[IMG]http://alexis.m2osw.com/images/indicators-invisible.png[/IMG]

---

### Post by Frogs Hair on 2014-02-27
The dconf editor includes properties for the various panel applets and making sure the defaults are set might be worth checking. This problem / bug occurs as result of upgrades and re-installing the applets works for many people. The Unity panel uses a different set of applets than the Gnome panel found in the flashback session . Check Ask Ubuntu also .

---

### Post by Alexis Wilke on 2014-08-31
I got at least a temporary solution to this problem today!

I was looking into another issue I have with gnome terminals not always (to not say, nearly never) load up as expected. As I was doing so, I bumped in this question/answer about wmctrl: [http://askubuntu.com/questions/394998/why-wmctrl-doesnt-work-for-certain-windows/395476#395476](http://askubuntu.com/questions/394998/why-wmctrl-doesnt-work-for-certain-windows/395476#395476)

That made me think maybe I can find the window and apply some function over the one(s) that cause problems.

Indeed, I could just use the [FONT=courier new]wmctrl -i[/FONT] to apply an "show above" to the applet window. Now I see my applets again! 8-)

I have a complete answer with command line options, etc. here:

[http://askubuntu.com/questions/436590/lost-all-my-applets-last-time-i-upgraded-to-13-10-how-can-i-get-them-back/518500#518500](http://askubuntu.com/questions/436590/lost-all-my-applets-last-time-i-upgraded-to-13-10-how-can-i-get-them-back/518500#518500)

It may not be a permanent answer, as in, it does not solve the order in which the windows get open and thus it will occur each and every time I reload X, but at least in this way I can see my applets. I'll post a script later once I have one that can do the [FONT=courier new]add,above[/FONT] automatically.

---

