---
title: "Desktop right-click menu missing (Maverick, GNOME)"
date: 2012-03-27
forum: Desktop Environments
---

### Post by santosh83 on 2012-03-27
Hello All,

I'm using Ubuntu 10.10 (Maverick Meerkat) and primarily use the GNOME desktop, though I've got KDE, Xubuntu-desktop, LXDE, and a few others installed simply to try them out. I find GNOME 2.xx the most convenient.

But since a weeks I've noticed that the right-click menu on the GNOME desktop is missing, i.e., when I right-click on the mouse, the context menu doesn't appear.

Does anyone know of a method to fix this?

---

### Post by Tamlynmac on 2012-03-28
Just a thought, I'm wondering if your desktop is turned off. In your "system tools/configuration editor" (gnome configuration editor) under "apps/nautilus/preferences/show_desktop" is the box checked or unchecked?

If the box is unchecked no icons or context menus will show on the desktop. Thus, when you right click on the desktop, no menu will show.

One other thing I've noticed is when visual effects are turned off (None), you can also loose the desktop context menu.
"system/preferences/appearance/visual effects tab"
I've had this happen on a number of systems and immediately when the visual effects are checked to normal the context menu returned.

Good Luck & hope this helps.

---

### Post by santosh83 on 2012-03-28
> **Tamlynmac said:**
> Just a thought, I'm wondering if your desktop is turned off. In your "system tools/configuration editor" (gnome configuration editor) under "apps/nautilus/preferences/show_desktop" is the box checked or unchecked?

If the box is unchecked no icons or context menus will show on the desktop. Thus, when you right click on the desktop, no menu will show.

One other thing I've noticed is when visual effects are turned off (None), you can also loose the desktop context menu.
"system/preferences/appearance/visual effects tab"
I've had this happen on a number of systems and immediately when the visual effects are checked to normal the context menu returned.

Good Luck & hope this helps.

Awesome thanks! That was exactly the problem, and I've turned desktop back on again! I did install a "Windows 7" look-alike theme a few months ago, and I suspect that's probably what caused this configuration change, as it's uninstall script failed midway, leaving an altered panel and other changes.

I'm loath to say goodbye to GNOME 2.x, so am going to hang on to Maverick as long as possible. In my opinion GNOME 2.x hit the sweet spot between minimalism and too many bells-and-whistles.

Thanks again for the tip!

---

### Post by Tamlynmac on 2012-03-28
> santosh83
I'm loath to say goodbye to GNOME 2.x, so am going to hang on to  Maverick as long as possible. In my opinion GNOME 2.x hit the sweet spot  between minimalism and too many bells-and-whistles.

Glad it helped.

I also believe Gnome 2 is the stuff and continue to run 10.04. I'll switch to [Xubuntu]("http://xubuntu.org/") when support runs out for 10.04 in 2013. Xubuntu (XFCE) is very similar to 10.04. You indicated that you had it installed on your system - what is your opinion? Or have you not had an opportunity to try it?

I used a live cd for initial testing and then installed Xubuntu on one of our desktops. So far, it's been rock stable and we haven't had any issues with compatibility.

Mac

---

### Post by santosh83 on 2012-03-29
> **Tamlynmac said:**
> Glad it helped.

I also believe Gnome 2 is the stuff and continue to run 10.04. I'll switch to [Xubuntu]("http://xubuntu.org/") when support runs out for 10.04 in 2013. Xubuntu (XFCE) is very similar to 10.04. You indicated that you had it installed on your system - what is your opinion? Or have you not had an opportunity to try it?

I used a live cd for initial testing and then installed Xubuntu on one of our desktops. So far, it's been rock stable and we haven't had any issues with compatibility.

Mac

I have tried XFCE to a small extent. Obviously the default version of XFCE that's installed in 10.10 is a little dated (4.6) at this point, but the general feel I got was that it's VERY similar to GNOME 2.x, but a little more rough around the edges. One positive was the file manager (Thunar) is virtually an order of a magnitude faster than GNOME's Nautilus. It's menu hierarchy was however not as well organised as GNOME's, but this may perhaps be lack of integration with Ubuntu, and it should've much improved by now.

I noticed that XFCE (as it exists on 10.10) had dependencies on GNOME (Totem, volume manager etc.), which kind of defeats the point of using it as a drop-in replacement for GNOME 2.x.

But now that GNOME 2.x is gone, I think XFCE has been forced to be much more standalone, depending only on the underlying GTK3 libraries, and hopefully has no GNOME 3 dependencies.

In any case, it's the closest we'll get to GNOME 2.x on current and future Ubuntu releases I suppose! Apart from LXDE, MATE and Cinnamon.

Although you can use LXDE (lubuntu-desktop) and XFCE (xubuntu-desktop) by installing them alongside GNOME (now Unity), I noticed some inconsistencies though. Some GNOME services are still being started up under XFCE and LXDE, and the menus seem rather jumbled in the latter. You might want to try the Xubuntu/Lubuntu CD for a clean XFCE/LXDE install. :-)

---

### Post by Tamlynmac on 2012-03-29
> santosh83
 You might want to try the Xubuntu/Lubuntu CD for a clean XFCE/LXDE install.

Which is exactly what we did with our test desktop that has Xubuntu  installed. My real concern is that Canonical (at some time in the not so  distant future) decides to stop supporting Xubuntu or any other  associated distro. Simply, to focus their resources & energies on  Ubuntu/Unity.

We've also tried MATE and Cinnamon finding them lacking with respect to  resource management and speed (at least on our test system). As for  Thunar (file manager) we also found it to be some what quicker, but have  experienced some problems attempting to transfer large files. Which  isn't a huge issue, as we don't perform that task very often.

All things considered, at present we feel that Xubuntu offers us an  viable alternative. I suspect the future may hold even fewer choices.  The key in my opinion is to be flexible and willing to search for  alternative solutions. At least, until forced by technology to adopt  that which the majority defines as acceptable. :sad:

Good Luck

---

