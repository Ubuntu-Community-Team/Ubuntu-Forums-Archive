---
title: "Metacity title bars with Compiz-Fusion ?"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by abelthorne on 2007-10-25
Hello,
If I remember correctly, Ubuntu 7.04 (Feisty) came with Compiz installed and its manager had an option to use the Metacity theme title bar rather than Compiz own one.
Is this feature still possible with Compiz-Fusion or is Emerald the only way to get something else than the default title bar ?

---

### Post by Forlong on 2007-10-25
Just remove Emerald or run ```
gtk-window-decorator
``` separately.

---

### Post by abelthorne on 2007-10-25
I don"t have Emerald installed and as far as I know, gtk-window-decorator is already handling the windows decoration. And it sets Compiz default title bar (with big white widgets), which I would like to change to the Metacity one.

---

### Post by Forlong on 2007-10-25
gtk-window-decorator does nothing else than using Metacity's themes on Compiz.

---

### Post by abelthorne on 2007-10-25
Mmm, there must be something broken, then. In Compiz-Fusion manager, the window decorator is set to "gtk-window-decorator --replace". Even if I try to run it manually in a shell, I get the Compiz titlebar... :/
Are there any special packages needed ?

---

### Post by Forlong on 2007-10-25
Could you please provide a screenshot of what you call "the Compiz titlebar"?

---

### Post by abelthorne on 2007-10-25
Here is a screenshot of my current desktop : [[IMG]http://img517.imageshack.us/img517/30/ubuntudesktopfq0.th.jpg[/IMG]](http://img517.imageshack.us/my.php?image=ubuntudesktopfq0.jpg)

All I can get with Compiz-Fusion is the default toolbar that you can see on the screenshot (semi-transparent, one color, one height, rounded corners, one widget style - big and white -) and I'd like to use the title bars of the several themes I have installed, such as Reuben, Tangodance, etc.

In Compiz, there was a specific option to use Metacity title bars instead of the default ones (it was not possible with Beryl I think and the only way to have custom title bars with it was to use Emerald).

I can't find such an option in the Advanced Desktop Effects Settings tool.

---

### Post by Forlong on 2007-10-25
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by abelthorne on 2007-10-25
```
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1              OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1              OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1                Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2                Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1              OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                         OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1              OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1                Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings
```

---

### Post by Forlong on 2007-10-25
What happens when you run this:
```
gnome-settings-daemon
```

---

### Post by abelthorne on 2007-10-25
I get an error message :
```
** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Abandon (core dumped)
```

---

### Post by Forlong on 2007-10-25
I'm sorry but I am still not sure what your problem is.
Is there any output when you run
```
gtk-window-decorator --replace
```
in a terminal?

---

### Post by abelthorne on 2007-10-25
No. No output at all.
The windows title bars disappear (I guess the current decorator is unloaded) then reappear.

---

### Post by Mr Greencastle on 2007-10-25
Are you sure that the title bar that you are looking at isn't part of your GTK theme?

Maybe try changing the theme and see if your titlebar changes... It could be as simple as that.

If you could, give a link to the theme too.

---

### Post by abelthorne on 2007-10-25
> **Mr Greencastle said:**
> Are you sure that the title bar that you are looking at isn't part of your GTK theme?

Maybe try changing the theme and see if your titlebar changes... It could be as simple as that.

If you could, give a link to the theme too.

100 % sure, as you can see which Metacity theme is selected in the screenshot ("Si"). The title bar won't change, whichever theme I choose and all works as expected when I revert back to Metacity by disabling Compiz-Fusion in the Appearance Gnome tool.
The only thing that changes when I change the title bar theme with Compiz-Fusion active is the color of the bar. The widgets stay the same (If I'm not mistaken, they're Compiz default ones), as does the bar height, the corners and so on.

Anyway, you can confirm that when using Compiz-Fusion in Gutsy (version from the repositories), I'm supposed to keep the Metacity title bar ?

When I was using Feisty some weeks ago, I installed Compiz-Fusion from the unofficial repositories, installed Emerald and so on. After the Gutsy upgrade, it was quite a mess and I thought I fixed everything by installing the right packages, removing Emerald and deleting my Compiz-Fusion preferences to get Gutsy's default.
So I guess there has to be some problems in my configuration.

---

### Post by Mr Greencastle on 2007-10-25
You've stumped me, because unless I'm mistaken, Compiz doesn't handle the window decoration other than the plugin.

And you said even after a 
```
gtk-window-decorator --replace
```

It remains the same? Really weird, this is beyond me.
You also said that changing to any other theme gives you the same results (titlebar), so unless there is a crazy conspiracy which is changing your titlebars, no clue.

The funny thing is, the titlebar theme that you are trying to get rid of, is actually very similar to the one I'm using with Emerald, and I've been trying to find a GTK version forever...

Mr Green

PS Have you tried #compiz-fusion on irc.freenode.net? You can get much faster answers there.

---

### Post by abelthorne on 2007-10-26
> **Mr Greencastle said:**
> The funny thing is, the titlebar theme that you are trying to get rid of, is actually very similar to the one I'm using with Emerald, and I've been trying to find a GTK version forever...

To me it really looks like the title bar that was used when installing Compiz (before it merged with Beryl to become Fusion). Thus why I keep calling it "Compiz default title bar". I'll check if it might be a remain of a previous Emerald installation (although I used a specific theme that didn't look like this one; but maybe it's "Emerald default title bar" when it can't find other themes).

> PS Have you tried #compiz-fusion on irc.freenode.net? You can get much faster answers there.

I'll try that as soon as I remember how IRC works (I haven't used it for ten years) :)

---

### Post by gemme on 2007-10-26
The same problem here.

Solved by setting **/apps/gwd/use_metacity_theme** to true in gconf-editor

More info:
[http://wiki.compiz-fusion.org/Decorators/GTKWindowDecorator](http://wiki.compiz-fusion.org/Decorators/GTKWindowDecorator)

Why Cairo-based decorator is used by default? IMHO this is a bug...

---

### Post by abelthorne on 2007-10-26
It works. Thans a lot !

Maybe it's a problem related to upgrading from Feisty to Gutsy ? Does the same problem occur with a fresh Gutsy install ?

---

### Post by michaelpagz on 2007-12-02
i have this exact problem where can i find apps/gwd/use_metacity_theme? or rather where is the gconfig_editor? can i get to it through the terminal? if so how? sorry im new-ish.

thanks,
mike

---

### Post by abelthorne on 2007-12-02
You can customize the Gnome menu from System -> Preferences. In Applications/System, check the Configuration editor entry.
Or you can run **gconf-editor** from a terminal.

---

### Post by michaelpagz on 2007-12-02
okay. when i use```
gtk-window-decorator --replace

``` it works using my selection in appearances under theme. however, as soon as I exit out of the terminal the title bar disappears. i went to gconf-editor and unchecked  use_ metacity_theme, it was already checked. i have tried it both check and unchecked and I still get the same results. i dont have a window theme at all. should i try to uninstall emerald theme manager? 
thanks
mike

---

### Post by Forlong on 2007-12-02
> **michaelpagz said:**
> okay. when i use```
gtk-window-decorator --replace

``` it works using my selection in appearances under theme. however, as soon as I exit out of the terminal the title bar disappears.
You can prevent this by using [Alt]+[F2] instead of the terminal.
> **michaelpagz said:**
> should i try to uninstall emerald theme manager?
If you want to use gtk-window-decorator anyway, that would be the easiest solution.

---

### Post by michaelpagz on 2007-12-02
got it! damn, i love this forum. thanks again!
mike

---

