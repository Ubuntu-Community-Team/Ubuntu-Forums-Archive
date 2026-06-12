---
title: "pekwm-a blessing for old pc/ few issues"
date: 2007-06-20
forum: Desktop Environments
---

### Post by ravisghosh on 2007-06-20
Looking for a sleek window manager, I tried xfce4, fluxbox, openbox, window maker, and ended up at pekwm. Pekwm seems to be the fastest among the ones I have tried on my old 1 GHz P-III/256 mb box. It takes only 5 mb or so. Its keyboard shortcuts are really great especially the way it icontifies windows and then those windows are not there in "alt+tab" menu. Also unlike other wm's, configuring pekwm is simple using text files. But it seems that interest in pekwm has gone down in the last 2 years. Since 2005, I do not see any post about pekwm in arch nor there are new themes in [http://www.hewphoria.com/](http://www.hewphoria.com/) newer than 2005.

I have a few issues with it.
1. Themes. There arent good themes for pekwm like *box. I'm really missing those. Is there a way to get those theme working in pekwm or are there places to look for themes apart from hewphoria. However, few themes downloaded from hewphoria do not work, e.g., r-box. Graphite, etc. It would be great if you guys can share the themes. 

2. If I place the themes in ~/.pekwm/themes/ then they do not appear in the root menu at all. However, if I copy them to /usr/share/pekwm/themes, then they do appear in the root menu and work. I have tried to change the path in config file to ~/.pekwm/themes, but still they dont work.

3. Background. Presently, I have put "fbsetbg -r path/to/folder" in my start file to get a random background. but I want to get rid of fluxbox completely and in that case fbsetbg will be gone. Is there a way to use feh directly to get random background when pekwm starts without being dependent on other programs. I do not need any icons or desktop and hence using rox, etc., to manage desktop will be waste of memory.

4. Mouse button. I use left hand for handling mouse. Could someone guide me how to change the mouse buttons on pekwm. On my xfce4 desktop, I use left-handed mouse. Interesting thing is that if i start rox or thunar from pekwm, my mouse becomes left-handed and also keyboard commands set on xfce4 start working. Thats good thing but soon I am going to get rid of xfce4 too and hence need to do all the keyboard shortcuts and mouse buttong change natively. Could someone please shed light on why it happens when I start rox/thunar.

5. Whats the command to show desktop?

6. To start a wine application, I added the following line in keys and menu respectively.
    KeyPress = "Ctrl Shift 1" { Actions = "Exec wine "c:\\program files\\amibroker\\broker.exe &" }

    Entry = "Amibroker" { Actions = "Exec wine "c:\\program files\\amibroker\\broker.exe" }

Although the command is fine and works on console, they do not work from menu or using the shortcut keys. Any idea about this.

7. Is there a way to start pekwm other than startx like startxfce4 for xfce4?

Also, do put in your suggestions to enrich pekwm and your opinion about it in comparison to others.

---

### Post by urukrama on 2007-06-21
I've never used pekwm, but do you only use it because it is light? Openbox uses between 3-6 MB on my system, and is still active in development. Fluxbox too runs very lightly

For the background, you can use feh. To set a background use:

```
feh --bg-scale /path/to/image
```

Then add this to your autostart menu: 

```
eval `cat $HOME/.fehbg` &
```

(Feh stores the last background in .fehbg)

I don't know about the wine applications, but in Openbox I use the following command:
```
wine "/home/USERNAME/.wine/Program Files/PROGRAM"
```

---

### Post by ravisghosh on 2007-06-23
I too played a lil with fluxbox, but if u use pekwm, you would just fall in love with it especially the keyboard support although themes is something that i really miss. 

Got the fix for wine thing, just need to use ' instead of "

also for background, I have put "nitrogen /path/to/folder" in start file after installing nitrogen.

---

