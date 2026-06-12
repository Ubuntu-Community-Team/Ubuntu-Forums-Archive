---
title: "Changing gtk slider color on scrollbar hover"
date: 2010-09-12
forum: Desktop Environments
---

### Post by Calimo on 2010-09-12
Hello,

I'm using the Human-Clearlooks theme on Lucid (Gnome) with compiz/nvidia driver.

I'd like to have the scrollbar sliders a bit (only) more visible. Ideally, it would switch orange when I hover it with the mouse, and stay gray otherwise. 
This is because my screen is quite large, and when the slider is small I find it difficult to find its position.

1. I opened the gtkrc file and set colorize_scrollbar = TRUE in the engine "clearlooks" block. Now the scrollbar sliders are always orange. I'd really like to have them orange only on hover.

2. There is a "clearlooks-scrollbar" style. I tried adding (fg|bg|base|text)[…] in it. I found that:
[INDENT]A. fg[…] is for the arrow within the top and bottom square boxes
B. bg[NORMAL] and bg[INSENSITIVE] define the color of the box containing the arrow (or if colorize_scrollbar = FALSE, the color of the whole scrollbar, including the square boxes and the slider itself)
C. bg[PRELIGHT] is the color of the box containing the arrow when hovered
D. bg[SELECTED] is the color of the slider (permanent)[/INDENT]

As it was most unsuccessful, I tried to force the murrine engine for the scrollbars only. Now with bg[PRELIGHT] = @selected_bg_color I get something fairly close to my expectations. 

Only I'd like the bar to be pre-lighted not only when the mouse is over the slider, but as soon as it is over the scrollbar. 
Here I must say I'm at loss, and I really can't find how to do it.

So, do you have any idea how to change the slider color on scrollbar hover? 

Thanks,
Calimo

---

### Post by JBAlaska on 2010-09-12
Unless you really want to do it "By Hand" try:
```
sudo apt-get install gnome-color-chooser
```

Very handy little app.

---

### Post by Calimo on 2010-09-12
Thanks for your answer.

I tried it&#8230; it's a really fine tool, but I still don't know what to change. :(
There are a few scrollbar colour and size settings in the "Specific" tab, but nothing to change the hovered scrollbar colour. Also I could change the details of rendering engine for the scrollbars, but I couldn't find a setting doing precisely what I want.

Can you please provide me with more precise instructions, or does that mean it's not possible to do precisely what I want?

Cheers,
Calimo

---

### Post by jgraham909 on 2011-04-17
> **Calimo said:**
> Thanks for your answer.

I tried it… it's a really fine tool, but I still don't know what to change. :(


This looks like an older issue so hopefully this will be useful for someone else coming here.

After installing gnome-color-chooser select the "Specific" tab and then look for the section "scrollbars" click the color next to "normal" and "hover" choose the color(s) you want and make sure the checkbox next to each is selected. Then click the apply button. You may need to move your mouse over scroll bars in open windows for the color change to take effect.

---

### Post by Calimo on 2011-04-22
It's old, but sill unsolved so thanks for your answer! :D

In fact I had been looking in the "Engines" tab where there was a "Scrollbars" line, but I had overlooked this specific infos.

So I tried what you said. But unfortunately it has no effect :(
I can change the normal color and scrollbar width/height and see it take effect immediately in gedit. 

The "hover" option corresponds to bg[PRELIGHT]. Only the top and bottom boxes with the arrow change their color when hovered (same for the "button pressed" one). Not the slider.

Maybe I wasn't clear enough with my explanations? What I'd like to change is the slider, that is this thing inside the scrollbar that both indicate your scroll level and that move when you scroll with the mouse and that you can grab and move to scroll on the page… I'm not sure I'm clear? This thing that's orange in the capture below. I'd like it to be orange only when the scrollbar is hovered!

Thanks anyway for the try!

---

### Post by Copper Bezel on 2011-04-22
It might not be possible within this engine. At the same time, if you really want to keep this theme but change the behavior of the scrollbar prelight, you could replace the scrollbar sections in the gtkrc completely to use pixmaps, and then you could have a "hover" pixmap in orange for the scrolling handle like you want.

---

### Post by Calimo on 2011-05-07
Thanks Copper Bezel,

I have tried different engines. Murrine offers the most options, but none could do what I want.
I could create pixmaps, but this looks a bit overkill and even then I'm not sure it would really do what I want.

So I'll stay like that for the moment.

Cheers,
Calimo

---

