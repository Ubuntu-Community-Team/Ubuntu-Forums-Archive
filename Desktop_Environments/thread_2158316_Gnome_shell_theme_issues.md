---
title: "Gnome shell theme issues"
date: 2013-06-28
forum: Desktop Environments
---

### Post by Tulainas on 2013-06-28
Hey everyone!

 I've been using Gnome shell 3.6 since a few months ago and i wanted to get rid of ubuntu's orange color in everything.... So I searched for a way to do it and found this: [http://antecblue.wordpress.com/2011/10/17/replace-the-orange-color-in-ubuntu-11-10-active-color/](http://antecblue.wordpress.com/2011/10/17/replace-the-orange-color-in-ubuntu-11-10-active-color/)

 I found that I was able to change colors but, from time to time, GS crashes at boot time and gives me:

 1) low resolution at startup (I can walkaroud this temporarily by executing " r " at [alt+F2] to reload the window manager, keeps happening )
 
 2) The iconset is back again to ubuntu's default plain orange. I like gnome's

 3) selection colors are back to orange + orange 



 The message i get, which I can read complete because the screen doesn let me is this one:
 (here, you can see the iconset was switched back to ubuntu's)

[IMG]http://imageshack.us/a/img27/3166/hc3l.png[/IMG]

 Here, i show you the Gnome shell's native selection blue color settings wich get messed up with ubuntu's orange colors:

[IMG]http://imageshack.us/a/img209/4827/5hz.png[/IMG]


 I've already tried to remove ubuntu-settings with no avail.

 Does anyone have a clue what could be happening?  How can I get rid of ubuntu's theme once and for all?


 Thanks!


Oh, this only happens on my desktop running Raring with an nvidia video card. Runnig Precise on the netbook behaves just nice (GS 3.4).


UPDATE: The main issue is: why GS crashes and switches themes?

---

### Post by Jonor on 2013-06-28
Install gnome-tweak-tool and change the themes from there, i also use a gnome shell extension that puts these advanced settings in the user menu for quick access.

---

### Post by Frogs Hair on 2013-06-28
The link describes a method for 11.10 which is gnome 3.2 and it is likely no longer applicable with Gnome 3,6 .

Additional Themes:  [http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=aa3d1253eff239a935216f3ba11f9707](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=aa3d1253eff239a935216f3ba11f9707)

I use this application but, it does not work with all themes and requires logout to apply changes to the whole theme .
Basic Color Change:  [http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html](http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html)

---

### Post by markbl on 2013-06-28
You want the default theme settings as used by Ubuntu GNOME? I think you can just:
```

apt-get install ubuntu-gnome-default-settings

```

---

### Post by Tulainas on 2013-06-29
> **markbl said:**
> You want the default theme settings as used by Ubuntu GNOME? I think you can just:
```

apt-get install ubuntu-gnome-default-settings

```

I've already installed it, but the problem is Ubuntu keeps going back to ubuntu's theme when GS crashes at boot.

---

### Post by Tulainas on 2013-07-01
hi there!

 Again, it was working right and, then suddenly orange colors came back!!! :-@

[IMG]http://img825.imageshack.us/img825/8254/4fa.png[/IMG]

---

### Post by Tulainas on 2013-07-02
I'm trying upgrading to GS 3.8... let's see if it improves.

---

### Post by Tulainas on 2013-07-06
Ok, I'ts been half a week since I upgraded and it kept happening:

[IMG]http://img199.imageshack.us/img199/6343/2fck.jpg[/IMG]

So it looks like it has nothing to do with Gnome-Shell... I'm opening a thread about this on the video hardware section.

---

### Post by 2Stoned on 2013-07-20
With gnome-tweak-tool you cannot change the colors used in gtk unless  you install another shell theme. When you change the icons, the colors  will remain the same.
To edit the color scheme, try installing the dconf editor and change ubuntu colors from there: 
```
sudo apt-get install dconf-tools
```

Go  to the GNOME menu. Open dconf editor. From the drop down menu --> org > gnome > desktop  > interface   --> and edit the gtk-color-scheme part. 
[COLOR=#d3b37d][/COLOR]I USE:[COLOR=#d3b37d] selected_bg_color:#D3B37D[/COLOR]

---

