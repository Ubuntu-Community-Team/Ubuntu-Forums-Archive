---
title: "Replace lousy gnome-panel with Kicker?"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by kvonb on 2007-10-21
I would like to use gnome, but I am sick to death of gnome-panel making the desktop look clunky.

It really is a neglected part of gnome, simple things like being able to change the colour of the fonts, the fonts themselves, the size of the icons, and most annoying of all is the way that some applications just don't play well with the panel backgrounds.

Things like network status icon being 1 pixel too short, netapplet having a blank white background, those damned lousy "move" handles that you cannot get rid of, they all ruin the "flow" of the menu, making it look like a duct tape and 6-inch nail affair.

I would like to run the kde menubar instead; kicker I believe it's called; instead of the lousy gnome panel.

Has anyone done this?  If so how can I do it?

Thanks, KEv :)

EDIT:  Ooops, wrong place, could an admin please move this to the relevant section?

---

### Post by overlord.gaurav on 2007-10-21
Hmmm, this would be interesting. If we're able to mix up **all** the fruitful features of KDE with GNOME, then..! ;)

Anyone tried it out??

---

### Post by kvonb on 2007-10-21
Well bugger me, it works :).

Have a look at the included screenshot.

I already had kdebase installed, and have used it on this machine before.  I would guess you simply run:

```
sudo apt-get install kicker
```

...and that should also install all the dependencies.

Now to remove all gnome-panels and put the command *kicker* into the sessions manager.

Easy as :).

---

### Post by dgrafix on 2007-10-21
What does that kicker thing offer that gnome panel doesnt then? it kinda looks the same to me (except the bkg bitmap and the way you have it layed out)

Heres how my gnome panel looks after a bit of minor jiggerypokery:
**[http://www.d-grafix.com/temp/Screenshot.png](http://www.d-grafix.com/temp/Screenshot.png) **
I like the way those buttons at either side of the bottom panel can be used to slide it off the screen and back (and the apps stretch to fill the gap :)

---

### Post by kvonb on 2007-10-21
Here is a screenshot after the modifications.

It works perfectly, but you can't easily get rid of the last gnome-panel very easily.  It can be done using the gnome configuration editor though.

Look closely, you can just see the last vestage of a gnome panel at the top centre of the screen.  I kept it just in case I need it.

You can make it extremely small and unobtrusive by using the gnome-conf-editor, press alt-f2 and type in: *gconf-editor*.

You might want to add the gnome control centre to your KDE menu to make it easier, simply add the command *gnome-control-center* to a new item.

dgrafix:

Kicker offers the ability to change font sizes/colours, change the colour of the desktop switcher background, doesn't have those annoying "handles" that you see on the ends of your panels, you have a better choice of applets, and best of all, you don't get the problem of applet backgrounds not working properly with the background.

To find out what I mean, add (through Synaptic), netapplet, you will see what I mean.  A lot of the applets I use don't handle the background properly, and it looks messy.

Plus the icons are far too big for the rest of the panel.  Your screenshot looks very nice, but the icons are as big as the panel, it looks "goombah-ish", or amateurish in my opinion.

Plus that also means that you can get less on each panel.  Which matters if you have a laptop or limited screen space as I have.

Also there are main menu replacements for Kicker, like kbfx, there is no such thing for gnome.

And try removing the *menu-bar*, and replace it with a *main menu* instead from the right-click / add to panel .  Reboot, and click on the menu button, see how long it takes to open the menu!

It's just shonky in my opinion :).

---

### Post by dgrafix on 2007-10-21
The menu certainly looks a bit better than the gnome one. Although i dont like the vista look you have got there (needs white text instead if its gonna stay like that :P) 
I see what you mean about the lack of item 'handles' too. These are annoying on the gnome one.

You can however change loads of options fot the gnome panel if you go deeper. I did most of my mods for font and colors in the  'configuration editor' Ive just scratched the surface but there are miles and miles of options for gnome in there. Prehaps theres a way to make the gnome one behave the same. Otherwise its just one extra thing to load at startup.

---

### Post by overlord.gaurav on 2007-10-21
Ok, then, currently my monitor is not operational. And I don't have ubuntu on my laptop. As soon as I get my monitor to work, I'll modify the gnome pannel as far as possible and share a few results with you guys. ;)

---

### Post by kvonb on 2007-10-21
> **dgrafix said:**
> The menu certainly looks a bit better than the gnome one. Although i dont like the vista look you have got there (needs white text instead if its gonna stay like that :P) 
I see what you mean about the lack of item 'handles' too. These are annoying on the gnome one.

You can however change loads of options fot the gnome panel if you go deeper. I did most of my mods for font and colors in the  'configuration editor' Ive just scratched the surface but there are miles and miles of options for gnome in there. Prehaps theres a way to make the gnome one behave the same. Otherwise its just one extra thing to load at startup.

Well, I'm not trying to convince you to change, I have no interest in that, you have a choice, that is one of the best things about Linux.

I might just switch to KDE totally when I go to download 7.10 in a few weeks (once the critical updates are released!), and try hard to convert myself.  I will still use Nautilus as my file manager though, it has a few features that I can't live without, like right-click make link, and other really useful right-click stuff.

Mix-and-match, make the best of what is available, and what you prefer :)

---

### Post by dgrafix on 2007-11-07
Id agree with that :)

---

