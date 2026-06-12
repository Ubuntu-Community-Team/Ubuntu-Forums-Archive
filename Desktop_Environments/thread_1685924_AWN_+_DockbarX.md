---
title: "AWN + DockbarX"
date: 2011-02-11
forum: Desktop Environments
---

### Post by quattroman on 2011-02-11
Hello all.

Does anybody has the configuration steps to get AWN with Dockbarx plugin to look like the image. 

Thanks

[IMG]https://lh5.googleusercontent.com/_1QSDkzYY2vc/TU6yZAX6hgI/AAAAAAAAC20/DEt0awQ-APA/dockbarx-0.43.png[/IMG]

---

### Post by nilarimogard on 2011-02-11
Why not ask directly on my post? :) I've actually answered to such a comment already so the answer was already there. Here it the theme: [http://dl.dropbox.com/u/1113424/webupd8-awn.tgz](http://dl.dropbox.com/u/1113424/webupd8-awn.tgz)

But to be able to use it, you need the latest AWN from the AWN PPA and to configure it, check out this video (just applying the theme won't work so watch the video): [http://www.webupd8.org/2010/10/video-how-to-customize-avant-window.html]("http://www.webupd8.org/2010/10/video-how-to-customize-avant-window.html")

---

### Post by Krytarik on 2011-02-11
> **quattroman said:**
> 
Does anybody has the configuration steps to get AWN with Dockbarx plugin to look like the image. 

I was asking me the same, the time I tried DockbarX. I now search for it in the web, and it turned out, that the new look of the preview, and the close-X were introduced in version 0.41, but Lucid users are only getting version 0.39 from its PPA, at least currently.

I now managed to upgrade its latest version, 0.43. Though this is definetely NOT the usual and safe way to install packages, but in the case of DockbarX it doesn't hurt at all, though I had to temporarily remove its theme package:
- open Synaptic
- go to "Settings -> Repositories -> Other Software"
- choose the entry of DockbarX' PPA, click on "Edit"
- enter into the field "Distribution" "maverick" instead of "lucid"
- click at "Ok", then "Close"
- then "Reload"
- filter the packages provided by the PPA with the "Origin" filter
- mark the package "dockbarx-themes-extra" for "Complete Removal"
- mark the other relevant packages for "Upgrade", in my case it was only "dockbarx", in your case at least also "awn-applet-dockbarx"
- "Apply"
- then install "dockbarx-themes-extra" again
- then choose in "DockbarX Preference" (grin) the theme "New"

---

### Post by Copper Bezel on 2011-02-11
Adding the PPA now on my Maverick machine resulted in the source being marked as a Maverick-distro PPA.

---

### Post by Krytarik on 2011-02-11
> **Copper Bezel said:**
> Adding the PPA now on my Maverick machine resulted in the source being marked as a Maverick-distro PPA.
Yeah, since you actually have Maverick! :lolflag:

---

### Post by Copper Bezel on 2011-02-11
Ah, I see. = )

I have to say, I've been doing this customization thing lately, and this is the tastiest candy to touch my display in a while. It's a damned quick way to get around, compared to using the AWN taskbar, and I don't see any disadvantages yet. Well, one - I find it odd that Intellihide doesn't work, now, acting instead as an auto-hide, but I keep the panel tiny and there's a tiny icon theme, so I don't mind that too much.

The window previews and closing apps from there are gorgeous - just gorgeous - to say nothing of the integration of the Scale plugin for multiple windows of the same app. This is something to show off to Windows people.

Hell, I'm impressed enough that OpenOffice doesn't confuse it like it does AWN's default task manager and Cairo-Dock.

---

### Post by Krytarik on 2011-02-11
Yeah, I would also prefer it over the AWN taskbar, with those new features I could try it again with AWN. Its own taskbar has a longstanding bug, that the window list looses the focus and closes immediately, when I try to select a window from it, not very cool for a taskbar, LOL. It only occurs if you have autofocus on mouseover enabled in Compiz.

Regarding the intellihide function, isn't this operated by AWN, and thus not to blame on DockbarX?

---

### Post by Copper Bezel on 2011-02-11
Yes and no. AWN's taskbar manages the intellihide function, so replacing the taskbar with DockbarX makes it stop working. It really doesn't make sense to "blame" either app.

I found the menu bug annoying, but it's not just the taskbar. Several of the widgets for AWN use that same default dialog and make them impossible to use with hover focus enabled.

---

### Post by Krytarik on 2011-02-11
> **Copper Bezel said:**
> 
I found the menu bug annoying, but it's not just the taskbar. Several of the widgets for AWN use that same default dialog and make them impossible to use with hover focus enabled.
You are most probably right. I wasn't sure if it isn't just confined to the taskbar, since I removed AWN after the trial.

---

### Post by Copper Bezel on 2011-02-11
Aha! I didn't fix your problem, but I fixed mine - all the necessary settings are present to make the AWN Taskbar empty (display only launchers, and then not give it any,) and if it's empty, it doesn't take up an icon slot, but it still manages the Intellihide function. = )

