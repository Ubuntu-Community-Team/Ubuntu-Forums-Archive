---
title: "Non-transparent window title bar in Maverick"
date: 2010-10-12
forum: Desktop Environments
---

### Post by coffeecat on 2010-10-12
I must admit, I've only just noticed this. In Lucid, there is a pleasant semi-transparency to the title bar of unfocussed windows - see my first screenshot. In Maverick I am getting (on three different machines) totally opaque unfocussed windows even with the same compiz settings. See second screenshot.

In Lucid I notice that the transparency affects other 3rd party themes, so this can't be a theme-specific feature. I've posted the two screenshots with the Ambiance theme set in order to make everything as similar as possible in the two. I've been testing Maverick since alpha and I'm sure the window title bars used to be transparent - in fact more so than in Lucid at one time. 

The Maverick terminal is still transparent - this seems to be affecting themes only.

Any ideas? Did anyone else see transparency during Maverick testing, or am I misremembering?

---

### Post by mcduck on 2010-10-12
Simple fix :)

Hit Alt-F2 and run "gconf-editor". Use that to browse to apps/gwd and set the *metacity_theme_active_opacity* and *metacity_theme_opacity* to suit your taste.

The values are between 0 and 1, 0 being fully transparent and 1 fully opaque. The toggleable "*shade_opacity*" options change between making the whole titlebar transparent and creating a fade from opaque to the set transparency.

(I believe the default values in Lucid were 0,75 for *metacity_theme_opacity* and 1 for *metacity_theme_active_opacity*, shade_opacity enabled for both.)

---

### Post by coffeecat on 2010-10-12
> **mcduck said:**
> Simple fix :)

I'm glad to hear it! :p

Thanks for that. Perfect. I thought it might be in gconf somewhere but didn't fancy rummaging around for it. I wouldn't have found that anyway. Which leaves the question: why did they change it for Maverick? It's a nice elegant and subtle effect which harms no one and which you can switch off by disabling compiz. Strange.

I'll check the actual settings in Lucid next time I use it, but now I know how to adjust it to my preference. Thanks once again!

---

### Post by KamiKazeKenji on 2010-10-13
Thank you very much for this. I missed the transparency!

---

### Post by karmila on 2010-10-23
I was thinking about this too. I'm using MM since Beta at my PC and metacity title bar was transparent for inactive window. Then I Changed window manager at my PC to emerald (so i don't know about this issue on my PC)

When MM final is released I installed it on my notebook and got no transparency. I was thinking that was a feature or an hardware related problem :). 

Now I have got the fix, thanks.

---

