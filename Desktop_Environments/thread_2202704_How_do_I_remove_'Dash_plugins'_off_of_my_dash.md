---
title: "How do I remove 'Dash plugins' off of my dash?"
date: 2014-01-30
forum: Desktop Environments
---

### Post by Jacob_Chang on 2014-01-30
I've been customizing a pilot Ubuntu image before 14.04 and have a whole list of customizations that I have done and will do. One of the things I want to accomplish but can't seem to overcome is  the 'Dash Plugins' display on the dash. I just want installed apps on my dash, and I've already removed the other lenses (files, music, shopping, etc), suggestions and so on. 

If you're not sure what I'm talking about, I attached a screenshot of what I want to remove, highlighted around a yellow box (sorry for the poor image quality, I had to resize the image for it to meet the requirements for attachments).
[CENTER][ATTACH=CONFIG]249941[/ATTACH]
[/CENTER]
 I've been using gsettings/dconf extensively, but cannot find this under any heading (if anything, it should be under somethng like 'com.canonical.unity'). Any idea on how to remove this? Thanks in advance.

---

### Post by Bibek on 2014-02-25
I am trying to do the same but i am not able to , anyone has any ideas about how to accomplish this ? Thanks

---

### Post by grahammechanical on 2014-02-25
I have never written a scope but if I knew how to write one I may also find out how to remove a scope. From the scope tutorial.

> [COLOR=#333333][FONT=Ubuntu]The .scope file will be installed into the same prefix as Unity, which will generally be[/FONT][/COLOR]*/usr/share/unity/scopes/masterscope/myscope.scope*[COLOR=#333333][FONT=Ubuntu]. Notice that if the scope is a master one, it will have a top-level directory under the */scopes folder. In our case, the scope will be under the graphics scope, so it will be installed in[/FONT][/COLOR]*/usr/share/unity/scopes/graphics/openclipart.scope*

[http://developer.ubuntu.com/scopes/tutorial/](http://developer.ubuntu.com/scopes/tutorial/)

---

