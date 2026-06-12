---
title: "Change alignment of title in metacity?"
date: 2006-10-30
forum: Desktop Environments
---

### Post by russianpirate on 2006-10-30
I was just always wondering if there was a way to change the alignment of the window title in metacity. It always bothers me since I like audacious to be shaded in the top and I've always been used to that. However, in the human theme the title is aligned to the center, so it annoys me to move audacious to the left right next to the control buttons.

Thanks in advance ;)

---

### Post by CatKiller on 2006-10-30
You could use [this page]("http://live.gnome.org/GnomeArt/Tutorials/MetacityThemes") and the metacity-theme-1.xml of themes with the title aligned differently as a guide to change the file in /usr/share/themes/Human/metacity-1 more to your liking.

---

### Post by russianpirate on 2006-10-31
I'm pretty sure that doesn't have alignment settings.. maybe it's possible by rewriting the whole layout but I don't really wanna do that. Any simpler program or guide/example how to do it? lol Thanks :D

---

### Post by CatKiller on 2006-10-31
> **russianpirate said:**
> I'm pretty sure that doesn't have alignment settings.. maybe it's possible by rewriting the whole layout but I don't really wanna do that. Any simpler program or guide/example how to do it? lol Thanks :D

I'm pretty sure it does. How do you imagine that some themes have the titlebar text aligned to the left and some have it centered if it doesn't actually get specified?

For example: ```
	<draw_ops name="DrawOp_TitleText">
		<clip x="0" y="0" width="width-8" height="height"/>
		<title color="#444444" x="TitleOffsetX + 1" y="(((height - title_height) / 2) `max` 0)+1"/>
		<title color="#FFFFFF" x="TitleOffsetX" y="((height - title_height) / 2) `max` 0"/>
	</draw_ops>
``` from SphereCrystal rather than ```
<draw_ops name="title_text">
  <title color="shade/gtk:bg[SELECTED]/0.75"
         x="(3 `max` (width-title_width)) / 2 + 1"
         y="(((height - title_height) / 2) `max` 0) + 2"/>
  <title color="shade/gtk:bg[SELECTED]/0.7"
         x="(3 `max` (width-title_width)) / 2 + 2"
         y="(((height - title_height) / 2) `max` 0) + 2"/>
  <title color="shade/gtk:bg[SELECTED]/0.4"
         x="(3 `max` (width-title_width)) / 2 + 1"
         y="(((height - title_height) / 2) `max` 0) + 1"/>
  <title color="#ffffff"
         x="(3 `max` (width-title_width)) / 2"
         y="(((height - title_height) / 2) `max` 0)"/>
</draw_ops>
``` in Human.

Now you're not going to find any easier tutorials from me, I'm afraid, since I don't care about any of this stuff. I'm happy to have it how the theme author designed it until such time as I feel the urge to learn how to make my own theme.

Either the alignment of the titlebar text bothers you enough to learn how to change it (in which case you do so) or it doesn't (in which case you ignore it). Either way, it's not a problem.

---

