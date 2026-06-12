---
title: "Gnome makes my favorite KDE applications look ugly"
date: 2009-07-07
forum: Desktop Environments
---

### Post by papajonesy on 2009-07-07
Hello friends. There are two KDE applications that I love, Kopete and Amarok. I have made my Ubuntu eye candy heaven, but when I use either of them they are all default grey with the exception of the window's title bar, I have an extremely sexy black theme and would like to keep the consistency. Can anyone tell me if there is a way to keep the theme even while using KDE apps? Thanks guys

---

### Post by Pogeymanz on 2009-07-07
Run qtconfig-qt4 and change the style to gtk+.

If you don't have that app already, install it via Synaptic.

If that doesn't work, that means that they are qt3 apps, and you should search Synaptic for 'qt gtk' and find whichever app it is that makes your qt apps match your gtk apps.


In case you didn't know, Gnome uses a window toolkit called GTK, whereas KDE uses the QT toolkit. Both have strengths and weaknesses, but also have to be themed separately.

---

### Post by morganpatrick on 2009-09-18
I think something must have changed with kde or gnome or something because this doesn't work. I can change things in qtconfig and they never actually show in the application.

On top of that, kcontrol is no longer in the repos for ubuntu. I think you have to install half the kde desktop to tweak the styles.

---

### Post by morganpatrick on 2009-11-19
[This is the ONLY solution I have found that works perfectly.]("http://ubuntuforums.org/showthread.php?t=1012759")

---

### Post by oldos2er on 2009-11-19
> **morganpatrick said:**
> [This is the ONLY solution I have found that works perfectly.]("http://ubuntuforums.org/showthread.php?t=1012759")

 Has anyone tried this wth 9.10, and KDE4.x ?

---

### Post by captaincrook on 2009-11-19
That (the link provided above) is listed for QT3 apps, so if you're using the latest Amarok/Kopete apps it won't work as they have moved to QT4. QT4-Config SHOULD work. Fire it up, change the "Select UI style" to "GTK+" and make sure to save the settings. Restart the apps. If this fails, try reinstalling QT Config and deleting the Trolltech.conf located in ~/.config.

For QT3 I'm not sure.

---

### Post by morganpatrick on 2009-12-09
oldos2er:

Here is the solution and then I'm going to mark this as solved, because it virtually is:

**KDE3:**

[do a google search for human.kcsrc]("http://www.google.com/search?q=human.kcsrc"). 

Then, like in the other tutorial, get kcontrol, the old program that controlled kde3, from the old hardy repos: [amd64]("http://packages.ubuntu.com/hardy-backports/amd64/kcontrol/download") | [URL="http://packages.ubuntu.com/hardy-backports/i386/kcontrol/download"]i386
[/URL]

Then unpack it to a temp directory. Copy all these into /usr/lib/kde3 (you'll need to be root):

~temp/usr/lib/kde3/kcm_icons
~temp/usr/lib/kde3/kcm_colors
~temp/usr/lib/kde3/kcm_fonts
~temp/usr/lib/kde3/kcm_style

and copy these to /usr/share/applications/kde (as root)

~temp/usr/share/applications/kde/icons.desktop
~temp/usr/share/applications/kde/colors.desktop
~temp/usr/share/applications/kde/fonts.desktop
~temp/usr/share/applications/kde/style.desktop

Then in a terminal you can type:
> kcmshell colors


and import the human color scheme mentioned above. ymmv on this -- I got a really perfect color scheme but I can't remember where i got it. try d/ling a couple and look on kde-look.org too. Keep in mind this will look like pre-karmic Ubuntu unless you can find a Karmic color scheme, but either way it will look better than the default KDE3.

> kcmshell style

And pick Plastik. It's not exactly the same but you'll see with your new color scheme it blends just right.

> kcmshell icons

And pick your Human icons or whatever you use instead. I use Tango and when I intalled them for GTK they automatically showed up here.

> kcmshell fonts

And change them. I think the Ubuntu default is sans 10 or deja vu regular 10.

[B]
KDE4:[/B]

This is easier. Install systemsettings and kdeartwork. Then in a terminal type:

> systemsettings

it should be easy to figure out from here. Change style to GTK and icons and fonts the same as above.

After this you'll see that if you go from your Ubuntu desktop to kde4 apps like kdenlive and digikam, and then to kd3 apps like basket and amarok 1.4, you will have a nice, consistent visual user experience.

Let me know if it works!

---

### Post by morganpatrick on 2009-12-09
Oh right it's not my thread so I can't mark it solved. It is, though, finally.

edit// one more thing: in Amarok, go to Settings > Configure Amarok > Appearance and uncheck "Use custom icon theme" and restart. Now Amarok 1.4 looks like everything else.

---

### Post by raditzman on 2010-10-10
It kinda works, because selected items in the menus show the distinctive orange color scheme, but the background of the window is still a dull grey.

---

### Post by claracc on 2010-10-12
Morganpatrick it works ( I didn't need to install kdeartwork) for kde4.

Now K3b, ktorrent, kalzium and other kde apps appears  more like gnome ones.

Only a problem, in my gnome appearance I have selected a whiteglass pointer as bigger as possible but each time I run a KDE app the size of pointer (cursor) is very small. Or if in panel I move pointer over ktorrent minimized the cursor is shown very small ¿¿??.

Thanks and regards

---

