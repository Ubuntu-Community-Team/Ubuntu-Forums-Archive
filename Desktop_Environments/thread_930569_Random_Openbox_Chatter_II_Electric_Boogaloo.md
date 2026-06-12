---
title: "Random Openbox Chatter II: Electric Boogaloo"
date: 2008-09-26
forum: Desktop Environments
---

### Post by Mark76 on 2008-09-26
Seems a shame to not carry on.

After a few months away I recently reinstalled OB as part of a minimal installation (well, at least it was until I started adding stuff :lol:). A lot of the problems I had before (with GKrellm and Feh) have been eliminated (yes! Feh is working for me :D) and the whole thing is going pretty smoothly. I'm really appreciating the dock's autohide function as it allows me to have gkrellm, wmdrawer, wmshutdown and bbrun on the desktop without them cluttering it up.  Apart from those I'm also using trayer (configured to be dynamic and tranparent) for a systray/notification area), tint2 for a tasklist, dclock (because it's funky), xfe for file management, xfw (xfilewriter) for text editing, xfi (xfileimage) for looking at pictures, ImageMagick for editing them (who'd have thought "display" was the launch command for that all along :o), exaile for listening to music (I'd have stuck with alsaplayer, but that doesn't have a systray icon and handy controls), vlc for watching video, gtk-chtheme for changing my gtk theme and many others.

Yay.

---

### Post by darkfox on 2009-01-10
Key bindings for special keys?

I've reverted to Openbox after a while away, having inherited a slow old laptop.
I use it with a plug-in keyboard and stand:  "Logitech Alto keyboard"
This thing has special keys to control volume and so on.

How can I find out the key value for these special keys?
Once I know this, how do I use them in my Openbox config?

---

### Post by Mark76 on 2009-01-10
Yay! A post. :D

I just wish I knew how to answer it :(

---

### Post by El_Belgicano on 2010-08-25
> **darkfox said:**
> Key bindings for special keys?

I've reverted to Openbox after a while away, having inherited a slow old laptop.
I use it with a plug-in keyboard and stand:  "Logitech Alto keyboard"
This thing has special keys to control volume and so on.

How can I find out the key value for these special keys?
Once I know this, how do I use them in my Openbox config?

This thread deserve to live...:p

I hope you've found an answer to your question by now, but here is what worked for the special keys of my laptop:

- Detection of the keycodes: terminal: "xev".

- Adding pairs keycode-action to the <keybindings> section in your rc.xml.

- Reconfigure OB.

- Done.

---------------

I've ran into something weird today, my rc.xml is set to keep the borders "on" when undecorated, so far so good, now, when setting margins to 40 at all four sides and maximizing, only the top border keeps appearing, when maximizing horizontally, the top and bottom ones appear but not the left and right ones, now, when maximizing vertically, all four sides have the border appearing.
At first I thought it could be so because of tint2 sitting on the top side, apparently I was wrong because setting tint2 on the left side didn't change anything.

So:
- I'd like to understand why the top one is appearing when the others are (or not) appearing depending of the kind of maximize I use.

- I'd like the left one to appear, so I can set tint2 on the left, how do I tell OB to do it the way I want?

Thanks in advance.

PS: If you feel the need for screenshots to better understand the situation, just ask for them, I'll probably have them posted by the next day.

---

