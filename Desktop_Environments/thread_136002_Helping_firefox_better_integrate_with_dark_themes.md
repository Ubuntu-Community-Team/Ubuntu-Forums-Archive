---
title: "Helping firefox better integrate with dark themes?"
date: 2006-02-25
forum: Desktop Environments
---

### Post by Zeroangel on 2006-02-25
Hey all,

I've installed the VistaBut gnome theme from gnome-look.org but am having a some difficulty getting firefox to fully cooperate with my theming system.

[img]http://www.kahkewistahaw.com/misc_images/ff-broken.png[/img]

The window at the bottom (foreground) shows how well the theming system works with an application, whereas the top window (background) shows how poorly it works with Firefox. 

Does anyone know how to set the font color on the menu bar to whatever the system menubar font color is?

---

### Post by Zeroangel on 2006-02-25
OK, I found this guide [ [http://www.mozilla.org/unix/customizing.html#ui](http://www.mozilla.org/unix/customizing.html#ui) ] on customizing mozilla/ff colors.

I went to the configuration URL [ about:config ] and added the value:
ui.menutext = #cccccc

When I closed out the browser and reopened it, the menu bar's font color was changed, unfortunatly the background and foreground color of the context-menu and menubar menus was also changed to #cccccc, making the text unreadable unless hovered over.

Time to do some more tampering with the ui.configs .

---

### Post by tk03759 on 2007-07-15
I have this problem too. Apparently so does: [http://ubuntuforums.org/showthread.php?t=481703&highlight=firefox+menubar+color+themes](http://ubuntuforums.org/showthread.php?t=481703&highlight=firefox+menubar+color+themes)

Did you figure out a fix?

---

### Post by picpak on 2007-07-18
Guess what guys...I have a fix!

1) Open up Nautilus and go to View > Show Hidden Files. Then go to .mozilla/firefox/xxxxxxxx.default/ (x = a random set of letters and numbers)/chrome.

2) Edit userChrome.css and place in it the following:

```
menupopup > menu, popup, menuitem {
color: black !important;
}
```

Save it and exit.

3) Restart Firefox, and you'll have readable menus. Special thanks to [this guide](http://studer.tv/newsweblog-detail.page?news.id=35) for showing me the way.

---

