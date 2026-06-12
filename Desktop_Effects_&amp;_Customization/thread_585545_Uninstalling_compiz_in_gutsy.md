---
title: "Uninstalling compiz in gutsy"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by Hitnrun on 2007-10-21
compiz is beautiful, but I don't want it. I want my computer fast and reliable.

So I uninstalled compiz, and after restarting I don't get any window decorations.

After some hours of investigation, I found that even after I uninstalled compiz, gdm tries to call it.

Calling gnome-wm, I get:

# gnome-wm 
exec: 140: /usr/bin/compiz: not found

Reading the gnome-wm script, I found that there is a gconf key to set this:

/desktop/gnome/applications/window_manager/default

I changed it to metacity and it worked, but this is a per user setting. I don't want to do this for all users.

Looking ahead on the script, I found:

> 
# If not exist, set to compiz.
if [ ! -x "$DEFWM" ]; then
    gconftool-2 -s /desktop/gnome/applications/window_manager/default /usr/bin/compiz --type string
    DEFWM=/usr/bin/compiz
fi


But I uninstalled compiz how can an script be fixed to a window manager that maybe don't even exists! This is a terrible design decision, totally different from what we are used in linux.

Is there a way to set the default window manager as default to metacity for the whole system?

---

### Post by FuturePilot on 2007-10-21
You don't need to uninstall it if you don't want to use it. Just go System>Preferences>Appearance. Click on the Visual Effects tab and select None. This is probably why you've lost the window boarders, because it's still set to run Compiz.

---

### Post by Hitnrun on 2007-10-21
I uninstalled it because even though I disabled it on this screen, when I rebooted it got back to what it was. It was running compiz, even if I disabled it.

I prefer to run more tried-and-true applications on my work computer.

---

### Post by Arthur Archnix on 2007-11-02
What happens when you just comment that whole section out?

---

### Post by crazybilly on 2007-11-03
Well, I did the same--I uninstalled compiz b/c I didn't want it taking up space on my small root partition. I uninstalled a lot of crap, pretty much anything that had 'compiz' in the name.

And now, I don't get any window decorations at all, including title bars. I also don't get the taskbar, or rather, my active windows dont' show up in it.  Since they don't have title bars, and I don't know they keyboard shortcut, I can't move windows around either. And things don't work quite right as far as window focus.

This is really strange to me.  I'm going to try reinstalling everythign I uninstalled...but I'm curious. Since I didn't have compiz running in the first place (my hardware won't support anything), why'd crap break when I uninstalled it?

I suppose this is more a rant than anything, huh?  Sorry about that.

---

### Post by Forlong on 2007-11-04
Post the output of ```
cat ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```

---

### Post by crazybilly on 2007-11-05
Well, I found my apt log (fortunately) and got everything reinstalled.  Gnome works right again.  Whew.

In any case, here's my output:

```
<?xml version="1.0"?>
<gconf>
        <entry name="current" mtime="1194237233" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
        <entry name="default" mtime="1194145653" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
</gconf>

```

Looks like compiz is my windows manager, huh?  Wierd. So all the fx just aren't turned on, then?

I just installed ccsm, the compiz config tool.  Seems to be the place to get this stuff figured out.

Thanks.

---

### Post by Forlong on 2007-11-05
Open the file in a text editor:
```
gedit ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```
and change ```
/usr/bin/compiz
``` (both) to ```
/usr/bin/metacity
``` (assuming you're on GNOME)

---

