---
title: "Trouble installing new themes"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by Errorsol on 2007-05-02
Alright I'm a complete noob when it comes to Linux. I installed ubuntu linux 6.10, a week ago or so and am currently looking into changing around the desktop user interface.  I am trying to install this theme ([http://www.gnome-look.org/content/show.php/VistaBut?content=32227](http://www.gnome-look.org/content/show.php/VistaBut?content=32227)) and to make my desktop look exactly like that, but every time I install it my desktop ends up looking default. I read the comments and installed the pixmap engine as well as the pixbuf engine, but it still doesn't change my desktop look. How do I go on about fixing that?

---

### Post by Steve H on 2007-05-02
When you say you are installing it, how do you mean? Usually I just download the zip/gz/etc and drag-and-drop it in to the Themes manager. I then just highlight the new entry and press ok. Works for me.

Does the new desktop need a new Icon set? maybe have a look on the website you got it from, they may mention which icon set they are using (or any other dependencies, for that matter).

Let me know how you get on.

:)

---

### Post by Errorsol on 2007-05-02
> **Steve H said:**
> When you say you are installing it, how do you mean? Usually I just download the zip/gz/etc and drag-and-drop it in to the Themes manager. I then just highlight the new entry and press ok. Works for me.

Does the new desktop need a new Icon set? maybe have a look on the website you got it from, they may mention which icon set they are using (or any other dependencies, for that matter).

Let me know how you get on.

:)

I download the tar.gz file, then go system -> preferences -> themes -> install theme.  This is what my desktop looks like when I install that vista theme:

[IMG]http://img87.imageshack.us/img87/2042/screenshotgt8.png[/IMG]

The layout is still the default ubuntu layout, instead of that revised vista look. Which is the look that I want to have for my desktop.

---

### Post by Steve H on 2007-05-02
I've had a look at the page you got it from, and it does say:

> Description:
Vista feel but some custom widgets...
(Linux is NOT Windows) :)

I upload icon theme soon (if finished...)
XFCE4 theme included!

So there will not be all the icons that you can see on the screenshot. Also it does say:

> Change menubar colours & fonts:
edit the Gtkrc file in theme dir and modify:
################Select your desired menubar colour!!!
#include "menubar-light.rc"
#include "menubar-blue.rc"
include "menubar-green.rc"

So i would do a search for the gtkrc file in the Theme directory and do as it suggests, adding the relevant line for the colour of menubar you want. 

It does look like this a pretty incomplete "theme" so it may be worth looking around for a better one, or waiting until the icons are uploaded.

Hope that helps.

:)

---

### Post by Errorsol on 2007-05-02
What I want to know is how do I change my desktop theme to look like that vista one or like a mac osx. Layout wise, and all that.

---

### Post by rolf-c on 2007-05-02
> **Errorsol said:**
> What I want to know is how do I change my desktop theme to look like that vista one or like a mac osx. Layout wise, and all that.

Take a look at [http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php) - scroll through the whole thing before you start and he includes screen shots of what you should expect to see when done.

---