---

### Post by nilarimogard on 2011-02-12
> **Krytarik said:**
> I was asking me the same, the time I tried DockbarX. I now search for it in the web, and it turned out, that the new look of the preview, and the close-X were introduced in version 0.41, but Lucid users are only getting version 0.39 from its PPA, at least currently.

I now managed to upgrade its latest version, 0.43. Though this is definetely NOT the usual and safe way to install packages, but in the case of DockbarX it doesn't hurt at all, though I had to temporarily remove its theme package:
- open Synaptic
- go to "Settings -> Repositories -> Other Software"
- choose the entry of DockbarX' PPA, click on "Edit"
- enter into the field "Distribution" "maverick" instead of "lucid"
- click at "Ok", then "Close"
- then "Reload"
- filter the packages provided by the PPA with the "Origin" filter
- mark the package "dockbarx-themes-extra" for "Complete Removal"
- mark the other relevant packages for "Upgrade", in my case it was only "dockbarx", in your case at least also "awn-applet-dockbarx"
- "Apply"
- then install "dockbarx-themes-extra" again
- then choose in "DockbarX Preference" (grin) the theme "New"

Why not use the WebUpd8 PPA? There are DockBarX packages from Karmic to Natty: [http://www.webupd8.org/2011/02/dockbarx-applet-043-released-with.html]("http://www.webupd8.org/2011/02/dockbarx-applet-043-released-with.html")

---

### Post by Krytarik on 2011-02-12
> **Copper Bezel said:**
> Aha! I didn't fix your problem, but I fixed mine - all the necessary settings are present to make the AWN Taskbar empty (display only launchers, and then not give it any,) and if it's empty, it doesn't take up an icon slot, but it still manages the Intellihide function. = )
Cool. Noted.

---

### Post by Krytarik on 2011-02-12
> **nilarimogard said:**
> Why not use the WebUpd8 PPA? There are DockBarX packages from Karmic to Natty: [http://www.webupd8.org/2011/02/dockbarx-applet-043-released-with.html](http://www.webupd8.org/2011/02/dockbarx-applet-043-released-with.html)
Ah, finally I've got one here to ask: What is it that drives you to advise a "dist-upgrade", instead of just "upgrade" the packages?! Seriously!

EDIT: I just yet learned that the option "dist-upgrade" doesn't necessarily make apt-get to upgrade to the next version of the distribution, this article explains it very good:
[http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/](http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/)

---

### Post by Copper Bezel on 2011-02-12
> Cool. Noted.

Yeah, I'm really loving this - if Gnome Panel is a "launcher and taskbar" way of thinking about window management and AWN is a "pinned application" way of thinking about it, DockbarX, combined with Helpers, is "application widgets"; control window functions like minimize, maximize, open, and close on any application group or individual windows, access recent documents, control Rhythmbox pause and skip, etc. It's also smart about apps with weird special needs, like OOo. I've been tweaking the preferences, and I'm kind of amazed what you can do from the taskbar, generally with one click (because so many of the functions are activated by hover.) This is something that really makes the whole OS feel "cutting edge."

---

### Post by quattroman on 2011-02-14
I figured it out following the steps on the second post from the first page. Only the theme I used was the default one instead of the one provided.
I also removed the dockbarx applet and used only AWN as the icons in dockbarx where always bigger and not "flowing" with the rest of the bar.


Will mark thread as solved.

I opened another one regarding the notification daemon task bar.

---

### Post by Copper Bezel on 2011-02-14
It's by design that they look slightly different to distinguish them from the applets. That said, it is too bad that you can't control the size directly, but only through the icon themes. Still, there are several size and spacing options in there.

You really have to use Lucido to get the icons to blend in. They're not aligned with the other icons, but again, I'm pretty sure that's by design.

---

### Post by Krytarik on 2011-02-14
> **quattroman said:**
> I figured it out following the steps on the second post from the first page. Only the theme I used was the default one instead of the one provided.

The case was, that after the upgrade no theme was selected at all at my system, maybe because I had to temporarily remove the theme-pack.

However I didn't find a theme in their fairly long list that matches my taste "out of the box", but I could surely modify one into that direction, if I could get used to the general style of DockbarX. The items are just too small, but if want to make them bigger, it also increases the size of the panel, of course. And AWN is not really working that great at my 10-years-old machine, although it sits very well in the middle between honky-donk Cairo and biak Docky.;)

---

### Post by Copper Bezel on 2011-02-14
Yeah, I'm really happy with it, but my machine's under a year old.

> However I didn't find a theme in their fairly long list that matches my taste "out of the box", but I could surely modify one into that direction, if I could get used to the general style of DockbarX. The items are just too small, but if want to make them bigger, it also increases the size of the panel, of course. 

You mean because of the spacing? It looks like that depends on the theme, too. Or are you saying that they're padded? Changing the icon size in AWN doesn't change the size of DockbarX's icons at all. Am I doing something wrong?

I haven't tried creating a custom theme - I was okay with the default size and padding. I ended up using like "simple" or something.

---

### Post by Krytarik on 2011-02-14
> **Copper Bezel said:**
> 
You mean because of the spacing? It looks like that depends on the theme, too. Or are you saying that they're padded? Changing the icon size in AWN doesn't change the size of DockbarX's icons at all. Am I doing something wrong?
They just are too small for that type of function if the panel it resides on is set to 24px height, and they are getting even smaller when using the dockbar-style themes, but I don't want too give the panels even more space. So I guess I have to stick default gnome-panels until I assemble a new computer, somewhere beyond the end of Lucid's lifecycle.

Sorry, can't help with DockbarX' icons size in AWN. I installed and removed it many times, oscillating between "I want some better than gnome-panel." and "Just leave me alone.", and now it's gone, for the time being.;)

---

### Post by Copper Bezel on 2011-02-14
Ah, I see. Fair point.

I'm getting so attached to this layout that I fully intend to take it along into Gnome Shell if I can. I try to keep up with distro upgrades, though. I don't want to miss out on any of the new toys. = )

---

### Post by Krytarik on 2011-02-14
> **Copper Bezel said:**
> 
I'm getting so attached to this layout that I fully intend to take it along into Gnome Shell if I can. I try to keep up with distro upgrades, though. I don't want to miss out on any of the new toys. = )
OMG, this looks just *beeep* great, you swank!:lolflag:

