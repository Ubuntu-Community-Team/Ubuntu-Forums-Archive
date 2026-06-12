---
title: "How to change Double-Click speed in Lubuntu"
date: 2011-11-15
forum: Desktop Environments
---

### Post by marinara on 2011-11-15
I found I can only maximize/restore windows with a double click if I make an unusual effort to click hard.

I found how to change the double click time for window titles.

in Lubuntu
LXDE button/ Preferences/ Openbox Configuration Manager / Mouse

Change doubleclick time to 300 - 500 ms.

I haven't found how to change it for PCManFM.  The config file to do that seems to be missing on my Lubuntu.

:)

---

### Post by ac_d600 on 2011-11-16
Maybe using Synclient from the terminal??

[http://www.linuxmanpages.com/man1/synclient.1.php]("http://www.linuxmanpages.com/man1/synclient.1.php")

---

### Post by marinara on 2011-11-17
synclient is for laptop touchpads

---

### Post by stinkeye on 2011-11-17
Try [**_[COLOR="DarkRed"]THIS[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11433756&postcount=2").

---

### Post by marinara on 2011-11-17
> **stinkeye said:**
> Try [**_[COLOR="DarkRed"]THIS[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11433756&postcount=2").
That doesn't work.  I know because I just accidentally set it to 6ms and I could still double-click

---

### Post by stinkeye on 2011-11-17
Setting is a number between 100-1000.
eg
```
gconftool-2 --type int --set /desktop/gnome/peripherals/mouse/double_click 900
```

---

### Post by marinara on 2011-11-17
setting it to 100 doesn't change anything in PCManFM.

---

### Post by stinkeye on 2011-11-17
> **marinara said:**
> setting it to 100 doesn't change anything in PCManFM.
Ahhh sorry, after a bit of testing found 11.10 now uses d-conf.

eg
current setting
```
gsettings get org.gnome.settings-daemon.peripherals.mouse double-click
```


Change setting
```
gsettings set org.gnome.settings-daemon.peripherals.mouse double-click [COLOR="Red"]xxx[/COLOR]
```

---

### Post by marinara on 2011-11-17
after installing gsettings, I get an error when I read the double-click delay:
No such schema 'org.gnome.settings-daemon.peripherals.mouse'

same error if try to set the value

---

### Post by stinkeye on 2011-11-17
I can't really help you much more as I don't use Lubuntu and have no idea 
about the included packages.
Thought it was just LXDE on top.
On Ubuntu I had to install dconf-tools to get the dconf-editor package.
Don't remember installing gsettings but may have been brought in as a dependency, as I have 
**dconf-gsettings-backend** installed.

dconf-editor...

---

### Post by kudorgyozo on 2012-04-22
Hello did you find a solution for this? I am having the same problem, my double click speed is to high and my finger hurts.

Nevermind, I found it here: [http://ubuntuforums.org/showthread.php?t=1920761&highlight=double+click](http://ubuntuforums.org/showthread.php?t=1920761&highlight=double+click)

---

