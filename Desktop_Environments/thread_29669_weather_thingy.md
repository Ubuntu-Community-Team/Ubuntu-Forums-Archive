---
title: "weather thingy"
date: 2005-04-25
forum: Desktop Environments
---

### Post by MakarX on 2005-04-25
how do get the weather thingy on ur desktop

---

### Post by ubuntu-geek on 2005-04-25
[QUOTE=MakarX]how do get the weather thingy on ur desktop[/QUOTE]
 You can install gdesklets from universe and then visit [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) to get some cool addon's..

---

### Post by Ironi on 2005-04-25
gdesklets is intended for GNOME and will net a bunch of its dependencies. The KDE equivalent is superkaramba and [Liquid Weather](http://www.kde-look.org/content/show.php?content=6384).

---

### Post by Disorder2 on 2005-04-27
[QUOTE=Ironi] The KDE equivalent is superkaramba and [Liquid Weather](http://www.kde-look.org/content/show.php?content=6384).[/QUOTE]

where it says:
"IT REQUIRES SUPERKARAMBA >= v0.36."

and the latest available in the repos is 0.3.5

So I guess we'll have to live without weather for a while or install from source (which I avoid as much as I can)

---

### Post by NTolerance on 2005-04-27
[QUOTE=Disorder2]where it says:
"IT REQUIRES SUPERKARAMBA >= v0.36."

and the latest available in the repos is 0.3.5

So I guess we'll have to live without weather for a while or install from source (which I avoid as much as I can)[/QUOTE]

In the meantime you could also install kweather for your system tray or the forecastfox extension for Firefox.

---

### Post by Disorder2 on 2005-04-27
Thanks,
that one works well enough!

---

### Post by dekoi on 2005-05-19
I've actually gotten Liquid Weather to work with SK 0.35 (fr. the repos.). The only complication I've found are those "no character" boxes between every damn letter, and I've had little success in tweaking those out of the script; I'm also very open to suggestions here as I'm learning by fiddling around. ](*,)

---

### Post by Fintan on 2005-05-20
Hello out there,
Kweather works pretty good except for the font color. How can i change the font color?
I have a dark desktop and don't want change it just because of kweather.

Any ideas?

Cheers
Fintan

---

### Post by philipacamaniac on 2005-05-20
I skipped the packaged version of superkaramba altogether and downloaded the source and compiled it myself. So I have 0.36 and Liquid Weather working beautifully. (No funky symbols between letters!)

1. Download the source from [http://netdragon.sourceforge.net/ssuperkaramba.html](http://netdragon.sourceforge.net/ssuperkaramba.html)
2. ./configure
make
sudo make install

I can't remember if configure worked right away (as in no dependency problems), but I do remember that I didn't have to get anything that wasn't in the repositories. So, if configure gives you errors (missing Python 2.4 or something like that), use apt-get to install whatever is missing.

I created a deb package, but I did it with Checkinstall, so I don't know if would work on any other computer. If someone is interested in testing it, let me know.

Fintan: if you right click on the applet, you can configure all kinds of things, including the background theme and the font color.

---

### Post by Fintan on 2005-05-23
@philipacamaniac
Thanks, but if i right click on the kweather applet (which by the i did befor writing to the forum) all i get is "about kweather" and "configure kweather" Here you get besides the location display chooser the diplay options. Here you can only set which icon type you want but NOT the font color, size or anything else.
I thought there might be a text file where you can manually set color and style, size, etc.

I guess i'll just have to live with it.

Cheers 
Fintan

---

### Post by saev on 2005-05-23
[QUOTE=Disorder2]where it says:
"IT REQUIRES SUPERKARAMBA >= v0.36."

and the latest available in the repos is 0.3.5

So I guess we'll have to live without weather for a while or install from source (which I avoid as much as I can)[/QUOTE]
 you could always use the debian sid package for superkaramba 0.36 on kde-look.org, it works fine for me. 
[http://kde-look.org/content/show.php?content=23945](http://kde-look.org/content/show.php?content=23945)

---

### Post by philipacamaniac on 2005-05-23
[QUOTE=Fintan]@philipacamaniac
Thanks, but if i right click on the kweather applet (which by the i did befor writing to the forum) all i get is "about kweather" and "configure kweather" Here you get besides the location display chooser the diplay options. Here you can only set which icon type you want but NOT the font color, size or anything else.
I thought there might be a text file where you can manually set color and style, size, etc.

I guess i'll just have to live with it.

Cheers 
Fintan[/QUOTE]

When Liquid Weather is used on a correctly compiled Superkaramba 0.36, everything that is configurable shows up on the configure menu, removing the need for editing text files. It should be a menu entry like "Configure theme" (I think - I'm not on my Kubuntu right now).

I also recommend trying the Debian sid package at kde-look.org

---

### Post by Manzabar on 2005-05-23
[QUOTE=Fintan]Thanks, but if i right click on the kweather applet (which by the i did befor writing to the forum) all i get is "about kweather" and "configure kweather" Here you get besides the location display chooser the diplay options. Here you can only set which icon type you want but NOT the font color, size or anything else.
I thought there might be a text file where you can manually set color and style, size, etc.
[/QUOTE]
[KWeather](http://kweather.sourceforge.net/) is a different program than what most of this thread has been talking about. ([SuperKaramba](netdragon.sourceforge.net/) with [Liquid Weather++](http://www.kde-look.org/content/show.php?content=6384)).  I don't personally use KWeather (SuperKaramba with Liquid Weather looks much cooler) but if the only options you get when configuring it do not include the font color/size/whatever then most likely they aren't editable.  I tried looking at KWeather's website but didn't find anything useful there.

---

### Post by philipacamaniac on 2005-05-23
[QUOTE=Manzabar][KWeather](http://kweather.sourceforge.net/) is a different program than what most of this thread has been talking about. ([SuperKaramba](netdragon.sourceforge.net/) with [Liquid Weather++](http://www.kde-look.org/content/show.php?content=6384)).  I don't personally use KWeather (SuperKaramba with Liquid Weather looks much cooler) but if the only options you get when configuring it do not include the font color/size/whatever then most likely they aren't editable.  I tried looking at KWeather's website but didn't find anything useful there.[/QUOTE]

Hmm... my mistake. The thread had been referring to Liquid Weather++, so I didn't realize he was actually asking about KWeather... I prefer Superkaramba and LW++ myself.

---

### Post by Fintan on 2005-05-24
I didn't find anything in the kweather pages either.
Okay so i installed liquidweather, it does look cool but i've got the same problem as dekoi.
In the display and the config menu, well everywhere.
It looks very stange and is very difficult to read.
Plus it is only visible when all the windows are closed. Which, i mean, is rare, like at startup und shutdown.

Any suggestions to both situations, i am new to superkaramba.

Cheers and thanks for all the help.
Fintan

---

### Post by philipacamaniac on 2005-05-24
Read through this thread again. You can't use Superkaramba version 0.35 (which is the version in Universe); you have to use Superkaramba version 0.36

---

