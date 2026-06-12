---
title: "Firefox clicking links sometimes become drag operations"
date: 2006-01-14
forum: Desktop Environments
---

### Post by stoffe on 2006-01-14
When clicking around in Firefox, now and then there's a small misinterpretation of what I'm trying to do or something, because the result is to both navigate to the intended place, but also leaving the mouse cursor holding a shortcut for the very same place.

This is highly annoying, because there doesn't seem to be any way to cancel this either, the only way to get rid of it is to click somewhere. In the browser, this has the effect of going to the url again, which sometimes is *very* unwanted, especially in AJAX-heavy environments or others that have volatile session data for instance. Clicking on desktop for instance puts a shortcut link there. And so on.

That behaviour does not exist in Firefox on Windows, for instance, so there is something special with either FF on Linux, or on Ubuntu, or some other combination around there. I suppose that what causes it is that I move the cursor during the click, which is interpreted as a "drag" operation. Probably, it's just too sensitive, and being more sensitive than under Windows.

This is nothing new, as far as I can remember it has been this way as long as I've had Ubuntu (since Warty) and I've just come to live with it (bad idea, I know). But other, non-technical people who are using my computer is also complaining about this, so I finally figured I'd try to get some answers.

I've tried to search both google, launchpad/malone and this forum, and some other places, but I don't seem to find the right keywords if it has already been answered.

So: anybody know what the problem is, and even more importantly, any solutions? Can I tweak the sensitivity somewhere? Who's the culprit? Should bugs be filed?

---

### Post by Zelut on 2006-01-14
I have the same issue on my notebook.  I had assumed it was due to sensitivity with my touchpad & my big hands :)

Any solution would be appreciated here as well.

---

### Post by mustang on 2006-01-15
I'm also having the same problem and find it just as annoying as the threadstarter. Any input would be appreciated.

---

### Post by DigitalDuality on 2006-01-15
May i join in the chorus here in this "feature's" obnoxiousness?

---

### Post by quonsar on 2006-01-15
ditto here. i just now went to System > Preferences > Mouse > Motion and increased the drag and drop threshhold. we'll see if that will help.

---

### Post by stoffe on 2006-01-15
[QUOTE=quonsar]ditto here. i just now went to System > Preferences > Mouse > Motion and increased the drag and drop threshhold. we'll see if that will help.[/QUOTE]
Good call, I had somehow missed that one. It's a bit hard to test though, I've been trying to "click around sloppily" and so far haven't been able to trigger the effect. I'll guess I'll just wait a while and see if the effect seems to have disappeared. Does anyone know for a fact if Firefox uses that treshold to determine if it's a drag or not, or if it has its own system?

If so, that value should probably be adjusted from the install. It was at 8 from the start, now I have it at 10 (max). The actual numerical value can be found as gconf key desktop/gnome/peripherials/mouse/drag_treshold.

---

### Post by DigitalDuality on 2006-01-15
I have no clue as to whether FF uses it or not, but i'm about to find out.  Settings changed and i'll see how it goes from here :)

---

### Post by aysiu on 2006-01-15
[QUOTE=stoffe]
This is highly annoying, because there doesn't seem to be any way to cancel this either, the only way to get rid of it is to click somewhere.[/quote] Press **Escape**

> 
That behaviour does not exist in Firefox on Windows, for instance, so there is something special with either FF on Linux, or on Ubuntu, or some other combination around there. It's a Gnome thing. This doesn't happen in KDE or XFCE.

---

### Post by stoffe on 2006-01-15
[QUOTE=aysiu]It's a Gnome thing. This doesn't happen in KDE or XFCE.[/QUOTE]
Ok, thanks for the info! Now, for remedies then...?

Found this bug: [https://launchpad.net/distros/ubuntu/+bug/28435](https://launchpad.net/distros/ubuntu/+bug/28435) which also references a recent entry on the mailing lists: [http://lists.ubuntu.com/archives/ubuntu-desktop/2006-January/000181.html](http://lists.ubuntu.com/archives/ubuntu-desktop/2006-January/000181.html)

If changing treshold helps, then it probably should be set differently from the install. Or if there is some other reason, I'd like it fixed. I've seen it on lots of different setups, both laptop and normal, so it may just be a crappy default. :)

---

### Post by stoffe on 2006-01-15
[QUOTE=aysiu]Press **Escape**[/QUOTE]
Bah. It happened again, and escape had no effect. :???:

---

### Post by punkrockguy318 on 2006-02-17
[QUOTE=stoffe]Ok, thanks for the info! Now, for remedies then...?

Found this bug: [https://launchpad.net/distros/ubuntu/+bug/28435](https://launchpad.net/distros/ubuntu/+bug/28435) which also references a recent entry on the mailing lists: [http://lists.ubuntu.com/archives/ubuntu-desktop/2006-January/000181.html](http://lists.ubuntu.com/archives/ubuntu-desktop/2006-January/000181.html)

If changing treshold helps, then it probably should be set differently from the install. Or if there is some other reason, I'd like it fixed. I've seen it on lots of different setups, both laptop and normal, so it may just be a crappy default. :)[/QUOTE]

The threshold doesn't have a difference.  Nothing should be dragging when your mouse isn't pressed down, regardless of the threshold.  This is a severely annoying bug!

---

### Post by /phil on 2006-04-23
Can anyone knowledgable help with this issue? I haven't been able to find a resolve either.

Is there a simple way to turn off drag and drop of url's in Gnome?

Thanks

---

