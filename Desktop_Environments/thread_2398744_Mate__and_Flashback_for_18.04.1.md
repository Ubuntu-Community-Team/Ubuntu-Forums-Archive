---
title: "Mate  and Flashback for 18.04.1"
date: 2018-08-16
forum: Desktop Environments
---

### Post by merlinus on 2018-08-16
The top panel right-hand icons for connections (wired and wireless), logout/restart/shutdown/sound, etc. are not available in Mate.  How can these be restored, or are there workarounds?

Also, in flashback mode, the text at the top left (Application, Places, etc.) and icons are scrunched together, and the text is very small.  Any way to fix this?

---

### Post by Claus7 on 2018-08-16
Hello,

> **merlinus said:**
> 
Also, in flashback mode, the text at the top left (Application, Places, etc.) and icons are scrunched together, and the text is very small.  Any way to fix this?

The text at the top left is configured from Applications->System Tools->Preferences->Tweaks
and then choosing Fonts: Interface. 

Now, in order to change the space of the icons, (I guess excluding the option from pointing mouse on top of panel, then pressing Super+Alt+right click, then choosing Properties and from there changing the size, which, by increasing the size of the panel also increases the size of the icons), you should do the following:

Go to the folder of your theme: 
/usr/share/themes/*your_chosen_theme*/gtk-3.20

and from the file:
gtk-widgets.css

locate the part:
/**********
 * button *
 **********/
button {
    padding: 1px 2px;  

where the 2nd px (numbers here are just examples) will change spacing of the panel icons.

In case this does not work as it should, it might be a problem with your panels, which can be solved if you reset them. Before that it is advised to backup first:
dconf dump /org/gnome/gnome-panel/ > dconf_bup_panel
and then reset:
dconf reset -f /org/gnome/gnome-panel/
If something goes wrong you can revert with:
dconf load /org/gnome/gnome-panel/ < dconf_bup_panel

If I am not mistaken mate is based on gnome2, which means that you could check older themes of ubuntu, which include these icons and add them to your favorite themes.

Regards!

---

### Post by merlinus on 2018-08-17
Thanks for the info.  I was able to change the font size.  But editing the css for my theme did not change the size or spacing of toolbar icons.

I am running flashback, not mate, because the top right widget that has the shutdown/restart/logout options and internet connection info does not load in mate.

---

### Post by oldfred on 2018-08-17
I also use flash back and have no real issues.

Is your gpu set to match monitor? When not using default sizes, the scaling can be off.
       sudo lshw -c display 
      
 xrandr --q1 
            sudo get-edid | parse-edid

---

### Post by Claus7 on 2018-08-17
Hello,

> **merlinus said:**
> Thanks for the info.  I was able to change the font size.  But editing the css for my theme did not change the size or spacing of toolbar icons.

I am running flashback, not mate, because the top right widget that has the shutdown/restart/logout options and internet connection info does not load in mate.

if you could provide more info about your theme and provide also a picture about the problem you are facing in flashback, this might shed more light. I do not remember such a problem in mate so what *oldfred* suggests might help you in this case.

Regards!

---

### Post by merlinus on 2018-08-22
Here is a screenshot from the fallback desktop.  Note the garbled text next to Scale, and lack of space at the upper left of the top panel between icons and text.


[http://evening-sun.com/screenshot.png](http://evening-sun.com/screenshot.png)

---

### Post by merlinus on 2018-08-25
On both computers with this same problem, the size and resolution of the monitors is shown correctly.  1680x1050.  It is interesting that the fallback desktop is screwed up, but Mate works fine.

---

### Post by Claus7 on 2018-08-28
Hello,

in my flashback session, in place of the Scale option I have instead the option: Refresh Rate, and just underneath the option: Adjust for TV. Also I have Night Lite turned off. If I turn it on, the screen takes an orange hue. Why your Displays is like that I do not know, yet I would advice you to change theme and check again.

Please, also, provide more info about your theme, and how you changed the options of the file (you have to be root in order to do that). In my case it did change the space of the icons, so, if you provide more info I would replicate it and let you know. I do not have any theme installed that has both top bar and window with the colors in your picture.

Regards!

---

### Post by wildmanne39 on 2018-08-28
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by merlinus on 2018-08-29
This is not a url?  [http://evening-sun.com/screenshot.png](http://evening-sun.com/screenshot.png)

---

### Post by DuckHook on 2018-08-29
> **merlinus said:**
> This is not a url?  [http://evening-sun.com/screenshot.png](http://evening-sun.com/screenshot.png)It is now, but was not originally. wildmanne39 *edited* your original post to replace the large image with the current URL. He was just reminding not only you, but all who may read the thread, to replace images with URLs as a courtesy to those with low bandwidth.

---

