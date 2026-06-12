---
title: "GTK theme editing"
date: 2018-05-11
forum: Desktop Environments
---

### Post by kazakore on 2018-05-11
I've come to mostly like Adwaita Dark theme, it has one issue which I've been trying to work out how to edit the theme to get rid of. Unfortunately I can't take screenshots of what I mean as the action of taking the screenshot removes focus briefly and thus the highlight on the selected button disappears.  In short I want to be able to see which button is highlighted for selection with the Return/Enter key! 

Unfortunately it seems the Adwaita uses images for buttons, whereas Blackbird, Nodoka-Dark and all the other ones where this works done and I'm at a bit of a loss. I've tried editing various things on a copied  version of the theme and seem to have managed to change how the mouse-over is displayed, but not the active button for keyboard selection.

Any ideas?

This is the original main.rc file from Adwaita-dark: [https://paste.ubuntu.com/p/Sg6Kp3gDVp/](https://paste.ubuntu.com/p/Sg6Kp3gDVp/)

---

### Post by dino99 on 2018-05-12
If you are ready to tweak css hardcoded theme, then go with a custom renamed copy; but the second question is about gnome-shell ready to recognize such options ?

---

### Post by kazakore on 2018-05-12
> **dino99 said:**
> If you are ready to tweak css hardcoded theme, then go with a custom renamed copy; but the second question is about gnome-shell ready to recognize such options ?

Obviously that's what I was doing.

> I've tried editing various things on a **copied  version of the theme**

They do still have the same name in the selection list but I can live with that for testing purposes.

I did find the button section was missing the SELECTED attribute option that most other things had but adding this made no difference.

I also then noticed that many windows it does show the selected item, so wondered if it's a gtk2 vss gtk3 thing and pretty much gave up....



Currently gone back to using another one which is close but not quite there is a different area. Wish I did have more time to learn properly the ins and outs of how to configure a theme but I have far too many other projects I need to get finished to start another one in earnest! ;)


EDIT: Ahhh I've remembered what I don't like about this Theme (Blackbird.) You can't very easily see what has been highlighted on programs where it has correctly given me a dark background (including Mousepad and Gedit, which many dark themes miss even changing in the first place.) I wonder if that will be an easier niggle for me to edit and fix myself though....

---

### Post by cruzer001 on 2018-05-12
Changing the theme name these days will not work unless it is also changed in "settings.ini".

I have placed my theme modifications in /.config/gtk-3.0/gtk.css which will give system wide modifications on any theme you run.  I use this file to modify scrollbars and remove popups on any theme I run.

---

### Post by kazakore on 2018-05-12
> **cruzer001 said:**
> Changing the theme name these days will not work unless it is also changed in "settings.ini".

It's working fine for me as long as I edit the name in the index.theme file. Maybe that's because XFCE treats it different to Unity, or whichever DE you are using.

> I have placed my theme modifications in /.config/gtk-3.0/gtk.css which will give system wide modifications on any theme you run.  I use this file to modify scrollbars and remove popups on any theme I run.

When I tried installing themes in Home they didn't seem to be picked up so I'm editing them in the system folder. Probably not the best idea but I am doing it to copies and it's not the worst thing you could break....

But I have defininitely found it is gtk3.0 which is getting me issues. I have edits of the gtk2.0 side on a number of the dark themes I could be happy with but all of them still have something which doesn't look right to me in gtk3.0 programs. (This I have discerned by using apt-cache show <package> and seeing which libgtk version it depends on.) So by making a file as you mention above I should be able to override this settings from the theme's default?

One of them only has a single line in its gtk3 folder and I can't quite work out where it's pointing to for the resource. It looks like a dconf path but doesn't seem to match up when I check with dconf-editor.....
```
@import url("resource:///org/gtk/libgtk/theme/Adwaita/gtk-contained-dark.css");

```

Probably going to stop for today. Blackbird I could be happy with if I open any textual files with sublime so probably going to go with that, at least for the moment.....

---

### Post by cruzer001 on 2018-05-12
Here's what I got going on in /.config/gtk-3.0/gtk.css

