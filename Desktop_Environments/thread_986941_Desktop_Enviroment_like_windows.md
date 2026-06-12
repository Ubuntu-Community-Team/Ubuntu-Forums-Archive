---
title: "Desktop Enviroment like windows"
date: 2008-11-19
forum: Desktop Environments
---

### Post by patilkaustubhv on 2008-11-19
Which is the Desktop Enviroment that resembles closest to the Windows or can be similarly be used like windows....


Please do paste the links to download that particular enviroment (if possible..........):popcorn:

---

### Post by patrickballeux on 2008-11-19
If you want something that looks more like Windows, use KDE.  There are others Window Managers, but they do not have features that KDE has.

Basically, you have 3 mains Window Managers:

* Gnome : Ubuntu default: More like Macs
* Kde   : Kubuntu default: More like Windows
* XFCe  : Xubuntu default: More like Macs but lighter

So install Kubuntu or if you already installed Ubuntu, simply install the package "kubuntu-desktop" using the Synaptic manager.  No need for links as everything is in the reporsitories, ready to be downloaded and installed.

You should find KDE more to your liking is you are looking for somethink like the Windows GUI.

Me, I prefer Gnome, simpler, easier...

Tip:  To install something in (X)(K)Ubuntu, don't donwload from any site, use your Synaptic manager (System - Administration) to install your softwares.  So you'll benefit from the update and make sure that the source can be thrusted.  It's a bad habit from Windows to download and install from a website what your looking for... :)

Good luck!

---

### Post by Zorael on 2008-11-19
Neh, I'd say that the only thing about KDE that labels it "Windowsy" is the fact that it, per default, has its panel at the bottom of the screen, and that the links to applications, settings etc are gathered into one button rather than several menus, as the case is with Xfce and GNOME.

Everything's very malleable; you can delete GNOME's lower bar, add a task manager to the upper one and then move the whole bar to the bottom of your screen. Then you have a setup akin to what you'll get when first starting up KDE. Likewise, you can break out all menus and the "systray" applet into its own bar at the top of the screen, leaving only the task manager and the pager at the bottom panel, GNOME/Xfce-esque.

I'd say that the one thing that would give the most Windowsy oomph would be to find a Vista/XP theme for whatever desktop environment you decide to go with. If you do go with KDE, you should be able to change the menu button into something that looks like a start button. Perhaps there are already themes like this over at [http://kde-look.org](http://kde-look.org), I'm not sure. Also, there's [http://gnome-look.org](http://gnome-look.org).


When calling GNOME "simpler [and] easier", keep in mind that some settings simply cannot be altered without popping up a gconf editor (think registry editor for Windows). Also, KDE is at a generation shift from KDE 3.5.1x to KDE4, and as such it will likely still take a few releases to get everything fleshed out. Xfce is made to be lighter stuff, so you may find it less configurable. KDE4 has its Plasma gadget layer, so if you like Mac-y applets that might be something to look into.

Get live cds of all three versions - Ubuntu, Kubuntu, Xubuntu - boot them up, and evaluate the interface. Colors and stuff can be changed with themes.

---

### Post by ad_267 on 2008-11-19
I say Gnome, just remove the top panel, then get a button that says "start" and use the menu with a single button. What other Windows like features do you need? There are plenty of themes on gnome-look that look like different Windows versions.

---

### Post by fiendishfish on 2008-11-19
One question:

I don't understand why one would WANT to have Linux look like Windows, isn't it 'part and parcel' of using Linux, loosing Windows loving tendencies?

-fiendishfish

---

### Post by patrickballeux on 2008-11-19
> **Zorael said:**
> 
When calling GNOME "simpler [and] easier", keep in mind that some settings simply cannot be altered without popping up a gconf editor (think registry editor for Windows). 

Just out of curiosity, why do you need to open the gconf editor in Gnome?  I mean, I use it everyday, applied a theme, changed some fonts and color, set a background but I never had to go in the gconf to "set" something.

The only time I have to go in there is when I "geek" around some new software or want to debug something.

I understand that KDE has a tons of setup that you can change and that's why I like GNome, there is none of that.  Just basic stuff that I need:  Easier, simpler.  

I'm not really into customizations of my desktop as I mostly work with a computer, but for sure that if your like setting everything to your taste, Gnome can be frustrating (screensavers for example :)  )

