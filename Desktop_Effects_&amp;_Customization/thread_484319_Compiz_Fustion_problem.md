---
title: "Compiz Fustion problem"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by defrex on 2007-06-25
Hello,

I recently followed this thread to install Compiz Fusion:
[http://ubuntuforums.org/showthread.php?t=481615](http://ubuntuforums.org/showthread.php?t=481615)

Unfortunately, when I run compiz --replace, the top-left quadrant of my screen seems to be running Compiz Fusion fine, and the rest is a screenshot of what I turned it on (but without window borders).

I tried putting a new install on a spare partition (though I kept my /home), but ran into the same problem.

I'm using an nvidia card with the restricted drivers manager, and beryl runs fine.

---

### Post by imcc on 2007-06-25
I had a problem that involved the missing window borders. I didnt have the quadrant error. I also had the same problem in Beryl, so this fix is not 100% related.

I have an nvidia card, standard ubuntu install with gnome and the default nvidia driver. I'm using emerald themes.

compiz --replace &

followed by:

emerald --replace &

sorted it.

I have no idea what the '&' is for or if you need it. I'm very new to Ubuntu.

I also discovered you can add these commands to start up, by going to preferences > sessions, then adding those 2 commands. Now I have compiz running really smoothly and it starts up fine each time.

Before this I would boot into Ubuntu and compiz wasnt enabled and any attempt to activate it would loose my window decoration (borders and title bar).

Also if the graphics are really fubar then you can try ctrl-alt F2 to get back to shell, or ctrl-alt backspace to restart X.

Hope you get it working as compiz fusion is just so smooth and lovely.

---

### Post by Vorian on 2007-06-25
another thing you can do when you start CF is just run

```
compiz --replace -c emerald &
```

---

### Post by defrex on 2007-06-25
Thanks for the replies, however all of those seem to give me the same issue. Compiz Fusion does correctly render the window boarders, but only in the top-left quarter of the screen. I can also only see my mouse, or any kind of movement, really (including 3d cude switching), in that quadrant. It's rather odd...

---

### Post by Sushubh on 2007-06-25
compiz --replace -c emerald &

gives me compiz without titlebars. :(

---

### Post by defrex on 2007-06-25
Does compiz --replace alone? If it works, maybe you don't have emerald installed.

---

### Post by defrex on 2007-06-26
Just for the record, I solved my problem.  I deleted .beryl .emerald .compizconfig out of my home directory and restarted x. After that, it worked fine.

---

### Post by Sushubh on 2007-06-26
what exactly are emarald and metacity?

---

### Post by Depressed Man on 2007-06-26
Window managers. They&#341;e basically most of the GUI (graphical user interface) that allows people to click an X to close a window, a - to minimize, and more. Quite painful when you have to use the terminal and your not use to it (I learned that myself lol)

---

### Post by xpod on 2007-06-26
> what exactly are emarald and metacity?

It gets worse.....or of course "better" depending on your point of view:p
[http://xwinman.org/](http://xwinman.org/)

---

### Post by Sushubh on 2007-06-26
umm so how are they different to compiz/beryl? are they not window managers?

---

### Post by forrestcupp on 2007-06-26
For nvidia problems, did you try:
```
compiz --indirect-rendering --replace
```

---

### Post by ForumUser1234567890 on 2008-02-08
Hello. Just to let anyone know that I had a similar problem to this and I managed to solve it.

I was having the problem of only being able to see the top left quarter or quadrant of the screen, and managed to solve it by changing two settings in the 
CompizConfig Settings Manager (listed as Advanced Desktop Settings under Preferences in Gnome).
The two settings were

in General Options>Display Settings

changing Sync to VBlank to checked from unchecked,
and Detect Outputs to checked from unchecked.

---

