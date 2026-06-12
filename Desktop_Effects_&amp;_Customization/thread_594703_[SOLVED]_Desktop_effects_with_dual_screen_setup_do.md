---
title: "[SOLVED] Desktop effects with dual screen setup doesn't work"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by honda on 2007-10-28
I have a nvidia fx5600 with dual screen crt + tv. I don't want to use twinview, because the tv is used only for mythtv and is normally not even turned on. I can't enable desktop effects from the menu, it just returns after a while saying that it's not possible to enable. I found out that I can enable compiz manually with:
compiz --only-current-screen
, then it works perfectly. But for some reason it doesn't work if I add this to the startup sessions. Anybody got any ideas how to make compiz start using this flag by default?

---

### Post by techstop on 2007-10-28
When I was running dual monitors on feisty, I used this script here;

[http://ubuntuforums.org/showthread.php?t=544145](http://ubuntuforums.org/showthread.php?t=544145)

Hope this helps...

---

### Post by honda on 2007-10-28
Thanks for the reply. I'm really not interested in running compiz on both screens, and it also seems as it wouldn't help even if I could start compiz successfully on both screens. 

The problem seems to be caused by the gutsy (sorry hadn't changed profile to gutsy user...) "desktop-effects manager". If I don't have desktop effects activated, I can run compiz --only-current-screen, and everything will work fine. But then 'it' recognizes that compiz is running and switches the setting to 'custom'. Next time I boot, 'it' will try to restart compiz WITHOUT the essential --only-current-screen, and fail, and swich the setting to 'none'... So in essence with compiz --only-current-screen as startup program I will have desktop effects every second time I log in...

So the big question is: How can I make the "ubuntu-automatic-compiz-start-program-thing" understand that compiz should be started only on screen 0? Or remove it completely so I can start compiz myself at startup?

---

### Post by honda on 2007-10-28
Found it!!!

I changed the last line in the file /usr/bin/compiz

from
${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS
to:
${COMPIZ_BIN_PATH}${COMPIZ_NAME} --only-current-screen $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS

Then I have what I want, compiz fusion only on screen 0.

EDIT: You will need Yendors fix below to have also, otherwise you won't have window decorations on the second screen. Not that it is needed for fullscreen video....

---

### Post by medeshago on 2007-11-04
But using that method leaves me with no window decoration in the TV and if I run "metacity --replace" in the second monitor, Metacity also replaces emerald in the first screen. 

Sorry for the noobness.

---

### Post by Yendor on 2007-11-08
Thank you honda, for finding this fix.  One more change is needed in the compiz file to have metacity run on the second monitor though:

Near the end of the file (just a few lines above honda's fix), find:
```
verbose "Starting gtk-window-decorator\n"
${COMPIZ_BIN_PATH}gtk-window-decorator --replace &
```

and add the line in between:
```
verbose "Starting gtk-window-decorator\n"
metacity --replace &
${COMPIZ_BIN_PATH}gtk-window-decorator --replace &
```

Now you have compiz running on your main display with no delay when right-clicking or opening menus, and you have window decorations on your second display.

I don't have a clue if it works for emerald or kde though.

---

### Post by honda on 2007-11-08
That's nice. When I come to think about it, I really don't know if I have window decorations on the second screen, since I only run mythTv fullscreen on it... I'll check if I need that fix also.

---

### Post by honda on 2007-11-10
Yes I definitely need Yendors fix to have window decorations on the second screen. Thank you!

---

