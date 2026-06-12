---
title: "how to disable tooltips ?"
date: 2010-06-23
forum: Desktop Environments
---

### Post by AM_SOS on 2010-06-23
hi,

i am sure someone has to have complained about this one.
since i installed 10.04 i have noticed constant and irritating tips which ubuntu keeps providing soon as the pointer rests just about anywhere.
now i do appreciate the idea behind such tips but surely this is a case of overkill !
my irritation was further aggravated when i began using open office. simply exploring the menus to check up on its differences with MS office became quite a task. i had to constantly keep moving the cursor in order to be able to see what the main menus in the open office program had to say !
so can someone please put me out of my misery and suggest a way to at least temporarily if not permanently disable these tool tips ?
thanks !

---

### Post by stinkeye on 2010-06-23
If your using compiz you can set the tooltips opacity to zero in
CCSM > accessibility > opacity brightness and saturation.
[B]Move the slider above zero before closing so if you make a mistake, all
your windows aren't transparent. [/B]

There is also a setting in gconf-editor to turn off tooltips for the panel.
/apps/panel/global/tooltips_enabled

---

### Post by warfacegod on 2010-07-07
I got most of the way through reading the first post when I realized that Compiz could turn them invisible. Then I saw stinkeye's post and realized I was right. However there is a flaw. It doesn't work for Firefox. I just figured out a way around that.

.01 Type about:config into the address bar (don't worry about the warning)

.02 In the Filter bar type> toolbar

.03 Find> browser.chrome.toolbar_tips and Toggle it so that its Value is false

No more tool tips in Firefox. If you spend any amount of time on this Forum, you know exactly how monstrously irritating those things can be.

---

### Post by lovinglinux on 2010-07-07
> **warfacegod said:**
> I got most of the way through reading the first post when I realized that Compiz could turn them invisible. Then I saw stinkeye's post and realized I was right. However there is a flaw. It doesn't work for Firefox. I just figured out a way around that.

.01 Type about:config into the address bar (don't worry about the warning)

.02 In the Filter bar type> toolbar

.03 Find> browser.chrome.toolbar_tips and Toggle it so that its Value is false

No more tool tips in Firefox. If you spend any amount of time on this Forum, you know exactly how monstrously irritating those things can be.

Keep in mind that also affects the browser chrome, so extensions will not display any tooltip.

I think a better solution would be to try to increase the delay before the tooltip is displayed, but I don't know how to do that in Compiz or Kwin.

---

### Post by warfacegod on 2010-07-10
Why would changing the delay in Compiz work if turning them invisible doesn't?

---

### Post by arizonalarry2 on 2010-07-24
Any chance of adding in a simple thing to turn off tooltips in a future version of Ubuntu? I had to disable compiz a couple of years ago because it was giving me trouble with something, I don't remember what. But it seems like it would be an easy enough thing to do.

---

### Post by doublewitt on 2010-08-15
I found the solution (for me),

"The way to get rid of ALL tool tips is open your Compiz Config Settings Manager, enable "Opacity, Brightness and Saturation" under "Accessibility". Click on the button to go into the settings.

Under the "Opacity" tab go down to "Window Specific Settings" and click "Add". Type "Tooltip" and slide the opacity down to zero. Click "Close".

You're done."

[NB: It is possible you already have "Tooltip" included under another entry, for example if you've made your menus, popups, dropdowns etc transparent. If so just edit that entry and remove "Tooltip" form it so you don't have two conflicting opacity settings.]

from:  [http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html]("http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html")

**[SIZE="6"]*[/SIZE]**there are other alternatives on this page...

If Compiz was a problem for you way back, I suggest that you try it again and apply this solution - it works great! and yet, there are other ways to do it on this page...

---

### Post by nrundy on 2010-12-15
Has anyone come up with a way to turn off Tooltips? These things get incredibly annoying!

---

### Post by bvc on 2010-12-15
For gtk, put the following at the top of the theme's gtkrc, save, apply a different theme and reapply the modified theme.
```
gtk-enable-tooltips = 0
```

For gnome panel, open gconf-editor and go to apps>panel>global and uncheck tooltips_enabled.

For metacity, open gconf-editor and go to desktop>gnome>interface and make sure hide_decorator_tooltip is checked.

---

### Post by nrundy on 2010-12-16
Thanks so much for your help bvc, but what is "gtk"?  I did the last two you mentioned, but might you post a link or more info on where I can learn about this "gtk"? I have no clue what you're talking about.  Thank you again :)

---

### Post by bvc on 2010-12-16
> **nrundy said:**
> Thanks so much for your help bvc, but what is "gtk"?  I did the last two you mentioned, but might you post a link or more info on where I can learn about this "gtk"? I have no clue what you're talking about.  Thank you again :)Gtk is mostly what you see. Buttons, text entry, drop lists, scrollbars etc.... The gtkrc is just a text file that tells an gtk2 engine what to do.

_Quick and easy way_
If you have a .gtkrc-2.0 in your hone directory just put the code in it. If you do not have a .gtkrc-2.0, open a text editor and type```
gtk-enable-tooltips = 0
```then save it in your home folder as .gtkrc-2.0
Reset the theme in the Appearance preferences.

_Long and hard way_
Add```
gtk-enable-tooltips = 0
```to the very top of the gtkrc file in theme you are using and save it. Reset the theme in the Appearance preferences. System installed themes are in /usr/share/themes and require root privileges to edit but they can also be found hidden in your home folder in ".themes" where the user can edit. The gtkrc text file is in the theme folder. For example, either

/usr/share/themes/theme_name/gtk-2.0/
/home/user_name/.themes/theme_name/gtk-2.0/

The downside to this method is you have to edited a gtkrc text file for every theme you use.

Does that help?

---

### Post by nrundy on 2010-12-17
> **bvc said:**
>  _Quick and easy way_
If you have a .gtkrc-2.0 in your hone directory just put the code in it. If you do not have a .gtkrc-2.0, open a text editor and type```
gtk-enable-tooltips = 0
```then save it in your home folder as .gtkrc-2.0
Reset the theme in the Appearance preferences.



When you say &quot;Reset the theme...&quot; you just mean switch to another theme then switch back to the one you were using, right? I don't see a reset button or anything. 
 Thank you so much for your help bvc. I really appreciate it

---

### Post by bvc on 2010-12-17
> **nrundy said:**
> When you say &quot;Reset the theme...&quot; you just mean switch to another theme then switch back to the one you were using, right?Yes.

> **nrundy said:**
> Thank you so much for your help bvc. I really appreciate itYou're welcome!

---