---

### Post by patrickballeux on 2008-11-19
> **fiendishfish said:**
> One question:

I don't understand why one would WANT to have Linux look like Windows, isn't it 'part and parcel' of using Linux, loosing Windows loving tendencies?

-fiendishfish

Linux is not about hating Windows and denying it.  It's about freedom and choice.  If one prefer the Windows GUI or way to work, that's his choice.

Remember, Linux is not a religion, it's a choice.

---

### Post by ramaswamyps on 2008-11-19
kde can be configured to behave and look like windows

---

### Post by fiendishfish on 2008-11-19
> **patrickballeux said:**
> Linux is not about hating Windows and denying it.  It's about freedom and choice.  If one prefer the Windows GUI or way to work, that's his choice.

Remember, Linux is not a religion, it's a choice.


Fair point, I do see where you're coming from, but personally think it's freaky.

</offtopic>

---

### Post by Yownanymous on 2008-11-19
I find that the features with Enlightenment E17 look a lot like Vista's dreamscene. Unfortunately there's a lot of bugs and consequent crashes.
[http://seerofsouls.com/]("http://seerofsouls.com/")

---

### Post by win4thebin on 2008-11-19
Try XpDE a desktop environment that looks like windows xp but doesn't do much else. but i don't see the point in linux looking like windows.

---

### Post by Zorael on 2008-11-19
> **patrickballeux said:**
> Just out of curiosity, why do you need to open the gconf editor in Gnome?  I mean, I use it everyday, applied a theme, changed some fonts and color, set a background but I never had to go in the gconf to "set" something.

The only time I have to go in there is when I "geek" around some new software or want to debug something.
Naturally the most common settings can be modified via the normal interface. I haven't tried the version bundled with Intrepid yet, either. Can you change window managers outside of gconf-editing nowadays? Toggling and configuring icons displaying on desktop, boolean display/don't and other stuff like whether mounted devices should show or not? Desktop background color before wallpaper is applied (after logging in)?

> **patrickballeux said:**
> I understand that KDE has a tons of setup that you can change and that's why I like GNome, there is none of that.  Just basic stuff that I need:  Easier, simpler.
Many agree with you. I, on the other hand, find GNOME to be needlessly complicated when configurability is stashed away in gconfs, and KDE's stance toward having it all in a GUI "control panel" to be a desirable trait. I like to go through the settings and just think, "what can I tweak today?". Arguably I could do that in a gconf editor, too. Just... messier. Less intuitive. Harder.

I *stress* the point that new users should try all the three flavors (Ubuntu, Kubuntu, Xubuntu) before deciding. Ubuntu is the one that hits the news, so people default to it (and by extension, GNOME) without ever trying KDE nor Xfce. Each environment has its merits, and none is for every user and every system.

As far as the thread and its discussion topic goes, it is generally *environment-irrelevant*. The key is theming, I'd say.

I'm keeping myself in check; these threads have a tendency to degenerate into GNOME vs KDE wars. Then we get the usual FUD thrown between the two camps; "GNOME is stupid and simple and lacks functionality" vs "KDE is heavy and slow and if you like it you're just a Windows user who can't think outside the start menu", etc.


edit: As for why anyone would want it to look like Windows, don't judge. :3 Perhaps he wants to make a point that Linux is a valid system, without making it into too much of a cultural shock when you lose the start menu and Luna theming. Anyway, Linux is all about choice, so we should encourage it, instead of questioning it.

---

### Post by airtonix on 2008-11-19
> **Zorael said:**
> Neh, I'd say that the only thing about KDE that labels it "Windowsy" is the fact that it, per default, has its panel at the bottom of the screen, and that the links to applications, settings etc are gathered into one button rather than several menus, as the case is with Xfce and GNOME.


But of course i can make gnome behave this way too.


[LIST=1]
[*]remove top bar.
[*]insert secondary gnome mennu in bottom bar,
[*]insert systray in bottom bar,
[*]insert time app in bottom bar,
[*]insert window list in bottom bar,
[/LIST]
But of course you already mentioned this.

But i disagree with your assesment of the gConf, as it is not like the windows registry.

for a start, gConf is a collection of xml files found in your home folder and system folders. Any changes made to these ascii xml based files is reflected instantly.

windows registry is a binary blob, you can only edit it with regedit. and because it is a singular binary blob, it is far more prone to corruption.

It even takes longer to search through.                                                                                               __________________

---

### Post by Zorael on 2008-11-19
> **airtonix said:**
> But of course i can make gnome behave this way too.


[LIST=1]
[*]remove top bar.
[*]insert secondary gnome mennu in bottom bar,
[*]insert systray in bottom bar,
[*]insert time app in bottom bar,
[*]insert window list in bottom bar,
[/LIST]
Um, yeah. I, uh, said as much in the very next paragraph.
> Everything's very malleable; you can delete GNOME's lower bar, add a task manager to the upper one and then move the whole bar to the bottom of your screen. Then you have a setup akin to what you'll get when first starting up KDE. Likewise, you can break out all menus and the "systray" applet into its own bar at the top of the screen, leaving only the task manager and the pager at the bottom panel, GNOME/Xfce-esque.

---

### Post by airtonix on 2008-11-19
doublepost, apologies.

---

### Post by Zorael on 2008-11-19
> **airtonix said:**
> But i disagree with your assesment of the gConf, as it is not like the windows registry.

for a start, gConf is a collection of xml files found in your home folder and system folders. Any changes made to these ascii xml based files is reflected instantly.

windows registry is a binary blob, you can only edit it with regedit. and because it is a singular binary blob, it is far more prone to corruption.
Your edit invalidates my previous reply, naturally. :3

But don't you agree the user interface is largely analogous to the Windows registry? Ignoring, for the sake of the argument, the inner workings of both - not to mention the fact that the registry is an abominable mess.

---

### Post by patrickballeux on 2008-11-20
Hi,

> **Zorael said:**
> Naturally the most common settings can be modified via the normal interface. I haven't tried the version bundled with Intrepid yet, either. Can you change window managers outside of gconf-editing nowadays? Toggling and configuring icons displaying on desktop, boolean display/don't and other stuff like whether mounted devices should show or not? Desktop background color before wallpaper is applied (after logging in)?


I totally agree with your.  That's the kind of setting I don't care about so that would explain why I'm happy with Gnome.  KDE is more suitable is you want to go further into setting your desktop to your liking.

I tried KDE 4.x, and I must admit that I was tempted ...  :)

