---
title: "How to get application logo at top left corner"
date: 2012-09-18
forum: Desktop Environments
---

### Post by luvshines on 2012-09-18
I am using Ubuntu 12.04 with Unity desktop.

The issue I have is that the window which opens for any application, like terminal, firefox etc don't show the icon for that application

I had posted a similar question in the past when I was on 10.10 with gnome

[http://ubuntuforums.org/showthread.php?t=1576605](http://ubuntuforums.org/showthread.php?t=1576605)

The solution that I had implemented in that thread is no longer working with Unity :(

Any ideaz how to achieve this ?

---

### Post by ShadowVegan on 2012-09-18
I don't fully understand your question but if you just want things to look like they did in older releases, you could select Gnome Classic when logging in to your user account.

---

### Post by luvshines on 2012-09-19
> **ShadowVegan said:**
> I don't fully understand your question but if you just want things to look like they did in older releases, you could select Gnome Classic when logging in to your user account.

Ah !! that is not what I meant. Unity is fine

To explain what I really meant, I have added screenshot of firefox for example.
Currently when I open firefox, it looks the one where the window's top left corner is missing the firefox icon (the first screenshot)

I want to change it to look like the second one. This is exactly what I did for gnome in the other thread I have mentioned

---

### Post by Frogs Hair on 2012-09-19
If there is a setting to accomplish that it is  in advanced settings or a third party application like Ubuntu Tweak or MyUnity. I am logged into XFCE which displays the icon as in your screen shot.

---

### Post by luvshines on 2012-09-19
> **Frogs Hair said:**
> If there is a setting to accomplish that it is  in advanced settings or a third party application like Ubuntu Tweak or MyUnity. I am logged into XFCE which displays the icon as in your screen shot.

I couldn't locate any setting for this in Ubuntu Tweak or MyUnity.
I don't think there is any particular setting unless one goes ahead and changes the theme xml file itself

---

### Post by luvshines on 2012-09-19
And it's done :guitar:

I was able to do it again for Ambiance theme in 12.04

Changed the /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml file

For those interested, this is what I did

Original code snippet
```
<draw_ops name="draw_title_text_normal">
  <title color="#333" x="10" y="(((height - title_height) / 2) `max` 0)+1"/>
  <title color="#333" x="10" y="(((height - title_height) / 2) `max` 0)-1"/>
  <title color="#333" x="9" y="(((height - title_height) / 2) `max` 0)"/>
  <title color="#333" x="11" y="(((height - title_height) / 2) `max` 0)"/>
  <title color="#dfdbd2" x="10" y="(((height - title_height) / 2) `max` 0)"/>
</draw_ops>

<draw_ops name="draw_title_text_unfocused">
  <title color="#333" x="10" y="(((height - title_height) / 2) `max` 0)+1"/>
  <title color="#333" x="10" y="(((height - title_height) / 2) `max` 0)-1"/>
  <title color="#333" x="9" y="(((height - title_height) / 2) `max` 0)"/>
  <title color="#333" x="11" y="(((height - title_height) / 2) `max` 0)"/>
  <title color="#807d78" x="10" y="(((height - title_height) / 2) `max` 0)"/>
</draw_ops>
```

Changed it to
```

<draw_ops name="draw_title_text_normal">
  <icon  x="0" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
  <title color="#333" x="mini_icon_width + 10" y="(((height - title_height) / 2) `max` 0)+1"/>
  <title color="#333" x="mini_icon_width + 10" y="(((height - title_height) / 2) `max` 0)-1"/>
  <title color="#333" x="mini_icon_width + 9" y="(((height - title_height) / 2) `max` 0)"/>
  <title color="#333" x="mini_icon_width + 11" y="(((height - title_height) / 2) `max` 0)"/>
  <title color="#dfdbd2" x="mini_icon_width + 10" y="(((height - title_height) / 2) `max` 0)"/>
</draw_ops>

<draw_ops name="draw_title_text_unfocused">
  <icon  x="0" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
  <title color="#333" x="mini_icon_width + 10" y="(((height - title_height) / 2) `max` 0)+1"/>
  <title color="#333" x="mini_icon_width + 10" y="(((height - title_height) / 2) `max` 0)-1"/>
  <title color="#333" x="mini_icon_width + 9" y="(((height - title_height) / 2) `max` 0)"/>
  <title color="#333" x="mini_icon_width + 11" y="(((height - title_height) / 2) `max` 0)"/>
  <title color="#807d78" x="mini_icon_width + 10" y="(((height - title_height) / 2) `max` 0)"/>
```

Note:
1. The file will require sudo to change
2. You may have to switch to another theme and then rever back to Ambiance for the changes to be effective

Attaching new screenshot showing icons for chrome and firefox

And am too happy to mark this SOLVED

---

