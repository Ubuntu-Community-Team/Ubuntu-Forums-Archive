---
title: "Mate 1.6 Desktop Icons"
date: 2013-05-23
forum: Desktop Environments
---

### Post by MikeFranklet on 2013-05-23
I've tried the standard methods to remove the default desktop icons (home, computer, trash, volumes). I used dconf-editor to uncheck the values in org.mate.caja.desktop, and although they were unchecked, no changes took effect. I also tried using the gsettings command in the terminal to manually set the values to false. That didn't work either, restarting didn't make any changes take effect.

So I'm stuck with the computer, home, trash, and volume icons on the desktop. Any idea why these methods aren't working? The keys are valid, for sure, because when I mistype them, the terminal is quick to let me know, so I know I've changed the keys to false. It's almost as though they're dummy keys and the real ones are somewhere else, but I don't know. In mate 1.6 gsettings/dconf is the only settings editor supposed to be used so I have no idea what to do.

---

### Post by galgalesh on 2013-05-23
This might be a dumb answer, but have you tried logging off-on again?

---

### Post by sirius10 on 2013-06-02
I'm also very interested in this.
I have installed yesterday MATE 1.6.0  (on Ubuntu 12.04) and want to get rid of those icons appeared automatically (My Computer, Home and Trash) that I don't need/have moved on the upper panel. 
I found somewhere that I can edit something in Configuration editor, Apps, Caja. The problem is I don't have any Caja in Apps.
What can I do? Help, please! I like Mate, would have installed it sooner if I knew it existed, but I like a cleaner/clearer desktop without any default icons on it.

---

### Post by Frogs Hair on 2013-06-02
A search indicates Mate has a configuration application named " MateConf editor."

---

### Post by sirius10 on 2013-06-02
It appears that can't be installed anymore as it is not available now. And I don't know what to modify in gconf editor.
Anyone met this problem or knows something about it...?

---

### Post by Frogs Hair on 2013-06-02
The package was replaced with  Gsettings . > **Dropped packages:**
[COLOR=#373737][FONT=Helvetica Neue]Replaced MateConf with GSettings[/FONT][/COLOR]

[http://mate-desktop.org/2013/04/02/mate-1-6-released/](http://mate-desktop.org/2013/04/02/mate-1-6-released/)

---

