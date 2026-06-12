---
title: "Openbox not running my Autostart.sh"
date: 2010-01-19
forum: Desktop Environments
---

### Post by HangukMiguk on 2010-01-19
Yes, I've set it to execute, yes it's located at ~/.config/openbox/autostart.sh

Here's the autostart.sh:

xset m 0 7 &
.HOME/.fehbg &
tint2 &
wicd-monitor &
conky &
pidgin &

Pidgin starts, conky doesn't, tint2 starts, wicd doesn't show up in the tray, feh doesn't load my wallpaper (but a default linux mint wallpaper does load...every time, have to reset my wallpaper), and my cursor moves at blinding speed.

What is up with this?

EDIT: this is still happening.  I have even moved it over to /etc/xdg/openbox/autostart.sh, set it as executable, and it doesn't work.

---

### Post by HangukMiguk on 2010-03-10
Bump with new info on what I've done to troubleshoot.  Still happening, this is really annoying when I have to reboot Openbox.

---

### Post by hhh on 2010-03-10
Have you tried adding the commands to autostart.sh one by one and seeing which one is choking it?

-edit- BTW, for wallpaper with FEH I use this in autostart.sh...
```
eval `cat $HOME/.fehbg` &
```

---

### Post by HangukMiguk on 2010-03-10
Well the thing that I'm questioning, is that it still loads a default mint wallpaper every time.  this is saying to me that openbox is getting its settings from elsewhere.

is that possible?

---

### Post by hhh on 2010-03-10
Sure it's possible, if you're using Openbox in conjunction with a desktop environment like Gnome. If you log out, what session does it show you logging into?

---

### Post by Jose Catre-Vandis on 2010-03-10
try the full paths to applications as well

---

### Post by kerry_s on 2010-03-10
it's a delay issue, most *box's have it.
you need to put a sleep on the ones that are missing, whats happening is the background is covering them.

xset m 0 7 &
cat $HOME/.fehbg &
tint2 &
sleep 3;wicd-client &
sleep 4;conky &
pidgin &

you can play with the time, wicd needs the panel fully loaded & conky has to come after the background is done.

---

### Post by hhh on 2010-03-10
> **kerry_s said:**
> sleep 3;wicd-monitor &
sleep 4;conky &
That works? I've never seen that, I've only seen...
```
(sleep 3 && wicd-monitor) &
```
etc...

---

### Post by kerry_s on 2010-03-10
> **hhh said:**
> That works? I've never seen that, I've only seen...
```
(sleep 3 && wicd-monitor) &
```
etc...

maybe it all depends on what openbox uses in it's startup. my *box skills are really rusty. :lolflag:

that wicd-monitor command don't look right though, i think it should be just "wicd" or "wicd-client" ?

edit: looked up its "wicd-client &".

---

### Post by hhh on 2010-03-10
wicd-client &, right. Hope the original poster sees that.

---

### Post by MooPi on 2010-03-10
Have not used the commands you listed. My wall paper is set by this simple but rock solid command: ```
feh --bg-scale ~/.background/cosmos.jpg &
``` 
Just an option ?

---

### Post by HangukMiguk on 2010-03-11
> **hhh said:**
> Sure it's possible, if you're using Openbox in conjunction with a desktop environment like Gnome. If you log out, what session does it show you logging into?

Openbox Session.  I keep my Openbox vanilla style, no mixing and matching! lol

> **kerry_s said:**
> it's a delay issue, most *box's have it.
you need to put a sleep on the ones that are missing, whats happening is the background is covering them.

xset m 0 7 &
cat $HOME/.fehbg &
tint2 &
sleep 3;wicd-client &
sleep 4;conky &
pidgin &

you can play with the time, wicd needs the panel fully loaded & conky has to come after the background is done.
I'll try this.  That's probably it.  Especially the fact that I didn't put cat with feh.


> **hhh said:**
> wicd-client &, right. Hope the original poster sees that.

D'oh.  I can't believe I bonked that.  I even looked it up in obmenu, as that's how I've been loading it.



I'll let you know if this solves everything.

---

### Post by kerry_s on 2010-03-11
> **MooPi said:**
> Have not used the commands you listed. My wall paper is set by this simple but rock solid command: ```
feh --bg-scale ~/.background/cosmos.jpg &
``` 
Just an option ?

that's good if you don't want to use feh's gui to change the wallpaper, but feh is capable of doing more, like for instance a slide show background or fetching images from the net, etc....

---

### Post by HangukMiguk on 2010-03-11
> **kerry_s said:**
> that's good if you don't want to use feh's gui to change the wallpaper, but feh is capable of doing more, like for instance a slide show background or **fetching images from the net**, etc....

i had no clue that feh could do this as well, but i always used the dynamic way just so i wouldn't have to change my autostart.sh every time i changed my setup.

---

### Post by kerry_s on 2010-03-11
> **HangukMiguk said:**
> i had no clue that feh could do this as well, but i always used the dynamic way just so i wouldn't have to change my autostart.sh every time i changed my setup.

yeah, i think most people miss that in the man page.

---

### Post by HangukMiguk on 2010-03-11
Ok, not too far off now.  the wicd tray icon shows up in tint2 now, but no feh wallpaper, no conky yet.

EDIT: hhh's method of using feh in autostart worked like a charm.  Awesome!

Conky still isn't working.  I've got it set to (sleep 7 && conky) & and it still isn't loading.

But still...that's progress!

---

### Post by kerry_s on 2010-03-11
does conky start when you run it from terminal?

i think we forgot the " ' " around the feh command. it's hard to tell but i count 3 ' when i look at the command. see pic

---

