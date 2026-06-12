---
title: "local background color of light text"
date: 2015-06-12
forum: Desktop Environments
---

### Post by chopra on 2015-06-12
Hi all,
I have an unusual issue with color.  I like terminals with black background and white text, but there was one disadvantage to the dark color; both broken links and files ending with .gz were colored red.  For a white background, or other color, the broken links had a black bar behind them, just like world writable directories, sticky directories, suid files, and sgid files, all have bars (green, blue, red, yellow.)  This black bar was also behind device files, as they're bright yellow.

At one point, after an update, the black bar changed to a darkish grey, allowing it to be seen.  I don't know how it happened, but it was great.  Now, it's gone.  I was playing around with the color settings for a secondary account I have, under edit > profile preferences > color from the terminal shell's menu.

Now, after changing things back, the grey bars have turned to black.  To show the difference, I've got a screen shot of the /dev directory for my main account (with the color scheme as it is supposed to be) and one of the secondary account, and as can be seen, the bars are only visible in one of them. What is the setting for something like this?  I tried background color, text color, palette, and nothing affected it.  Only if I change the background to some obscure color, like rust brown, does the bar change colors, to yellow or something.  But it's gone for the settings I like.

Chopra

---

### Post by ajgreeny on 2015-06-12
Which terminal and DE are you using; looks like gnome-terminal and unity, but difficult to tell for sure.

---

### Post by chopra on 2015-06-12
It's the gnome terminal, but I'm using compiz.  I did temporarily switch to unity to see if that changed things (I select from a drop-down menu on login), and the situation is the same.

---

### Post by ajgreeny on 2015-06-13
> **chopra said:**
> It's the gnome terminal, but I'm using compiz.  I did temporarily switch to unity to see if that changed things (I select from a drop-down menu on login), and the situation is the same.
I don't know what you mean by this; unity is dependent on compiz so even in unity you will have compiz as window manager.

Are you using the gnome classic desktop with gnome-panel etc etc, but also running it using compiz, not the standard metacity?

---

### Post by chopra on 2015-06-14
> **ajgreeny said:**
> I don't know what you mean by this; unity is dependent on compiz so even in unity you will have compiz as window manager.

Are you using the gnome classic desktop with gnome-panel etc etc, but also running it using compiz, not the standard metacity?

Yes, I'm using the classic gnome desktop, running with compiz, not metacity.

---

### Post by chopra on 2015-06-16
I did manage to fix the problem, with a sort of "hack".  I copied the

 ~/.gconf/apps/gnome-terminal//profiles/Default/%gconf.xml

file from my primary account to the corrupted one, while logged in to the primary account (using su -l to become the secondary user as necessary), overwriting the original file.
Then I rebooted and logged in to the secondary account, and the color settings were duplicated from the original account.

I had tried this before, but only when logged on as the secondary user, which prevented it from working.

I'm not sure if this warrants a bug report or not.  Entering the edit->profile preferences->color->built-in schemes:custom settings seems to prevent the colors from returning exactly to the way they were before, even if "use colors from system theme" is checked.

Chopra

---

