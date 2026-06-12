---
title: "fractional scaling conflicts with monitor dimensions"
date: 2024-05-20
forum: Desktop Environments
---

### Post by goodstuff9 on 2024-05-20
[COLOR=#0C0D0E][FONT=-apple-system]Ubuntu 22.04.4, gnome shell 42.9, wayland (per the "About" screen under Ubuntu settings).[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I have two monitors, I set the fractional scaling on each to be 125%.  Each has a resolution of 1920 X 1080.  [/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]On the left monitor, I have an icon on the desktop appearing in the middle of the monitor. I can move it around on that monitor, but: Something strange happens if I try to move it to one of the three rightmost "columns" of that left monitor. If I try to move it to one of those three rightmost columns on the left monitor, it ends up in one of the three leftmost columns of the right monitor. (But: Attempting to place an icon in one of the three leftmost columns of the right monitor does NOT place it in one of the three rightmost columns of the left monitor - In this case the icon stays on the right monitor where I intend for it to be.)  Don't have this problem when the resolution is set at the default of 100% on each monitor.  

I have the resolution on each monitor to be 1920 X 1080. When I leave the fractional scaling - under the Ubuntu settings display option - at the default of 100%, in the monitors.xml file the x,y coordinates for the two monitors are exactly as I'd expect them to be: viz., 0,0 for the left monitor, and 1920,0 for the right monitor. However, when I change that fractional scaling setting from 100% to 125% on each monitor, and leave the resolution on each monitor at 1920 X 1080, the x,y coordinates automatically get changed to 0,0 and 1536,0. My simplistic understanding is that this change effectively makes the left monitor get cutoff at 1536 instead of at 1920, basically moving the rightmost 20% of that monitor's x dimension to be treated as part of the right monitor's x dimension. If I manually fix the x,y coordinates in the monitors.xml file, then at next reboot the fractional scaling is automatically reset to 100% on each monitor. I obviously do not understand the relationship between fractional scaling and monitor dimensions in the monitors.xml file. (Incidentally, in gnome tweaks under the font setting I have throughout all this left the scaling option at the default of 1.0. Don't know how, if at all, that interacts with the fractional scaling in the Ubuntu settings.)  

[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Why is this happening?
[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]How do I fix this problem?[/FONT][/COLOR]

---

### Post by him610 on 2024-05-20
Was not familiar with "fractional scaling" so I looked it up...
> Is fractional scaling good in Ubuntu?
That really depends on the applications you use. On native wayland, fractional scaling looks absolutely perfectly sharp and, even better, multiple monitors with different scaling work great together. If you're running an application that needs X11 then indeed fractional scaling incurs some blur.

This leads to the question, "Are you using Wayland or X11?"

---

### Post by goodstuff9 on 2024-05-20
> **him610 said:**
> Was not familiar with "fractional scaling" so I looked it up...


This leads to the question, "Are you using Wayland or X11?"


Thanks for replying.  

I'm not sure of the point you're making.  As I wrote in the original post, according to the About option in Ubuntu settings, it says that the windowing system is Wayland.  Are you suggesting that what Ubuntu reports on that screen is incorrect?  Can you clarify please?  Thanks.

---

### Post by him610 on 2024-05-20
I missed *wayland* in your original message. You had a lot of text to wade through in your original message that turns cranky old people with fading eyesight off.
>  Are you suggesting that what Ubuntu reports on that screen is incorrect? Can you clarify please?
I am not suggesting anything. I don't know anything about *fractional scaling.*
Maybe the next person who reads this thread will be more helpful.

---

### Post by goodstuff9 on 2024-05-20
> **him610 said:**
> I missed *wayland* in your original message. You had a lot of text to wade through in your original message that turns cranky old people with fading eyesight off.

I am not suggesting anything. I don't know anything about *fractional scaling.*
Maybe the next person who reads this thread will be more helpful.

Ha,  ha, no harm,  no foul.  I thought maybe you were on to something.  

You may be interrested in how this turns out if your eyesight is no longer ideal:  I'm interested in the fractional scaling for that very same reason.  My understanding is that it is supposed to allow overall enlarging images and text, which is what I'm looking for.

---

### Post by sudodus on 2024-05-20
My 2 cents:

Fractional scaling causes blur due to interpolation of the pixel values, but may still be an improvement, if text and graphic elements are to small to see with the default resolution. But I have not tried it with more than one monitor. I think the overlap that you are describing is caused by a bug, and maybe you can report it to [https://launchpad.net](https://launchpad.net).

But if you scale with integer steps, typically 2 (often expressed as 200%), there will be no blur, the length scale will be 2 and the area scale will be 4.

Alternatives to try:

- You can try Xorg (the old alternative instead of Wayland), and it might not be affected by the overlap bug that you are describing.

- Another alternative is to change the default fonts in the application programs that you use most of the time. That is a bit more complicated, but I think the final result will be better than what you get with fractional scaling.

- A third alternative is 'panning', to show only part of the nominal screen, using the default resolution, and making it possible to scroll vertically and horizonally by moving the mouse to 'drag the edges' of what is displayed on the monitor. I have not tested how it works with more than one monitor, but it might work for you. [This link](https://discourse.lubuntu.me/t/help-scaling-the-desktop-on-lubuntu/4810/7) discussed it for the community flavour Lubuntu (in a slightly different context, but you can use the command **[FONT=Courier New]xrandr[/FONT]** as described, when using Xorg).

---

### Post by Claus7 on 2024-05-20
Hello,

this is not a (direct) solution to your problem. You could try though to increase the font size of your gnome shell and see if you are happy with it. If not, you can revert back easily: 
cd /usr/share/themes/Yaru-(here add color of choice)/gnome-shell
sudo gedit gnome-shell.css
and change the font-size value. Save and exit.

That way I do not think that you will have any issue with resolution blurriness. 
If you do not like the result, again go to the same file and change back the font to its original value. Have in mind that from noble and on it is not anymore as pt, yet as em, which means that you are providing a scaled font value instead of an absolute one.

Regards!

---

### Post by him610 on 2024-05-20
I still don't have a good grasp on "fractional scaling"; however, I normally position the monitor closer, and if that isn't enough I use *Ctrl+* to enlarge the text font.

---