```
scrollbar slider {
    /* Size of the slider */
    min-width: 15px;
    min-height: 15px;
    border-radius: 17px;

    /* Padding around the slider */
    border: 2px solid transparent;
}

scrollbar trough {
  background-color: #E6EFE3;
}

scrollbar button,
scrollbar button.vertical,
scrollbar button.horizontal,
scrollbar .button,
scrollbar .button.vertical,
scrollbar .button.horizontal {
    color: shade(@theme_bg_color, 0.4);
    background-color: shade(@theme_bg_color, 0.7);
}

scrollbar.vertical slider,
scrollbar.vertical .slider {
    background-image: radial-gradient(ellipse at center, #F3F3F3 0%, #87A77C 100%);
}

scrollbar.horizontal slider,
scrollbar.horizontal .slider {
    background-image: radial-gradient(ellipse at center, #F3F3F3 0%, #87A77C 100%);
}

tooltip {
    opacity: 0;
}
```

I like a static and wide scrollbar which this will give me.  I also customize the colors, you will need to change colors to taste if you use this.

I also dislike tooltips popping up and the last three lines removes most of them.

I do run a custom gnome desktop, but I would think this should work on any gtk3 theme.

---

### Post by kazakore on 2018-05-12
Got it to something I think I happier with than any of my previous installs. Rather a hack though....

It seems Greybird has a number of options that should be selectable but it wasn't obvious now to do so from XFCE. These appear to affect GTK3+ so as you suggested I edited the ~/.config/gtk3.0/gtkrc file to contain:
```
gtk-application-prefer-dark-theme=true
```

This gave me GTK3 windows looking reasonable and being usable, including buttons selected and highlighted text both being visible (my usual two failings with the themes.) But GTK2 apps still were taking the light themes. So I copied the gtk-2.0 folder from my edited version of Blackbird (which I assumed must be an exported version of the dark Greybird but as it doesn't work across everything guess it's not) into my copy of the Greybird folder to give me the other apps looks as I desired.

It's not perfect but I'm happy enough with this for at least a while. Thanks you for the pointers, they definitely helped :)

---

### Post by cruzer001 on 2018-05-12
I will also have to keep your (above) trick in mind :)

See ya

---

### Post by kazakore on 2018-05-12
Advanced question:

Any idea, or any luck, getting Qt5 programs to follow the GTK theme? Checked two of my most common used programs which don't follow the theme and they're both using Qt5. I have checked the line in Trolltech.conf and tried setting the environment variable as per this Arch wiki page to no avail....

[https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications](https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications)

---

### Post by kazakore on 2018-05-13
> **kazakore said:**
> Advanced question:

Any idea, or any luck, getting Qt5 programs to follow the GTK theme? Checked two of my most common used programs which don't follow the theme and they're both using Qt5. I have checked the line in Trolltech.conf and tried setting the environment variable as per this Arch wiki page to no avail....

[https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications](https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications)

Think this was working in 16.04 thinking back to it, my notification bubbles for Qasmixer definitely took the dark theme and think the main app did too. They don't on 18.04 though.....

---

### Post by kazakore on 2018-05-13
BINGO!!

Use the qt5ct package and instructions on this page, then restart and qt5 apps are showing with the dark theme :)

[https://wiki.archlinux.org/index.php/Qt#Configuration_of_Qt5_apps_under_environments_other_than_KDE_Plasma](https://wiki.archlinux.org/index.php/Qt#Configuration_of_Qt5_apps_under_environments_other_than_KDE_Plasma)

---

### Post by cruzer001 on 2018-05-13
Nice find

You must of installed some qt base apps, I don't see any on my Gnome install.

But still nice to know if I ever do :)

---

### Post by kazakore on 2018-05-13
Qasmixer and VLC are the only two I know for sure, really don't like Parole and I run a purely Jack Audio environment so use Qasmixer with it's system tray icon to replace the stock audio mixer (Ubuntu Studio here, so XFCE on the whole.)

---

