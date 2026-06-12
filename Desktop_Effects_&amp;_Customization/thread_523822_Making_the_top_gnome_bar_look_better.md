---
title: "Making the top gnome bar look better?"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by quadomatic on 2007-08-12
I recently got Compiz Fusion working, and I'm not customizing the look of the desktop to look better...

The top GNOME bar really stands out, and I was wondering if anyone knew whether there was a way to make it looks better with the rest of the desktop.

Thanks

---

### Post by ubuntu27 on 2007-08-12
Hello quadomatic. :)
How about posting a screenshot of your desktop. :)

---

### Post by quadomatic on 2007-08-12
> **ubuntu27 said:**
> Hello quadomatic. :)
How about posting a screenshot of your desktop. :)

[[IMG]http://img67.imageshack.us/img67/3071/screenshot1tu8.th.png[/IMG]](http://img67.imageshack.us/my.php?image=screenshot1tu8.png)

Thanks

---

### Post by kazamx on 2007-08-12
What about making the bar blend in with your desktop?

Right click the bar - properties - background - select solid color. 

Now your desktop and the bar become one :-)

---

### Post by isaacj87 on 2007-08-12
You can try gnome-look.org...they have some nice transparent bars that you can you...I personally just set my bar to transparent. have a look.

---

### Post by tadada on 2007-08-12
you could always adjust the transparency to make it disapear into the desktop a little bit =]

---

### Post by AndrewGene on 2007-08-12
Or you could always autohide your bar and have a dock at the bottom...

---

### Post by petit.padavoine on 2007-08-12
Get rid of the panel altogether :D

---

### Post by petit.padavoine on 2007-08-12
Andrew: how do you get the panel to autohide so well? If I autohide mine, I can still see the bottom of the panel sticking out and it looks really ugly.

---

### Post by quadomatic on 2007-08-12
> **isaacj87 said:**
> You can try gnome-look.org...they have some nice transparent bars that you can you...I personally just set my bar to transparent. have a look.

What's that dock you're using? Avant? Mine doesn't look like that...

BTW: I think I got the top bar just how I like it. I changed to a Vista-ish emerald theme. How do I remove the drop shadow from the top bar though?

---

### Post by isaacj87 on 2007-08-12
Yes, it's avant...what version do you have?

---

### Post by quadomatic on 2007-08-12
> **isaacj87 said:**
> Yes, it's avant...what version do you have?

Lemme check...

avant-window-navigator-svn 0.1.2-svn240-1

It says the newest version is 0.1.2-svnrevisions-1...can I just update? I THINK I followed this guide, but I'm not positive

[http://ubuntuforums.org/showthread.php?t=385981&highlight=avant](http://ubuntuforums.org/showthread.php?t=385981&highlight=avant)

---

### Post by quadomatic on 2007-08-12
Never mind, I figured out which Avant I needed for the 3D angle. It looks pretty nice.

---

### Post by AndrewGene on 2007-08-13
> **petit.padavoine said:**
> Andrew: how do you get the panel to autohide so well? If I autohide mine, I can still see the bottom of the panel sticking out and it looks really ugly.

Press alt-f2 and type gconf-editor...
apps->panel->toplevels->top_panel_screen0 and set auto_hide_size to 0

enjoy.  It is nice 'cause my CF theme puts a glow around the gnome panel still....It gives my desktop a little shine.

---

### Post by petit.padavoine on 2007-08-15
Neat!

I got rid of the glow that compiz fusion added so that it wouldn't stick out but I'm gonna see what it looks like your way.

Anyway, now that I got rid of the glow, my panel looks nice if it's totally transparent, even if it's not hidden.

---

### Post by alex_anthony on 2007-08-15
if you fine a nice and well made system theme, it will include a style for the panel. Selecting menus looks better. I have transparency and Murrina Dash of Blue from gnome-look.org (requires murrine engine (in repos))

---

### Post by simianstyle on 2007-08-15
> **petit.padavoine said:**
> Neat!

I got rid of the glow that compiz fusion added so that it wouldn't stick out but I'm gonna see what it looks like your way.

Anyway, now that I got rid of the glow, my panel looks nice if it's totally transparent, even if it's not hidden.

How did you get rid of the glow? I can't seem to find that setting, there's still a drop shadow underneath my top panel and I want it gone. I'm using compiz-fusion with emerald as my window manager.

Any help would be appreciated. :)

---

### Post by saz on 2008-03-27
> **AndrewGene said:**
> Or you could always autohide your bar and have a dock at the bottom...

how can i get my bottom bar to look like yours???

---

### Post by rico4295 on 2008-03-28
read a post back about the panel shadow. try in advanced desktop settings / window decorations - shadow windows and put in `any & !(type=dock)`

---

### Post by VictorR on 2008-03-28
I found that the word "DOCK" must be in upper case, like
```
!(type=DOCK)
```

---

