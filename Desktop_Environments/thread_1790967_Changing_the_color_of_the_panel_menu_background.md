---
title: "Changing the color of the panel menu background"
date: 2011-06-25
forum: Desktop Environments
---

### Post by Phoenix220 on 2011-06-25
I know how to change the colors of the panels. But on the parts were the ubuntu symbol, the menus (Applications, Places, and Systems), the date and time, and the indicator applets is, they do not change at all. And pretty much the same problem on the bottom panel.

I tried Gnome color changer but only works for the texts and the drop down menus. I use Gnome classic (hated Unity). My goal is to make ALL of the panel background black. I hope I provided all the info (my first post). Thank you in advance.

---

### Post by steinerd on 2011-06-25
Try this tutorial.  Worked for me on gnome 2.X  [http://shallows.bounceme.net/tiki-index.php?page_ref_id=16](http://shallows.bounceme.net/tiki-index.php?page_ref_id=16)

It's my site, I try to collect everything I use to one area making it easier to find it when I reload lol...

---

### Post by Krytarik on 2011-06-26
> **steinerd said:**
> Try this tutorial.  Worked for me on gnome 2.X  [http://shallows.bounceme.net/tiki-index.php?page_ref_id=16](http://shallows.bounceme.net/tiki-index.php?page_ref_id=16)
That would only affect the colors, but not the overlaying background image.

Incited by this thread, I've just converted and updated an earlier UF post of mine, please see here:
[http://ubuntu4beginners.blogspot.com/2011/06/customize-appearance-of-gnome-panel.html](http://ubuntu4beginners.blogspot.com/2011/06/customize-appearance-of-gnome-panel.html)

Greetings.

---

### Post by inameiname on 2011-06-26
....Edited by user....


It is indeed the ~/.gtkrc-2.0 that can be tweaked to suit your needs, but I do not know for sure what code should be added/removed/tweaked for such. You can also just tweak specific theme's gtk-2.0 inside its folder in /usr/share/themes, but that might be a bit too much for you.

One simple question, cannot you simply right click the panel, go to Properties -> Background and change the background image to some all black image? Although, I would think just changing the color to black would be best, but I guess that's your problem, its not working.

---

### Post by Phoenix220 on 2011-06-26
> **Krytarik said:**
> That would only affect the colors, but not the overlaying background image.

Incited by this thread, I've just converted and updated an earlier UF post of mine, please see here:
[http://ubuntu4beginners.blogspot.com/2011/06/customize-appearance-of-gnome-panel.html](http://ubuntu4beginners.blogspot.com/2011/06/customize-appearance-of-gnome-panel.html)

Greetings.

I tried this idea and it WORKED!! Thank you guys so much! I have three more questions, 

1. The window bar (on the panel), I tried GNOME color chooser to select the hover and selected parts, but the background part does not work either. What file do I use to change it? 

2. Is it possible to change the color of the Ubuntu symbol on the top left?

3. I love the window icons on top, I was wondering if the colors can be changed?

---

### Post by jerrrys on 2011-06-26
two ways to change the menu icon

[http://ubuntuforums.org/showthread.php?t=1668889](http://ubuntuforums.org/showthread.php?t=1668889)

also ubuntu tweak has other little tricks for changing things

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+menu+icon&sa=Search&cof=FORID:9#941](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+menu+icon&sa=Search&cof=FORID:9#941)

---

### Post by Krytarik on 2011-06-26
> **Phoenix220 said:**
> 
1. The window bar (on the panel), I tried GNOME color chooser to select the hover and selected parts, but the background part does not work either. What file do I use to change it?They are specified in the very same file, just below of the general panel settings. The task buttons are set up to use images, either transparent or the ones you are trying to affect. You can either add your custom images to the "gtk-2.0/apps/img" subdirectory and set them to the "prelight" and "active" button specs, set those to the same transparent image as the others, or remove the image specs completely and instead add color specs like these, and set the colors like you want:
```
    bg[NORMAL]        = @bg_color_dark
     bg[ACTIVE]      = shade (0.8, @bg_color_dark)
      bg[SELECTED]      = @selected_bg_color
     bg[PRELIGHT]      = shade (1.0, "#4D4C48")
      bg[INSENSITIVE]   = shade (0.85, @bg_color_dark)

```> **Phoenix220 said:**
> 
2. Is it possible to change the color of the Ubuntu symbol on the top left?
> **jerrrys said:**
> 
[http://ubuntuforums.org/showthread.php?t=1668889](http://ubuntuforums.org/showthread.php?t=1668889)

+1 and thanks for the pointer, as I didn't really remember having put that up here. ;)
> **Phoenix220 said:**
> 
3. I love the window icons on top, I was wondering if the colors can be changed?Therefore, you need to change the button images in the "metacity-1" subdirectory.

---

### Post by Phoenix220 on 2011-06-28
I took some time to attempt the steps... with the first one, I pasted the code in the panel file, but I do not know what to do with the code. I changed some of them, but nothing changed. I did use GNOME Color Changer, and TEMPORARILY changed the window bar background (to what I wanted), and then it changed back when I restarted I do believe.

On a side note, I tried to put a color value to @bg_color_dark (ex. @bg_color_dark = "#4D4W83")... But it didn't work. I apologize for being a noob.

On the 2nd question, i figured it out and changed the logo to my liking. I consider it solved.

On the 3rd, I finally figured out that I have to change the buttons files to change the color. So, I'll consider this one solved as well.

---

### Post by Krytarik on 2011-06-29
For modifying the style of the task buttons, please read my instructions once again. I've also updated the guide I linked to, there it may be a bit more clear and structured.

---

### Post by Phoenix220 on 2011-06-29
@Krytarik

I had to read it a couple of time to understand it... I ended up changing the necessary components and would like to thank you and everyone else who helped me out!! :D :D

---

### Post by Krytarik on 2011-06-29
You're welcome!

---

