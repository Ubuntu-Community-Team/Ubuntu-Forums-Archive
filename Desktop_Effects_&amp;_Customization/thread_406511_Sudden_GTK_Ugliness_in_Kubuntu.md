---
title: "Sudden GTK Ugliness in Kubuntu"
date: 2007-04-11
forum: Desktop Effects &amp; Customization
---

### Post by odelay on 2007-04-11
I was recently playing around in the KDE system settings to get Thunderbird to look less horrible.  I didn't do anything crazy (or anything I hadn't done before) and all of the sudden, both Firefox and Thunderbird look terrible.

The fonts in Firefox seem OK...but for some reason the menubars and right-click contextual menus are all buggy.  When I first click on a menu, it looks fine.  Like this.

[IMG]http://farm1.static.flickr.com/188/454968561_85eee3fcc1_o.png[/IMG]

Then as I start to scroll down, the lines darken.  They stay darkened until I close the menu.

[IMG]http://farm1.static.flickr.com/239/454968563_5f928f2b7b_o.png[/IMG]

I get the same behavior in Thunderbird.  Just to give you an idea of how ugly my Thunderbird is...there's a screenshot below


First...what happened with the menu thing and how can I fix it?

Second...how do I make Thunderbird normal looking?

---

### Post by odelay on 2007-04-11
OK...after scouring one last time through the preferences, I found one that I missed.

In System Settings > Colors, there's a tiny little checkbox at the bottom left "apply-colors to non-KDE applications."  That fixed problem #1.

Thunderbird is still terribly ugly...just not as discolored now.  Has anyone found a way to make the text in Thunderbird more legible/pleasing?

Thanks!

---

### Post by odelay on 2007-04-11
Another thing to note that could save someone some aggravation:

If you change set the font to a fixed DPI in System Settings, this caused the error for me again.  The frustrating thing was when I disabled fixed DPI, it didn't fix the problem.  In fact, the only way I could fix it was to first uncheck the "apply to KDE-apps" option in the Colors section.  Apply it.  Then change it back, and apply it again.  Is this a known bug?

---

### Post by apogee on 2008-05-19
I am using Kubuntu 8.04 and am suddenly having the same problem as this slackware user:
[http://www.linuxquestions.org/questions/slackware-14/slackware-12.1-pango-and-seriously-mangled-fonts-640063/]("http://www.linuxquestions.org/questions/slackware-14/slackware-12.1-pango-and-seriously-mangled-fonts-640063/")

except my Thunderbird just does not load at all, here's the konsole output:

> ivan@apogee:~$ thunderbird

(thunderbird-bin:24005): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 12'

(thunderbird-bin:24005): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 27'

(thunderbird-bin:24005): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Trebuchet MS Bold 13.5'
*** Calendar schema version is: 7

(thunderbird-bin:24005): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 9'
Segmentation fault
ivan@apogee:~$


Any ideas?

---

