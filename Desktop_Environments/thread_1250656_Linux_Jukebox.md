---
title: "Linux Jukebox"
date: 2009-08-26
forum: Desktop Environments
---

### Post by jayleesan on 2009-08-26
Hi all,
Im am looking for a good way to set up a linux jukebox with minimal of extra's.
What I basicly want the computer to do is boot up and start rhythmbox (or mayebe songbird) in "Party mode" (Just a one time button press to start playing music realy fast).
I wasn't able to find a good HowTo to set something like this up to my satisfaction but mayebe some of you can point me to some good way to realize this?
Thanks!
~Jay

---

### Post by linux000019 on 2009-08-26
editeeddddd

---

### Post by jayleesan on 2009-08-27
I think I've found a good way to do so. Thought I'd share it ...

For a screenshot click here:
[http://kooijman-design.nl/crap/linux-jukebox.png](http://kooijman-design.nl/crap/linux-jukebox.png)

What you should have installed to accomplish this:
- globalmenu-paneel-applet
- Rhythmbox
- Compiz settings manager

From the default gnome desktop:
- Add Rhythmbox to startup programs via system settings.
- Start Rhythmbox and maximize it, set preferences to your preferences (I disabeled the sidebar), than close rhythmbox.
- Remove the Gnome bottom panel.
- Clear the top panel from all shortcuts and info's you don't want (Might want to keep the ubuntu main menu untill you're done), leave a shutdown button on it!
- Add globalmenu-paneel-applet to the top panel and set "Enable Global Menu For GTK applications".
- Open Compiz settings manager and use it to disabele window borders.

If you restart your session, rhythmbox will start (still maximized) without window border and your screen should look something like the screenshot I provided.

To points of critic from my part on this setup:
- I want it to be used by childeren, but I don't know if they can still mess up the settings.
- Would be great to have ubuntu automaticly log in to the gnome session we've prepared (mayebe during insallation?)

Please respond to make this better!

---

### Post by jayleesan on 2009-08-27
> **jayleesan said:**
> Would be great to have ubuntu automaticly log in to the gnome session we've prepared (mayebe during insallation?)Found the solution for this:```

System > Administration > Login Window

Click Security.

Enable Automatic Login, choose user.
```

---

