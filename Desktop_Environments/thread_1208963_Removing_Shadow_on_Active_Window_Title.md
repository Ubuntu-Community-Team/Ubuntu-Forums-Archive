---
title: "Removing Shadow on Active Window Title?"
date: 2009-07-09
forum: Desktop Environments
---

### Post by deathblossom on 2009-07-09
Anyone know how to get rid of it? I'm sure it serves some sort of purpose, but it just makes the font look blurry and hard to read. I'd rather it be crisp and clear. I looked in Compiz for a way, but wasn't able to find it. 

I put a screenshot in to show what I mean.

---

### Post by wojox on 2009-07-09
The keys are stored in /apps/compiz/plugins/decoration/allscreens/options

---

### Post by deathblossom on 2009-07-09
Actually, I had to go into the metacity theme file for DarkRoom and erase two of the three focused title fonts. -_-;;

---

### Post by psylem on 2009-08-12
> **deathblossom said:**
> Actually, I had to go into the metacity theme file for DarkRoom and erase two of the three focused title fonts. -_-;;

Thanks for the hint, it's such a nice theme apart from that font shadow that makes me feel like I'm drunk. So in summary for others...

```
$ sudo nano /usr/share/themes/DarkRoom/metacity-1/metacity-theme-1.xml
```

Then customise the ```
<draw_ops name="title_text">
``` section, or alternatively, change this section...

```
<draw_ops name="title">
  <include name="title_text"/>
</draw_ops>
```

to this...

```
<draw_ops name="title">
  <include name="title_text_unfocused"/>
</draw_ops>
```

To give the focused title the same text style as the unfocused title (this is the safer option).

---

