---
title: "games inadvertently exiting fullscreen"
date: 2009-02-27
forum: Gaming &amp; Leisure
---

### Post by Geoffzx6r on 2009-02-27
my games are inadvertently exiting fullscreen as I'm gaming. I was just playing openarena and playing 10 minutes into the game I lose control of it and it goes into windowed mode and back to fullscreen. Except when it goes back to fullscreen it keeps flickering so I'm forced to quit. Other games I lose complete control of my mouse or control of the game and I'm forced to force quit the game.

I have no idea what's causing this. It seems weird. All I can think of is when something like this happens in windows it's because of a background process. Usually the instant messenger firing a message to me.

any help would be appreciated. Thanks:popcorn:

---

### Post by Mercedes300 on 2009-02-27
It is Compiz. either run games in windowed mode from jump, or run in Metacity when gaming.

Switch to Metacity:
```
metacity --replace &
```

Switch back to Compiz:
```
compiz --replace &
```

Hope that helps! :popcorn:

---

### Post by Montblanc_Kupo on 2009-02-27
As M3K said, it's probably Compiz conflicting with the game.

The solution I use is to create a separate user account for gaming. I don't have compiz enabled on the account, and I've got it stripped down to the barest minimum of running processes and services to maximize system memory.

---

### Post by Cappy on 2009-02-28
It's the screensaver/compiz. I used a script like this
```
killall gnome-screensaver && game_name && gnome-screensaver
```
as the problems occurs for me in metacity also.

---

### Post by grossaffe on 2009-02-28
> **Cappy said:**
> It's the screensaver/compiz. I used a script like this
```
killall gnome-screensaver && game_name && gnome-screensaver
```
as the problems occurs for me in metacity also.

so does that kill the screen saver, start the game, and then bring the screen saver back when the game is exited?

---

### Post by Geoffzx6r on 2009-02-28
ya, you guys are right. It's the screensaver. That would explain why it would do that at ten minutes all the time. I disabled the screensaver and everything is working. Thanks

---

