---
title: "Get rid of the shadow on my menu bar? [Kubuntu]"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by psycoshot on 2008-01-06
Hey'
Ok, I use kubuntu and I've gone to a white, clear theme.
So now I want my menu bar to be 100% clear and make it look like the icons are floating.
I've achieved that except for the shadow on top of the bar.
Anyone know how to get rid of that shadow?

Here are some screens.
[IMG]http://i215.photobucket.com/albums/cc18/psycoshot/screenbar1-1.png[/IMG]
[[COLOR="Lime"]And here is a link to my full desktop.[/COLOR]]("http://i215.photobucket.com/albums/cc18/psycoshot/screenbar1.png")

Cheers!

---

### Post by BBin on 2008-01-06
In gnome (if you have compizconfig-settings-manager installed) you go to ccsm (type in terminal or run window) -> Window decoration -> shadow windows -> Type in "!dock" and close.
Might be the same in kde, try it!

---

### Post by psycoshot on 2008-01-06
Ahhh yay! Wonderful.
Thanks so much!

---

### Post by _Stevie_ on 2008-02-14
that worked, but how can i make the shadow visible in the bar when the windows are minimized?

---

### Post by rouge568 on 2008-04-15
Sorry to resurrect a bit of an old thread, but I'm agreeing with _Stevie_. I want it so that my menu bar has a shadow most of the time, but none when there are maximized windows.

---

### Post by Zorael on 2008-04-16
I'm not sure I understand.

If you want Compiz to "ask" the Kicker panel if all windows are minimized and if so, draw shadows, then the answer is likely no. The !dock exclusion is an easy **rule**, but any other solutions would mean writing extra code into Compiz.

Don't your windows maximize over the shadow anyway?

---

### Post by Desmo UK on 2008-04-16
I have the same problem. Windows minimize under the shadow, so any shadow starts to obscure the top of the window. However, I'm happy to use the !dock option so I'll try that out tonight :)

---

