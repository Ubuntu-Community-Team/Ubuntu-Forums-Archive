---
title: "Changed icon set... can you change the icons in the window border?"
date: 2005-08-31
forum: Desktop Environments
---

### Post by VTHokie on 2005-08-31
Hey all, I'm new to Ubuntu and relatively new to linux and I really like it a lot as everything is working well but I have a couple of questions that I couldn't seem to find an answer for when searching the forums.  My first, as I said in my title is that I changed over to the nuoveXT icon set and I really like it, but the icons that are in the window border (I'm not sure how to word this right, but I mean the icons in the upper left side of a window across from the maximize/minimize/close buttons) of a program (say, firefox for example) are the same icons from the previous set.  This isn't always the case as when I open a folder in my browser, the new folder icons are used, so I'm not sure what's going on.  Is there a way to change it so the new icon set is seen in the window border as well?

My last question is  I went through the ubuntu guide and installed the media codecs but when I run a movie or any video for that matter using totem, its a little choppy.  I found a thread similar to my problem (I think) here:

[http://ubuntuforums.org/showthread.php?t=2595](http://ubuntuforums.org/showthread.php?t=2595)

but when I tried the code: sudo hdparm -d1 /dev/hdc the choppy-ness of the video files did not change when using totem.  Does anyone know how I might fix this?  Thanks in advance for any help you can offer me.

VTHokie

---

### Post by Perfect Storm on 2005-09-01
> Hey all, I'm new to Ubuntu and relatively new to linux and I really like it a lot as everything is working well but I have a couple of questions that I couldn't seem to find an answer for when searching the forums. My first, as I said in my title is that I changed over to the nuoveXT icon set and I really like it, but the icons that are in the window border (I'm not sure how to word this right, but I mean the icons in the upper left side of a window across from the maximize/minimize/close buttons) of a program (say, firefox for example) are the same icons from the previous set. This isn't always the case as when I open a folder in my browser, the new folder icons are used, so I'm not sure what's going on. Is there a way to change it so the new icon set is seen in the window border as well?

It really depends which application we are talking about. The icons are mostly shattered into the diffrent applications but some a gathered at /usr/share/piximaps or /usr/share/icons/hicolor and some a diffrent place. The best way is to look in synaptic to see where the diffrent stuff are installed.
Eg. When I want to totally change Firefox icon completly:
```

sudo cp default.xpm /usr/lib/mozilla-firefox/chrome/icons/default

sudo cp default.xpm /usr/lib/mozilla-firefox/icons

sudo cp mozicon16.xpm /usr/lib/mozilla-firefox/icons

sudo cp mozicon50.xpm /usr/lib/mozilla-firefox/icons

sudo cp document.png /usr/lib/mozilla-firefox/icons

sudo cp mozilla-firefox.png /usr/share/pixmaps

sudo cp mozilla-firefox.xpm /usr/share/pixmaps

```

As you see some of the icons go to the commen place of icons called piximaps, but some are placed in the firefox libary.
But if you post which application you want icons changed I'll help you finding it.
It's requiring a bit work to find, rename and change files.

> My last question is I went through the ubuntu guide and installed the media codecs but when I run a movie or any video for that matter using totem, its a little choppy. I found a thread similar to my problem (I think) here:

[http://ubuntuforums.org/showthread.php?t=2595](http://ubuntuforums.org/showthread.php?t=2595)


Personally Totem is a  poor choice IMHO, try with MPlayer or VCL instead. They are more reliable.


.:=The AI Dude=:.

---

### Post by VTHokie on 2005-09-02
Thanks for the help Artificial Intelligence  ;-)  First, I went with your suggestion with using VLC (I use it all the time in windows, its great) and MPlayer and the choppy video problem is gone when I use either of them.  On the icons, mostly I guess its the ones that I use primarily (thus far that is) such as the terminal, vlc, rythmnbox (sp?), and thunderbird.  Thanks again for you help.

VTHokie

---

### Post by Perfect Storm on 2005-09-02
My pleasure ^^


Okay first Thunderbird there's alot of icons they are called:
mozilla-thunderbird-menu.xpm
mozilla-thunderbird.xpm
default.xpm
mozicon50.xpm
mozicon16.xpm
messengerWindow.xpm
mozilla-thunderbird.xpm
messengerWindow16.xpm

This will completly change the thunderbird icon. Find the prefer icon you want to use instead of the default. Open gimp, rename it to all those name listed above and save it it in the same folder. Note that .xpm files can't show transparent and can look a bit choppy. Perhaps resizing the icon(s) will also be a good idea. When it's done then:

```

cd /where/you/saved/all/the/thunderbird/icons

sudo cp mozilla-thunderbird-menu.xpm /usr/share/pixmaps

sudo cp mozilla-thunderbird.xpm /usr/share/pixmaps

sudo cp default.xpm /usr/share/mozilla-thunderbird/icons

sudo cp mozicon50.xpm /usr/share/mozilla-thunderbird/icons

sudo cp mozicon16.xpm /usr/share/mozilla-thunderbird/icons

sudo cp messengerWindow.xpm /usr/share/mozilla-thunderbird/chrome/icons/default

sudo cp mozilla-thunderbird.xpm /usr/share/mozilla-thunderbird/chrome/icons/default

sudo cp messengerWindow16.xpm /usr/share/mozilla-thunderbird/chrome/icons/default

```

Terminal icons: Do the same in gimp, the icon files are called:

gnome-terminal.png
gnome-terminal.xpm
If you also want to change the root terminal it's gksu-root-terminal.png

```

cd /where/you/saved/all/the/terminal/icons

sudo cp gnome-terminal.png /usr/share/pixmaps

sudo cp gnome-terminal.xpm /usr/share/pixmaps

sudo cp gksu-root-terminal.png /usr/share/pixmaps

```

Same with Rhythmbox, the icon file is:
rhythmbox.png
rhythmbox.xpm

```

cd /where/you/saved/all/the/rhythmbox/icons

/usr/share/pixmaps/rhythmbox.png
/usr/share/pixmaps/rhythmbox.xpm

```

VLC and XXMS are tricky. I havn't found the right icons for those two applications, I suspect they icons are installed in a weird place.

---