Thanks for your fair answer.

Pat

---

### Post by apmcd47 on 2008-11-21
> **patrickballeux said:**
> Linux is not about hating Windows and denying it.  It's about freedom and choice.  If one prefer the Windows GUI or way to work, that's his choice.

Remember, Linux is not a religion, it's a choice.

Choice! I'd love choice!

KDE -> Windoze wannabe
Gnome -> KDE wannabe
XFCE -> CDE wannabe.

So between KDE and Gnome (in my opinion) there is no real choice. KDE is better integrated and looks nicer, which is why I use KDE. I'm not sure what the Xubuntu developers are on - they've made their XFCE look like Ubuntu's Gnome with two panels top and bottom (presumably Gnome went that way to make it look less like KDE?) If you look at the screenshots on the XFCE web site ([www.xfce.org](www.xfce.org)) you will see that they use a single "front panel" by default.

I don't understand the idea that application launchers should clutter the desktop and iconised windows should be in the task bar. Application launchers should be in the task bars (toolbars in Windoze; panes in KDE/Gnome). XFCE had it right, but with Version 4 they seem to have been drawn into the Dark Side. They seem to have put the iconised windows back onto the desktop with 4.1 or 4.2, but it's an option which you have to turn on, and you cannot change the default positioning of the icons. At least you couldn't. I need to have another look.

And don't get me started on the KDE menu!

Bring back Sun View - all is forgiven!

---

### Post by Temporary Saint on 2008-11-25
[QUOTE=patrickballeux;6209266]
So install Kubuntu or if you already installed Ubuntu, simply install the package "kubuntu-desktop" using the Synaptic manager.  No need for links as everything is in the reporsitories, ready to be downloaded and installed.
QUOTE]

If I install "kubuntu-desktop" from Synaptic and I'm running HH8.04 will I automatically get the latest version of KDE?  I'd prefer KDE 3.5.10, not 4.X.

Steve

---

