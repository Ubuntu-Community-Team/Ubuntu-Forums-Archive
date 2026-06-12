---
title: "Interesting issue (I think it is)"
date: 2011-04-07
forum: Desktop Environments
---

### Post by djetch on 2011-04-07
(WARNING: Loooooong post! :D )

Alright, I'm not new to linux, started playing with Debian back in late 90s.  By no means am I even a strong intermediate user.  I would say maybe a strong beginner.  Anyways let's get to it.

I have a 6-7 year old HP Pavillion DV9000 laptop that wasn't being used so I slapped Ubuntu 10.10 desktop edition on it.  It's got a dual AMD64 proc, 2GB RAM, 110GB HD.  No dual boot or anything fancy.  Vanilla install worked just fine for me for a while.  Got a couple of things up and running (SSH, NXserver, SABnzb+, SickBeard and Couch Potato <--Doesn't matter if you don't recognize the last 3) and everything was fine.

...Until I realized I had an extra flat panel 24" monitor laying around.  It's a viewsonic.  Fought with it for a bit but was unable to get it running.  Even did a 'special' update to xserver-common & xserver-xorg-*somthing*.

That seems to have upset things.  Now when I log into GNOME while I get in, it's just not 'right'.  Here's what I mean: the top and bottom panels are present; the virtual desktops are not; open any thing (config editor, text editor, file browser, etc.) and the window has no borders or title bar; most of the time the windows open in the upper left hand corner with 'File', 'Edit', etc. is on top of the top panel.  Click on the show desktop button (bottom left corner) and I get an error stating that the action was not able to be completed or there is no window manager loaded???

I have reset my xorg.conf, forced a reinstall of the xserver-xorg-*something* & xserver-common packages; all with no improvement.

What have I done because it had to be something I did?

NOTE: I have Xubuntu & Xfce installed and they are both working just fine.

---

### Post by Copper Bezel on 2011-04-07
> That seems to have upset things. Now when I log into GNOME while I get in, it's just not 'right'. Here's what I mean: the top and bottom panels are present; the virtual desktops are not; open any thing (config editor, text editor, file browser, etc.) and the window has no borders or title bar; most of the time the windows open in the upper left hand corner with 'File', 'Edit', etc. is on top of the top panel. Click on the show desktop button (bottom left corner) and I get an error stating that the action was not able to be completed or there is no window manager loaded???

Under Ubuntu, you can use either Compiz or Metacity as a window manager. Something in your window manager (presumably Compiz, if you're using any desktop effects) didn't like something you changed in your xorg settings, and you're getting no window manager at all. Try this:

```
metacity --replace
```

And see what happens - whether or not you get back your window frames, especially. This isn't a fix, but it'll give us some idea of just how borked your settings are. = )

---

### Post by djetch on 2011-04-07
Heh.  I think you might have zoned in right on it.  While I have a decent understanding of the CLI world, I'm still learning all of the layers of the GUI.

So, in all of my installing & removing of packages I do believe I removed Compiz.  I was under the impression that it was just an 'extra' something you added to GNOME and not something that was required.  Now I think I'm starting to get a better picture.

Is metacity better/preferred over compiz?  Oh, I guess at this point I might as well just reinstall compiz.

Thanks for the quick reply.  I shall return shortly.

---

### Post by djetch on 2011-04-07
> **Copper Bezel said:**
> Under Ubuntu, you can use either Compiz or Metacity as a window manager. Something in your window manager (presumably Compiz, if you're using any desktop effects) didn't like something you changed in your xorg settings, and you're getting no window manager at all. Try this:

```
metacity --replace
```

And see what happens - whether or not you get back your window frames, especially. This isn't a fix, but it'll give us some idea of just how borked your settings are. = )

:KS :KS :KS

3 gold stars for you my friend.  One shot, one kill!  Problem solved.  Reinstalled Compiz and BAM! GNOME is normal again.  Thank you, thank you, thank you.

-Mat

---

### Post by Copper Bezel on 2011-04-07
Glad to hear it! = ) (Go ahead and mark the thread as "Solved" in Thread Tools at the upper right.)

Yeah, I'm the other way around - I've mostly just played with the GUI and know very little Bash. Metacity is the default window manager in other distros like Fedora, but Ubuntu  treats it as a fallback from Compiz (if any desktop effects are enabled, or by default in 11.04) because Compiz is much more configurable but easier to break and pickier about video cards.

---

