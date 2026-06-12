---
title: "help me slim down Big Gnome menu plz"
date: 2010-08-05
forum: Desktop Environments
---

### Post by markthekdeguy on 2010-08-05
Hi i've posted and read and been through metacity forums,
and still cant find a answer to slimming down the Gnome menu.

The only way i can get the list shorter (less wasted space between menu entries, going top downwards) is a certain GTK theme (LK OS-K Blue) but i dont care for the metallic theme.
i have spend 6 hours tonight tweaking .gtkrc files here and there, with varying results,
the spacing is really horrible and makes an otherwise good desktop look horrible.

the fonts are small, unused entries are hidden, resolution is 1600x900.

it can be done via a certain Metacity theme, 
but x=thickness and y=thickness & Treeviews in gtkrc have either no effect,
or affect the wrong widgets, scrollbars,buttons or checkboxes. etc.
i have compared both themes gtkrc files side by side,too. no progress.

i have been chasing this UI 'feature' for months, but now i'm getting fed up.
anyone have any better / more detailed info ?
Mark

---

### Post by stinkeye on 2010-08-05
Install gnome-color-chooser
```
sudo apt-get install gnome-color-chooser
```


Installs under System > preferences

Open the panel tab and under the **Start Menu** section 
you can change the distance between your menu entries using the  **Y-Padding**

---

### Post by mojo2012 on 2010-12-26
Hi guys,

the bloatness of the gnome UI has always been bugging me too ;-) So I created my own "lightweight" elementary based theme.

You can download it from google code (svn checkout [http://unified-gnome-theme.googlecode.com/svn/trunk/theme/unified](http://unified-gnome-theme.googlecode.com/svn/trunk/theme/unified) unified-gnome-theme-read-only) and copy the "unfied" folder to ~/.themes/

Just look at the attached images to see how slim the theme is ;-)

Btw, the theme is not complete yet - I'm working hard on making it even better ;-)

---

### Post by baluvix on 2011-01-14
Thanks! Worked for me.

---

### Post by amilauduwerella on 2011-02-08
open "~/.themes/<name_of_theme>/gtk-2.0/gtkrc"
file and search for "gtk-icon-sizes" and comment the whole line
and put, something like;

gtk-icon-sizes = "panel-menu=16,16:panel=8,8:gtk-button=16,16:gtk-large-toolbar=24,24:gtk-small-toolbar=16,16"

---

### Post by mojo2012 on 2011-02-09
That makes the icons smaller, yeah. But that does not "unbload gnome". In fact for a long time I used 16x16 small toolbar icons, but now I have them on 24x24 and 32x32 for large toolbar and guess what ... the icons really look better ;-)

---

### Post by Copper Bezel on 2011-02-09
I used [this]("http://gnome-look.org/content/show.php/kreator_theme%20(openoffice%20fixed)?content=112414") theme for about a year or so, largely because of its very neat, thrifty menus. I agree with the general sentiment here - all of that atrocious padding is terribly annoying. Seeing this thread might actually motivate me to reduce the menu padding in the theme I'm using now.

---

### Post by mojo2012 on 2011-02-09
The problem I noticed so far is that you can break so much stuff if you decrease the paddings/thickness of widgets. Although the standard gtk widgets look fine, all xul or swt widgets look squeezed because the developers have already implemented separate workarounds for gtk's massive waste of screen space. So you have to "bloat" those widgets again, so that they look like the slimmed down gtk widgets ...

But as these widgets toolkits are not really gtk you cannot easily theme them ... it's really horrible.

Unfortunately, for most people this doesn't seem to be a problem so I guess it won't improve in the near future.
Nonetheless, I really hope that gtk+ 3.0 has better theming support, maybe with css styles??

---

