---
title: "GTK Theme won't change"
date: 2013-05-27
forum: Desktop Environments
---

### Post by CosmicFlux on 2013-05-27
Hi,

I'm trying to install a GTK theme on Lubuntu 13.04. The Metacity components (window borders & titlebar) change OK, but none of the context menus or widgets change. They are just using the default grey Metacity theme. 

I'm using the following command:

```
gsettings set org.gnome.desktop.interface gtk-theme "THEME NAME"
```

Any suggestions?


Cosmic

---

### Post by vasa1 on 2013-05-27
Lubuntu uses Openbox, not Metacity.

---

### Post by CosmicFlux on 2013-05-27
Sorry, should have made myself clear. I've manually set my session to use Metacity. But it's not the WM components I'm having issues with, just the widgets and menus. 


Cosmic

---

### Post by kansasnoob on 2013-05-27
I'm curious how you got LXDE/Lubuntu to use the Metacity WM :confused:

I'm not complaining at all, just wondering :D

---

### Post by vasa1 on 2013-05-27
> **CosmicFlux said:**
> Sorry, should have made myself clear. I've manually set my session to use Metacity. But it's not the WM components I'm having issues with, just the widgets and menus. 


Cosmic
You were quite clear about what you wanted. 

It's just that calling something Lubuntu, mentioning Metacity, and then reporting difficulties about changing themes may confuse users new to Lubuntu; they may get the impression that something is fundamentally wrong with Lubuntu when something as basic as a theme can't be changed.

For the record, it's perfectly easy to change themes in **default Lubuntu**.

---

### Post by CosmicFlux on 2013-05-27
Hi,

**Kansasnoob** - I created a custom desktop session that I can log into on startup. The idea is that modern Linux systems provide a graphical environment by default, with the option of accessing the shell through a terminal session or tty session. I have a somewhat irrational dislike for GUI's. I find them bloated and unnecessary, full of window animations and shiny effects that serve no purpose and use up system resources. As a result, I prefer accessing my system through the command line. I wrote a bash script that executes when the session starts and basically creates a command-line environment that runs on top of X, which allows me to still access graphical applications when necessary. I use Lubuntu because it's one of the more lightweight 'Buntu variants. I've included a screenshot link to give you some idea of what I mean.

[http://img203.imageshack.us/img203/4509/screenshotfrom201305271.png]("http://img203.imageshack.us/img203/4509/screenshotfrom201305271.png")
[http://img153.imageshack.us/img153/990/screenshotfrom201305272.png]("http://img153.imageshack.us/img153/990/screenshotfrom201305272.png")

**Vasa1** - I would prefer if you would refrain from answering any of my queries on this forum in future. I've suffered your 'advice' on a previous occasion and I find your tone and attitude to be somewhat harsh and dissuading. You seem more interested in lecturing than making any serious attempt to assist with a genuine query. I don't know if you are in any way affiliated with Lubuntu in any official capacity, but you seem very defensive. Linux is all about freedom and that freedom allows me to use any window manager I choose, for whatever reason I see fit and not be tied down by system defaults. That's the Windows way. I wasn't insinuating that my issue was any fault with the distro, just with my particular setup. 

If anyone else has any useful advice regarding this issue then please feel free to offer any ideas or suggestions. 


Thanks

CosmicFlux  ;)

---

### Post by mcduck on 2013-05-28
> **CosmicFlux said:**
> Hi,

I'm trying to install a GTK theme on Lubuntu 13.04. The Metacity components (window borders & titlebar) change OK, but none of the context menus or widgets change. They are just using the default grey Metacity theme. 

I'm using the following command:

```
gsettings set org.gnome.desktop.interface gtk-theme "THEME NAME"
```

Any suggestions?


Cosmic
Which theme are you trying to use, and does it contain correct versiosn of both GTK2 and GTK3 themes? Most new apps use GTK3 these days, but older ones might still be using GTK2 and the theme formats are not compatible so you ned to have both included...

---

### Post by CosmicFlux on 2013-05-28
Hi,

It's my own custom theme I'm trying to implement, and yes there is support for both GTK2 & GTK3. I've tried using some of the built-in themes too in order to eliminate any possibility of error within my own theme and they, too, do not implement. I open up **lxappearance** from the command line and it gives me the following:

[[IMG]http://img21.imageshack.us/img21/9721/screenshotfrom201305281.png[/IMG]](http://imageshack.us/photo/my-images/21/screenshotfrom201305281.png/)

I then use the dialog to navigate to my theme but when I click **Apply** the terminal window tabs do not change, demonstrated in the following screenshot:

[[IMG]http://img69.imageshack.us/img69/9721/screenshotfrom201305281.png[/IMG]](http://imageshack.us/photo/my-images/69/screenshotfrom201305281.png/)

When I close out **lxappearance** and start it up again it defaults to Raleigh, which is the theme I'm trying to replace.

I should note that my terminal is **gnome-terminal** and not the default **lxterminal**, but the themes work in the default Lubuntu session. Just not my custom session. 


Cosmic

---

