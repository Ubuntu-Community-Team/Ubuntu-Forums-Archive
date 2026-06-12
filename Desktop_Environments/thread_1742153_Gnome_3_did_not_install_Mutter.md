---
title: "Gnome 3 did not install Mutter"
date: 2011-04-28
forum: Desktop Environments
---

### Post by dobstera on 2011-04-28
Or at least it looks that way ...
I'm new to Ubuntu and Linux in general, so i apologize in advance if the question is stupid.

Installed Ubuntu 11.04. First thing I did was connect to the internet and install Gnome 3 as described here: [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
```

Everything installed OK, but when I logged out and then back in with Gnome shell, this is what it looked like:
[IMG]http://img850.imageshack.us/img850/2814/screenshot1mk.png[/IMG]

Quite ugly and not at all like the slick pictures on the Gnome3 website.
I did a bit of reading and from what I understand gnome 3 uses Mutter. I installed it, but nothing changed.

So, basically I'm asking if anyone can help me make my gnome shell look as slick as it should be by default?

---

### Post by Mercury_Alpha on 2011-04-28
I suspect it has to do with your chosen theme, which appears to be different than the one used in the Gnome 3 demos. It's called Adwaita and should be available in the Appearence Preferences.

---

### Post by Krytarik on 2011-04-28
It were not even been possible to install Gnome 3 without Mutter, and it wouldn't even run at all. No, what you are missing are the standard themes, since those package isn't installed automatically as a dependency:
```
sudo apt-get purge gnome-accessibility-themes
sudo apt-get install gnome-themes-standard
```[http://ubuntuforums.org/showthread.php?t=1725221](http://ubuntuforums.org/showthread.php?t=1725221)

Greetings.

---

### Post by dobstera on 2011-04-30
> **Krytarik said:**
> It were not even been possible to install Gnome 3 without Mutter, and it wouldn't even run at all. No, what you are missing are the standard themes, since those package isn't installed automatically as a dependency:
```
sudo apt-get purge gnome-accessibility-themes
sudo apt-get install gnome-themes-standard
```[http://ubuntuforums.org/showthread.php?t=1725221](http://ubuntuforums.org/showthread.php?t=1725221)

Greetings.

Worked beautifully. Thank you.

---

