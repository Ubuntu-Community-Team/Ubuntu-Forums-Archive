---
title: "Get rid of the Black"
date: 2018-09-08
forum: Desktop Environments
---

### Post by sarisisop on 2018-09-08
Hello I'm hoping someone can help me. Since upgrading to 18 I have been searching for a solution but I'm getting nowhere. 

I hate black backgrounds as it hurts my eyes, and I would like to change the black to something like grey/silver on the following.

#1 Dock
#2 Top Bar
#3 Pop ups / notifications

I have tried the tweak tool and looked at some themes, but someone please tell me there is a simple way of getting rid of the Black.

Thank you.

---

### Post by TheFu on 2018-09-08
[https://help.ubuntu.com/stable/ubuntu-help/look-background.html.en](https://help.ubuntu.com/stable/ubuntu-help/look-background.html.en) doesn't work?

---

### Post by sarisisop on 2018-09-08
No that only changes the wallpaper background and lock screen. I want to change the black background on.

The dock where the aps are.

The top bar where the wifi sound etc are.

And preferable the pop ups.

I just want to get rid of the annoying black.

---

### Post by TheFu on 2018-09-08
Ah ... with Gnome2/3, you can use different "themes".  [https://itsfoss.com/best-gtk-themes/](https://itsfoss.com/best-gtk-themes/) has some with light menus.  Be certain that you include any non-default themes in your backup procedures. I think Aptik has a checkbox to include them.

---

### Post by jimmy-frydkaer on 2018-09-08
[http://gnome-look.org](http://gnome-look.org) has emense  amount of themes

---

### Post by sarisisop on 2018-09-08
Thank you both. But like I said I did look at some themes, but so far nothing appeals to me. And I don't see the point in installing a theme just to change one color.

All I want to do is change the black, I'll have a look at going back to 16 or seeing if I can get Unity back it was much easier and nicer.

Thank you anyway.

---

### Post by TheFu on 2018-09-08
The theme controls the color.  You can modify them.  I don't use gnome, so cannot help.  I bet there is documentation about this at gnome.org somewhere.

---

### Post by sarisisop on 2018-09-08
Maybe I'm missing something, I only switched from Windows to Ubuntu last year. 

I have been very happy even though it took me a while to get Ubuntu the way I liked it, but now with the new upgrade to 18 it's starting to annoy me.

When you say you don't use Gnome, I'm confused as I don't seem to have a choice. Can I ask what you do use as I thought this forum was about the software Ubuntu what I am using. 

Sorry if it sounds dumb, but are you saying I don't have to use Gnome ?

---

### Post by TheFu on 2018-09-08
The GUI is just another program, not the OS.
You can pick from about 50 different GUIs to use.  These can be swapped about as easily as a logout and login.  No need for a reinstall.

The GUI you see is a bunch of layers.  X/Windows at the bottom and built up from there.  The big layers are 
X11 --> Window Manager --> Desktop Environment

I just don't use any DE, which is what Gnome provides.To me, it is bloat and gets in the way. DEs are relatively new, only about 10 yrs old (I think).  Window Managers, WMs, have been around since well before I started using Unix.  Be different people like different sort of GUIs and different types of "cheese."   Cheese is  all that stuff not necessary, but it can make something taste better, if you need it. Think broccoli + cheese.  If you actually LIKE broccoli, then you don't need/want any cheese.

The major DEs are LXDE, XFCE, Mate, Unity, KDE, Cinnamon, and Gnome3.  IMHO, Gnome3, Unity and KDE are too heavy to be considered. Of the remaining, Mate is a compromise between bloat and good resource use.  Mate is based on Gnome2, I think.

You can google "ubuntu change de" for how-to guides, if you need one. [https://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](https://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/) is one result - it is from 2014, but the ideas should still be the same.  

Rather than installing each and trying them, I'd suggest visiting youtube and looking at the different desktops available there.  There are a few caveats - like always use a temporary account when testing out new GUIs/DEs. Why?  Sometimes the gonfig files with different GUIs are the same and settings perfectly valid in 1 don't work at all in the other.  Linux is multi-user, so take advantage of that and create a few temporary accounts for testing.

---

### Post by sarisisop on 2018-09-08
Mmmmmmm Thank you TheFu it's a little over my head but certainly something I need to read up on. 

I thought Ubuntu was just a substitute for Windows, plug it in away you go. I switched and was very happy, it wasn't till the 18 upgrade that I started going off it. 

But now you have explained and opened my eyes I will do some more digging. 

I prefer Cauliflower and Comté so that's what I need to find.

---

### Post by Frogs Hair on 2018-09-08
You can give the this [extension ]("https://extensions.gnome.org/extension/1011/dynamic-panel-transparency/")a try. It includes opacity settings.

---

### Post by TheFu on 2018-09-08
But editing a theme that you mostly like would be the easiest. 
[https://www.dedoimedo.com/computers/gnome-edit-theme.html](https://www.dedoimedo.com/computers/gnome-edit-theme.html)

That same author wrote a **Linux for Windows Users** introduction, with some information you may have missed.  This is the first article that I send **every** new Linux user to read. It explains so many things that are really helpful if you've been warped by using Windows.   [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)  Probably best to begin with that guide before the other.  

Looking over some of the diagrams, I see some mistakes in details most people will never need to know, but he does an excellent job explaining things.  

And because the article was written in 2014, some things have changed.  For example, there aren't any runlevels since all the main distros changed to systemd for system startup.  Runlevels (the numbers) have been around since the early 1970s on Unix and have worked well and were fairly consistent, but that all changed around 2016. Most users don't need to know much about runlevels unless they want a single-user boot or a non-graphical boot instead of the normal multi-user with GUI boot.

---

### Post by sarisisop on 2018-09-09
@Frogs Hair, I tried that but still couldn't get it to change the dock on the left hand side where all my apps live.

@TheFu, thank you for the links I will have a read.

I have managed to make the top bar tranparent by making a theme and adding the following:

```
#panel.solid {
    background-color: transparent;
    }
```

But I still can't find out how to do the same for the Dock.

Edit:

I have just installed Dash to Dock and that has given me enough options to customize the dock. I can live with that and my theme to change the top bar, I will look at changing the colour of the pop ups another day as that is not so important.

Thank you.

Edit #2 See posts below it may be of interest.

---

### Post by TheFu on 2018-09-09
Ubuntu might be using a CSS-like control language for GUI elements too. I think this was their goal when they were still working on having desktops, phones, and tablets all use the same look-n-feel.  That gave me an idea - googled ... "ubuntu 18.04 dock look and feel" Result: [https://linuxconfig.org/how-to-customize-dock-panel-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-customize-dock-panel-on-ubuntu-18-04-bionic-beaver-linux)

**Other background BEFORE I found the stuff above.**

The dock is a separate program with settings controlled some other way.  You need to track down the dock program and find which Xresources it supports. Then pretty much everything can be controlled, probably.  

Unless the programming team behind the dock didn't follow X/Windows programming standards.  

Every proper GUI has these controls.  There is a program that will dump all the X-resources that a program supports. Each of these can be controlled.  It has been decades since I did it, so I don't remember the exact methods.  Let me google ... "xresources discovery" [https://www.linuxjournal.com/article/1154](https://www.linuxjournal.com/article/1154) was the first result.

A few programs go out of their way NOT to allow local control. I suppose that is because their designers are arrogant and think they know better than we do how to best font/color/size different parts of the GUI. Last time I looked, Firefox did this. Very frustrating.   The pure X/Windows programs generally support a huge range of Xresources - xterm, xclock, xman, ... you get the idea.

---

### Post by sarisisop on 2018-09-09
> **TheFu said:**
> Ubuntu might be using a CSS-like control language for GUI elements too. I think this was their goal when they were still working on having desktops, phones, and tablets all use the same look-n-feel.  That gave me an idea - googled ... "ubuntu 18.04 dock look and feel" Result: [https://linuxconfig.org/how-to-customize-dock-panel-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-customize-dock-panel-on-ubuntu-18-04-bionic-beaver-linux)


Aha that was better. Dconf Editor is what I needed. 

It's easy in there to change the dock colour. I no longer need the Dash to Dock app. 

Shame they keep it all hidden away.

---

### Post by TheFu on 2018-09-09
I absolutely despise Dconf.  It violates 2 of the core "Unix Philosophy" tenets.
[https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)

---

