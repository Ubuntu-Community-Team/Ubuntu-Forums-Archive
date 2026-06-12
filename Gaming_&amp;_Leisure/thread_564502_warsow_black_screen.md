---
title: "warsow black screen"
date: 2007-10-01
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2007-10-01
When I try to start warsow, I get a message from my monitor that the display is not supported, and a black screen.  I can tell that the game is in the background because I can hear the sound, and mouse clicks on menu's, but I cant see anything.  All of my other games run just fine. Can anyone help?

Oh, and I have a widescreen monitor if that helps.

---

### Post by madsmeg on 2007-10-01
Try going into the warsow config file (~/warsow/basewsw/config.cfg) and changing the values of
```

seta vid_customheight "####"

seta vid_customwidth "####"

```

to somthing like 786 and 1024
this will start the resolution a little lower see if that will sort it (the current settings may be out of your monitors range

if that does not work try putting 
```

seta vid_fullscreen "#"

```

to 0

---

### Post by david.halliday on 2010-12-02
Hi, I have just tried warsow under Ubuntu 10.10 While this is an old thread it came up as a google search result to the problem so I'm adding a reply with my findings so next person who lands here has an extra hand.

I have a widescreen with an Nvidia card. The card (and screen) are fairly good so the default graphics "Very high" option was picked. Due to my screen I was in trouble like you with a blank screen.

There are some interesting features of X which came into play here. If you hold down "Ctrl" + "Alt" and tap "-" twice (in my case) the screen should reappear with warsow in the top left. From there go in and set some settings that will work on your screen then exit the application.

This will then create the configuration file: ~/.warsow/basewsw/config.cfg

Into which you can put your custom options as suggested by madsmeg

In my case:
```

seta vid_customheight "1050"
seta vid_customwidth "1680"

```

The key shortcut is for X allowing you to change the resolution on the fly.

---

