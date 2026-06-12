---
title: "Metacity - Center titles regardless of the number of window buttons"
date: 2012-02-26
forum: Desktop Environments
---

### Post by CardexDave on 2012-02-26
Hello everyone!

I am trying to edit a metacity theme to make it center the title.
I looked on the web and all the answers I found were like "x=(width-title_width)/2.
The problem with that setting is it was already like that in the metacity theme file, but the titles were not centered.
I think the main cause of it is the close, maximize and minimize buttons, who pushes the title some pixels to the right (I set those buttons to the left).
Then I tried to cheat a little bit and set x=((width-title-width)/2)-36, to counter the displacement caused by the window buttons. While it was perfect for many windows, it is broken if a window does not have the maximize button for example, as the space taken by the windows buttons are not 36 pixels anymore, and the title is then misplaced a little bit to the left.

Does anyone know a way to set the x value of the title such that it is always centered, regardless of the number of window buttons the current window is displaying?

Thanks,

Dave

PS: English is not my native language, sorry for the potential errors I made... =/

---

### Post by Krytarik on 2012-02-26
Although it's kinda strange, it doesn't seem like there is a way to achieve that; have a look at this official doc:

[http://live.gnome.org/GnomeArt/Tutorials/MetacityThemes](http://live.gnome.org/GnomeArt/Tutorials/MetacityThemes)

And upon further googling that, I've found this nice elaboration, also corroborating that perception:
> In Mac OS Classic, title-text is centred between the left and right edges of the window, while Metacity draws the title frame piece between the left and right titlebar buttons. Thus, if one side of the titlebar has more than the other, Metacity's title will be subtly off-centre. Which method is better largely depends on how unbalanced your button layout is - Metacity's default has three times as many buttons on one side than the other, so I think they made the right choice.

It would be nice if there were some way to work around this, but I couldn't find one, so I'm putting up with this minor inexactitude.Source: [http://thristian.livejournal.com/89296.html](http://thristian.livejournal.com/89296.html)

Regards.

---

### Post by CardexDave on 2012-02-27
Thanks for your answer!

It's a bit disappointing to discover that this is really impossible to do...
I think centered titles are somewhat elementary and a basic feature, am I wrong?
Did metacity devs already made a statement regarding to this issue, something like "we don't think it's a bug, we intended it that way", or should I try to let they know somehow?

---

### Post by Frogs Hair on 2012-02-27
I have had a few themes that the title bar text has been off center . They were not made with buttons on the left in mind . If the theme is forced to place the buttons on the side that was not intended it will offset the whole title bar. 

My experience with this is with older GTK 2 themes.Ubuntu went to buttons on the left in 10.04 but many distros using Gnome did not. I'm sure many developers didn't have Ubuntu in mind. 
    
I have only one noticed this with one GTK 3. The theme was specifically made for the Gnome Shell, which has buttons on the right by default.

---

### Post by Krytarik on 2012-02-27
> **CardexDave said:**
> It's a bit disappointing to discover that this is really impossible to do...
I think centered titles are somewhat elementary and a basic feature, am I wrong?
Did metacity devs already made a statement regarding to this issue, something like "we don't think it's a bug, we intended it that way", or should I try to let they know somehow?
Think about smaller windows, where a window title centered between the edges of the window - as opposed to be centered in the available space - would inevitably lead to a heavy clipping of either the left or the right side of the title, depending on the button placement; it's kinda hard for me to imagine how they could work around that.

So, as also concluded in the post I've quoted, I think it was the right decision to *not* base the titlebar formatting on the edges of the window, by default; but I also think it would be good to at least offer some variables in case someone actually desires to set the title text to the absolute center of the window.

As far as statements from the Metacity devs reg. that matter, or filed bug reports go, I didn't come across any upon googling it earlier, and quickly checking Launchpad now, but you could search yourself, and try filing a bug report - but be prepared that it would likely end up in the "Wishlist" state, or be dismissed altogether - for that, I think this is a good place to start:

[https://bugs.launchpad.net/ubuntu/+source/metacity](https://bugs.launchpad.net/ubuntu/+source/metacity)

---

### Post by CardexDave on 2012-02-29
Thank you very much for answering my questions! :)

---

