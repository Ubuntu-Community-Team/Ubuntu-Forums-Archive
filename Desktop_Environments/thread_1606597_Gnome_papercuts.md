---
title: "Gnome papercuts"
date: 2010-10-26
forum: Desktop Environments
---

### Post by MorayJ on 2010-10-26
OK, so I guess this is going to be a bit of a whine...but what the hell. Couldn't see a rants thread so will do this as a Gnome commentary in Ubuntu 10.10.

I don't know if other people are getting these types of problems, but these are problems I've run into during the course of today - not necessarily just happening today, but a day in the life thing.

I hadn't noticed that in Keyboard shortcuts there was a terminal starter (ctrl-alt-T), so I added my own (Alt-t). My Alt-T one worked, but it opens a terminal in the root directory. Ctrl-Alt-T simply doesn't work (even after I removed my own one).

I logged in and my top panel was mangled - the logout button not there and a couple of icons just repeated and others missing. This is usually ok, but sometimes it's like this. I hit ctrl-alt-backspace which I enabled the other day to restart x...nothing. I had to use ctrl-alt-del and to reboot the machine as that doesn't have a log-out option.

I loaded evolution as that is the only thing that populates the calendar you get on the panel. It couldn't read mail from google as it didn't understand the response google sent, apparently. So back to Thunderbird and no useful calendar on the clock.

The login window is set as far as I understand to not make a sound, but every time I come to the log in window it gives me a loud and annoying drum beat. The reason I log in manually is that when I log in automatically the gnome-keyring comes up two or three times (yes, I'm typing the password correctly) asking for my password, somewhat defeating the idea of automatically logging in.

Also, by not logging in automatically, I can have gnome-do run at start-up. With automatic login and gnome-do at start up, gnome-do would be waiting for the keyring in some way which locked up the whole of X (that was in 10.04 I think, and maybe fixed, but I'm trying to live the easy life).

I kind of mention this to get it off my chest, so please feel free to slate me for it, suggest I log bugs, google for the answers. But I didn't log on today to do any computing. I logged on to do some other work and I don't want to be having to hunt down solutions for lots of tiny errors which are sometimes very difficult to google for anyway as they can be difficult to describe.

I mean Gnome is fantastic. Some people disregard compiz as eye-candy, but it adds to a whole smooth experience for me and using Vista feels physically clunky in comparison. I'm not keen on the whole look of KDE - it doesn't seem terribly serious to me. I like Gnome overall, but today I'm trying to be a human being.

Perhaps I should have stuck with 10.04, but the mangled panel and the gnome-do problem happened there as well - not sure about the others.

So, is this linux for human beings? Right, I'll shut up now.

---

### Post by 3Miro on 2010-10-26
The rant sub-forum is called testimonial experience. This thread is going there as soon as the mods see it.

I don't know about the keyboard shortcuts, I will have to test that sometimes. It is possible that the Ctr + Alt + T opens a "Root Shell" as opposed to a regular shell with your home folder.

Panel icons is a known bug. It has been there for a while.

Evolution and the sounds are annoying and I don't know anything about them. However, Gnome Keyring should not popup three times. This has to be a bug of some sort (even if three things try to access the keyring at once, there should be only one popup). Does it do the same without the auto-login?

Compiz experience strongly depends on how and what you are doing as well as what hardware you have. I recently realized that it is  very smooth if you disable most of the effects.

I think I might actually have a solution to all your problems ... Well maybe not, but have you tried XFCE. You can install it along side Gnome to give it a try (XFCE in 10.10 is much better than 10.04). XFCE looks and feels a lot like Gnome, it can do some basic effects and can even run compiz well. It lacks some of Gnome's features (you have to set your own keyboard shortcuts, cannot drag-drop icons form the menu onto the panel, dual monitor takes a few extra steps to set ...), however, XFCE is very fast and very stable.

---

### Post by MorayJ on 2010-10-28
Thanks - wasn't particularly expecting a constructive answer to a not constructive criticism, but will give XFCE a go. I've never really considered it and maybe it's worth a go.

Out of interest, I keep my home directory when reinstalling and did a fresh install of 10.10 after upgrading from 10.04 at first. I see, in my startup applications, I have 3 separate instances saying "gnome keyring: " followed by ssh, or something else. This is presumably what causes the multimple password inputs and may be something to do with multiple installs, but I don't know.

Thanks for the thougts.

Cheers
Moray

---

### Post by MorayJ on 2010-10-29
I got round to googling for answers to a couple of these, and I'll add them here although they are elsewhere, in case someone happens to be here.

The drum beat on the login screen (ie the screen where you pick the user and type in the password) can be silenced by renaming the sound file (actually a link to the sound file, but same differenc). There are other methods that may work (gconf didn't do what I expected), but this is the one that I've used.
```
cd /usr/share/sounds/ubuntu/
```
```
sudo mv system-ready.ogg system-ready-OFF.ogg
```
You can rename it back to the original name if you want it back.

The problem with Ctrl+Alt+T not opening a terminal is solved (assuming you have compiz installed!) by making sure you've got CompizConfig Settings Manager installed. Go to the Gnome compatibility plugin in that, and make sure "Open a terminal" has a shortcut there. Mine was disabled.

Ctrl+Alt+Delete, which can be added in Preferences->Keyboard->Layout->Options and selecting "Key sequence to kill X server". Mine had come undone, presumably due to clutziness when setting it and clicking it off again before I left.

---

