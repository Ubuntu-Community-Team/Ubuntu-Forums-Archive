---
title: "Help me and help my eyes"
date: 2008-12-04
forum: Desktop Environments
---

### Post by mythmgn on 2008-12-04
I upgraded my ubuntu to 8.10 last week.
But,unfortunately,I can't get used to the default Chinese-font -- serf(Is it the name&#65311;)
The font makes my eyes tired.

How can i resume my 8.04's font? The default font of 8.04 is very very very comfortable for me

Can i degrade it by using some commands?

---

### Post by Zorael on 2008-12-04
Serif, sans-serif and monospace are "metafonts", if that makes sense. They're not *real* fonts, but rather an order of fonts listed in priority, defined in **~/.fonts.conf**. Here's an example:
```
<?xml version="1.0"?>

<fontconfig>
	<alias>
		<family>serif</family>
		<prefer>
			<family>Times New Roman</family>
			<family>DejaVu Serif</family>
			<family>Kochi Mincho</family>
			<family>Sazanami Mincho</family>
		</prefer>
	</alias>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>DejaVu Sans</family>
			<family>Kochi Gothic</family>
			<family>Sazanami Gothic</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>DejaVu Sans Mono</family>
			<family>Kochi Gothic</family>
			<family>Sazanami Gothic</family>
		</prefer>
	</alias>

	<match target="font" >
		<edit mode="assign" name="embeddedbitmap" >
		<bool>true</bool>
		</edit>
	</match>
</fontconfig>
```
Let's say I have this .fonts.conf file and my system wants to output a certain character - let's say **Ä** - in serif. Then it will first try **Times New Roman**, since it's the first one defined for serif. If that font does not have that character, it will go down the list to **DejaVu Serif**. Likewise, if DejaVu Serif lacks it, it will try **Kochi Mincho**.

The "embeddedbitmap" setting toggles whether **bitmap fonts** should be used for characters that support it. A bitmap font is basically a font that is defined [per pixel](http://upload.wikimedia.org/wikipedia/en/2/29/Original_Mac_fonts.png); they're the ones that look good (and only look good) in smaller sizes. Other, normal (vertex?) fonts are basically defined in shapes and curves, so while they look great even at huge sizes, they soon become fuzzy and illegible at smaller sizes. Likewise, bitmap fonts look good at smaller sizes, but become very blocky when you scale them up. [Comparison](http://www.utdallas.edu/~cantrell/online/font-comparison-A.gif).

Asian characters quickly become fuzzy if you have bitmaps disabled, or if you don't have any fonts with bitmaps defined (for serif/sans-serif/monospace). Furthermore, not all fonts *have* bitmaps. So you probably want to first enable bitmaps (with the setting there) and then find a good font or two that have bitmaps for your Chinese characters.

I generally put the "nicest" looking fonts up top (Times New Roman and DejaVu Serif). They generally lack bitmaps for my Japanese characters, so then I put fonts with good bitmaps below those (Kochi Mincho, Sazanami Mincho).


Try experimenting with that file (**~/.fonts.conf**), adding/removing fonts and enabling/disabling bitmaps. You should only need to save the file and open a new application to view the effects.


(To regenerate your fonts cache, if that is at all necessary, enter '**sudo fc-cache -fv**'.)

---

### Post by mythmgn on 2008-12-05
thank you,but i have done that
I have enable the bitmap emeded bitmap attribute.But the characters look fuzzy as well.

I'm so hopeless to get along with it.

These days,I'm considering whether I should degrade it to 8.04.
It worked good in version 8.04

---

### Post by Zorael on 2008-12-05
Could you post the contents of your .fonts.conf file then, please?

---

