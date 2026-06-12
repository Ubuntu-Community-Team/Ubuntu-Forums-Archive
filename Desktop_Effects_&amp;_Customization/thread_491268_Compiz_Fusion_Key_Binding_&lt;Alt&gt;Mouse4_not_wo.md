---
title: "Compiz Fusion Key Binding &lt;Alt&gt;Mouse4 not working"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by psyopper on 2007-07-03
**RESOLVED**: By switching to the flatfile backend from the GConf backend (default) I got this working properly. This actually fixed a number of other annoying keybinding issues as well. 

Be warned: Not all of your settings will migrate from the Gconf backend into the flatfile, be prepared to make some adjustments when you make this switch. 

Hi all,

I installed Compiz Fusion (Ubuntu 7.04 Gnome) (I think a healthy improvement over Beryl) but am having a problem:

In the Compiz Config Settings Manager (ccsm) Under General Options -> Actions -> Opacity Settings I have listed (the default) of 

Increase Opacity      <Alt>Button4
Decrease Opacity    <Alt>Button5

Here's the rub: <Alt>Button5 (mousewheel down) decreases opacity just dandy, but <Alt>Button4 (mousewheel up) does not increase opacity. My mousewheel otherwise functions normally, scrolling web pages and Nautilus just dandy. 

As it turns out if I <Alt>Button4 in Firefox it scrolls up at half speed instead of full speed. 

To test I created a new user account, logged into it and started Compiz Fusion. Surprisingly <Alt>Button4 and <Alt>Button5 worked as they should, increasing and decreasing opacity properly.

So apparently I have a non-overridable keybinding somewhere in my profile to <Alt>Button4 that is not giving itself up to Compiz. This is where I hope someone here can help... 

Where can I find that key binding?

Thanks in advance!!

---

