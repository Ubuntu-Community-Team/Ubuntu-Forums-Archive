---
title: "Lost my gnome panel, can't get it back."
date: 2010-07-03
forum: Desktop Environments
---

### Post by x-shaney-x on 2010-07-03
I tried the une/unity PPA to poke around at it.
While trying to get it working better with compiz I set unity to autostart with my gnome session rather then use the unity session and my gnome panel didn't appear (it wasn't hidden behind the unity panel but actually not loading at all).
I've since removed unity but still can't get my panel to work.
I've done the gconftool stuff to reset the panel settings but it hasn't helped.
One thing I noticed is that gconf > desktop > session > required_components only listed the window manager (usually includes the panel and file manager to).
I unset this and afterwards the panel WAS listed but it still isn't starting.

So at the moment the only way I can get my panel is to add it to autostart or manually launch it.

---

### Post by rykel on 2010-07-03
Not sure if this is what you are looking for, but I reset my Gnome-Panel using:

[INDENT][B]$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
[/B][/INDENT]
Hope that helps!

---

### Post by x-shaney-x on 2010-07-03
Thanks but that is one of the things I tried.
Running gnome-panel manually does bring back the original 2 panel layout, showing that the settings ARE reset but it's not doing it automatically so the problem must be elsewhere.

I really don't fancy deleting .gconf, too many other settings I don't want to mess with.

---

### Post by yossell on 2010-07-04
I'm not sure about gconftool - is it doing effectively the same thing as gconf-editor? I'm assuming it is more or less - but this may be wrong.

Anyway, opening gconf-editor up and going to
desktop > gnome > session

on the right-hand page does the value of 
required_components_list 
include 'panel'? If not, try adding it.

Note, that this is different from 
desktop > gnome > session > required_components

where the right hand panel should include the values set for your filemanager, panel and windowmanager.

I interpreted your post to be about that second area - though do check that the values here are set correctly.

---

### Post by x-shaney-x on 2010-07-04
I hadn't noticed the settings in session itself but indeed panel is listed.
Also, since I moved the gconf folder completely, it seems it is not related to anything in there.

Since it only happened after I installed unity I assume it was to do with that but I removed every trace of it I could find in my home folder.

I have since re-installed unity and tried it on my second user account.
There everything is working fine and the panel appears as normal when returning to the gnome session.

---

### Post by yossell on 2010-07-04
hm - I am at a bit of a loss.

Just for clarity, just so we can rule it out - when you said in your original post, `i unset this' what does this mean? The required components folder should have 3 things listed, one of which is panel, and the value of panel should be `gnome-panel'.

I think you probably know this, but I'm just want to make sure it's not the settings here that are the problem

---

### Post by x-shaney-x on 2010-07-04
When I mentioned unset, I couldn't remember the exact command but it was this:
[COLOR=#FF0000]***gconftool --recursive-unset  /apps/panel ***[/COLOR]

But like I said, I had moved the .gconf folder and let it create a new one so it most definitely WASN'T a gconf setting causing the problem.

However, the problem is fixed, if not resolved:

I tried logging into a failsafe gnome session, in which the panel appeared normally.
Afterwards I logged into my normal session and the panel is back.
Clearly the failsafe gnome session must have recreated a missing file somewhere.
Still no idea what was missing.

---

