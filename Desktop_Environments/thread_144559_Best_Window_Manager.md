---
title: "Best Window Manager"
date: 2006-03-14
forum: Desktop Environments
---

### Post by tigrez on 2006-03-14
A simple question. Which's more faster or more usable?
:p

---

### Post by Zelut on 2006-03-14
Thats a pretty loaded question :).  People could argue for months over KDE & gnome (and they do).  

If you want my opinion I like Xfce for my personal box (lightweight & barebones) & gnome for my other machines.

---

### Post by shakin on 2006-03-14
Window manager as in Kwin, Metacity and Fluxbox? Or desktop environment as in KDE, Gnome and Xfce.

I prefer KDE and I think it's faster than Gnome. It's definitely got more features. Xfce in Ubuntu has never worked right for me (very slow in Dapper right now, probably because of its composite manager that I haven't found a way to turn off except possibly through the GUI, which is too slow to use).

Window managers are lighter, but provide fewer features than a desktop environment. Desktop environments use window managers to draw the windows. KDE uses Kwin and Gnome uses Metacity. I've used Enlightenment, Blackbox and Fluxbox as alternatives to Kwin and Metacity with KDE and Gnome. I've also used a number of window managers on their own. Personally, I don't think they offer enough features to be very usable unless you want to spend a lot of time figuring out new ways to use your computer that work well with your chosen window manager. As replacements for Kwin and Metacity they don't integrate well enough into the desktop environment and are often heavier on the RAM. Kwin in particular is quite light.

---

### Post by sandyeggoboy on 2006-03-14
Ok so here is another possibly loaded question ... how is one able to then install Ubuntu Dapper, and then load XFCE, then un-install the gnome environment? nor should i just leave them both on there just in case?

---

### Post by mrgnash on 2006-03-14
Fluxbox>The Rest.

---

### Post by Adrian on 2006-03-14
[QUOTE=sandyeggoboy]Ok so here is another possibly loaded question ... how is one able to then install Ubuntu Dapper, and then load XFCE, then un-install the gnome environment? nor should i just leave them both on there just in case?[/QUOTE]

To install XFCE, just install the **xubuntu-desktop** package. It's in the universe repository.

Check out this thread about uninstalling GNOME:
[http://www.ubuntuforums.org/showthread.php?t=96046](http://www.ubuntuforums.org/showthread.php?t=96046)

However, having multiple desktop environments can be really nice :)

---

### Post by Bolverk on 2006-03-14
[QUOTE=Adrian]However, having multiple desktop environments can be really nice :)[/QUOTE]
Oh yeah. I use KDE for everyday work and Fluxbox for gaming. Works great. \\:D/

---

### Post by sYs^ on 2006-03-27
Is it possible to change metacity to a faster windowmanager but use gnome?

for example use fluxbox as window manager but use gnome as desktop enviroment?

---

### Post by Joshuwa on 2006-03-31
[QUOTE=sYs^]Is it possible to change metacity to a faster windowmanager but use gnome?

for example use fluxbox as window manager but use gnome as desktop enviroment?[/QUOTE]

Yes, I just replaced Metacity w/ OpenBox in Gnome the other day.

```
sudo apt-get install openbox obconf
```

```
openbox --replace
```

```
gnome-save-session
```

is what I did (obconf is a graphical configuration tool for openbox).

I prefer openbox to fluxbox; nearly the same, but ob seems a bit quicker.

---

