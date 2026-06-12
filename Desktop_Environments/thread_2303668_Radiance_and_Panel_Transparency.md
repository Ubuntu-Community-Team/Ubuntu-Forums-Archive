---
title: "Radiance and Panel Transparency"
date: 2015-11-20
forum: Desktop Environments
---

### Post by Crimple on 2015-11-20
Hi.

I've been customizing Unity (in VirtualBox) and I much prefer the Radiance theme. The problem is that it turns the (top) panel white and when I set it to transparent the text shows sort of blurred, even when using Faenza icons which have Ambiance and Radiance options. I tried tweaking with Ravefinity themes and icons and it's the same.

[IMG]http://i.imgur.com/OyL49LK.png[/IMG]

[IMG]http://i.imgur.com/ONulP7T.png[/IMG]


[IMG]http://i.imgur.com/qKXy0kE.png[/IMG]

[IMG]http://i.imgur.com/WtPLhCE.png[/IMG]


The more readable snapshots are with Ambiance, which doesn't blur when the panel is transparent.
Is there a way of having windows and menus with Radiance but keeping the panel with the original black?

Thanks.

---

### Post by Copper Bezel on 2015-11-22
Interesting. I'd almost think that this was purely an effect of how transparency is being handled, but I use [Zukitwo]("http://gnome-look.org/content/show.php/Zukitwo?content=140562"), which is a light theme with a light panel and black text, and it doesn't create those artifacts around the text, even with transparency enabled. 

[IMG]https://dl.dropboxusercontent.com/u/17749392/Image%20Hosting%202015/11/Screenshot%20from%202015-11-22%2011%3A10%3A37.png[/IMG]

Radiance *does *create the same greebly garbage for me, though. I hate to suggest just using another theme entirely, but it's possible Radiance just isn't designed to properly accommodate that feature.

---

### Post by mc4man on 2015-11-22
It appears ambiance is light/white text with a dark/black border, radiance is dark/black text with a light/white border. The border is only apparent when panel heads toward the opposite of the border. By default radiance is a light panel, ambiance a dark panel, both are default affected by chosen Background image

In addition the panel is also affected if  using the "Background Color" override ('opacity > transparency'), again choosing a light color in ambiance or dark color in radiance will expose the effect.

---

### Post by Crimple on 2015-11-23
Many thanks to both.

---

### Post by Copper Bezel on 2015-11-23
I think mc4man is more right than I was. If I use a dark bg and dial down the opacity to complete transparency, I get the same ugly outline with Zukitwo. I think it really does all come down to how much contrast you have between the text color and the actual color of the panel once transparency is applied.

---

### Post by Crimple on 2015-11-23
It really is too bad because I do hate the omnipresent black. Maybe I could live with it in the windows but not on the menus as well.

---

### Post by Copper Bezel on 2015-11-23
Yeah, it's frustrating that the panel transparency feature is so incompletely implemented. I actually came here looking for a solution to a problem where it was simply rendering a thin strip of non-transparent panel at the bottom edge, but that seems to have gone away. Now I've just realized that a pile of artifacts I was getting under the panel was a result of using the Static Blur rather than the Active Blur in the Dash, which seems rather buglike. = /

I'm not sure at what point the transparency became a blend between the panel color and the dash color, instead of just making the panel transparent. I'm not sure how I feel about that.

---

### Post by mc4man on 2015-11-23
> **Copper Bezel said:**
> 

I'm not sure at what point the transparency became a blend between the panel color and the dash color, instead of just making the panel transparent. I'm not sure how I feel about that.
That happened a while ago, probably around the time the Dash started merging into the panel.
I had a bug on the fact that the custom "Background Color" also affected the panel as - 
1. it's not described as affecting the panel & the panel has it's own opacity setting
2. seems to be involved in preventing having a truly transparent panel, ie. you just see your Desktop background image with 'floating' text & icons

---

### Post by Copper Bezel on 2015-11-24
Yeah, I know. It makes design sense for those things to be combined in that way. The way they're referred to in the settings, and the counter-intuitive combinations of these effects, seems less well designed. And again, I really think it's fairly weird that the "static blur" option basically makes the transparent panel unusable. I can see how that result comes out of the way the system works, but it's also pretty clear that the developers didn't actually think through or test what would happen when those two features collided, and simply make the panel a special case of some kind.

Edit: Another more obvious one is much simpler and easier to encounter in the process of twiddling this particular set of dials - you simply can't have a very light color as the Dash color, because the icon descriptive text in the Dash is always white. Right now, my Dash color is quite light, favoring the readability of my clock and battery percentage in the panel (in their light-theme, dark-text color) over the readability of the icon text for applications I generally recognize by their icons rather than by their text. But if the panel text color and icon text color were linked to the Dash color, that wouldn't be a problem. And even opting not to manually set the Dash color but leave it connected to the wallpaper instead, a light wallpaper will have the same effect. Each feature is really being considered, first and foremost, on how it'll play when all of the others are set to default, including Ubuntu's (to me rather oppressive) dark theme and a <50% wallpaper.

Also notice that changing the opacity of the Dash color does have an effect, but that effect isn't directly changing the opacity of the Dash. And lighter colors are more opaque regardless of what they're overlaying, so that setting the Dash to white, whether its opacity is 255 or 0, the result is the same.

---