---

### Post by Copper Bezel on 2011-02-15
Thanks! = )

---

### Post by quattroman on 2011-02-15
> **Copper Bezel said:**
> Ah, I see. Fair point.

I'm getting so attached to this layout that I fully intend to take it along into Gnome Shell if I can. I try to keep up with distro upgrades, though. I don't want to miss out on any of the new toys. = )



Which is the applet on the top right (task bar looking applet)?

---

### Post by Copper Bezel on 2011-02-15
More AWN, which is why it matches the dock. It's an "Always Visible"  ("Always on Top") panel with Indicator Area and Notification Area. It only differs from the icon style of the dock because the dock's all set up with custom icons.

Oh, this is kind of cool - because my GTK theme is modified to match the one I'm using with AWN, it integrates really nicely into maximized windows. The silver border meets at the edges, so it looks like it's cut out of the window.

---

### Post by arzali on 2011-02-15
> **Copper Bezel said:**
> It's by design that they look slightly different to distinguish them from the applets. That said, it is too bad that you can't control the size directly, but only through the icon themes. Still, there are several size and spacing options in there.

You really have to use Lucido to get the icons to blend in. They're not aligned with the other icons, but again, I'm pretty sure that's by design.

Im using this option to change the icon size according to the size of applets to get them in one line

[[IMG]http://uppix.net/2/e/2/e37aa6b684f64b97426857543abe9t.jpg[/IMG]]("http://uppix.net/2/e/2/e37aa6b684f64b97426857543abe9.png")

---

### Post by Copper Bezel on 2011-02-15
That's for the AWN icons, though. It doesn't affect DockbarX's, and there doesn't seem to be an equivalent option within DockbarX's configuration - the icon size is set by the DockbarX theme, which of course you could probably modify in text form (I assume, as I haven't tried it.)

In other words, if you look at the first screenshot I posted, the DockbarX icons are slightly larger than the widgets on the left and right sides of them. I prefer it that way, so this isn't a problem for me, but it is something to note if you're planning on using DockbarX in AWN.

---

### Post by arzali on 2011-02-15
I am using dockbarx with awn :)

the offset changes only the size of my dockbarx icons see here:

[[IMG]http://uppix.net/4/c/1/fdf30ee67610d51a80dade457bafft.jpg[/IMG]]("http://uppix.net/4/c/1/fdf30ee67610d51a80dade457baff.html")

of corse you could change the icon size with the config file by editing 
    <get_icon size="-13" />
but if you like it that way its fine :)

---

### Post by Copper Bezel on 2011-02-15
Intriguing. That setting's not changing the size of my DockbarX icons, but it definitely lined them up nicely - thanks for both tips!

---

### Post by quattroman on 2011-02-16
> **Copper Bezel said:**
> More AWN, which is why it matches the dock. It's an "Always Visible"  ("Always on Top") panel with Indicator Area and Notification Area. It only differs from the icon style of the dock because the dock's all set up with custom icons.

Oh, this is kind of cool - because my GTK theme is modified to match the one I'm using with AWN, it integrates really nicely into maximized windows. The silver border meets at the edges, so it looks like it's cut out of the window.

How did you manage to have two (2) awn running at the same time?

---

### Post by Copper Bezel on 2011-02-16
I'm not, it's just a separate AWN panel. arzali seems to be using a similar layout, but you can have as many as you want - just go to Dock Preferences and click New Panel, same as with the Gnome Panel.

---

### Post by quattroman on 2011-02-16
Thanks.

---

### Post by puntigamer on 2011-02-20
Nice dock, but I used to use Docky for a long time... Anyway, I give it a try ;)

---

