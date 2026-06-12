---
title: "Odd cursor size/theme issues with 11.10 running Unity"
date: 2012-01-30
forum: Desktop Environments
---

### Post by Johnny on the line on 2012-01-30
Hello everyone!

After a long break from using ubuntu 'cause of getting my new rig (10.04 up to 11.04 simply didn't wanna play with my new GTX 560 Ti back then), I've came back to 11.10, and I'm liking it so far!

The only BIG issue here (oh the pun) is the cursor gettin' super large/changing theme to one I configured it to using advanced settings (ex gnome tweak tool afaik). Now that happens when I'm using a browser - or simply put it seems to change whenever the pointer is over some  HTML/editable text!

It is a fresh installation, and the only thing I feel I should point out is that I (out-of-curiosity) tried high-contrast option from access menu during the install, which enlarged the pointer to approximately this size, and enlarged text as well.

Screen-shots of behavior I've captured so far are coming up at the bottom of the post.

Also: What the hell were they thinking? I mean the settings panel is worse joke than XP's Control Panel (can't argue with 7's one, it works flawlessly and intuitively).

Thanks for your time!

[http://imgur.com/EIiMv,XrROi,ayJoQ,5Ppr1,K38ot](http://imgur.com/EIiMv,XrROi,ayJoQ,5Ppr1,K38ot) (It's an album, navigate through it, I doubt it'll be much of an issue, and I don't have to throw in a bunch of links)

---

### Post by Johnny on the line on 2012-01-31
Just came to notice that Screenshot app actually does not show what I do see on the screen!
I presume that could mean that unity/compiz are overriding my settings to DMZ/White small (which is what I'd want, or maybe a black one, it doesn't even matter, just not at that size!), which gets overridden by my settings (although I can't change the size) when the screenshot fires up.

Hope that provides some more useful information, as I am stuck with this and in a need of direction!

Thanks again!

---

### Post by lolpenguin on 2012-01-31
Use GNOME Tweak Tool (it's in universe repo). Changing the cursor to DMZ White should work. You probably have to restart for full effect. (I noticed that not restarting would cause the standard pointer to remain the same, and all other ones (working, arrowrs, move, etc.) to change.)

---

### Post by Johnny on the line on 2012-01-31
Did so, that changed the cursor to DMZ black (as I wanted it to do), but in firefox/seemingly other HTML docs and text edit fields still have that super large cursor!

Any other advices? My cursor is just as on the pictures while using the firefox or something else, while in the normal system usage it retains it's normal size although it's not depicted so, probably due to some sort of a rendering issue of the screenshot app as I mentioned before.

EDIT: So, I've came to a solution myself... Oddly enough, I accessed it with dconf-editor, just to see that the cursor size is set to double, and that it didn't apply in all the applications, but solely in firefox/text editors, terminal text screen and so on...
Works now, thanks for help, I guess.

---

