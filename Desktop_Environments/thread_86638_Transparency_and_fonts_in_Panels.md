---
title: "Transparency and fonts in Panels"
date: 2005-11-05
forum: Desktop Environments
---

### Post by adam.tropics on 2005-11-05
Couple things,

Surely there must be a simple(ish) way to change the font colours in panels, so that, given transparency and dark backgrounds, we can still read txt? If not, any chance of someone far more experianced than I creating one!??

Also, probably the wrong place, but where does Amorak 1.3 go when it claims to minimise to tray/panel??

Finally, bear with me, I know nothing!!, but if it is possible to have terminal with transparency, why not gaim??

Sorry if in the wrong place for any of these asks, but hey, why write 3, when one should do!

Cheers people..

---

### Post by Manny C on 2005-11-06
[LIST=1]
[*]Are you using KDE or GNOME? If you are using KDE, see [Taskbar v.2]("http://www.kde-look.org/content/show.php?content=25615") or wait for [KDE 3.5]("http://developer.kde.org/development-versions/kde-3.5-features.html") to be released ([end of November]("http://developer.kde.org/development-versions/kde-3.5-release-plan.html")). If you are using Gnome, then consider using [gdesklets]("http://gdesklets.gnomedesktop.org/"). Both can get panel transparency working properly. I don't know what exactly you are referring to otherwise.   
[*]If you are using KDE, the Amarok minimises to the system tray. I don't know about GNOME. In fact if you are using GNOME, then it is probably better to use Banshee (a native GNOME music player).   
[*]You need to use some [special, unstable features]("http://www.ubuntuforums.org/showthread.php?t=75527&highlight=vista") of X for this to work. The transparency with terminal is faked and not a real transparency. [/LIST]

---

### Post by adam.tropics on 2005-11-06
Yep, Gnome. Used to use kde, but thought I should give it a fair go! Have gdesklets and like it, but are there any more sources around for the panel replacements? or in fact the desklets in general?

Amorak I start from a panel launcher, and i suspect, although not entirely sure that it effectivly  minimises to its own launcher (in the visual sense at least)??? Whatever, it certainly (??!!) remains in memory as clicking the launcher once it dissapears is pretty instant...Hope that makes some sense.

As for the panel, my concern really was the text colour as opposed to transparency, and yes i could use gdesklet, but with so much being configurable it surprises me that something as simple as a font colour is an issue!!

---

### Post by Manny C on 2005-11-06
Hmm...see [this]("http://ubuntuforums.org/showthread.php?t=77694") post by Artificial Intelligence. 

As for Amarok...Amarok is a KDE app. It is not optimised for use in Gnome. This is why you may be experiencing these minimising problems. Try Banshee. It is an Amarok equivalent (and some say it is even better) for Gnome. To install it simply:
```
 sudo apt-get install banshee 
```

---

### Post by agapito on 2005-11-15
I have a simple way to change the colors in the gnome panel.

In ~/.gtkrc-2.0 insert this line

include "/home/<user_name>/.gnome2/panel-fontrc"

then create the file panel-fontrc in .gnome2, which consists of the following lines:

style "my_color"
{
fg[NORMAL] = "#4353b6"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

and that's it. All you have to do is choose the color and do a killall gnome-panel. The second "widget" line affects only the applets and the first one does the rest.
To chose the color you can use the color select dialog in GIMP or, even better, use this:
[http://http://gcolor2.sourceforge.net/](http://http://gcolor2.sourceforge.net/)
it allows you to pick colors from anywhare in the gnome desktop. It compiled smothly in Hoary.

Have fun!

---

### Post by adam.tropics on 2005-11-17
Thanks for the response. gcolor2, all good, installed/working.
Not to sound thick, but where the hell would I find .gtkrc-2.0? Loads of gtkrc files, but can't seem to find that one!

---

### Post by adam.tropics on 2005-11-17
Sorry, one of those days, I have .gtkrc-1.2-gnome2 ??? But the file says:

# Autowritten by gnome-settings-daemon. Do not edit

include "/home/adam/.gtkrc.mine"


and being autowritten, rewrites itself! - my edit!

No .gtkrc-2.0

---

### Post by adam.tropics on 2005-11-17
Like I said..one of those days!!!!

If you can't find it, make it yourself!!

All working, thankyou so much. Also used same file to get rid of shadow from nautilus fonts. Makes desktop fonts far crisper....[http://www.ubuntuforums.org/showthread.php?t=89197]("http://www.ubuntuforums.org/showthread.php?t=89197")

---

### Post by agapito on 2005-11-22
It's nice to know it helped you.
Sorry for not aswering you sooner.
We all have to work sometime, right? :smile: 
By the way, thanks for the tip on removing shadow from nautilus fonts.

---

### Post by 23meg on 2005-11-22
adam.tropics : Are you sure you have a notification area on your Gnome panel? That's where Amarok is supposed to go.

---

### Post by adam.tropics on 2005-11-22
Yeah got that, but felt too hopelessly thick to post and say so!!!

Funny though, as far as i can tell, my first install didn't have one by default, but i have a feeling the second one did! I don't know, have been suffering 'forum tweak fever' of late (and i lost the notebook and pen that keep track!!), so it may well have been me.

---

### Post by 23meg on 2005-11-22
[QUOTE=adam.tropics]I don't know, have been suffering 'forum tweak fever' of late (and i lost the notebook and pen that keep track!!), so it may well have been me.[/QUOTE]
Here's something that will help you keep track if you're using Firefox: [Scrapbook]("https://addons.mozilla.org/extensions/moreinfo.php?id=427").

---

