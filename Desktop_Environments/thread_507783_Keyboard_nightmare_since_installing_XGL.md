---
title: "Keyboard nightmare since installing XGL"
date: 2007-07-23
forum: Desktop Environments
---

### Post by Spam Banjo on 2007-07-23
I'm probably being a big noob, but since installing XGL, my keyboard shortcuts are all over the place. Ctrl doesn't work, nor super (windows key). And kill session has been re-mapped to Shift+Backspace, as apposed to CTRL+ALT+Backspace.

So my questions are:

[LIST=1]
[*]Can I get CTRL to function normally??
[*]Can I swap the shortcuts back??
[*]Am I just being a noob or is this a common issue??
[/LIST]

I really want to run under XGL for Beryl on ATI card. It works beautifully and runs so well... It seems a shame to go all flat and lifeless just for 1 key on the keyboard.

BTW: Yes... The CTRL key works fine under GNOME & in Window$ Vist-eeeeeerrrr!!!!

Advanced thanks..!

---

### Post by gorgor_bay on 2007-07-23
I have exactly the same problem appearing today. Hopefully it's something that can be fixed easily because it is quite annoying. But so far I found absolutely no answer...
Also maybe it is a bug in compiz fusion because I don't remember any XGL update coming this morning, and all was working perfectly last week.

---

### Post by Spam Banjo on 2007-07-23
I do not have Compiz... I do however have Beryl.

The no CTRL problem appears anyway... without Beryl running, which leads me to believe that XGL is the problem, not Beryl.

---

### Post by Spam Banjo on 2007-07-23
This will fix the Shift & Backspace problem.

[INDENT]xmodmap /usr/share/xmodmap/xmodmap.uk[/INDENT]

Replace uk with us or whatever your national locale is.

You can add that little command to System>Preferences>Session>Startup to fix the keyboard layout on startup.

[COLOR="Red"]This did not however, fix my NO CTRL key issue.
STILL NEED HELP... BIG TIME!![/COLOR]

---

### Post by xMemphisx on 2007-07-23
I was actually about to start a topic asking about a lot of these same questions.

I have CompizFusion running on my laptop, and i had beryl before that, and before that i ran the generic Compiz. Well i had compiz on my desktop for a while, but because i have an ATI video card, i HAD to use an XGL session... is there any way around using an XGL session... and still getting compiz fusion working?

---

### Post by gorgor_bay on 2007-07-24
In fact I noticed that the crazy-ctrl-behaviour is also happening under Gnome for me... 
Seriously guys I've seen several other issues like that but no answer at all. Does this mean I'll have to reinstall my whole system ? Really looking for some help here...

---

### Post by Spam Banjo on 2007-07-24
> **xMemphisx said:**
> ...is there any way around using an XGL session... and still getting compiz fusion working?

This is all I have though about for the last 12 hours... There must be something for us. DAMN YOU ATI!!!

---

### Post by Soybean on 2007-07-24
For those using Fusion, have you tried the "Gnome keybindings" plugin? I believe it's installed by default, down at the bottom of the CompizConfig list, in the "Uncategorized" category. I'm not really sure what it does, but it could be related.

---

### Post by gorgor_bay on 2007-07-24
I've just tried gnome-keybidings plugin for compiz fusion.
What it does is freezing the computer, then, then only way to get out is to kill xorg manually. (ctrl+alt+backspace)
If I lauch compiz from a terminal with this plugin enabled, the windows losses its decoration and the two taskbars (top and bottom) of nautilus disappear, then nothing happens, the mouse can be moved but doesn't reacts to clicks, everything gets frozen just like when enabling the plugin while compiz is running.

---

### Post by gorgor_bay on 2007-07-25
I'm really looking for help, is there anybody out there ?

---

### Post by macabro22 on 2007-07-27
I used to have the same problem before. 
If it is what I am thinking, you guys also get ugly standard gnome icons and font in spite of whatever chosen on  art manager.
That had been solved before using a startup script when I had Compiz-Fusion installed from Trevino's repo.
Then I adventure installing compiz-fusion from GIT following this [http://fusioncast.blogspot.com](http://fusioncast.blogspot.com).
Now, compiz-fusion works great, with most of the newest plugins (havent fixed em all yet), but I can't startup using my old XGL script and I loose my keyboard shortcuts like you guys.

Here's what I currently have at my startup script:
```
#!/bin/sh
Xgl :1 -br -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
# Start Compiz window manager heliodor &
# Start GNOME 
sleep 3
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz --replace --sm-disable ccp &
exec dbus-launch --exit-with-session gnome-session &

```

Also, I get these error messages from my .Xsession-erros file when starting up with that script:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "htorres"
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
/home/macabro22/.Xsession: 13: gnome-window-decorator: not found
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
```

---

### Post by macabro22 on 2007-07-27
Doodes.

My problem is resolved by adding ```
gnome-settings-daemon
``` to the startup session.

System==>preferences==>Sessions.

Hope it works for you as well.

Cheers

---

