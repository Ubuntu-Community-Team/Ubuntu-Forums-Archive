---
title: "Change Clock 2.26.0 font colour?"
date: 2010-02-22
forum: Desktop Environments
---

### Post by isee on 2010-02-22
Is it possible to change the font colour from black to white in the Clock?  I love my Ubuntu desktop, but the configuration of panels and icons I have leaves the Clock on my panel over a dark area (I've tried different panel locations).

If I could change the font colour to white I'd be able to make my panel completely transparent, as everything else is over light areas the black text is fine.  Just a vanity thing.  Plus I'd like to know how.

Thanks Much!

---

### Post by koleoptero on 2010-02-22
Run gconf-editor, and go to apps/panel/applets/clock_screen0/prefs there. It should have a color setting. (I can't check cause I'm not in gnome right now)

---

### Post by wojox on 2010-02-22
[http://www.linuxine.com/2008/07/trick-customize-clocks-font-colour-on-gnome.html](http://www.linuxine.com/2008/07/trick-customize-clocks-font-colour-on-gnome.html)

---

### Post by isee on 2010-02-22
koleoptero  I can't find a font colour setting in that file, but thank you very much for introducing me to that aspect of Clock.

wojox   Thanks for the link.  I really appreciate your responses!  I'll follow through soon.

:popcorn:Double salt Double butter to wojox.

---

### Post by isee on 2010-03-06
OK well I didn't have much luck with that.

I entered this into Edit Key under custom_format

<span color=”#FF0000&#8243;>96Y 96B 96d 96A</span><b>96H: 96M</b>

like it says in step 2 (copied and pasted into Edit Key from the web page.)

and then I used Edit Key in the format field to change it's value to custom like it says in step 3.

This is what appears in my panel when I make those changes -

<span color=”#FF0000&#8243;>2010 March 05 Friday</span><b>23: 36</b>Friday, 05 March 2010

aaarrrrrgggg   so close.

I can reset the values so it looks normal, but am I doing anything wrong?

---

### Post by stinkeye on 2010-03-06
You could just use gnome-color-chooser and set the font color for the panel.

---

### Post by isee on 2010-03-06
Thats pretty nifty stinkeye.  Changes all the panel fonts rather than just the clock, but it works for me!

Thanks! :D

---

### Post by stinkeye on 2010-03-06
No problem.
You might be interested in this thread which shows you how to change
the time format.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1375603[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1375603")

---

