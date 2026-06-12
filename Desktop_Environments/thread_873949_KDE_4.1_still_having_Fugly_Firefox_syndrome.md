---
title: "KDE 4.1 still having Fugly Firefox syndrome?"
date: 2008-07-29
forum: Desktop Environments
---

### Post by z0mbie on 2008-07-29
I thought KDE 4.1 was going to fix all of this. I remember seeing screenshots in development where GTK apps looked gorgeous in KDE4.

---

### Post by ProbablyX on 2008-07-29
First you need to:
```

sudo aptitude install gtk-qt-engine-kde4

```

Then go into KDE settings, appearence (first row far right) then "GTK Styles and Fonts" on the left
"Use my KDE theme in GTK applications".
Then click "Install scroolbar fix..."

Now logout and login again :)

---

### Post by ibutho on 2008-07-29
> **z0mbie said:**
> I thought KDE 4.1 was going to fix all of this. I remember seeing screenshots in development where GTK apps looked gorgeous in KDE4.

The problem is not with KDE because its the Firefox that uses a different toolkit. Install gtk-qt-engine-kde4 as suggested above and hopefully that will make things a bit better.

---

### Post by z0mbie on 2008-07-29
Hey, thanks ProbablyX it helped a lot. 

Is anyone having this problem with the tabs:

[CENTER][[IMG]http://img186.imageshack.us/img186/7933/gtkkde4firefox3en9.th.png[/IMG]](http://img186.imageshack.us/my.php?image=gtkkde4firefox3en9.png)[/CENTER]

> **ibutho said:**
> The problem is not with KDE because its the Firefox that uses a different toolkit. Install gtk-qt-engine-kde4 as suggested above and hopefully that will make things a bit better.
Yeah, it looks like we'll have to wait for Qt Firefox for a better integration. Thanks for you help.

---

### Post by ProbablyX on 2008-07-29
I'm using QtCurve for buttons etc but I'm having some graphics issues too with the tabs too like colour change and graphics "falling away"

---

### Post by z0mbie on 2008-07-29
A lot of people found better results with [gtk-kde4]("http://www.kde-look.org/content/show.php/gtk-kde4?content=74689"), but I can't seem to find the dependencies to install it from source.

---

### Post by changhua on 2008-07-30
Even using the GTK/QT bits as suggested above, there is still some ugliness with the tabs.

The only options I came up with:

1. Use the Firefox add-on theme "Aero Silver Fox Basic".  While that doesn't use the native KDE4 theme, it looks better (at least with Oxygen).

2. Use the QTCurve theme (available on KDE Look and most distros' repositories) which has a unified look between its QT4, QT3, and GTK versions, even an older GTK1 version if needed.  (Note that color scheme changes don't always take for the non-QT4 version.)

I would have suggested configuring Konqueror to look like Firefox, but it still has some rendering issues, even on sites as common as Digg.

You might also try the Epiphany browser to see if that works better with the QT/GTK stuff.

---

### Post by ponkarthik on 2008-07-30
I have installed gtk-qt-engine-kde4 and Oxygen theme(addon). Its much better. But still there is a greyish ugly border around all form widgets. And check boxes are not rendered properly. They are visible only partially. On mouse overing it gets rendered but still the grey border is visible.

Karthik

---

### Post by liquidcable on 2008-08-02
Install the [Kde4 + Firefox3 0.10]("https://addons.mozilla.org/en-US/firefox/addon/7574") theme.  It's seems to work great.

You will have to register for a login, as they consider it an alpha release.  But the tabs and rendering are working fine now.

---

### Post by Xmister on 2008-08-03
> **z0mbie said:**
> A lot of people found better results with [gtk-kde4]("http://www.kde-look.org/content/show.php/gtk-kde4?content=74689"), but I can't seem to find the dependencies to install it from source.

I have just tried it, and it's much better indeed.
It lets you choose icon theme, and with that the save to dialog looks nice, just in gnome :)

And you don't have to compile it, download the first binary and copy the files to the locations as the reademe says

---

### Post by qbashi on 2008-08-03
The best distribution to try out KDE4.1 is openSuSe 11 it is more complete than Kubuntu 8.04

---

### Post by z0mbie on 2008-08-05
Hey guys good news. With the recent updates to Kubuntu the dependency issues were resolved so that means you can install [this alternative version of gtk-kde4]("http://www.kde-look.org/content/show.php/gtk-kde4?content=74689") for gtk-qt4 apps in KDE4.1. I just installed it from source, make sure you read the readme file all the dependencies are there in the repositories and make sure you enable all your repositories before you start installing. After you install that, make sure you install this [Firefox 3 theme addon]("http://ramonantonio.net/kde-firefox/"). Here's a screenshot:

[CENTER][[IMG]http://img507.imageshack.us/img507/9308/gtkkde4screenshotob8.th.png[/IMG]](http://img507.imageshack.us/my.php?image=gtkkde4screenshotob8.png)[/CENTER]

---

### Post by zeltak on 2008-08-16
Hi Zombie

im also trying to install it but i cant find a package for gtk-engines-pixmap, how did you install it?

thx

Zeltak

---

### Post by exactopposite on 2008-08-18
i used the kde4/firefox3 theme mentioned previously and i installed these 2 pacakges:

kde4-style-qtcurve-kdeconfig
gtk-qt-engine-kde4

After that firefox looks great in kde

---

### Post by kenono on 2008-09-04
I was having problems with the tabs also, I tried the KDE4 + Firefox theme, but I felt that the [Strata Aero]("https://addons.mozilla.org/en-US/firefox/addon/7390") theme (The default one for Vista) also looks just as good.

---

### Post by sayakb on 2008-09-04
Add **gnome-settings-daemon** to startup if you have Gnome installed with KDE4.1
That should bring up all themes you used on Gnome in the GTK apps you run under KDE4.1

---

### Post by sicer on 2008-09-07
> **changhua said:**
> Even using the GTK/QT bits as suggested above, there is still some ugliness with the tabs.

The only options I came up with:

1. Use the Firefox add-on theme "Aero Silver Fox Basic".  While that doesn't use the native KDE4 theme, it looks better (at least with Oxygen).

2. Use the QTCurve theme (available on KDE Look and most distros' repositories) which has a unified look between its QT4, QT3, and GTK versions, even an older GTK1 version if needed.  (Note that color scheme changes don't always take for the non-QT4 version.)

I would have suggested configuring Konqueror to look like Firefox, but it still has some rendering issues, even on sites as common as Digg.

You might also try the Epiphany browser to see if that works better with the QT/GTK stuff.

TNX MAN, I Have more fan with 1st solution :)

Thanks again, stay cool.

---

### Post by ky5566 on 2009-06-09
> **liquidcable said:**
> Install the [Kde4 + Firefox3 0.10]("https://addons.mozilla.org/en-US/firefox/addon/7574") theme.  It's seems to work great.

You will have to register for a login, as they consider it an alpha release.  But the tabs and rendering are working fine now.


Im using this theme under ff3.0.10 + kubuntu8.10. but it can not render after start firefox and freeze my machine. The GUI of firefox is black with unreadable fonts or even not display. I have to use default one. :oops:

---

