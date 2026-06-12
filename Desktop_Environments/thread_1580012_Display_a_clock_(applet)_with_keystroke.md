---
title: "Display a clock (applet?) with keystroke"
date: 2010-09-22
forum: Desktop Environments
---

### Post by shakma on 2010-09-22
Helloooo Forum!

Ok, so I'm trying to do something a little crazy with my netbook, and I'm looking for some sage advice.  Since I'm trying to maximize free screen space on my 10" netbook, I have top and bottom the panels auto-hide.  No problems there, and since I use a lot of keyboard shortcuts (some default, some custom) I don't even use the touchpad unless I absolutely have to.  My most common apps are shortcutted, and I've got Alt-F2 for everything else.  However, by hiding the top panel, I don't have a clock on the screen.  This is fine in essence, but when I want to know the time, I have to mouse up to the top of the screen.  Not *horrible*, but it goes against my nature!

So my question is:  Is there any way to make holding a key/combo display the time, then have it disappear when the key is released?  I would love for this to happen when I hold the windoze key, as it is currently unused.

(btw, my windoze key will soon be an Ubuntu key, thanks to the good people at System76 and their free sticker set:
[http://www.system76.com/article_info.php?articles_id=9](http://www.system76.com/article_info.php?articles_id=9)
Can't wait for them to arrive!)

I know how to add custom keyboard shortcuts, but other than launching a clock app, I have no idea how to make this happen, or if it's even possible.

Pipe dream, or real possibility?  Thanks in advance, and long live the ubuntuforums!

Peace.

P.S.  I'm a Gnome user.

---

### Post by roggenschrotbrot on 2010-09-22
compiz widget layer + screenlets, cairo-clock or conky would be the easiest way to accomplish this.

edit: if you don't use compiz you could still toggle cairo-clock via a script, or bind a key to
```
notify-send "Time:" "$(date)"
```
you might need to install libnotify-bin

edit2:
```
#!/bin/bash
if ! pgrep cairo-clock ; then
cairo-clock
else
pkill cairo-clock
fi
```
toggles cairo-clock

---

### Post by shakma on 2010-09-22
> **roggenschrotbrot said:**
> 

edit: if you don't use compiz you could still toggle cairo-clock via a script, or bind a key to
```
notify-send "Time:" "$(date)"
```
you might need to install libnotify-bin



This command bound to a key *almost* worked once I installed libnotify-bin.  However, I get a nice pop-up that actually says:

Time:
$(date)

See the attached screenshot.

This would be perfect... if it actually showed the current time.  What am I missing?  I don't use compiz on my little netbook, and I'm trying to keep it as sleek as I can. (Plus, the graphics rendering leaves something to be desired.)  I used cairo-dock briefly.  Looks great, but again, too mouse-clicky for me.  That simple little pop-up is exactly what I'm looking for.

Thanks for the great response.  I'm so close...

Peace.

---

### Post by cj.surrusco on 2010-09-22
Okay, here's my plan. You set up a gnome-terminal to open up with a keyboard shortcut (you can set it up to open with certain demensions if you wish) and have it run the command for the time. Then when you want to close the terminal, you just hit the ctrl+c.

A command you would want to set as a keyboard shortcut would be:
> gnome-terminal --geometry 56x3 -e "watch -n 1 date" 
That would open a 56x3 terminal with a command to have an updating time. 

Hope that helps.

---

### Post by shakma on 2010-09-22
Not bad, cj!  It definitely works as advertised... but it's not quite as "elegant" in appearance as the notification pop-up.  Plus, I was hoping to avoid the added keystroke to close it.

I did find a cool way to implement this, though, if anyone else is interested.  I just use the combo Crtl-Alt-C to run the command, then take my finger off Alt and hit Ctrl-C to close it!

Thanks again.  Still interested in actually getting the time to appear with roggen's method, too.

Peace.

---

### Post by kerry_s on 2010-09-22
```
zenity --info --text="$(date)"
```

**"man date"** for the many ways you can customise.


edit: just saw about the number of keystrokes.
so you got notify-send right?

```
notify-send "$(date)"
```

---

### Post by shakma on 2010-09-22
Hi Kerry,

Please see my screenshot in post #3.  My notification actually says "$(date)"
It doesn't actually display the time.  Any clue why this is?

Thanks for responding.

Peace.

---

### Post by kerry_s on 2010-09-23
the reason it didn't work is the extra "
mine don't have extras

```
notify-send "$(date +"%a %d %b, %l:%M %p")"
```

works here, see screenshot

with icon:
```
notify-send -i clock "$(date +"%a %d %b, %l:%M %p")"
```

---

### Post by shakma on 2010-09-23
> **kerry_s said:**
> the reason it didn't work is the extra "
mine don't have extras

```
notify-send "$(date +"%a %d %b, %l:%M %p")"
```

works here, see screenshot

:confused:

Ok, kerry.  don't leave just yet.  yours definitely works from the terminal, but now when I bind that to a key combo, I get nothing!  The code that didn't actually display the time was working with Win+T (and any other combo I tried), but yours seems to just not respond to any combo I try with it.  But it works EXACTLY as I'd like when I run the command in terminal.

Any ideas?  So very close...

---

### Post by kerry_s on 2010-09-23
looks like you need to put it in a script & call that.

since you know what the terminal is:

gedit ~/.time

put:
#!/bin/sh
notify-send -i clock "$(date +"%a %d %b, %l:%M %p")"

make it executable:
chmod +x ~/.time

for the shortcut you need to put the full path:
/home/you/.time

---

### Post by shakma on 2010-09-23
We have a winner!!!
:guitar:

kerry, you are the man.  as you can see in my screen shot, it is now just after midnight local time.  (w00t!  I just used the combo to check the time!!!  Feels so natural...)  I'm going to bed to dream sweet linux-flavored dreams.

God bless the forums; this dream of mine was realized in less than a day.  Plus, I learned a LOT in the process.

Thanks to all who responded. Again, kerry - you rock.

Peace.

---

### Post by kerry_s on 2010-09-23
=D> have a good nights sleep my friend.

---

