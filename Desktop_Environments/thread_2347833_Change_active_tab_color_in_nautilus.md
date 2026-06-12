---
title: "Change active tab color in nautilus"
date: 2016-12-29
forum: Desktop Environments
---

### Post by tigerjack89 on 2016-12-29
I have the Ambiance-Dark theme installed on Ubuntu 14.04 with Unity and I'm not satisfied with the tab colors of Nautilus tabs. The active/inactive tab colors are pretty much identical, so it's very difficult to understand on which tab I am on. 

I'd like to increase the contrast between them (hopefully in a more firefox-ish way), but I don't know what I have to modify. I already looked into the */usr/share/themes/Ambiance-Dark/gtk-3.0/apps/nautilus.css* but it doesn't seem to have any entry for this.

---

### Post by vasa1 on 2016-12-29
See if [https://ubuntuforums.org/showthread.php?t=1871472](https://ubuntuforums.org/showthread.php?t=1871472) is of any help. I don't use Nautilus and so can't offer any specific code to address your issue.

---

### Post by tigerjack89 on 2016-12-31
> **vasa1 said:**
> See if [https://ubuntuforums.org/showthread.php?t=1871472](https://ubuntuforums.org/showthread.php?t=1871472) is of any help. I don't use Nautilus and so can't offer any specific code to address your issue.
Thanks for your help. Unfortunately, I've tried to see a lot of threads, modified many .css files, but the result doesn't change. The very bad thing is that this behaviour propagates to all windows, from gedit to gvim.
Any help is really appreciated.

---

### Post by vasa1 on 2016-12-31
Have you tried another theme?

This is what gedit looks like using Adwaita. Pretty decent contrast there.

Edit: I spent a couple of minutes modifying /home/vasa1/.themes/MyAmbiance/gtk-3.0/gtk-widgets.css to get contrast there as well. MyAmbiance is nothing but the default Ambiance copied over to ~/.themes. See the image titled modified-ambiance.png.

```
/* give active tab a background, as it might be dragged across of others when reordering */
.notebook tab:active {
    background-color: @selected_bg_color;
}

```Before my fiddling, it was 
```
/* give active tab a background, as it might be dragged across of others when reordering */
.notebook tab:active {
    background-color: @bg_color;
}
```

And modified-greybird.png is what a (heavily) modified version of the Greybird theme looks like.

---

### Post by vasa1 on 2017-01-01
By the way, if you wish, you can see what (most) applications look like with a dark version of Adwaita. I mention this because you stated you were using something called Ambiance Dark. Open a terminal and try:
```
GTK_THEME=Adwaita:dark gedit
```
as an example. (But make sure that no other instance of the application is running. This holds true for any theme mod you're making!)

---

### Post by yetimon_64 on 2017-01-03
> **vasa1 said:**
> See if [https://ubuntuforums.org/showthread.php?t=1871472](https://ubuntuforums.org/showthread.php?t=1871472) is of any help. I don't use Nautilus and so can't offer any specific code to address your issue.

On all seven gtk themes installed here your old thread tip works perfectly. Though I am running an install built from a minimal cd with multiple DE's installed (if that can affect the difference between the OP's and my experience here). I should note I did my changes as root altering the theme files in /usr/share/themes/<theme-name>/gtk-3.0/gtk-widgets.css and they all worked without a hitch.
 **IMPORTANT NOTE:** _*being in root owned locations I created copies as .BAK files first for safety*_.

I now have nice contrast on the tabs in gedit, gnome-terminal and even nautilus (see attached screenshot below of one of the theme adjustments). BTW, I am on 14.04 and set it all up in xfce, but have now changed to unity and the three standard themes available to me in unity,[s] Adwaita,[/s] Ambiance and Radiance all have retained the differently set up contrast levels. Nice work finding that tip vasa1, cheers, yeti.

[ATTACH=CONFIG]273006[/ATTACH]

---

### Post by vasa1 on 2017-01-03
> **yetimon_64 said:**
> ... Nice work finding that tip Vasa1, cheers, yeti.

You're most welcome!

---

### Post by tigerjack89 on 2017-01-03
Thanks, I've been able to modify the theme changing only one line in the gtk-widget.css.
Btw, from the trial and error experience related to this days, and for my Ubuntu 14.04, all the relevant files were mainly located in 3 different directories. 

[LIST=1]
[*]```
/usr/share/themes/<theme-name>/gtk-3.0
```
[*]```
/usr/share/themes/<theme-name>/gtk-3.0/apps
```
[*]```
~/.config/gtk-3.0/gtk.css
```.
[/LIST]

I think that the files in those directories form a kind of hierarchy, in which point 1 define global .css files (f.e. gtk-widget.css), point 2 define .css files specific for some applications (f.e. you have the nautilus.css, gedit.css and gnome-terminal.css files there) and point 3 define a user specific file that overwrite/extend the definition of files in the previous 2 folders (f.e. I used it to modify the active tab for my user only).

Again, this is only a guess based on my experience and I'm not 100% sure that this is really so.

Many thanks to vasa1 for pointing me in the right direction.

---

### Post by vasa1 on 2017-01-03
> **yetimon_64 said:**
> ... BTW, I am on 14.04 and set it all up in xfce, but have now changed to unity and the three standard themes available to me in unity, Adwaita, Ambiance and Radiance all have retained the differently set up contrast levels. ...
yeti, if you come by this way again, please can you clarify how you managed to modify Adwaita? My understanding is that even in 14.04, modifying Adwaita isn't a simple matter of just editing *gtk-widgets.css*. There are new-fangled files such as *gtk.gresource* and *gtk.gresource.xml* and a folder called *scss* :(

Adwaita in 16.04 has been assimilated by the GNOME borg. In the gtk-3.0 folder, there's a single file, gtk.css, with just one line:```
/* Adwaita is the default theme of GTK+ 3, this file is not used */
```

The [QnA here]("http://unix.stackexchange.com/questions/175385/where-may-i-find-a-reference-scheme-for-gnome-3-theming-e-g-adwaita") goes into more detail but the link in the answer, How to hack GNOME Adwaita GTK theme, has outdated information.

---

### Post by yetimon_64 on 2017-01-03
You are right vasa1, adwaita in my last post is a mistake, there isn't even a gtk-widgets.css file for that theme; I only changed 7 files and all were gtk-widget.css. I'll strike it out in my last post. yeti.

---

### Post by vasa1 on 2017-01-03
> **yetimon_64 said:**
> You are right vasa1, adwaita in my last post is a mistake, there isn't even a gtk-widgets.css file for that theme; I only changed 7 files and all were gtk-widget.css. I'll strike it out in my last post. yeti.
Well, in a sense I was hoping you succeeded! Greybird, which has been my go-to theme, is using the new format in 16._10_ and I suspect that by the time the next LTS rolls out, most themes will be in the new format. I have a thread here: [https://ubuntuforums.org/showthread.php?t=2322710](https://ubuntuforums.org/showthread.php?t=2322710).

---

