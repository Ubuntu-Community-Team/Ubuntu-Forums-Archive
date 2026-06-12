---
title: "Gnome 3 Appearance settings/gtk theme"
date: 2011-04-20
forum: Desktop Environments
---

### Post by samstreet101 on 2011-04-20
Hi all, I know from internet searches this is a pretty common problem with the new Gnome 3 but so far I haven't found a good answer. I actually quite like the way gnome 3 works but my biggest gripe is that you can't change a damn thing without using the terminal! Not opposed to using a terminal at all but it just seems like a huge step backward. Most importantly i can't find a way to change the appearance settings such as the gtk theme, fonts, icons etc... without using gnome tweak. Anyone managed to do it?

---

### Post by Mike V on 2011-04-20
I know this is a bit of terminal but have you give it a try?

[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

---

### Post by samstreet101 on 2011-04-20
That's just it though (thanks for the reply by the way) it's using the terminal. I used gsettings to change my gtk theme myself, its not that you can't do it, i just can't believe that gnome 3, i.e. the newer version of gnome, doesn't have a gui tool for changing appearances!

---

### Post by Simian Man on 2011-04-20
> **samstreet101 said:**
> That's just it though (thanks for the reply by the way) it's using the terminal. I used gsettings to change my gtk theme myself, its not that you can't do it, i just can't believe that gnome 3, i.e. the newer version of gnome, doesn't have a gui tool for changing appearances!

Gnome has a *long* history of removing features and customization for the sake of "usability".  They may have plans to add this back, but that's also what they said about GDM 2, so who knows?

---

### Post by samstreet101 on 2011-04-20
> **Simian Man said:**
> Gnome has a *long* history of removing features and customization for the sake of "usability".  They may have plans to add this back, but that's also what they said about GDM 2, so who knows?
Yeah seems like you're right. It's such a falacy to think that removing functionality increases usability. All they needed to do was store the tools in a way that wouldn't over clutter or confuse newer users not remove them completely. I guess I'll have to get used to it as I have to say I prefer it to unity. Though I could give KDE a try, any thoughts on either of them?

---

### Post by Simian Man on 2011-04-20
> **samstreet101 said:**
> Yeah seems like you're right. It's such a falacy to think that removing functionality increases usability. All they needed to do was store the tools in a way that wouldn't over clutter or confuse newer users not remove them completely. I guess I'll have to get used to it as I have to say I prefer it to unity. Though I could give KDE a try, any thoughts on either of them?

I use KDE personally, if you like lots of features and options, it blows everything else out of the water :).

---

### Post by samstreet101 on 2011-04-20
> **Simian Man said:**
> I use KDE personally, if you like lots of features and options, it blows everything else out of the water :).
I may give it a try then :) maybe you can answer a question then, been looking through some themes for KDE on KDE-look. What is the file extension for a KDE theme? I've found a few different ones on there, slightly confusing

---

### Post by thugwithyoyo on 2011-05-04
> **Mike V said:**
> I know this is a bit of terminal but have you give it a try?

[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

I checked out this link.  It was quite helpful.  Still, it would be nice if there were a more direct way to change the appearance of gnome.

---

### Post by trusktr on 2012-05-04
The thing about GTK3 themes is that they are much more complex than GTK2 themes in terms of styling. GTK3 themes use CSS for styling, which allows a theme designer to create any number of colors and styles (not just a limited number of colors like GTK2).

What we need is an appearance editor that can read a theme's CSS file and generate an interface on the fly based on the colors detected in the CSS. It'd be similar to the interface used for Emerald themes, except for being generated on the fly.

---

