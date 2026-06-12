---
title: "A few issues..."
date: 2005-11-19
forum: Desktop Environments
---

### Post by katiad on 2005-11-19
So in September, I moved from Windows to Ubuntu solidly for my main computer, except for for a few programs I love too much on Windows, which stay on my secondary computer. In any case, I installed Ubuntu, and everything worked great. Wanted to play with KDE, so I installed that, too. Then came some issues... 

Sound
------------
In KDE, my sound is all messed up. I can play music in xmms fine, but as noted in a previous thread a month or so ago, I have no system sounds. When I go to the system preferences, the test button on the main system sound page works fine, and plays the kde startup sound. But i can't get any other sounds to play, no matter what settings I use. I've reinstalled arts, done the kde upgrades that came out over the update manager a couple weeks ago... still nothing. Would /really/ love sounds. 

Sound works fine in gnome, btw.

X Crashing
-------------
X crashes. A lot. Waaay more than it should. Looking over logs gives me nothing too useful (I can't, at the moment, being at work, recall the errors it gave, but I do remember asking about this some time ago, also...), and there's definately no common thread in when the crashes happen. This happens in both gnome and kde - no surprise there. I'm wondering: could this be a hardware failure of some sort? Is this likely, or is it more likely to be a configuration problem? Video drivers are correctly installed.

Thunderbird Address Book
-------------------------
This isn't a KDE problem at all, (I don't think) but... what the heck is up with t-bird continually popping off with error messages saying my address book has been corrupted or is unreadable, so a new one will be created? It's done this /dozens/ of times. I mean, I hardly ever use it, so it's not a huge deal - just a pain in the ass. Any ideas what's going on here?

Update Notification
---------------------
Is there a way to get update notifications in KDE like they happen in gnome? or not? I mean, I log into gnome periodically anyway because I like a change of scenery, but it'd be nice to have updates notify me automatically.

Font Size
-------------
So I've changed all my system's fonts so they're larger... but the conversations in gaim are STILL tiny in kde, whereas, in gnome, at the same resolution, they're normal sized and readable. Firefox often starts out with super tiny fonts, too. Not sure why. Is there another place I can change these? I know I can change the font size for gaim, but unfortunately, this makes it quite huge to whoever I'm speaking with... and quite huge when I switch over to gnome, also.

Thanks for your replies!

---

### Post by mlomker on 2005-11-19
[QUOTE=katiad]But i can't get any other sounds to play, no matter what settings I use. I've reinstalled arts, done the kde upgrades that came out over the update manager a couple weeks ago... still nothing. Would /really/ love sounds. [/quote]

I'm not sure what you mean by system sounds.  Are you saying that amaroK won't play anything?

> could this be a hardware failure of some sort? Is this likely, or is it more likely to be a configuration problem? Video drivers are correctly installed.

There's really no way to know if it's a bad driver or a hardware issue without some kind of error message to go by.  Did this machine run WinXP or another operating system without a problem?  If another version of linux ran properly then you could rule that out.

> Is there a way to get update notifications in KDE like they happen in gnome? or not? 

Nope.  I suggested that in a thread to the developer of Adept but I don't know if that's on the to-do list or not.  I would like to have it.

> So I've changed all my system's fonts so they're larger... but the conversations in gaim are STILL tiny in kde, whereas, in gnome, at the same resolution, they're normal sized and readable.

I've recently had some font problems, myself.  Do you have the gtk2-engines-gtk-qt package installed?  In theory it causes gnome applications to use your KDE themes and fonts.

---

