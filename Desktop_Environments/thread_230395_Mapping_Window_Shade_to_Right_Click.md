---
title: "Mapping Window Shade to Right Click"
date: 2006-08-05
forum: Desktop Environments
---

### Post by one_stinky_bum on 2006-08-05
Hi there,

I would like to know if it is possible to map right-clicking on the titlebar to window shading. Right now it is mapped as <Ctrl><Alt>s in Compiz, and I tried to change it in the gconf-editor but it didn't take all the creative combinations of <Right-Click>,<right-click>, <RightClick> or <rightclick>.

Is there a way to map right clicking on the titlebar to window shading? I'm on 6.06 LTS with Compiz.

---

### Post by one_stinky_bum on 2006-08-07
Anyone know the gconf-editor string value for right click? Been searching for a while but I haven't come up with anything.

---

### Post by mcduck on 2006-08-07
I can't check that now as I'm at work, but I think it's <Button3> or perhaps just Button3 or something like that.

<Right> is the right arrow button on keyboard, and there sure wasn't any 'click' in the name for any button..

You could easily check that from gconf-editor, just browse through the settings and see what names are used for keyboard shortcuts that are activated with mouse. Rotate or Move, for example, as both use left mouse button.

---

### Post by one_stinky_bum on 2006-08-07
> **mcduck said:**
> perhaps just Button3 or something like that.

You rock! A complete howto:
Open a terminal, type gconf-editor. Then navigate as follows:
apps->compiz->general->allscreens->options
 Then under the "value column", of the toggle_window_shaded_button key, enter **Enabled**. Enter **Button3** for the toggle_window_shaded_key value.
Close gconf-editor and you're all set!

Again, thanks to the duck.

Edit: Oops - that seems to disable regular use of right click in compiz. Right clicking anywhere in a window results in a window shade and right click on desktop doesn't work. Working on a fix.

 [COLOR="Red"]**Edit2:**[/COLOR]Can't get it to work. Switched back to **<Control><Alt>s** for toggle_window_shaded_key value and  toggle_window_shaded_button key = **Disabled**

---

