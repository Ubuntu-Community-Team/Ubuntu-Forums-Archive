---
title: "Notify position on ubuntu 11.04?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by amanetta on 2011-05-04
Is there any way to change the position of the notifies?
I post a screenshot to explain better...

---

### Post by Krytarik on 2011-05-04
See my earlier post regarding adjusting the position of the Notify-OSD bubbles:
[http://ubuntuforums.org/showthread.php?p=10115367#post10115367](http://ubuntuforums.org/showthread.php?p=10115367#post10115367)

It refers to this article: [http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

Greetings.

---

### Post by amanetta on 2011-05-04
[QUOTE=It refers to this article: [http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)[/QUOTE]
I've tried this but it doesn't work then I tried to install the tar.gz but I realized that I'm not able to work with this file....so can u help me?:confused:

---

### Post by Krytarik on 2011-05-04
> **amanetta said:**
> I've tried this but it doesn't work then I tried to install the tar.gz but I realized that I'm not able to work with this file....so can u help me?:confused:
Place "notifyosd-bubble-position.py" into "/usr/local/bin",
and "notifyosd-bubble-position.desktop" into "/usr/share/applications".

Of course, you need root access to do so.

Then run:
```

sudo rm /usr/share/applications/desktop.*.cache
sudo sh -c "/usr/share/gnome-menus/update-gnome-menus-cache /usr/share/applications/ > /usr/share/applications/desktop.${LANG}.cache"
```

---

### Post by amanetta on 2011-05-04
ok program installed but nothing has changed: the system notifies are in the right position but the program notifies are still in the same position. I post two screenshoots.

---

### Post by Krytarik on 2011-05-04
> **amanetta said:**
> ok program installed but nothing has changed: the system notifies are in the right position but the program notifies are still in the same position.
Well, you know that you need to run the tool and modify the position to make it affect *anything*, right!?

It's name is "NotifyOSD Position" and you should find it in "<Power Button> -> System Settings -> Personal" and in the Dash of course.

---

### Post by amanetta on 2011-05-05
[QUOTE=It's name is "NotifyOSD Position" and you should find it in "<Power Button> -> System Settings -> Personal" and in the Dash of course.[/QUOTE]
done....but nothing changes even if it's settled on"top right"...look the screenshot!!

---

### Post by Krytarik on 2011-05-05
> **amanetta said:**
> done....but nothing changes even if it's settled on"top right"...look the screenshot!!
Ok, I didn't mention that you first need to install a patched version of Notify-OSD, the article I linked to.

Unfortunately, there seems to be no Natty version available as of now, but I believe you can just install the deb-package built for Maverick from Leolik's archive without any problems:
[https://launchpad.net/~leolik/+archive/leolik/+packages]("https://launchpad.net/%7Eleolik/+archive/leolik/+packages")

If it unexpectedly somehow doesn't work, just reinstall "notify-osd" from the official repos:
```
sudo apt-get install --reinstall notify-osd
```If there are unsolvable dependencies, you will be warned before anyway.

---

### Post by amanetta on 2011-05-05
[QUOTE=If it unexpectedly somehow doesn't work, just reinstall "notify-osd" from the official repos:
```
sudo apt-get install --reinstall notify-osd
```If there are unsolvable dependencies, you will be warned before anyway.[/QUOTE]
nothing...still the same position!!!...but I've two different programs!!!
look the screenshoot!

---

### Post by Krytarik on 2011-05-05
> **amanetta said:**
> nothing...still the same position!!!...but I've two different programs!!!
look the screenshoot!
Now you installed the configuration tool mentioned in the article.

Did you also install the needed patched version?

Also, you need of course to relogin!

---

### Post by amanetta on 2011-05-05
[QUOTE=Krytarik;10772184]Now you installed the configuration tool mentioned in the article.

Did you also install the needed patched version?/QUOTE]

yes I think!!!...although this stuff doesn't work...

---

### Post by Krytarik on 2011-05-05
Depending on if you have the i386 or AMD64 version of Ubuntu running, just click the respective link, a download window should pop up then, where you choose "Open with GDebi", there you will get the point then.

i386: [https://launchpad.net/~leolik/+archive/leolik/+files/notify-osd_0.9.29-0ubuntu3-leolik%7Eppa1_i386.deb](https://launchpad.net/~leolik/+archive/leolik/+files/notify-osd_0.9.29-0ubuntu3-leolik%7Eppa1_i386.deb)

AMD64: [https://launchpad.net/~leolik/+archive/leolik/+files/notify-osd_0.9.29-0ubuntu3-leolik%7Eppa1_amd64.deb](https://launchpad.net/~leolik/+archive/leolik/+files/notify-osd_0.9.29-0ubuntu3-leolik%7Eppa1_amd64.deb)

If the installation was successful, relogin and try again.

---

### Post by amanetta on 2011-05-05
[QUOTE= i386: [https://launchpad.net/~leolik/+archive/leolik/+files/notify-osd_0.9.29-0ubuntu3-leolik%7Eppa1_i386.deb]("https://launchpad.net/%7Eleolik/+archive/leolik/+files/notify-osd_0.9.29-0ubuntu3-leolik%7Eppa1_i386.deb")[/QUOTE]
this program is already installed but it seems not working!!!
look the screenshoot

---

### Post by Krytarik on 2011-05-05
Maybe I don't get what you want to achieve.

Where would you like to have the bubbles?

Also, try setting "Positioning" there to "Fixed" and press "Apply", that positions the bubbles the best at my system.

---

### Post by mc4man on 2011-05-05
Here's a natty modified notify-osd that adds a close on click option
[https://launchpad.net/~qwerty12/+archive/notifyosd](https://launchpad.net/~qwerty12/+archive/notifyosd)

amanetta - open up gconf-editor and ck. that a gravity key is there - screen show, 1 is the default upper right

---

### Post by amanetta on 2011-05-05
[QUOTE= amanetta - open up gconf-editor and ck. that a gravity key is there - screen show, 1 is the default upper right[/QUOTE]
could you explain this step by step?

---

### Post by Krytarik on 2011-05-05
@mc4man: Cool, thanks! Too bad that I can't install it in Lucid.
> **amanetta said:**
> could you explain this step by step?
Just run these commands:
```
sudo add-apt-repository ppa:qwerty12/notifyosd
sudo apt-get update
sudo apt-get upgrade
```Then relogin and try again, whatever you want to achieve.

---

### Post by amanetta on 2011-05-05
nothing....with this the notify disappears totally....
now I've uninstalled all the tool previously installed...
only the volume notify works on the top right the others work down this one...

---

### Post by Krytarik on 2011-05-05
To revert to the official repo version of "notify-osd", run:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:qwerty12/notifyosd
```

---

### Post by mc4man on 2011-05-05
> **Krytarik said:**
> ! Too bad that I can't install it in Lucid.

If inclined to build notify-osd (as debian package) then fairly sure the hack will work fine
(I modified the closeonclick patch so it applies and builds fine on the lucid notify-osd source together w/the leoliksmods patch

The qwerty12 package works fine here though I did rebuild it making the hacks enabled by default, ie. no need to add options to ~/.notify-osd
There is another modded but not hacked notify-osd for natty - linked on the qwerty12 ppa page

---

### Post by Krytarik on 2011-05-05
> **mc4man said:**
> If inclined to build notify-osd (as debian package) then fairly sure the hack will work fine
(I modified the closeonclick patch so it applies and builds fine on the lucid notify-osd source together w/the leoliksmods patch

Nah, those little mod isn't worth it for me to install all build prerequisites (again) and compile it myself.

---

### Post by amanetta on 2011-05-09
Solved!!!
;)
sudo add-apt-repository ppa:qwerty12/notifyosd
sudo apt-get update
sudo apt-get install notify-osd

---

