---
title: "KDE adjustments for Firefox"
date: 2006-05-14
forum: Desktop Environments
---

### Post by elamericano on 2006-05-14
I'm not sure if all of these are KDE issues or Firefox issues.

1) Firefox doesn't open new windows maximized anymore. At some point, playing with resolution and font size, I lost this and I can't get it back.

2) When I mouse over a link I get a cheesy pointing finger. I loaded a new KDE cursor theme, but the thing is still there. I never saw that in gnome.

3) I'd like to make the text in the menu and address bar bigger. Preferences only seems to make web page fonts bigger. KDE settings haven't affect Firefox, so far.

Updating to 3.5.1 and adding some KDE themes has made a world of difference. I just have a couple more adjustments that hopefully, I will be able to make. I'll ask those in a different thread, if I don't find it in a howto or by experimentation.

I hope someone has already overcome these FF issues, or has some general knowledge to share.

Thanks.

---

### Post by Neo Ex on 2006-05-14
[QUOTE=elamericano]I'm not sure if all of these are KDE issues or Firefox issues.

1) Firefox doesn't open new windows maximized anymore. At some point, playing with resolution and font size, I lost this and I can't get it back.
[/QUOTE]
You can try deleting your ~/.mozilla folder (maybe make a backup of it before), or you can do this:
Click on the Firefox icon in the window decoration -> Advanced -> Special window settings or Application special settings and choose to always start Firefox maximized.

> [...]
3) I'd like to make the text in the menu and address bar bigger. Preferences only seems to make web page fonts bigger. KDE settings haven't affect Firefox, so far.
KControl -> Look'n'Feel -> GTK styles and fonts.

---

### Post by elamericano on 2006-05-14
I deleted the ~/.mozilla folder. That was a good idea, but it had no effect.

Changing the gtk font worked, but the toolbar height didn't increase with it, so I returned to the original settings, bug the toolbars didn't return to their original size. They are still too small (see attached)

Man, things get screwed up with a little experimentation, and they don't go back.

---

### Post by GeneralZod on 2006-05-14
If I recall, there's something rather odd about Firefox's Menu etc fonts in that they can be manually adjusted by editing your userChrome.css.

Inside my ~/.mozilla/firefox/*<profile name>*/chrome/userChrome.css are these lines - you might want to try closing all instances of Firefox, tweaking the font-size, and seeing if it makes a difference.

```

/* If you have true type fonts enabled, you might want to add these lines
* to get good fonts for menu, toolbar, dialog boxes, etc.
*/
menubar, menubutton, menulist, menu, menuitem, textbox, toolbar, tab, tree, tooltip
{
font-family: Arial !important;
font-size: 10pt !important;
}


```

---

### Post by elamericano on 2006-05-15
I kneel before Zod, :mrgreen: 

I had tried to use their example chrome a bit, but only succeeded of changing the font size in the menus. I see you have a lot more controls to choose from. I will try to change as little as possible to get something that works for me. I suppose I should look at using a full theme too, but I've never seen one I liked.

I have been able to return to normal by uninstalling, deleting ~/.mozilla/firefox, and re-installing FF.

---

### Post by pbb on 2006-05-19
Okay, my problem was that the Firefox menu fonts were too *big*. The solution was quite simple (though difficult to find):

Go to about:config (type that in the address bar), then scroll down to browser.display.screen_resolution, and change this value to the current KDE resolution value (75 in my case).

Now the menu font should be the same size as in the other applications.

More info: [http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

---

### Post by pbb on 2006-05-19
Aw, I see now that this change also makes all text on webpages that is defined in real-life units (pt, mm) very small... :-(

---

### Post by D!mon on 2006-05-23
Have u fixed that 'cheesy finger'? I have the same problem..

---

### Post by pbb on 2006-05-23
Yes, I believe I have! You need to install "gnome-control-center", open it (from a terminal window) and go to Font > Details > Resolution, and set that to the same as your KDE resolution (KDE default is 75dpi). From now on, the font sizes set in this control panel will be the same as in KDE.

(Edit: it's gnome-control-center, not gnome-control-panel.)

---

### Post by pbb on 2006-05-23
Okay, I am getting so sick of Linux-quirks... Now it turns out that changes made with gnome-control-panel don't stay after a reboot! Rebooting my computer turns the Firefox menu-fonts back to their old big size.... ](*,) :???: :evil: :mad: :( :cry:

---

### Post by carrellt on 2006-05-29
Here is a solution that should solve the font problem in Firefox (and other Gnome-like programs).

     cd ~/.kde/Autostart
     ln -s  /usr/lib/control-center/gnome-settings-daemon

Now when you restart KDE, the fonts (and other settings) are loaded correctly.

I don't know if this is the ideal solution, but it works (so far).

---

### Post by pbb on 2006-05-30
Wow, thanks a lot, that worked for me!

---

### Post by James R. Phillips on 2006-11-14
I did something quite similar, and it worked well.  I browsed to ~/.kde/Autostart in konqueror, then used the context menu to create a new "shortcut to application", with the command being "gnome-settings-daemon".  Of course, the gnome-settings-daemon package must be installed.  Using the advanced properties button, turn off the lauch feedback button, to avoid an annoying button on the taskbar when it starts.

---

### Post by UncommonGuy on 2006-11-16
Thank you GeneralZod. This was driving me nuts but you nailed it with your userChrome solution. Firefox is usable again! I don't know why this was a problem on my laptop when I have the exact same setup (suse 10.1) on my home computer and had no problems. Ah well. 

I really appreciate it Zod.

--UncommonGuy

---

