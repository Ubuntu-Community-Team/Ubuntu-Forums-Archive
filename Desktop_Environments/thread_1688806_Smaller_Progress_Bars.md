---
title: "Smaller Progress Bars"
date: 2011-02-15
forum: Desktop Environments
---

### Post by FearfulJesuit on 2011-02-15
Normally, I never post in the forums. Especially for something like this. But this kind of has me stumped. I am trying to reduce the size of progress bars on the ambiance themes. Check the image out. Those are the progress bars I'm trying to reduce.

[http://johan.kiviniemi.name/tmp/what-gtk]("http://johan.kiviniemi.name/tmp/what-gtk")

The width is too broad for my liking. Usually, this kind of stuff is handled by the gtkrc files. However, when I checked those out, I found that the GtkProgressBars line is commented out. Uncommenting those didn't do anything. Then I figured gconf-editor might have something and I tried changing the nautilus settings but couldn't find anything. Let me know if you guys have any ideas.

---

### Post by JOHNNYG713 on 2011-02-15
Did you try changing the parameters after uncommenting them ? Then save, swithch to another theme, and then back again, for changes to take effect

---

### Post by FearfulJesuit on 2011-02-17
Yeah, that was the first thing I tried. However, same size no changes. I even tried rebooting just to see if it would work but no dice. Why would they be commented in the first place if the theme is supposed to pay attention to it. They might be directly controlled within the murrine engine itself. I'm still searching but nothing of use so far.

---

### Post by Krytarik on 2011-02-17
The window in your screenshot doesn't really looks like "Ambiance", but like "Human-Clearlooks"?! See attached screenshot of "Ambiance".

And the dimensions of the progress bars look common to me, and imo there is not much an author of a theme can do about it. Are there major differences in the themes you know, regarding this?

---

### Post by Krytarik on 2011-02-22
I worked a bit with themes in the last days and noticed today that there is indeed a way to control the height of the progress bars, but unfortunately it's only possible to set a minimum height, so if the height of the bar is specified by an app and is set heigher than that, it doesn't affect it.

Those are the respective entries, they are usually set in the "default" style section of a theme's gtkrc file, or in the respective sub-section/-file:
```
GtkProgressBar::min-horizontal-bar-height    = XX
GtkProgressBar::min-vertical-bar-width       = XX

```[http://library.gnome.org/devel/gtk/unstable/GtkProgressBar.html#GtkProgressBar.style-properties](http://library.gnome.org/devel/gtk/unstable/GtkProgressBar.html#GtkProgressBar.style-properties)

---

### Post by FearfulJesuit on 2011-02-23
Krytarik,
I didn't know they were set by certain apps. I guess I'll keep that in mind. I remember setting those very parameters you mentioned but I remember it didn't do anything. But I'll keep testing with various apps to see which ones it affects. If I find anything else of relevance. I'll be sure to post it here. 

BTW, I just put up an image of the progress bars I wanted to change. So it was the first thing I found in a google image search of the topic. I guess I could have take a screen shot instead.

---

### Post by Krytarik on 2011-02-23
> **FearfulJesuit said:**
> 
BTW, I just put up an image of the progress bars I wanted to change. So it was the first thing I found in a google image search of the topic. I guess I could have take a screen shot instead.
Yeah, you should have done it. ;-) I believe we all know what progress bars are.

For example the screenshot I posted is -you may have guessed it- from Synaptic, it has a fixed/set height, whereas those in the sent email progress window of Thunderbird isn't set, there the minimum height setting gets used.

EDIT: Actually those in the "Installation progress" window of Synapic also isn't set, just saw it after posting, while applying the updates to get the update notifier disabled, after I tested the aforementioned.

---

