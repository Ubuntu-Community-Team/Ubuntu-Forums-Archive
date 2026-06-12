---
title: "How do I turn off animated progress bar in Gnome?"
date: 2009-05-04
forum: General Help
---

### Post by CTenorman on 2009-05-04
Hi Guys,

I'm a minimalist sort of guy some of the time, and if I'm installing or downloading something, I'd rather the progress bar wasn't animated. Just plain old solid and boring - and non-attention-grabbing!

Does anyone know how to turn off the animated progress bar in Gnome, or replace it with something I'll never notice? Thanks!

---

### Post by Tipped OuT on 2009-05-04
Change the theme to one of the more Windows like theme from the Appearance menu?

---

### Post by CTenorman on 2009-05-05
I was hoping to keep the default theme if I could. Can I change only the theme of the progress bar?

---

### Post by Tipped OuT on 2009-05-05
Haha. No. You can maybe make your own theme? Not to sure how though. What's the big deal with animated progess bars any ways? It's like complaining that your meal you ordered came with an extra drink.

---

### Post by wersdaluv on 2009-05-05
You should compile the gtk engine of your theme again in such a way that the progressbar is turned on. You're probably talking about the default Ubuntu theme using the murrine engine. If so, you should recompile murrine with progressbar animation turned off. I just don't know how to do that.

If you want, you can use a different theme altogether where the progressbars aren't animated. There is a good number of choices that are minimalist. If you haven't done it yet, you can check [http://gnome-look.org](http://gnome-look.org) :)

---

### Post by kerry_s on 2009-05-05
open gconf-editor, search animation, uncheck the ones you don't want. i think it's called "configuration editor" in the menu.
i disable them all on mine.

---

### Post by b@sh_n3rd on 2009-05-05
> **Tipped OuT said:**
> Haha. No. You can maybe make your own theme? Not to sure how though. What's the big deal with animated progess bars any ways? It's like complaining that your meal you ordered came with an extra drink.

haha, well put! :D. (If this was like FB i'd have clicked "like" under ur pic :D...yeah it's cool :D)

Well, strange how one wouldn't like the animation. To tell you the truth I'm sad about some themes I like that don't have that feature. But then again it DOES kinda slow down the PC when resources are kinda tight. Like my one without 3D acceleration. Annoying...:(

---

### Post by CTenorman on 2009-05-05
I went into gconf-editor and turned off any animation key I could see, but it still seems to do it.

I know it may seem a bit odd wanting it turned off, but I find my eyes are drawn to movement, and I don't focus quite so well on what I should be working on (writing, etc). By having the progress bar change visually only when there's actual progress, my eyes aren't distracted from their work unless something worthwhile is happening.

I was hoping there might be an easy way to simply swap out that part of a theme, but I'll have to see about recompiling or getting a new theme. Thanks for your help!

---

### Post by flyingsquirrel625 on 2009-06-07
Any more information on this?  My girlfriend gets dizzy from seeing motion.  This is a major accessibility issue for her.  Any feedback on disabling these animations would be helpful.

---

### Post by CTenorman on 2009-06-07
Perhaps we should consider filing a bug with Gnome about this as an accessibility problem? In theory when one disables "animations" in gconf, it could also disable it for any themes with progress bars.

However, I too would love to hear from anyone who has an immediate fix for this problem. If it's distracting you from doing what you want, it's not a feature.

---

### Post by strangeattractor on 2009-06-15
This is how I solved this problem.

I am using the Human theme in Ubuntu Jaunty Jackalope.  It is based on the Murrine engine.  In order to keep using the theme without having animated progress bars, I edited the gtkrc file for the theme.

How to shut off the animated progress bar in Gnome:

1. Back up your theme's copy of gtkrc.

You could do it on the command line like:
```

cd /usr/share/themes/Human/gtk-2.0/
sudo cp gtkrc gtkrc.old

```

This creates a copy of your current configuration file, named gtkrc.old, that you could use to restore your settings if you somehow screw up while editing the file.

2. Edit the gtkrc file.
```

sudo gedit gtkrc

```

You can turn the highlighting on in gedit, so the various words are different colours, by going to the View menu and choosing View -> Highlight Mode -> Others -> GtkRC

Then, in the part of the file after it says 

```
engine "murrine" {
```

change the setting for the animation from TRUE to FALSE.

```
animation = FALSE
```

Furthermore, if you want to get ride of the candy-striped appearance of the progress bar, and make it appear plain, add this line to the list of settings, in the same place.  

```
	progressbarstyle    = 0     # 0 = plain, 1 = striped
```

I put in in alphabetical order between menustyle and reliefstyle.

Then, save the gtkrc file.

3. Change themes, then back to the theme you edited.

To see the changes take effect, change to another theme, then change back to the theme you edited.  One way to do this is to go to the System -> Preferences -> Appearance.  Another way is to right-click on the desktop and choose Change Desktop Background.  Choose the Theme tab, select another theme, then select the theme you edited.  Your progress bars should now be static.

One way to easily check what the progress bars look like is to install the Widget Factory package from the Synaptic Package Manager.   Or type into a terminal:

```
sudo apt-get install thewidgetfactory
```

Then you can run it by typing into a command line

```
twf
```

This will show the various widgets used in the theme, all at once, including what the progress bars look like.

I hope this information is useful to other people who want to stop the moving progress bars.

---

