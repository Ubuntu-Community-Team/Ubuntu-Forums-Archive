---
title: "Editing transparency of the background title bar?"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by Death &amp; Taxes on 2007-07-14
With Compiz enabled the title bars of (inactive) windows in the background are partly transparent, as you can see here:

[IMG]http://img295.imageshack.us/img295/2861/backgrndhb4.jpg[/IMG]

However not the whole bar is transparent, just the upper half is (actually it's a gradient from transparent to solid). I was wondering whether it is possible to edit that? I'd like to have the whole bar transparent, rather than just the upper half of it. I hope it's not hard coded.

---

### Post by crimesaucer on 2007-07-14
Is that Emerald using a vrunner engine theme?

---

### Post by Death &amp; Taxes on 2007-07-14
No, that's the standard Compiz that came with Ubuntu 7.04 and a metacity theme. Didn't install anything new there.

---

### Post by crimesaucer on 2007-07-14
Sorry then, I only know about Emerald window themes.


If you do decide to install Emerald (Beryls window decorations that Compiz Fusion also uses), then you will be able to edit your themes and the different transparencies.

---

### Post by Death &amp; Taxes on 2007-07-14
I don't know. I'm glad that everything runs really fine now and I'm afraid that things may break when I play around. I don't want to reinstall the whole thing because I can't figure out why Compiz won't work again (I remember those experiments with Compiz last summer, very exciting but a pain because I had to reinstall everything a couple of times).

I was actually hoping that it's just a PNG that is mapped onto the title bar or something easy like that.

Thanks for the hint though :)

---

### Post by hyperair on 2007-07-15
Well, that looks like you're running the gtk-window-decorator. If you're using Compiz Fusion, then you should install and run Emerald.
```

sudo apt-get install emerald emerald-themes

```
Emerald gives you those fancy customizable title bars, and you can download themes for it too =)

Take a look at this screenshot, using the Vrunner-Quicksilver theme (which comes with Emerald) for Emerald.

---

### Post by Death &amp; Taxes on 2007-07-15
Well I wasn't running Compiz Fusion but I gave it a try...and it works! Didn't break anything, actually it seems to be much easier to setup. Emerald works too, yay!

Now I only need to figure out why VLC displays a partly transparent video when running fullscreen, and how I turn off transparency for the menus, but that shouldn't be a problem.

Thanks for the help guys.

---

### Post by hyperair on 2007-07-15
Go to CompizConfig Settings Manager, general settings->opacity settings->window opacities, and delete whatever is there. I think that should fix your problem.

---

### Post by Death &amp; Taxes on 2007-07-15
Yup, already found the solution in [this thread]("http://ubuntuforums.org/showthread.php?t=483542").

---

### Post by crimesaucer on 2007-07-15
> **Death & Taxes said:**
> Well I wasn't running Compiz Fusion but I gave it a try...and it works! Didn't break anything, actually it seems to be much easier to setup. Emerald works too, yay!

Now I only need to figure out why VLC displays a partly transparent video when running fullscreen, and how I turn off transparency for the menus, but that shouldn't be a problem.

Thanks for the help guys.


Ok...now that you have Emerald installed, open up the Emerald Theme Manager:


then select the theme that you would like to change, and then click: Edit themes


Now your Emerald Theme manager should look like this: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-45-11.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-45-11.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-45-12.png[/IMG]


Select the large drop down menu button that I have highlighted called "Select Engine". Each theme has a theme engine, the best two in my opinion are tru glass and vrunner.


When you click on the "Select Engine" button, it should show the "Colors" and "Frame" tabs, and the settings for Active Window and Inactive Window within the "Colors" tab.


This is where you can change any setting to make it your own theme (like mine pictured). Just save it with a new name and it will be in your list of default themes...and you won't damage the original theme that you just modified because it will still be saved under the original name.


Once you play around with all of the settings like: "Frame Engine", "Buttons", "Frame/Shadows", "Titlebar", and "Theme"...you will see how cool Emerald is....plus you can always upload any theme that you want to share.


I haven't installed a theme for 8 months, I just make my own Window decorations with the tru glass engine and what ever colors I need to match my current desktop theme.

---

### Post by Death &amp; Taxes on 2007-07-16
Thanks crimesaucer, works great!

---

